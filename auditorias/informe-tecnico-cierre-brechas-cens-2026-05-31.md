# Informe Técnico — Cierre de brechas de certificación CENS

Para: equipo de desarrollo (backend, frontend, datos)
Fecha: 2026-05-31
Origen: traducción a ingeniería del veredicto de `cens-certificacion-virtual.md` (remediado) y `auditoria-cens-certificacion-virtual-2026-05-30.md`
Método: estado verificado contra el código (3 exploraciones dirigidas + verificación de paths). Cada path citado existe; "no existe" cuando aplica.

## Cómo leer esto

El veredicto CENS, en una frase de ingeniería: **ningún sello es otorgable hoy porque el gate de Seguridad reprueba (Software 57.1%, RCE 62.5%) y la interoperabilidad está sin implementar**. Los tres sellos dependen del mismo núcleo. Este informe descompone ese núcleo en trabajo concreto, marca para cada ítem **si toca el dominio (→ OPM MANDA, se modela primero en `hd-opm`) o es realización técnica pura (arrancable ya)**, y da el patrón de implementación con paths reales.

Convención por brecha: **Estado real** · **Qué falta** · **¿Toca OPM?** · **Archivos** · **Criterio de aceptación (tests)** · **Esfuerzo**.

---

## 1. Tabla maestra — estado real por brecha

| Brecha | Diseñado | Implementado | ¿Toca OPM? | Palanca | Esfuerzo |
|---|---|---|---|---|---|
| **B3 RBAC productivo** (gate) | ADR 0016 completo | **~80%** (tablas `auth.*`, `PgIdentityService`, middleware, `/auth/login`) | No (seguridad técnica) | Desbloquea gate de 2 sellos | 2 sprints |
| **B4 Auditoría / no repudio** (gate) | F6 append-only (ADR 0005) | **~70%** (`audit_event` INSERT-only + RLS + 0068) | No | Refuerza gate | 1 sprint |
| **KMS / cifrado en reposo** (gate) | Contrato §S5 (diferido) | **0%** (sin ADR) | No (infra) | Parte del gate de confidencialidad | 1-2 sprints + decisión |
| **A1 Consentimiento digital** | Modelo de datos + puerto | **0%** en código | **Sí — verificar en hd-opm** | Bloquea Telemedicina + RCE | 2-3 sprints |
| **A2 Adaptador FHIR** | Contrato + 3 puertos | **0%** (cero archivos `.ts`) | No (borde externo, dominio limpio) | Bloquea Telemedicina + Interop + Compatibilidad | 3-4 sprints |
| **A3 Identidad / MPI** | ADR 0003 + contrato | **Base sí** (UUID v7 + `source_identifier`), **matching/merge no** | **Sí — merge es proceso** | Bloquea Telemedicina + Interop | 2-3 sprints |
| **A4 Firma electrónica avanzada** | Mencionado como diferido | **0%** | **Sí — acto de firmar** | Bloquea gate Software + RCE | 2 sprints (o diferir V2) |
| **B1 WCAG 2.1 AA** | — | parcial (86 `aria-`) | No | Sube Usabilidad | 1 sprint |
| **B2 RTO/RPO** | — | doc parcial | No (institucional) | Sube Fiabilidad | 1 sprint |
| **B5 CENS Pharma** | — | catálogo sin binding | No | Documental | 1 día |
| **B6 T&C interoperabilidad** | — | no | No (acto admin HSC) | Documental | 1 día |

**Conclusión operativa:** la mayor palanca es el **gate de seguridad (B3+B4+KMS)** — reprueba 2 de 3 sellos y es **realización técnica pura (no pasa por OPM)**, así que es arrancable de inmediato. **A2 FHIR** también es técnico puro. **A1/A3/A4 tocan dominio** y pasan primero por `hd-opm`.

---

## 2. Corrección al eval: el RBAC está más avanzado de lo reportado

El eval (y la auditoría) hablaban de "matriz de acceso = puerto fake en P0". **La realidad verificada es mejor:** existe infraestructura de identidad real, no un stub. Esto reduce el esfuerzo del gate.

Lo que **ya existe** (verificado):
- Esquema `auth` con 4 tablas: `auth.identity` (Argon2id, MFA TOTP opcional), `auth.identity_role`, `auth.session` (token opaco, TTL ≤8h, revocación), `auth.policy` (role×action×object→allow/deny, **default deny**). Migraciones `0062`–`0066`.
- `adaptadores/auth/identidad-pg.ts` — `PgIdentityService`: `login()` con verificación Argon2id, `resolveSession()`, `revokeSession()`, `createIdentity()`. Es el "funtor α: Identidad → ActorContext" del ADR 0016.
- `interfaces/api/middleware/identidad.ts` — `registerIdentityMiddleware`: lee cookie httpOnly `hd_session`, resuelve a `req.actor`.
- `POST /auth/login` en `interfaces/api/server.ts`.

Lo que **falta** para cerrar el gate de RBAC (ver §3.1).

---

## 3. Gate de Seguridad — la mayor palanca (arrancable ya, no toca OPM)

### 3.1 — B3: RBAC productivo

**Estado real.** Identidad y sesión productivas; **autorización NO se aplica**. El único `AccessControlPort` con backing real es `PgAllowAllMaterialesAccessControl` (`adaptadores/postgres/soporte-pg.ts:971`) — un *allow-all*. La tabla `auth.policy` existe pero **ningún adaptador la consulta**. `server.ts` inyecta actores simulados `PG_ACTOR_*` en **54 puntos**, no `req.actor`.

**Qué falta:**
1. `PgPolicyAccessControl implements AccessControlPort` que lea `auth.policy` (con cache + TTL) y devuelva `allowed|denied` (default deny). Engancha en `adaptadores/postgres/soporte-pg.ts` (junto a los `*AccessControl` existentes).
2. Reemplazar, en `interfaces/api/server.ts` y `pg-execution.ts`, los `PG_ACTOR_*` simulados por `req.actor` (obligatorio no-null en endpoints de escritura). Hoy el middleware está instalado pero **no es enforcing**.
3. Endpoints faltantes: `POST /auth/logout`, `GET /auth/yo`, `POST /auth/login/mfa`.
4. Seed de `auth.policy` con reglas reales por rol (medico, coordinador, admin, soporte) × acción × objeto.

**¿Toca OPM?** No — es realización de seguridad (ADR 0016 ya lo fija). El `Purpose` y el `ActorContext` ya están en `aplicacion/{slice}/contexto.ts`.

**Archivos:** `adaptadores/postgres/soporte-pg.ts` (nuevo `PgPolicyAccessControl`) · `interfaces/api/server.ts` + `pg-execution.ts` (enforcement) · nueva migración `0069-auth-policy-seed.sql` o seed de fixtures · `adaptadores/memoria/seguridad.ts` (ya tiene `PolicyAccessControl` para tests).

**Criterio de aceptación:**
- Test PG-e2e: endpoint de escritura con `req.actor` cuyo rol **no** tiene fila `allow` en `auth.policy` → **403** y `audit_event.result='denied'`, sin efecto de dominio.
- Test: misma acción con rol autorizado → 200 + `audit_event.result='allowed'`.
- Test: ausencia de fila en `auth.policy` → denegado (default deny).

### 3.2 — B4: Auditoría / no repudio

**Estado real (verificado).** `audit_event` es **INSERT-only** real (`adaptadores/postgres/seguridad-pg.ts`, `PgSecurityAuditPort.record()`), con RLS por `establishment_id` y **REVOKE UPDATE/DELETE físico** en `migrations/0068-append-only-revoke.sql`. Cada caso de uso de escritura emite el evento antes del efecto (guard). El `actor_ref` es `session:<id>` (no expone identity_id).

**Qué falta:**
1. **Sello lógico encadenado:** la columna `sello_logico` existe en `audit_event` (migración 0009) pero **siempre es null**. Implementar `hash(fila_previa + evento_actual)` en cada INSERT + validación de cadena en lectura. Esto es lo que convierte "append-only" en "resistente a manipulación" (no repudio fuerte).
2. **`correlation_id`:** columna existe, nunca se genera. Generarlo por transacción para correlacionar eventos entre slices.
3. **audit_log por episodio (Pasado CA#10):** el componente UI `interfaces/web/src/componentes/audit-access-panel.tsx` existe pero **no está conectado a datos reales**. Falta el endpoint de lectura (`GET /episodios/:id/accesos`) y su proyección desde `audit_event`.

**¿Toca OPM?** No — realización técnica de la propiedad de integridad (D ya modelada).

**Archivos:** `adaptadores/postgres/seguridad-pg.ts` (sello + correlation) · `interfaces/api/server.ts` (endpoint lectura) · `interfaces/web/src/componentes/audit-access-panel.tsx` (cablear).

**Criterio de aceptación:**
- Test: insertar N eventos → recomputar la cadena de `sello_logico` valida; alterar un evento intermedio → la validación de cadena falla.
- Test web: `audit-access-panel` muestra accesos reales de un episodio (no stub).

### 3.3 — KMS / cifrado en reposo

**Estado real.** **No existe.** Ningún ADR menciona KMS/cifrado en reposo. `password_hash` usa Argon2id (correcto, pero es hash, no cifrado reversible). PII de paciente/domicilio/diagnósticos en PostgreSQL está en claro. IndexedDB de la PWA sin cifrar (ADR 0013 lo deja abierto). Contrato §S5 lo lista como diferido.

**Qué falta (decisión primero, luego implementación):**
1. **ADR nuevo (0017) de política de secretos + KMS:** dónde viven credenciales/keys (env vs vault vs secret operator), rotación, auditoría de acceso. Decidir KMS (Vault / cloud KMS / infra HSC).
2. **Inventario de columnas sensibles a cifrar:** PII paciente, domicilio/geolocalización (riesgo físico), diagnósticos/medicación. (No `password_hash`.)
3. **Implementación:** app-side encryption (libsodium/Tink) o `pgcrypto`; reencriptación de datos migrados; respaldos cifrados (`pg_dump` + AES).
4. **PWA:** IndexedDB cifrada + purga segura al logout.

**¿Toca OPM?** No — infraestructura.

**Nota:** este ítem no estaba como brecha B numerada en el eval; surge del análisis del gate de Confidencialidad (6.1). Agregarlo al Bloque B.

---

## 4. Bloque A — bloqueantes de sello

### 4.1 — A2: Adaptador FHIR (recomendado arrancar primero del Bloque A: no toca OPM)

**Estado real.** Diseño completo, **cero código**. El contrato `docs/02-datos/contrato-interoperabilidad-salud.md` mapea 20 recursos FHIR (Patient, Encounter, ServiceRequest, CarePlan, Condition, Observation, DocumentReference, Consent, AuditEvent, Provenance, …) y fija terminologías (SNOMED CT, CIE-10, LOINC, SNRE, Core CL/NID). Los 3 puertos están especificados en prosa en `docs/05-especificaciones/puertos/interoperabilidad-salud.md` (`HealthInteroperabilityPort`, `PatientIdentityPort`, `TerminologyPort`) pero **no existen como tipos TypeScript** ni hay directorio `adaptadores/fhir/`. Base existente reutilizable: `source_identifier` (migración `0002`).

**Qué falta:**
1. Declarar los 3 puertos como TS en `aplicacion/interoperabilidad/puertos.ts` (transcribir métodos del `.md`: `receiveReferral`, `exportEpisodeSummary`, `exportPatientPortableRecord`, `publishClinicalDocument`, `validateResource`).
2. Adaptador `adaptadores/fhir/` con mappers dominio→FHIR (empezar por el slice mínimo Telemedicina: **Patient, Encounter, ServiceRequest, Consent**).
3. Validación contra perfil Core CL v1.9.4 (fijar versión exacta en ADR antes).
4. Tests de **no filtración de datos sensibles** (gate del contrato).

**¿Toca OPM?** **No.** El contrato es explícito: "dominio no contaminado por FHIR; FHIR es borde externo". Es realización en `adaptadores/` + `interfaces/`. Por eso es el bloqueante más barato de iniciar.

**Criterio de aceptación:** un `Patient` + `Encounter` + `ServiceRequest` generados desde el dominio validan contra el perfil Core CL; test de no-filtración pasa; `exportPatientPortableRecord` produce un Bundle FHIR (cierra también Portal CA#8).

### 4.2 — A1: Consentimiento informado digital

**Estado real.** Diseñado en `docs/02-datos/modelo-datos-hd-hsc-os.md` (≈líneas 338-348) **como faceta documental, no entidad nueva**: `informed_consent` es un tipo de `episode_document` (estados pending→granted) compuesto con `document_signature` + `document_attachment`. **No existe** tabla/migración de consentimiento ni dominio/puerto/adaptador. La base documental sí existe (`episode_document` en migración `0008`).

**Qué falta:**
1. Realizar el estado `pending→granted` (hoy es "meta del proceso", no columna persistida) y el proceso otorgar/revocar.
2. Migración nueva (`0069+`) si se decide tabla dedicada, o extender `episode_document`.
3. Puerto + caso de uso (otorgar, revocar, consultar vigencia) + adaptadores memoria/PG, siguiendo el patrón de slice (§5).
4. Conexión con teleatención (gate C4 de Telemedicina) y con `exportPatientPortableRecord` (Portal CA#8).

**¿Toca OPM? SÍ — verificar primero en `hd-opm`.** El objeto Consentimiento y su proceso (otorgar/revocar, con vigencia y revocación) deben estar fijados en el modelo OPM antes de implementar. Si el modelo no tiene el proceso de consentimiento de teleatención como tal, **se modela en `hd-opm` primero** (regla OPM MANDA — no "avanzar + marcar deuda").

**Criterio de aceptación:** caso de uso de teleatención exige consentimiento `granted` vigente (sin él → bloqueo con ActionGuard); revocación deja traza en `audit_event`; el consentimiento viaja en el Bundle de portabilidad.

### 4.3 — A3: Identidad / MPI

**Estado real.** Cimientos implementados: UUID v7 como PK (`gen_uuid_v7()`, migración `0001`; ADR 0003) y `source_identifier` (migración `0002`, con dedup en `0067`) para identidades externas (RUN/SGH/FHIR) sin usar RUN como PK. **Matching probabilístico y merge auditable: no existen.** `PatientIdentityPort` está diseñado (`resolvePatientIdentity`, `linkExternalIdentifier`, `recordMergeDecision`) pero no como código.

**Qué falta:**
1. `PatientIdentityPort` en TS + servicio de matching (exacto por `source_identifier`, luego probabilístico con gate de revisión humana — "nunca promociona sin gate").
2. Tablas: `patient_merge_audit`, eventual `patient_identity_block` (identidad en cuarentena).
3. Integración PIXm/PDQm con MPI nacional (cuando MINSAL lo exponga) — **distinguir de Clave Única** (autenticación, no MPI).

**¿Toca OPM? SÍ — el merge de paciente es un proceso** (y puede introducir un estado "identidad en cuarentena"). Verificar/modelar en `hd-opm` antes de implementar el merge.

**Criterio de aceptación:** match exacto por RUN; caso ambiguo devuelve candidatos con confianza (no auto-promueve); merge exige evidencia y deja `patient_merge_audit` + `audit_event`; merge a paciente con episodio activo → rechazado.

### 4.4 — A4: Firma electrónica avanzada

**Estado real.** **No existe nada.** Sin `document_signature`, sin paso "Firmar", sin integración HSM/certificado. "Epicrisis firmada" en la migración legacy es solo texto heredado, no firma criptográfica.

**Qué falta:** ADR nuevo (firma legal HSC, Ley 19.799) · tabla `document_signature` · `DigitalSignaturePort` + adaptador (proveedor acreditado / sello de tiempo) · paso "Firmar" en cierre.

**¿Toca OPM? SÍ — firmar es un acto/proceso** sobre el documento (estado "firmado").

**Recomendación:** **diferir a V2 con ADR explícito.** Es el bloqueante más caro y el de menor frecuencia de uso para el MVP; documentarlo como diferido honesto (no inflar) mientras se cierran B3/B4/A2/A1, que destraban más sello por unidad de esfuerzo.

---

## 5. Patrón canónico de slice (referencia para todo lo anterior)

Cualquier brecha que toque dominio se construye con el mismo esqueleto de 7 pasos (verificado contra el slice reciente de suspensión de indicación, B-1.3). **Última migración: `0068`; la próxima es `0069`.**

| Paso | Path | Qué va |
|---|---|---|
| 1. Dominio | `dominio/{slice}/{ids,errors,entity,events}.ts` | Entidad `readonly` + transiciones puras que validan invariantes y lanzan `DomainError` |
| 2. Puertos | `aplicacion/{slice}/puertos.ts` + `contexto.ts` | Interfaces de repositorio + soporte (`ClockPort`, `AccessControlPort`, `SecurityAuditPort`, `DomainEventSink`); `ActorContext`/`Purpose` |
| 3. Caso de uso | `aplicacion/{slice}/{caso}.ts` | Clase con `execute(input)`: **guard de acceso ANTES del efecto**, carga, transición de dominio, emit evento, audita allowed/denied/failed |
| 4a. Fake | `adaptadores/memoria/repositorios*.ts` + `seguridad.ts` | `InMemory*Repository`, `FakeClock`, `PolicyAccessControl`, `InMemoryAuditLog` |
| 4b. PG | `adaptadores/postgres/repositorios-{slice}-pg.ts` + `soporte-pg.ts` | `Pg*Repository` con Kysely + `withTenant` (RLS por `establishment_id`); UPSERT `.onConflict()` |
| 5. Migración | `adaptadores/postgres/migrations/0069-*.sql` | Tabla + índices + CHECK + `ENABLE ROW LEVEL SECURITY` + policy; DAG en comentario |
| 6. Interfaces | `interfaces/api/server.ts` + `pg-execution.ts` + `build-backend.ts` | Endpoint Fastify → parse input → ejecuta (PG o memoria) → traduce `DomainError`→422 / `AccessDenied`→403 → DTO |
| 7. Tests | `tests/{slice}/*.test.ts` + `tests/api/*-pg.test.ts` | Dominio unitario · aplicación con fake · PG-e2e Testcontainers (read-after-write) · API e2e · componente web |

Invariantes no negociables del patrón: **guard antes del efecto**, **audita siempre**, `audit_event` nunca UPDATE/DELETE, RLS por tenant, no exponer `DomainErrorCode` interno en el HTTP body.

---

## 6. Secuenciación recomendada

```
ARRANCABLE YA (técnico puro, no pasa por OPM):
  Ola 1 — GATE DE SEGURIDAD (destraba 2 de 3 sellos)
    B3 RBAC productivo (PgPolicyAccessControl + enforcement req.actor + seed policy)
    B4 sello lógico encadenado + correlation_id + audit-access-panel conectado
    KMS: ADR 0017 (decisión) → cifrado de columnas sensibles + respaldos
  Ola 2 — INTEROPERABILIDAD
    A2 puertos TS + adaptador FHIR (Patient/Encounter/ServiceRequest/Consent) + validación Core CL
    (cierra de paso Portal CA#8 portabilidad)

PASA POR hd-opm PRIMERO (toca dominio):
  A1 Consentimiento — modelar proceso otorgar/revocar de teleatención en OPM → implementar slice
  A3 Identidad/MPI — modelar proceso de merge/cuarentena en OPM → matching + merge auditable
  A4 Firma — DIFERIR a V2 con ADR (acto de firmar)

DOCUMENTAL / INSTITUCIONAL (paralelo, bajo costo):
  B1 WCAG AA · B2 RTO/RPO · B5 CENS Pharma · B6 T&C interop
```

Racional: el gate de seguridad reprueba Software y RCE y es lo más barato de cerrar (B3 está al 80%). A2 destraba Telemedicina + Interop + sube Compatibilidad de Software. A1/A3/A4 quedan detrás de OPM por diseño del proyecto.

---

## 7. Reglas operativas para quien tome esto

- **OPM MANDA es techo.** A1, A3 y A4 tocan dominio/estado/proceso nuevo: se fijan en `hd-opm` **antes** de tocar `dominio/`. No vale "implementar + marcar deuda". B3, B4, KMS y A2 son realización técnica y no requieren paso por OPM.
- **No inventar.** La auditoría que originó este informe encontró 7/9 endpoints inventados en otro documento. Todo path aquí está verificado; al implementar, calcar el patrón de un slice existente, no asumir nombres.
- **Repo multi-agente.** Conviven carriles paralelos (steipete backend, Steve-web-ux frontend, Hermes). Commit por ruta explícita, **nunca `git add -A`**; la frontera frontend↔backend es el contrato de API.
- **Seguridad es gate, no promedio.** El criterio que este informe persigue es cerrar el gate, no subir el promedio. No reportar "cumple" mientras Seguridad esté bajo umbral.

---

## 8. Artefactos relacionados

- `cens-certificacion-virtual.md` — evaluación remediada (veredicto + §9 changelog).
- `auditoria-cens-certificacion-virtual-2026-05-30.md` — auditoría que originó la remediación.
- `handoff-cens-certificacion-2026-05-30.md` — handoff de la evaluación.
- ADRs: `0003-identidad-fisica.md`, `0005`, `0007` (RLS), `0016-identidad-auth-rbac.md`.
- Contratos: `docs/02-datos/contrato-interoperabilidad-salud.md`, `docs/02-datos/contrato-seguridad-informacion-salud.md`.
- Puertos: `docs/05-especificaciones/puertos/interoperabilidad-salud.md`.
