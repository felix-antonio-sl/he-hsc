# Handoff — Ola B-1 (seguridad clínica cableada en UI)

**Carril:** steipete (backend). **Fecha:** 2026-05-30.
**Branch:** `worktree-steipete+ola-b1-seguridad-clinica` (nace de `origin/master` ab0fe61).

## Resumen

La Ola B-1 buscaba activar tres palancas de seguridad clínica que la UI de Steve ya
renderiza pero hoy recibe vacías/SinDato. Al ejecutarla, **una de las tres (B-1.3)
se entregó e2e**; las otras dos (B-1.1, B-1.2) **quedaron bloqueadas por OPM MANDA**
(introducen dominio nuevo no fijado en `~/projects/hd-opm`).

## Entregado — B-1.3 · Suspensión de indicación médica (Plan CA#6)

Slice vertical completo, loop cerrado contra PG real:

| Capa | Artefacto |
|------|-----------|
| dominio | `suspendIndication` (valid→suspended), espejo de `fulfillIndication`; `IndicationNotSuspendable` añadido al coproducto `DomainErrorCode` |
| aplicación | `SuspendMedicalIndication` (guard+audit allowed/denied/failed, barrera de pertenencia al episodio, emite `MedicalIndicationSuspended`) |
| API | `POST /episodios/:episodeId/indicaciones/:indicacionId/suspension` |
| persistencia | sin migración nueva: `PgMedicalIndicationRepository.save` (UPSERT) absorbe el estado |

**Contrato publicado para Steve-web-ux:**

```
POST /episodios/:episodeId/indicaciones/:indicacionId/suspension
  (sin body)
  200 → MedicalIndicationDto { id, episode, description, state: "suspended" }
  403 → { error }  acceso denegado (es-CL)
  422 → { error }  indicación no vigente (es-CL, sin filtrar code)
  404 → { error }  indicación no encontrada / no corresponde al episodio (es-CL)
```

El estado `"suspended"` ya se renderiza en `plan.tsx` (INDICATION_STATE_LABEL).
Antes solo aparecía vía seed estático; ahora el endpoint lo activa real. La UI con
confirmación irreversible puede cablear este POST directamente.

**Tests:** 4 dominio + 7 caso de uso + 4 e2e Testcontainers (read-after-write,
pertenencia cruzada, 422 cumplida, 404 inexistente). Commit `307e13d`.

## Bloqueado por OPM — B-1.1 (safetyFlags en censo) y B-1.2 (alergias en plan)

Ambas exigen un modelo de dominio **inexistente**: alergia y condición de seguridad
clínica (p. ej. anticoagulación) como hechos clínicos del paciente/episodio. No están
en `dominio/` ni en el modelo OPM de `hd-opm` (verificado: no hay tabla `allergy`,
no hay agregado de banderas).

Por el principio no negociable **OPM MANDA**, no se modelan sin fijarlas primero en
`~/projects/hd-opm`. Mismo estatus que la Ola 3 (derivador).

**Desbloqueo:** fijar en hd-opm la entidad/atributo de seguridad clínica (alergia +
condición de seguridad, con su anclaje a Paciente/Episodio y su proyección al censo
y al plan). Hecho eso, el patrón backend es directo:

- una tabla `clinical_safety_flag` (append-only, ancla `patient_id`, RLS por establecimiento);
- proyección a `CensusDto.safetyFlags: string[]` (etiquetas es-CL) y a
  `EpisodePlanDto.allergies: { substance, severity? }[]`;
- si no hay registro → `[]` honesto (ausente≠normal).

**Nota de contrato:** `CensusDto` y `EpisodePlanDto` viven en `interfaces/web/src/api/client.ts`
(zona de Steve). Cuando se desbloquee, el backend devolverá los campos nuevos y Steve
los agrega al DTO + los pasa a `PatientBand.banderasCriticas` / vista de plan.

## Frentes NO bloqueados por OPM (candidatos al siguiente loop)

- **B-3.4** `GET /episodios/:id/accesos` — proyección de `audit_event` por episodio
  (la UI muestra SinDato hoy; `/portal` ya proyecta accesos globales del tenant).
- **B-3.5** auth real por handler — cablear `req.actor` de sesión (cookie `hd_session`,
  middleware ya existe) en vez de `PG_ACTOR_*`. Cierra deuda transversal Fase 3.
- **B-4** catálogos para pickers — GET establecimientos/bodegas/productos/autorizaciones/
  despachos; vuelve los identificadores-a-mano en selectores.
- **Eje B** migración de VISITAS (~7.681) — `care_execution`/`visita` ya modelados;
  falta transform Φ_mig + extender extract + tests RED contra dato real-like.

## Paso 1 OPM — estado (modelado de la fuente de B-1.1/B-1.2)

El desbloqueo de B-1.1/B-1.2 pasa por fijar el dominio en `~/projects/hd-opm` (OPM MANDA).
Avance:

- **Forma decidida por el operador:** opción B — objeto paraguas `Condición de seguridad
  clínica` exhibido por `Paciente`, unfold en `{Alergia, Contraindicación, Precaución}`.
- **Anclaje:** operacional nivel 2 (`hsc` captura alergias real); no normativo → descriptivo.
- **Propuesta (delta) commiteada en hd-opm:** `1e2f77a`
  `docs/propuesta-condicion-seguridad-clinica-2026-05-30.md`.
- **Pendiente:** plasmar R20 en opforja **sobre v1.2** (hay un v1.2 paralelo en curso en
  hd-opm, ajeno) → exportar JSON → versionar `models/`+`opl/`+glosario. Recién ahí se
  desbloquea el paso 2 (backend).

## Supuestos declarados

1. **`Alergia` sin ciclo de estado** (opción a): un registro está vigente; corregir = nuevo
   registro. Fiel a cómo `hsc` lo guarda; reversible a estados `{activa, inactiva}` (b) si se
   requiere desactivación auditada.
2. **`Condición de seguridad clínica` sin estado propio**: es agrupador estructural; el nivel
   de riesgo del censo se *proyecta* de las partes, no se almacena.
3. **B-1.3 atribuye al actor simulado** `PG_ACTOR_CLINICO` (ADR 0012); la atribución al actor
   real de sesión es B-3.5 (auth por handler), aún pendiente.

## Riesgos

- **Colisión OPM (medio):** v1.2 del modelo se está plasmando en paralelo en hd-opm. La
  propuesta R20 debe plasmarse SOBRE v1.2, no v1.1. No tocar el v1.2 ajeno (untracked en hd-opm).
- **Merge a master (bajo):** otra sesión tiene untracked en master (`segunda-pasada.test.ts`,
  `handoff-diagnostico-opm`), disjuntos de mi backend. El merge no los toca, pero hay actividad
  concurrente: el push debe ser controlado (rebase + ff, sin merge commit de ruido).
- **Contrato pendiente de Steve:** `safetyFlags`/`allergies` aún no existen en `CensusDto`/
  `EpisodePlanDto` (zona de Steve). Cuando B-1.1/B-1.2 se materialicen, Steve añade los campos
  al DTO. B-1.3 ya es consumible sin cambios de contrato (usa `MedicalIndicationDto` existente).

## Estado de integración

- B-1.3 (código + handoff) → integrado a master vía rebase + fast-forward (sin merge commit).
- Gate: suite completa verde antes del push.
- B-1.1/B-1.2: bloqueados hasta plasmar R20. B-2/B-3/B-4 y Eje B (migración visitas): disponibles.
