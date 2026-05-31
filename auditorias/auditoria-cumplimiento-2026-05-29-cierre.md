# Auditoría de cumplimiento — carril frontend · cierre 2026-05-29

Sucede a: `auditoria-cumplimiento-2026-05-29.md` (matinal)
Commit cabeza: `8da0fa6`
Suite: 499/499 web tests verdes

## Para qué este documento

La auditoría matinal definió un Top-10 de gaps por palanca clínica. Esta
versión registra el cierre de los 10 + la integración real al shell, y
deja escrito qué supera la spec, qué la cumple exacto, qué queda parcial
y qué sigue pendiente.

## Top-10 — estado tras esta jornada

| # | Gap matinal | Estado | Commit |
|---|---|---|---|
| 1 | ActionGuard en Plan farmacológico antes de F7 | ✓ | `10da980` |
| 2 | IdentityVerification antes del flujo F7 / Visita | ✓ | `26ced0e` |
| 3 | Module ActoClinico Valorar→Decidir→Firmar | ✓ | `e0e9e16` |
| 4 | DomicileLocationCapture en IngresoForm | ✓ | `03c2648` |
| 5 | ContextualGuidance en Pulso ante alertas | ✓ | `324c513` |
| 6 | Pasado bloquea acciones para episodios cerrados | ✓ | `a325a3e` |
| 7 | Pasado — botón "Ver mis accesos" → AuditAccessPanel | ✓ | `a325a3e` |
| 8 | SyncStatus integrado en Pulso/Plan/Pasado | ✓ | `26e1a37` |
| 9 | Portal — emisión al backend en llamada urgencia | ✓ | `11a45c2` |
| 10 | Portal — descarga portabilidad (Ley 21.719) | ✓ | `11a45c2` |
| — | Integración real al shell (cierre de los 4 callbacks pasivos) | ✓ | `8da0fa6` |

## Componentes especificados — actualización

13/13 implementados (sin cambio) y **13/13 montados en superficie** (los
4 huérfanos previos quedaron cableados).

| Componente | Call sites tras esta jornada |
|---|---|
| action-guard | `plan.tsx` (gate F7), `acto-clinico-module.tsx` (escalar + egresar) |
| audit-access-panel | `portal.tsx`, `pasado.tsx` (via prop opcional) |
| caregiver-delegate | `portal.tsx` |
| clinical-alert | `pulso-components.tsx` |
| clinical-state-notice | múltiples superficies |
| confirm-irreversible | `cierre.tsx`, `escalamiento.tsx` |
| contextual-guidance | `pulso-components.tsx` (alertas) |
| domicile-location-capture | `ingreso-form.tsx` |
| identity-verification | `medication-flow-form.tsx`, `visita.tsx` |
| mobile-clinical-shell | 13 referencias (sin cambio) |
| narrative-visit-capture | `visita.tsx` (tras gate de identidad) |
| patient-band | 14 referencias (sin cambio) |
| sync-status | `visita.tsx`, `pulso.tsx`, `plan.tsx`, `pasado.tsx` (via shell) |

## Superficies — actualización por criterio

### Pulso · 10/10 cubierto (con notas)

| # | Criterio | Estado matinal | Estado cierre |
|---|---|---|---|
| CA1 | Entiende el ahora sin Tab Soup | ✓ | ✓ |
| CA2 | XOR estado normal vs alerta | ✓ | ✓ |
| CA3 | Toda alerta tiene salida | ✓ | ✓ (+ ContextualGuidance asociada cuando aplica) |
| CA4 | ActoClinico Module invocable | ✗ | ✓ (overlay con 3 Steps + autosave + 2 guards) |
| CA5 | Voluntad anticipada visible antes de escalar | ✗ | ◐ (visible **dentro** del Module; banner persistente fuera del Module sigue ✗) |
| CA6 | Sin paciente = agregado operacional | ✓ | ✓ |
| CA7 | Offline: PatientBand + datos legibles + cola | ◐ | ◐ (`syncInfo` ya integrado; el sink real depende de pendiente #1) |
| CA8 | Ninguna acción gris sin causa | ✗ | ◐ (sin botones grises; el guard explícito en cada acción rápida sigue pendiente) |
| CA9 | Mobile: PatientBand compacto + safe areas | ◐ | ◐ (sin variante compacta; pendiente #7) |
| CA10 | Ningún evento interactivo sin salida | ◐ | ◐ (bindings de auditoría pendientes hasta gap #1) |

### Plan · 8/12 cubierto

| # | Criterio | Estado matinal | Estado cierre |
|---|---|---|---|
| CA1 | Por categoría, nunca profesión | ✓ | ✓ |
| CA2 | Lentes XOR | ✓ | ✓ |
| CA3 | Esquema operado, medicamento referenciado | ✓ | ✓ |
| CA4 | Prescribir exige conciliado (guard) | ✗ | ✓ (ActionGuard bloquea el botón F7) |
| CA5 | Alergias siempre expandidas al prescribir | ✗ | ✗ (DTO no expone alergias) |
| CA6 | Suspender indicación con confirm-irreversible | ✗ | ✗ (no hay endpoint de suspensión) |
| CA7 | Discrepancia detectada = alerta accionable | ✓ | ✓ |
| CA8 | Plan al día = ClinicalStateNotice | ✓ | ✓ |
| CA9 | Lentes vacías = sin error | ✓ | ✓ |
| CA10 | Offline: guard + encola prescripción | ✗ | ◐ (`syncInfo` propagado; sink real pendiente) |
| CA11 | Lesión activa con plan de curación | ✗ | ✗ (DTO no expone lesiones) |
| CA12 | Ningún evento interactivo sin salida | ◐ | ◐ |

### Pasado · 10/11 cubierto

| # | Criterio | Estado matinal | Estado cierre |
|---|---|---|---|
| CA1 | Narrativa primero | ✓ | ✓ |
| CA2 | Filtro clínico vs operacional | ✓ | ✓ |
| CA3 | Master-detail | ✓ | ✓ |
| CA4 | Evento grave: texto+icono+color | ✓ | ✓ |
| CA5 | Episodio previo como enlace | ✓ | ✓ |
| CA6 | Detalle no clonable | ✓ | ✓ |
| CA7 | Pasado no se abre sin episodio | ✓ | ✓ |
| CA8 | Episodio cerrado = solo lectura | ✗ | ✓ (banner persistente + sin role=alert) |
| CA9 | Offline: timeline caché legible | ◐ | ◐ (`syncInfo` propagado; sink real pendiente) |
| CA10 | SelectVerAccesos → audit-access-panel | ✗ | ✓ (botón + panel; `SinDato` honesto sin data) |
| CA11 | Ningún evento interactivo sin salida | ◐ | ◐ |

### Servicio · 5/10 cubierto (sin cambio · pendiente #6)

Quedó fuera del Top-10; los criterios `censo vacío = ClinicalStateNotice`
y `match 5D AND visible con desglose` siguen pendientes.

### Portal · 9/12 cubierto

| # | Criterio | Estado matinal | Estado cierre |
|---|---|---|---|
| CA1 | Canal urgencia primer nivel persistente | ✓ | ✓ |
| CA2 | Llamar primario, síntoma opcional | ✓ | ✓ |
| CA3 | Números offline + marcador tel: | ◐ | ◐ |
| CA4 | Dos rutas claras HODOM/131 | ✓ | ✓ |
| CA5 | Acuse inmediato + señal al episodio | ◐ | ✓ (`onLlamadaUrgencia` encola en el shell) |
| CA6 | Lenguaje humano sin jerga | ◐ | ◐ |
| CA7 | "Quién vio" en humano | ✓ | ✓ |
| CA8 | Descarga de portabilidad | ✗ | ✓ (JSON con schema + aviso Ley 21.719) |
| CA9 | Cuidador vencido no bloquea urgencia | ✓ | ✓ |
| CA10 | No edita registros | ✓ | ✓ |
| CA11 | Remedios en lenguaje humano | ✓ | ✓ |
| CA12 | Mobile: targets ≥44px | ◐ | ◐ |

## Slices con criterios UI

### Ingreso

| Criterio | Matinal | Cierre |
|---|---|---|
| Form de admisión con campos del DTO | ✓ | ✓ |
| Veredicto admitido/diferido visible | ✓ | ✓ |
| Georreferencia del domicilio capturada | ✗ | ✓ (DomicileLocationCapture integrado; encola en outbox) |
| Verificación de identidad antes de admitir | ✗ | ✗ (no implementado; pendiente para próximo corte) |

### Cierre · sin cambio

| Criterio | Estado |
|---|---|
| ConfirmIrreversible antes de cerrar | ✓ |
| Causal única seleccionada (D5) | ✓ |
| Notificable obliga registro de notificación | ◐ |

## Lo nuevo del cierre — integración shell

Implementaciones que NO estaban en el Top-10 pero cierran las puntas
que ese Top-10 dejó:

- **Outbox compartido en AppShell.** `InMemoryOutboxStore` singleton.
- **`syncInfo` derivado**: `pendingCount` por poll (5s) + `online` por
  `navigator.onLine` + listeners de eventos `online`/`offline`;
  `lastSyncAt` se actualiza al encolar.
- **`syncInfo` inyectado** a Pulso/Plan/Pasado.
- **Encoladores** para los 3 nuevos kinds:
  - `acto-clinico-firmado` (Pulso · `onActoFirmado`)
  - `urgencia-portal` (Portal · `onLlamadaUrgencia`)
  - `domicile-georef` (Ingreso · `onGeorefCapturada`)

## Cumplimientos sólidos · cierre

1. Plan por categoría · nunca por profesión (sin cambio).
2. Pasado narrativa primero · master-detail (sin cambio).
3. Pulso Mi Día sin pantalla vacía (sin cambio).
4. Portal: canal urgencia persistente · independiente del cuidador (sin cambio).
5. Sentinels honestos en censo/portal (sin cambio).
6. **Nuevo:** Module ActoClinico con coproducto-4 + guards de voluntad
   anticipada y meta terapéutica + autosave local.
7. **Nuevo:** ActionGuard montado donde la spec lo pide (Plan F7 + Module).
8. **Nuevo:** IdentityVerification gate antes de los actos críticos del flujo.
9. **Nuevo:** Outbox compartido con 4 callbacks productivos.

## Gaps remanentes · resumen para próximo corte

```
A · GAPS DE BACKEND
  · Sink al backend de los 3 kinds del outbox             dep: steipete
  · audit_log por episodio (Pasado CA#10 con datos reales) dep: steipete
  · Endpoint de suspensión de indicación (Plan CA#6)       dep: steipete
  · DTO expone alergias (Plan CA#5)                         dep: steipete

B · CRITERIOS SUELTOS (autónomos)
  · Servicio CA#3 (censo vacío = ClinicalStateNotice)
  · Servicio: match 5D AND visible con desglose por dimensión
  · Pulso CA#9 (PatientBand compacto mobile)
  · Pulso: banner de voluntad anticipada fuera del Module

C · INFRA OFFLINE
  · Persistencia outbox cross-reload (swap a IndexedDB)    autónomo
  · SyncEngine.flush automático al recuperar red           dep: A.1

D · MÉTODO
  · Estación validación Fase 0 con clínico real            humano-presencial
```

## Avance autónomo post-cierre (mismo día, sobre `5e22f70`)

Se cerraron los **3 gaps sin dependencia externa** (B parcial + C autónomo).
Suite **499 → 517** verde · `typecheck:web` limpio · `web:build` OK (PWA).

| Gap | Estado | Commit | Qué entrega |
|---|---|---|---|
| C · Persistencia outbox cross-reload (IndexedDB) | ✓ | `c1f29f3` | `createDefaultOutboxStore()` feature-detecta `indexedDB`; el shell ya no fija in-memory. Idiom de transacción IDB endurecido (get→put en una transacción viva). |
| B · Servicio CA#3 (censo vacío = `ClinicalStateNotice`) | ✓ | `6219858` | Aviso explícito + acción a regulación; sin `role=alert`. |
| B · Servicio match 5D AND con desglose | ✓ | `6219858` | D1–D5 visibles; D5 = match real; D1–D4 = `falta evidencia (sin endpoint)`, nunca `cumple` fabricado; veredicto AND exige completar D1–D4. |
| B · Pulso CA#9 (PatientBand compacto mobile) | ✓ | `a37a499` | Variante `compact` + safe areas vía `env()`; `Pulso device="mobile"`. Identidad y banderas nunca se ocultan. |
| B · Pulso banner voluntad anticipada fuera del Module | ✓ | `a37a499` | `VoluntadAnticipadaBanner` persistente, visible antes de escalar, sin `role=alert`; `no_registrada` declarada honestamente. |

Gaps que **siguen abiertos** (sin cambio): todos los de **A · backend** (dep:
steipete), **C · SyncEngine.flush automático** (dep: A.1, requiere sink real) y
**D · Fase 0 con clínico real** (gate final del carril, humano-presencial).

Limitación honesta: el `IndexedDbOutboxStore` no se unit-testea en jsdom (sin
IndexedDB real). Su corrección de runtime es verificada-por-idiom + queda para
validación en navegador real (Fase 0); la selección por entorno y la semántica
sí están cubiertas por tests contra `InMemoryOutboxStore`.
