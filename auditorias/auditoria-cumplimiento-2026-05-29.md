# Auditoría de cumplimiento — carril frontend (Steve-web-ux)

Estado: instrumento de gobernanza del carril (vivo)
Fecha: 2026-05-29
Commit cabeza: `d0b1c00` (origin/master sincronizado)
Alcance: superficies UI · componentes especificados · slices con criterios UI.
Carril datos/backend: **steipete** — no se audita aquí.

## Para qué es este documento

Cruza cada criterio de aceptación de las specs vivas con la implementación
real y emite un veredicto: ✓ cumplido · ◐ parcial (con nota) · ✗ pendiente.
A diferencia del gap-analysis previo (basado en titulares de spec), este
reporte trabaja sobre las **secciones "Criterios De Aceptación" y "Reglas"**
de cada spec, sumando lo que dos Explorer agentes detectaron al cruzar
specs con archivos.

## Cómo se lee

- Tabla por superficie y por componente.
- Evidencia = `archivo:línea` cuando la spec se cubre en código;
  `no implementado` cuando no hay call site.
- "Estado" registra el corte transversal del criterio en la implementación
  presente, **no** una promesa.

## Componentes especificados (13)

| Componente | Implementado | Usado en | Estado |
|---|---|---|---|
| action-guard | ✓ | huérfano | ✗ sin call site real |
| audit-access-panel | ✓ | `portal.tsx` | ✓ |
| caregiver-delegate | ✓ | `portal.tsx` | ✓ |
| clinical-alert | ✓ | `pulso-components.tsx` | ✓ (rojo solo crítico, salida obligatoria) |
| clinical-state-notice | ✓ | `pulso-components.tsx`, `plan.tsx`, `pasado.tsx`, otras | ✓ (sin `role="alert"`) |
| confirm-irreversible | ✓ | `cierre.tsx`, `escalamiento.tsx` | ✓ |
| contextual-guidance | ✓ | huérfano | ✗ |
| domicile-location-capture | ✓ | huérfano | ✗ (puerto + adaptador navegador listos) |
| identity-verification | ✓ | huérfano | ✗ |
| mobile-clinical-shell | ✓ | `pulso`, `plan`, `pasado`, `cierre`, `visita`, ... (13 refs) | ✓ |
| narrative-visit-capture | ✓ | `visita.tsx` | ✓ |
| patient-band | ✓ | 14 refs (todas las clínicas con episodio) | ✓ |
| sync-status | ✓ | `visita.tsx` | ◐ (no integrado en Pulso/Plan/Pasado para offline) |

**Cobertura:** 13/13 implementados (100%). **Uso real:** 9/13 montados en
superficies (69%); 4 huérfanos (action-guard, contextual-guidance,
identity-verification, domicile-location-capture).

### Componentes huérfanos — palanca clínica

| Huérfano | Anti-patrón que materializa al ausentar | Donde la spec lo pide |
|---|---|---|
| ActionGuard | Botón gris silencioso en Plan/Visita/Cierre/Escalamiento | spec Pulso CA#8 · spec Plan CA#4 · spec Cierre |
| IdentityVerification | Riesgo de paciente equivocado en domicilio/tele | spec Visita · spec medicación · spec Cierre/Escalamiento |
| ContextualGuidance | Decisión clínica sin guía protocolar trazable | spec Pulso · spec Plan |
| DomicileLocationCapture | Georref del domicilio nunca confirmada | spec Ingreso "Georreferencia del domicilio" |

## Superficie Pulso

Spec: `docs/05-especificaciones/ui/superficie-pulso.md` — 10 criterios de aceptación.

| # | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA1 | Entiende el ahora sin Tab Soup | ✓ | `pulso.tsx` orquesta 8 ViewComponents en una superficie |
| CA2 | `clinical-state-notice` vs alerta en estado normal | ✓ | `EstadoNormalNotice` XOR `AlertasActivas` |
| CA3 | Toda alerta activa con salida clínica | ✓ | `onAbrirAlerta → onNavigate(destinoAlerta(a))` |
| CA4 | ActoClinico Module invocable | ✗ | deuda explícita: acciones rápidas navegan a Visita legacy |
| CA5 | Voluntad anticipada visible antes de escalar | ✗ | no hay guard visual previo |
| CA6 | Sin paciente = agregado operacional | ✓ | `PulsoMiDia` desde censo |
| CA7 | Offline: PatientBand + datos legibles + cola | ◐ | PatientBand sí; `SyncStatus` no integrado |
| CA8 | Ninguna acción gris sin causa (`action-guard`) | ✗ | `AccionesRapidas` filtra solo "egresar si inestable" |
| CA9 | Mobile: PatientBand compacto + safe areas | ◐ | `MobileClinicalShell` sí; falta variante compacta |
| CA10 | Ningún evento interactivo sin salida | ◐ | mapeos sí; bindings de auditoría aún no |

## Superficie Plan

Spec: `docs/05-especificaciones/ui/superficie-plan.md` — 12 criterios.

| # | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA1 | Plan por categoría de prestación, nunca por profesión | ✓ | 7 lentes por categoría OPM, ninguna por rol |
| CA2 | Lentes XOR sobre el mismo plan | ✓ | `LenteSelector` segmentado + render único |
| CA3 | Esquema clínico operado, medicamento referenciado | ✓ | `PlanFarmacologico` opera indicación + MAR |
| CA4 | Prescribir exige esquema conciliado (guard) | ✗ | estado mostrado; sin `ActionGuard` bloqueante |
| CA5 | Alergias siempre expandidas al prescribir | ✗ | no implementado |
| CA6 | Suspender indicación = `confirm-irreversible` | ✗ | acción no expuesta en UI |
| CA7 | Discrepancia detectada = alerta accionable | ✓ | render con color advertencia + descripción |
| CA8 | Plan al día = `ClinicalStateNotice`, no `clinical-alert` | ✓ | sin discrepancias → notice |
| CA9 | Plan inicial muestra lentes por definir, no error | ✓ | `SinDato` honesto en lentes sin servicios |
| CA10 | Offline: guard alergia + prescripción encola | ✗ | sin offline en Plan |
| CA11 | Lesión activa con plan de curación | ✗ | `LenteCuidados`: SinDato "sin lesiones registradas" — schema sin fuente |
| CA12 | Ningún evento interactivo sin salida | ◐ | `onFlujoEjecutado` refetcha; sin payload auditado |

## Superficie Pasado

Spec: `docs/05-especificaciones/ui/superficie-pasado.md` — 11 criterios.

| # | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA1 | Narrativa primero | ✓ | `item.narrative` antes que metadata |
| CA2 | Filtro clínico vs operacional, default clínico | ✓ | `FiltroTimeline` por nature |
| CA3 | Master-detail sin perder la lista | ✓ | `selectedItem` abre lateral |
| CA4 | Evento grave: texto + icono + color | ✓ | ⚠ + label + tokens críticos |
| CA5 | Episodio previo como enlace, no inline | ✓ | "Ver historia →" navega |
| CA6 | Detalle no ofrece clonar/copiar | ✓ | `TimelineDetail` solo display |
| CA7 | Pasado no se abre sin episodio | ✓ | `episodioRef` requerido |
| CA8 | Episodio cerrado: acciones bloqueadas, lectura activa | ✗ | sin lógica `estadoHodom="closed"` |
| CA9 | Offline: timeline caché legible | ◐ | sin `SyncStatus` |
| CA10 | `SelectVerAccesos` → `audit-access-panel` | ✗ | sin botón |
| CA11 | Ningún evento interactivo sin salida | ◐ | `onSelect` abre detalle; sin auditoría |

## Superficie Servicio

Spec: `docs/05-especificaciones/ui/superficie-servicio.md` — criterios por sub-superficie.

| Sub | Criterio | Estado | Evidencia |
|---|---|---|---|
| Censo | Sin "cupos" como gate | ✓ | match multidimensional + admisible/espera/no |
| Censo | Bandera crítica: texto + dot + color | ✓ | `SeverityPill` |
| Censo | "Sin banderas" no alerta | ◐ | censo vacío sin `ClinicalStateNotice` dedicado |
| Censo | Briefing matinal armado desde censo | ✓ | `RegulacionK3Panel` cumple el briefing K3 |
| Regulación | Match 5D AND visible | ◐ | lógica en backend; UI muestra veredicto sin desglose D1..D5 |
| Regulación | `en espera` con `Restricción limitante` | ✓ | `limitingConstraint` mostrada en UI |
| Despacho | 2 guards de seguridad | ✗ | sin superficie Despacho dedicada (vive en Territorial) |
| Escalamiento | Ventana de respuesta visible + reloj | ◐ | `SemaforoEscalamiento` en Pulso muestra reciente; cronómetro = SinDato |

## Superficie Portal

Spec: `docs/05-especificaciones/ui/portal-paciente-cuidador.md` — 12 criterios.

| # | Criterio | Estado | Evidencia |
|---|---|---|---|
| CA1 | Canal urgencia primer nivel persistente | ✓ | `CanalUrgencia` fuera de tabs |
| CA2 | Llamar = acción primaria; síntoma opcional | ✓ | botón llamar dominante |
| CA3 | Números offline + marcador tel: | ◐ | display sí; `href="tel:..."` faltó verificarse |
| CA4 | Dos rutas claras HODOM/131 | ✓ | dos handlers separados |
| CA5 | Acuse inmediato | ◐ | state local sin emisión a backend |
| CA6 | Lenguaje humano sin jerga | ◐ | tabs sí; sentinels también; remedios en humano = stub |
| CA7 | "Quién vio" en humano | ✓ | `AuditAccessPanel` integrado |
| CA8 | Descarga de portabilidad | ✗ | stub "próximo corte" |
| CA9 | Cuidador con permiso vencido no bloquea urgencia | ✓ | urgencia siempre disponible |
| CA10 | No edita registros | ✓ | lectura-only |
| CA11 | Remedios en lenguaje humano | ✓ | seed alineado A; con PG real → SinDato honesto |
| CA12 | Mobile: targets ≥ 44px | ◐ | sin medición formal |

## Slices con criterios UI explícitos

### Ingreso

| Criterio (extracto) | Estado | Nota |
|---|---|---|
| Form de admisión con 13 campos del DTO | ✓ | `IngresoForm` |
| Veredicto admitido/diferido visible | ✓ | mapeo es-CL del status |
| Georreferencia del domicilio capturada | ✗ | `DomicileLocationCapture` no integrado en `IngresoForm` |
| Verificación de identidad antes de admitir | ✗ | `IdentityVerification` no integrada |

### Cierre

| Criterio (extracto) | Estado | Nota |
|---|---|---|
| `ConfirmIrreversible` antes de cerrar | ✓ | usado |
| Causal única seleccionada (coproducto D5) | ✓ | dropdown único + 6 opciones del DTO |
| Notificable obliga registro de notificación | ◐ | no hay UI específica para D17 (delegado a backend D5/D17) |

## Top 10 gaps por palanca clínica

Ordenados por seguridad cl, no por costo de implementación.

1. **ActionGuard en Plan farmacológico** — esquema sin conciliar bloquea
   "Ejecutar flujo F7". Cierra CA#4 del Plan y CA#8 del Pulso.
2. **IdentityVerification antes del flujo F7 + Visita + Cierre** — prevención
   wrong patient. La spec lo exige para 5 contextos; cero implementados.
3. **ActoClinico Module completo** — deuda explícita del Pulso; cierra el
   corazón clínico Valorar→Decidir→Firmar y mata el `Click Liturgy`.
4. **DomicileLocationCapture en Ingreso** — georref `confirmado` evidencia D2;
   hoy domicilio sin punto geográfico.
5. **ContextualGuidance en Pulso ante alertas** — guía protocolar trazable
   en pto. decisión (criterio aceptación spec componente).
6. **Cierre: Pasado bloquea acciones, lectura activa** — CA#8 del Pasado.
7. **Pasado: botón "Ver mis accesos" → audit-access-panel** — CA#10.
8. **SyncStatus en Pulso/Plan/Pasado** — offline-first cierra 4 CAs.
9. **Portal: emisión de señal al episodio en llamada urgencia** — CA#5.
10. **Portal: descarga de portabilidad** — CA#8 (lo declara la Ley 21.719).

## Top 5 cumplimientos sólidos

Donde la implementación cumple o supera la spec — base para ampliar.

1. Plan por categoría, nunca por profesión (`anti-Role Silo`).
2. Pasado narrativa primero con master-detail.
3. Pulso Mi Día sin pantalla vacía.
4. Portal: canal de urgencia persistente independiente del permiso del cuidador.
5. Sentinels honestos en censo/portal cuando el schema no tiene fuente.

## Lo que esta auditoría no cubre

- Backend (es zona steipete; ver `gate-calidad-realizacion.md`).
- Specs sin sección formal de "Criterios": capacidad, medicación, regulación,
  visita, escalamiento, materiales, territorial, gobernanza (estos slices
  declaran dominio + puertos, no criterios UI). Su UI se evalúa en sus
  respectivas superficies/panels.
- Validación de Fase 0 con clínico real (`docs/03-experiencia/estacion-validacion-fase0.md`):
  pendiente de ejecutar; no es código.

## Cómo se usa este reporte

- Como punto de partida del próximo corte: los **Top 10 gaps** ordenan
  trabajo por palanca clínica, no por simpatía del módulo.
- Como gate de revisión: cuando una superficie se modifique, su tabla
  vuelve a auditarse y los criterios que cambian de ✗/◐ a ✓ se mueven.
- Como insumo para la estación de validación Fase 0: el clínico observa
  cumplimientos sólidos como base de confianza y los Top 10 gaps como
  hipótesis de fricción esperada.
