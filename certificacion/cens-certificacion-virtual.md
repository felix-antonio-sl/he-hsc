# Evaluación Virtual CENS — hd-hsc-os

Estado: autoevaluación pre-sello
Fecha: 2026-05-29 · **Remediada 2026-05-30** (ver §9 y `auditoria-cens-certificacion-virtual-2026-05-30.md`)
Alcance: 3 sellos de calidad de software de CENS + B-PRACSIS (madurez institucional) + Asesoría de Interoperabilidad
Metodología: emulación del framework de evaluación CENS contra el código, documentación y evidencia del repo

## Nota de alcance y de método (leer antes de las tablas)

**Catálogo CENS.** CENS ofrece **seis** certificaciones/programas: Sello Software en Salud, Sello RCE, Sello Telemedicina, B-PRACSIS, Programa Formativo en Salud Digital y Certificación de Perfiles Laborales. Este documento cubre los **3 sellos de software** + **B-PRACSIS** (que **no es un sello de software** sino una herramienta de madurez institucional) + la **Asesoría de Interoperabilidad** (un servicio, no un sello). No son "4 sellos": son 3 sellos + 1 herramienta de madurez + 1 asesoría.

**Notación de veredicto.** `/` = cumple · `◐` = cumple con observaciones / parcial · `✗` = no cumple / brecha bloqueante · `—` = fuera de alcance.

**Cuantificación (reproducible y declarada).** Cada subcaracterística se puntúa con un **mapeo fijo**: `/` = 1.0, `◐` = 0.5, `✗` = 0.0, `—` = excluida del cómputo. El score de una característica es el promedio ponderado de sus subcaracterísticas con sus pesos relativos; el global es el promedio ponderado de características con **pesos normalizados a 100%**. `◐` = 0.5 es un punto medio conservador único para todo el documento (la versión previa usaba valores de `◐` que variaban entre 50% y 80% según la característica, lo que hacía el score no reproducible; corregido).

**Seguridad es gate, no sumando.** Coherente con el invariante del proyecto *seguridad clínica > estética > conveniencia técnica* (`CLAUDE.md`): si la dimensión/característica de Seguridad cae bajo el umbral, el sello **no se otorga** aunque el promedio global lo supere. No se promedia seguridad reprobada con usabilidad aprobada para "rescatar" un sello.

**Versión ISO.** Se evalúa contra el modelo de **ISO/IEC 25010:2011** (8 características), que es el modelo que CENS usa de facto. La norma fue revisada a **ISO/IEC 25010:2023** (9 características; añade *Safety* y renombra Usabilidad→*Interaction capability*, Portabilidad→*Flexibility*). *Safety* — especialmente pertinente a software clínico — queda fuera del marco 2011 aquí usado; es una limitación declarada.

**Umbrales.** Los umbrales de aprobación (≥70% Software, ≥75% RCE) son **inferidos**: CENS no publica thresholds numéricos; entrega un informe de hallazgos y recomendaciones.

---

## 1. SELLO CALIDAD: SOFTWARE EN SALUD (ISO/IEC 25010:2011)

### Subcaracterísticas evaluadas con evidencia y veredicto

| # | Subcaracterística | Criterio | Peso | Evidencia | Veredicto |
|---|---|---|---|---|---|
| **1.1** | Completitud funcional | Cobertura de requisitos specs vs implementación | 15% | `usuarios-y-requerimientos.md` define 12 usuarios (U1-U12), 6 requerimientos transversales R1-R6, 10 slices. Componentes UI montados en superficie. 10 de 10 slices con dominio + puertos + adaptadores e2e. | `/` |
| **1.2** | Corrección funcional | Tests verifican invariantes de dominio | 15% | **538 casos de test web + 606 backend (121 archivos de test)**. D1-D24 mapeados en `gate-calidad-realizacion.md`. `tests/postgres/p0-paridad-fx.test.ts` (escenarios FX-01..FX-09) verifica fake=PG; `p0-d12-conmutatividad.test.ts` cubre proyecciones D12. | `/` |
| **1.3** | Pertinencia funcional | Dominio derivado de metodología formal (OPM ISO 19450) | 5% | `categoria-dominio-hodom.md` deriva de `hd-opm`. Regla: ninguna entidad entra al dominio sin estar en el modelo OPM. | `/` |
| **2.1** | Comportamiento temporal | Connection pooling, índices, queries eficientes | 10% | `Pool` de `pg` + wrapper Kysely en `adaptadores/postgres/db-client.ts`. **173 `CREATE INDEX`** en migraciones. Joins tipados (sin N+1 detectable). `postgresql.conf` deployment-specific (fuera de alcance). | `/` |
| **2.2** | Utilización de recursos | Caching, estrategia offline | 5% | `establishment_id` cache (ADR 0007). PWA con IndexedDB outbox store. Sin cache distribuida (Redis): no requerida para el perfil HODOM (60-80 episodios concurrentes). | `/` |
| **3.1** | Coexistencia | Coexistencia con legacy hdos durante migración | 5% | `estrategia-migracion-hdos-db.md`: extracción, transformación, staging, cutover. FKs con `source_identifier` (nunca PK universal). Dry-run validado. | `/` |
| **3.2** | Interoperabilidad | FHIR R4 + Core CL + terminologías MINSAL | 15% | `contrato-interoperabilidad-salud.md` con mapeo FHIR (20 recursos, tabla líneas 77-96). Puertos `HealthInteroperabilityPort`/`PatientIdentityPort`/`TerminologyPort` **documentados en `puertos/interoperabilidad-salud.md`, sin existir como tipos TypeScript ni adaptador**. Implementación: cero. → se evalúa a fondo en el Sello de Interoperabilidad. | `◐` (solo diseño documental) |
| **4.1** | Reconocibilidad de adecuación | Superficies cognitivas (Pulso, Plan, Pasado) | 10% | 7 ViewContainers en `ifml-hodom.md` (Pulso/Plan/Pasado/Servicio/Conocimiento/Sistema/Portal); 4 con spec individual `superficie-*.md`. Implementación React alineada. | `/` |
| **4.2** | Capacidad de aprendizaje | Patrones consistentes | 5% | `componentes-clinicos.md` define **12 componentes canónicos** (`## Propósito` + 12 secciones de componente); `interfaces/web/src/componentes/` tiene 16 `.tsx` (los 12 + `sin-dato`, `card`, `action-card`, `table-dense`). | `/` |
| **4.3** | Operabilidad | Mobile-first, offline-first, safe areas | 5% | `mobile-clinical-shell.tsx` con `env(safe-area-inset-*)`. `sync-status.tsx` visible en Pulso/Plan/Pasado/Visita. PWA `display: standalone`. | `/` |
| **4.4** | Protección ante errores de usuario | ActionGuard, ConfirmIrreversible, IdentityVerification | 5% | `action-guard.tsx` (explicación, nunca botón gris). `confirm-irreversible.tsx` (ceremonia nombrando efecto). `identity-verification.tsx` con **5 contextos definidos: `visita | tele | prescripcion | acceso-delegado | irreversible`**. | `/` |
| **4.5** | Accesibilidad | aria-*, safe areas, WCAG 2.1 AA | 5% | **86 usos de atributos `aria-`** en `interfaces/web/src`. `role="alert"` reservado a alertas clínicas. Safe areas via `env()`. `densidad-responsive.md`. Sin auditoría formal WCAG 2.1 AA → brecha. | `◐` |
| **5.1** | Madurez | Tests dominio/aplicación/integración/e2e | 10% | 1.144 casos de test (538 web + 606 backend). Testcontainers (PostgreSQL real). Paridad fake-PG. Vitest + jsdom. | `/` |
| **5.2** | Disponibilidad | Offline-first, sync engine, modo degradado | 5% | IndexedDB outbox cross-reload. Sync engine con merge idempotente (ADR 0011). Modo degradado documentado. RTO/RPO pendiente institucional. | `◐` |
| **5.3** | Tolerancia a fallos | Transacciones, validación en API | 5% | try/catch en endpoints. Fastify schema validation. Transactions con `withTenant()`. Domain event transaccional (D11). | `/` |
| **5.4** | Capacidad de recuperación | Outbox append-only, replay | 5% | F6 monoide libre append-only (`domain_event`). Outbox reproduce `state_history` sin huecos (D12.2). IndexedDB sobrevive cierre/refresh. | `/` |
| **6.1** | Confidencialidad | RBAC/ABAC, autenticación, cifrado | 15% | ADR 0016 define RBAC por action×object×role×purpose. `hd_session` cookie httpOnly. argon2 (`package.json`). Matriz de acceso: puerto fake en P0, **no implementada productivamente**. Cifrado en reposo = pendiente ADR de KMS. | `◐` |
| **6.2** | Integridad | Append-only logs, invariantes D5, D22, D24 | 10% | D5 cierre con única causal (exclusive-arc). D22 MAR append-only. D24 continuidad closed-loop. `seguridad-pg.ts`: `audit_event` solo `insertInto` ("NUNCA UPDATE/DELETE"). | `/` |
| **6.3** | No repudio | Auditoría resistente a manipulación | 5% | `audit_event` INSERT-only; todo acceso/escritura/exportación deja evento (F6 immutability, ADR 0005). **No implementado productivamente** — audit_log por episodio sin datos reales (Pasado CA#10). | `◐` |
| **6.4** | Autenticidad | Firma electrónica avanzada | 5% | La firma electrónica avanzada de documentos clínicos con validez legal se rige por la **Ley 19.799** (firma electrónica) y el marco de documentos electrónicos del Estado (NT 10, Ley 21.180). El `ActoClinico Module` incluye paso "Firmar" en diseño. **No hay implementación de firma en código.** | `✗` |
| **7.1** | Modularidad | Arquitectura hexagonal por capas | 10% | `CLAUDE.md:48-66`: 5 capas (dominio → aplicación → adaptadores → interfaces → docs), dependencia hacia adentro. Archivos `.ts`/`.tsx`: 87 dominio · 46 aplicación · 47 adaptadores · 9 API · 115 web. | `/` |
| **7.2** | Reusabilidad | Puertos agnósticos de tecnología | 5% | Puertos por slice en `aplicacion/{slice}/`. Misma interfaz implementada por `adaptadores/memoria/` (fake) y `adaptadores/postgres/` (real). Paridad por tests. | `/` |
| **7.3** | Capacidad de ser analizado | ADRs, documentación | 5% | **16 ADRs (0001-0016)**. `roadmap-construccion.md` con trazabilidad. `handoff-desarrollo.md`. | `/` |
| **7.4** | Capacidad de ser modificado | TS strict, suite completa | 5% | `strict` + `noUncheckedIndexedAccess` + `exactOptionalPropertyTypes` en ambos `tsconfig` (líneas 6-8). 1.144 casos de test. | `/` |
| **7.5** | Capacidad de ser probado | Tests aislados por capa | 5% | Unitarios (dominio), integración (aplicación con fakes), integración real (PostgreSQL/Testcontainers), e2e (API), componentes (RTL). | `/` |
| **8.1** | Adaptabilidad | PWA + API independiente | 5% | `vite-plugin-pwa` (manifest, SW, icons). API Fastify desplegable por separado. | `/` |
| **8.2** | Facilidad de instalación | PostgreSQL como única dependencia productiva | 5% | Solo PostgreSQL + Node.js. 68 migraciones SQL versionadas. Sin Redis/Kafka/Elasticsearch. | `/` |

### Puntuación Sello Software en Salud (mapeo fijo `◐`=0.5; pesos por característica = suma de subpesos, normalizados a 100%)

| Característica | Peso (norm.) | Puntaje | Nota |
|---|---|---|---|
| 1. Adecuación funcional | 17.5% | 100% | `/` |
| 2. Eficiencia del desempeño | 7.5% | 100% | `/` |
| 3. Compatibilidad | 10% | **62.5%** | `◐` interop solo diseño |
| 4. Usabilidad | 15% | 91.7% | `◐` WCAG formal pendiente |
| 5. Fiabilidad | 12.5% | 90% | `◐` RTO/RPO pendiente |
| 6. **Seguridad (GATE)** | 17.5% | **57.1%** | `◐`+`✗` firma — **bajo umbral** |
| 7. Mantenibilidad | 15% | 100% | `/` |
| 8. Portabilidad | 5% | 100% | `/` |

**Score global ponderado: 86.2%.**
**Veredicto: `✗` NO OTORGABLE en el estado actual.** La característica de Seguridad (gate) puntúa **57.1%**, bajo el umbral inferido de 70%, con firma electrónica avanzada `✗` y RBAC/audit/cifrado no productivos. El 86.2% global *no rescata* el gate de seguridad reprobado. Cerradas las brechas de seguridad (A4 firma, B3 RBAC, B4 audit, KMS cifrado), el sello pasa a otorgable con observaciones.

*(Para comparación: la versión previa reportaba "89% → CUMPLE" usando un `◐` variable y promediando la seguridad con mantenibilidad/portabilidad al 100%. Eso enmascaraba la seguridad reprobada — corregido.)*

---

## 2. SELLO CALIDAD: REGISTRO CLÍNICO ELECTRÓNICO (RCE)

### Dimensión Seguridad (GATE)

| # | Criterio | Peso | Evidencia | Veredicto |
|---|---|---|---|---|
| **S1** | Confidencialidad de datos clínicos | 25% | RBAC por action×object×episode×role×purpose **diseñado** (ADR 0016). `hd_session` httpOnly. Matriz de acceso declarada en `ingreso-hodom.md`. Implementación: puerto fake en P0, **no productiva**. | `◐` |
| **S2** | Integridad de registros clínicos | 25% | D22 MAR append-only. D5 cierre única causal. `audit_event` INSERT-only. `domain_event` transaccional (D11). Invariantes D1-D24 con tests P0. | `/` |
| **S3** | Gestión de seguridad (SGSI) | 25% | `contrato-seguridad-informacion-salud.md` como política. `evals/seguridad-informacion-salud.md` con checklist. **Dueño del SGSI ausente** (nivel institucional HSC). Ciclo de revisión no definido. | `◐` |
| **S4** | Disponibilidad del RCE | 25% | Offline-first con IndexedDB outbox. SyncStatus visible. Modo degradado documentado. **RTO/RPO pendiente**. Backup/restauración no probada. | `◐` |

**Score Seguridad RCE: 62.5%.** Bajo el umbral. Es **gate**: aunque la usabilidad apruebe, el sello queda condicionado a cerrar S1/S3/S4.

### Dimensión Usabilidad

| # | Criterio | Peso | Evidencia | Veredicto |
|---|---|---|---|---|
| **U1** | Principios de diseño clínico | 25% | 7 superficies cognitivas. IFML textual (`ifml-hodom.md`). `componentes-clinicos.md` como canon. | `/` |
| **U2** | Consistencia y estándares | 25% | PatientBand en múltiples ubicaciones. SyncStatus en Pulso/Plan/Pasado/Visita. ClinicalStateNotice vs ClinicalAlert. `densidad-responsive.md`. | `/` |
| **U3** | Prevención de errores clínicos | 25% | ActionGuard (nunca botón gris). ConfirmIrreversible (cierre/fallecimiento). IdentityVerification (5 contextos definidos). Alergias no expandidas al prescribir (Plan CA#5 pendiente: dep backend). | `◐` |
| **U4** | Visibilidad del estado del sistema | 25% | PatientBand identidad visible. SyncStatus cola + online/offline. ClinicalStateNotice. SeverityPill. SemaforoEscalamiento con ventana de respuesta. Sin indicador de auditoría de accesos con datos reales (Pasado CA#10, dep backend). | `◐` |

**Score Usabilidad RCE: 75%.**

### Veredicto RCE

| Dimensión | Score | Veredicto |
|---|---|---|
| Seguridad (GATE) | **62.5%** | `◐` — bajo umbral: dueño SGSI, RTO/RPO, matriz de acceso productiva |
| Usabilidad | 75% | `/` — en el umbral estimado |

**Veredicto RCE: `◐` CUMPLE CON OBSERVACIONES MAYORES, CONDICIONADO.** Usabilidad alcanza el umbral, pero el sello queda **condicionado al cierre del gate de Seguridad (62.5%)**. No se promedia a "75% cumple" como en la versión previa: la seguridad reprobada es bloqueante institucional, no diluible.

---

## 3. SELLO CALIDAD: TELEMEDICINA (ISO/IEC 25010:2011 + ISO 13131:2021)

### Dimensión Clínica

| # | Criterio | Peso | Evidencia | Veredicto |
|---|---|---|---|---|
| **C1** | Procesos asistenciales definidos | 20% | 9 procesos clínicos en `categoria-dominio-hodom.md`. F6 teleatención en `flujos-criticos.md:156-178`. Portal con urgencia + teleatención programada. | `/` |
| **C2** | Objetivos sanitarios alineados | 10% | Estrategia Nacional de Salud (ENS) 2022-2030 + Programa Nacional de Telesalud (MINSAL 2018) — alineamiento **implícito**, sin declaración explícita → mejora documental. | `◐` |
| **C3** | Actores involucrados | 15% | 12 tipos de usuario. U5 equipo en domicilio. U3/U6 médicos (teleatención). U2 cuidador con permiso delegado. Portal paciente. | `/` |
| **C4** | Trazabilidad del consentimiento informado | 25% | `informed_consent`/`consent_record` **diseñados** en `modelo-datos-hd-hsc-os.md` (estados pending→granted). **No existen como tabla/migración ni código de dominio/adaptador.** Portal CA#8 (portabilidad JSON con aviso Ley 21.719) sí existe; consentimiento digital para teleatención = stub. | `✗` |
| **C5** | Continuidad del cuidado | 30% | D24 closed-loop: emitted→delivered→acknowledged. Plan de continuidad post-HODOM. Pasado con trazabilidad. Episodio cerrado → solo lectura. Notificaciones a derivador. | `/` |

**Score Dimensión Clínica: 70%** — con **C4 (consentimiento) `✗` bloqueante**.

### Dimensión Técnica

| # | Criterio | Peso | Evidencia | Veredicto |
|---|---|---|---|---|
| **T1** | Compatibilidad / interoperabilidad | 25% | FHIR R4 declarado; Core CL/NID/SNRE referenciados. **Ningún adaptador FHIR; `HealthInteroperabilityPort` no realizado.** Integración con **Fonasa** (requisito explícito del Sello Telemedicina CENS) no abordada. | `✗` |
| **T2** | Usabilidad | 25% | Portal paciente/cuidador (6 superficies). Lenguaje humano. Dos rutas (HODOM/131). Urgencia siempre accesible. Targets ≥44px con safe areas. (Ver RCE U1-U4.) | `/` |
| **T3** | Fiabilidad | 20% | Caída de conexión documentada (sin grabación por defecto). Offline diseñado. IndexedDB outbox + sync. 1.144 casos de test. Sin test de carga de videollamada (servicio externo). | `◐` |
| **T4** | Seguridad | 30% | Cifrado en tránsito: deployment-concern (proxy/Nginx). En reposo: pendiente KMS. IdentityVerification gate diseñado. Consentimiento+identidad+medio/condiciones = spec, implementación parcial. `hd_session` httpOnly con expiración. | `◐` |

**Score Dimensión Técnica: 50%** — con **T1 (interop + Fonasa) `✗` bloqueante**.

### Veredicto Telemedicina

| Dimensión | Score | Veredicto |
|---|---|---|
| Clínica | 70% | `✗` — consentimiento informado digital (C4) no implementado |
| Técnica | 50% | `✗` — interoperabilidad FHIR + Fonasa (T1) no implementados |

**Veredicto Telemedicina: `✗` NO APROBADO.** Dos criterios bloqueantes `✗` (C4 consentimiento, T1 interop+Fonasa). El símbolo es `✗`, no `◐`: estar bajo umbral con bloqueantes es no-cumplimiento, no "cumple con observaciones". Requiere consentimiento digital + adaptador FHIR + integración Fonasa antes de re-evaluar.

---

## 4. B-PRACSIS — MADUREZ INSTITUCIONAL DEL HSC (NO AUTOEVALUABLE DESDE EL REPO)

B-PRACSIS es una herramienta de CENS que mide la madurez de la **institución prestadora** (Hospital de San Carlos) en 6 dimensiones, escala 1-6 (1-2 Básica, 3-4 Emergente, 5-6 Óptimo), mediante un instrumento de 171 preguntas aplicado **a la institución**.

**Advertencia metodológica (corrección 2026-05-30):** este eval **no puede autoasignar un nivel B-PRACSIS**. La versión previa infería niveles numéricos *desde un repositorio de software* y convertía "sin evidencia en el repo" en "Nivel 1 — Básica". Eso es un error: la **ausencia de evidencia en una fuente que no es el instrumento no es un nivel de madurez** — es *no evaluable* desde esta fuente (principio *ausente ≠ valor plausible*). El "2.8/6" previo (y el "3.8/6" que aparecía inconsistentemente en el handoff) **se retiran**: ninguno es un resultado B-PRACSIS válido. Abajo van **observaciones cualitativas** derivadas del repo, como insumo para que CENS+HSC apliquen el instrumento real, no como puntaje.

| Dimensión | Observación desde el repo (insumo, no puntaje) | Evaluable desde el repo |
|---|---|---|
| **Alineamiento Organizacional** | Separación de superficies por trabajo (no por rol) sugiere cultura de procesos. Proyecto liderado externamente; sin dueño institucional designado (Dirección HSC/UGP/SS Ñuble); SGSI sin responsable. | Parcial (liderazgo: **no evaluable** — requiere instrumento) |
| **Capacidad de Gestión** | Modelo de datos formal con 24 invariantes, REM derivado, auditoría diseñada, migración con proveniencia. Indicadores operacionales del censo HODOM existen (ver A.7). Sin política de gobierno del dato del HSC. **Finanzas/presupuesto: no evaluable desde el repo.** | Parcial |
| **Capacidad Operacional** | Greenfield externo; sin evidencia de equipo TI del HSC asignado; hosting (on-prem/cloud/híbrido), hardware móvil, VPN domicilio **no evaluables desde el repo**. | **No evaluable** |
| **Capacidad Técnica** | 9 procesos clínicos, 7 flujos críticos, specs de UI por superficie alineadas a trabajo real. Capacitación/inducción modelada pero no ejecutada. | Parcial (lo técnico observable es fuerte) |
| **Innovación** | OPM ISO 19450, diseño categorial (migración functorial), PWA offline-first, IA auxiliar trazable y descartable. Innovación en diseño, no en producción. | Parcial |
| **Capital Humano** | `staff_qualification` modelado, pero competencias digitales del staff actual del HSC **no evaluables desde el repo**. | **No evaluable** |

**Conclusión B-PRACSIS:** la **postura técnica/de diseño** observable en el repo es alta; la **madurez institucional** (liderazgo, finanzas, operaciones, capital humano) **no es autoevaluable** y debe medirse con el instrumento B-PRACSIS aplicado al HSC por CENS. La asimetría diseño-fuerte / institución-incierta es el principal riesgo de adopción, pero su cuantificación corresponde a CENS.

---

## 5. ASESORÍA DE INTEROPERABILIDAD

CENS estructura su Asesoría de Interoperabilidad en **cuatro servicios secuenciales**: (1) Evaluación de mensajería, (2) Diagnóstico, (3) Propuesta, (4) Implementación. **No hay una escala pública "Nivel 1-5"**; la versión previa citaba un "Nivel 2/5" que no corresponde a un framework CENS publicado (retirado). Abajo, el estado de hd-hsc-os frente a lo que cada servicio examinaría.

### 5.1 Madurez de interoperabilidad (diseño vs implementación)

| Criterio | Estado | Evidencia |
|---|---|---|
| Dominio no contaminado por FHIR | `/` | `auditoria-normativa-interoperabilidad.md:178`: "Dominio no contaminado por FHIR: fuerte" |
| FHIR como borde externo declarado | `/` | `contrato-interoperabilidad-salud.md` |
| Mapping dominio→FHIR documentado | `/` | 20 recursos FHIR (tabla líneas 77-96 del contrato) |
| Puertos de interoperabilidad definidos | `◐` | 3 puertos **en `.md`**, no como tipos TypeScript |
| Adaptadores FHIR implementados | `✗` | No existe directorio/archivo FHIR en `adaptadores/` |
| Validación de recursos FHIR | `✗` | `validateResource()` diseñado en puerto, no implementado |

### 5.2 Estándares sintácticos y semánticos

| Estándar | Referenciado | Implementado | Binding | Veredicto |
|---|---|---|---|---|
| FHIR R4 | `/` | `✗` | — | `◐` |
| Core CL v1.9.4 | `/` | `✗` | — | `◐` |
| NID (MPI) | `/` | `✗` | PIXm/PDQm pendiente | `◐` |
| NID (HPD) | `/` | `✗` | — | `◐` |
| EIS v0.1.0 | dependencia NID | `✗` | — | `◐` |
| CLIPS | dependencia NID | `✗` | — | `◐` |
| SNRE v0.9.6 | gate futuro | `✗` | No requerido aún | `—` |
| SNOMED CT | requerido en contrato | `✗` | Sin política terminológica ejecutable | `✗` |
| CIE-10 | requerido (estadística) | `✗` | Sin implementación | `◐` |
| LOINC | requerido (laboratorio) | `✗` | Sin implementación | `—` |
| CENS Pharma | no referenciado | `✗` | Catálogo de medicamentos sin referencia a CENS Pharma | `✗` |
| DICOM | no aplica (sin imagenología) | `—` | — | `—` |

*Versiones de estándares MINSAL: Core CL v1.9.4, SNRE v0.9.6 y EIS v0.1.0 verificadas en hl7chile.cl / interoperabilidad.minsal.cl. NID y CLIPS están en evolución (draft); fijar la versión exacta contra el IG publicado al momento de integrar.*

### 5.3 Identidad del paciente (EMPI/MPI)

| Criterio | Estado | Evidencia |
|---|---|---|
| Identificador interno opaco (no RUN como PK) | `/` | **UUID v7 como PK (ADR 0003)**, RUN/RUT como `source_identifier` (`modelo-datos-hd-hsc-os.md:133`) |
| Soporte pacientes sin RUN | `/` | Diseñado en espec de identidad |
| Matching con proveniencia | `/` | Diseñado en política de migración. No ejecutado contra MPI nacional |
| Política de merge/unmerge | `/` | Documentada en contrato de interoperabilidad |
| Integración con MPI nacional (PIXm/PDQm) | `✗` | No implementado |

*Nota conceptual: el MPI nacional (NID, PIXm/PDQm) resuelve **identidad/matching clínico**; **Clave Única** resuelve **autenticación de acceso ciudadano**. No son alternativas intercambiables; el plan A3 debe distinguirlas.*

### 5.4 Gobernanza de interoperabilidad

| Criterio | Estado | Evidencia |
|---|---|---|
| Términos y condiciones de uso (NT de Interoperabilidad, DS 12/2023) | `✗` | No definidos. Requeridos para órganos del Estado |
| Gestor de Solicitudes (NT de Interoperabilidad) | `—` | Rol de la Secretaría de Gobierno Digital, no del HSC directamente |
| Publicación de servicios de interoperabilidad | `✗` | No realizada |
| Registro de transacciones de interoperabilidad | `✗` | No implementado |
| Coordinación con Secretaría de Gobierno Digital | `✗` | No iniciada |

*Los artículos exactos de la NT de Interoperabilidad (DS 12/2023, modificado por DS 876/2025) que fijan T&C, Gestor de Solicitudes y registro de transacciones deben citarse contra el texto vigente al momento del envío; aquí se nombran los conceptos, no la numeración.*

### Veredicto Asesoría de Interoperabilidad

**Diseño documentado, implementación cero.** Frente a los 4 servicios de la asesoría CENS, hd-hsc-os tiene material sólido para el servicio de Diagnóstico (dominio limpio, contrato FHIR, puertos), pero **ninguna implementación productiva** (FHIR/Core CL/NID/SNOMED/MPI). El servicio de Implementación parte de cero.

---

## 6. CONSOLIDADO

| Sello / Evaluación | Score | Veredicto | Brechas bloqueantes |
|---|---|---|---|
| **Software en Salud (ISO 25010:2011)** | 86.2% global · **Seguridad 57.1% (gate)** | `✗` NO OTORGABLE (gate seguridad) | Firma electrónica avanzada, RBAC/audit/cifrado productivos, WCAG 2.1 AA |
| **RCE** | Usabilidad 75% · **Seguridad 62.5% (gate)** | `◐` CONDICIONADO | Dueño SGSI, RTO/RPO, matriz de acceso productiva |
| **Telemedicina (ISO 25010 + ISO 13131)** | Clínica 70% · Técnica 50% | `✗` NO APROBADO | Consentimiento digital, interoperabilidad FHIR, integración Fonasa |
| **B-PRACSIS (Madurez HSC)** | **No autoevaluable** | Requiere instrumento CENS aplicado al HSC | Propiedad institucional, capacitación, infraestructura, presupuesto |
| **Asesoría Interoperabilidad** | Diseño documentado | 0 implementaciones productivas | FHIR/Core CL/NID/SNOMED/MPI |

**Lectura honesta:** el sistema es fuerte en adecuación funcional, mantenibilidad, portabilidad y diseño de usabilidad; es **débil en seguridad productiva e interoperabilidad implementada**, que son precisamente los gates de los tres sellos. Ningún sello es otorgable hoy; los tres dependen del mismo núcleo de brechas (Bloque A).

---

## 7. PLAN DE CIERRE DE BRECHAS (ordenado por costo de no hacer)

### Bloque A — Bloqueantes para sellos (4 ítems)

| # | Brecha | Sello afectado | Esfuerzo | Dependencia |
|---|---|---|---|---|
| A1 | Implementar consentimiento informado digital trazable (`informed_consent`/`consent_record` como tabla+dominio+adaptador, no solo `.md`) | Telemedicina, RCE | 2-3 sprints | Backend (steipete) |
| A2 | Implementar adaptador FHIR (Patient, Encounter, ServiceRequest) + perfil Core CL v1.9.4 | Telemedicina, Software en Salud, Interoperabilidad | 3-4 sprints | Decisión de perfil Core CL |
| A3 | Identidad: distinguir e implementar (a) MPI nacional clínico (PIXm/PDQm, NID) para matching de paciente y (b) autenticación (eventual Clave Única) — son problemas distintos | Telemedicina, Interoperabilidad | 2-3 sprints | Disponibilidad del MPI MINSAL |
| A4 | Implementar firma electrónica avanzada para documentos clínicos (marco: **Ley 19.799**; documentos electrónicos del Estado: NT 10 Ley 21.180) | Software en Salud (Seguridad gate), RCE | 2 sprints | Proveedor de firma acreditado |

### Bloque B — Mejoras de puntuación (6 ítems)

| # | Brecha | Esfuerzo |
|---|---|---|
| B1 | Auditoría formal WCAG 2.1 AA (automática + revisión manual de ~10 pantallas) | 1 sprint |
| B2 | Definir RTO/RPO con HSC + runbook de modo degradado | 1 sprint (reunión institucional) |
| B3 | Matriz de acceso RBAC productiva (reemplazar puerto fake) — **parte del gate de seguridad** | 2 sprints |
| B4 | audit_log por episodio con datos reales (Pasado CA#10) | 1 sprint |
| B5 | Referenciar CENS Pharma como terminología de medicamentos | 1 día (documental) |
| B6 | Publicar términos y condiciones de uso del servicio de interoperabilidad (acto administrativo HSC) | 1 día (documental) |

### Bloque C — Madurez institucional (5 ítems, responsable HSC)

| # | Brecha |
|---|---|
| C1 | Designar dueño institucional del proyecto (Dirección HSC / UGP) |
| C2 | Designar dueño del SGSI y delegado de protección de datos (Ley 21.719) |
| C3 | Ejecutar B-PRACSIS formal con equipo del HSC (instrumento CENS) |
| C4 | Plan de capacitación del staff clínico (inducción) |
| C5 | Plan de infraestructura (servidores, red, dispositivos móviles, VPN domicilio) |

---

## 8. NOTA METODOLÓGICA

Esta evaluación es una **emulación** del proceso CENS; no reemplaza la evaluación oficial. Criterios reconstruidos desde:

- CENS (cens.cl/sellos-y-certificaciones; páginas de cada sello, B-PRACSIS y Asesoría de Interoperabilidad).
- ISO/IEC 25010:**2011** (modelo de 8 características; ver nota de versión: la vigente es 2023 con 9 características incl. *Safety*).
- ISO 13131:2021 (Health informatics — Telehealth services — Quality planning guidelines).
- Norma Técnica de Interoperabilidad (DS 12/2023, modificado por DS 876/2025).
- Normas Técnicas de la Ley 21.180. **Materias correctas:** NT 9 = Autenticación; NT 10 = Documentos y Expedientes Electrónicos. (La firma electrónica avanzada se rige por la Ley 19.799.)
- MINSAL Interoperabilidad (interoperabilidad.minsal.cl); NID, Core CL v1.9.4, SNRE v0.9.6, EIS v0.1.0.

**Cuantificación reproducible:** mapeo fijo `/`=1.0, `◐`=0.5, `✗`=0.0, `—`=excluida; pesos por característica = suma de subpesos normalizada a 100%; Seguridad tratada como gate. Umbrales (≥70%/≥75%) inferidos: CENS no publica thresholds.

**Costo (estimación, no tarifa de paquete oficial):** CENS publica tarifas por servicio: Sello Telemedicina ~99 UF; B-PRACSIS informe completo ~25 UF; Sello Software en Salud ~89-99 UF (las fuentes discrepan); **el Sello RCE no publica precio público**. La suma "~322 UF + IVA para 3 sellos + B-PRACSIS" es una estimación interna con esos insumos, **no un total cotizado por CENS**. Solicitar cotización formal.

**Próximo paso:** contactar a CENS (contacto público: Eric Rojas, erojas@cens.cl, y contacto@cens.cl) con este documento como pre-evaluación. Ver §A.9 para implicancias de la red real.

---

*Documento generado por evaluación virtual CENS. Autoevaluación pre-sello; no constituye certificación oficial.*

---

## 9. REMEDIACIÓN 2026-05-30

Este documento fue auditado (`auditoria-cens-certificacion-virtual-2026-05-30.md`) y remediado. Cambios sustantivos respecto de la versión 2026-05-29:

- **Scoring rehecho con metodología única y reproducible** (`◐`=0.5 fijo; pesos normalizados a 100%). El "89% CUMPLE" de Software en Salud pasa a **86.2% global con gate de Seguridad reprobado (57.1%) → NO OTORGABLE**. RCE pasa a **condicionado** (Seguridad 62.5% es gate, no se promedia). Telemedicina pasa de `◐` a **`✗` NO APROBADO** (notación reconciliada con la leyenda).
- **NT 9 / NT 10 corregidas** (eran materias cruzadas): NT 9 = Autenticación, NT 10 = Documentos/Expedientes; firma avanzada → Ley 19.799.
- **B-PRACSIS:** retirado el puntaje numérico (2.8/6 en el eval, 3.8/6 en el handoff — inconsistentes y mal fundados); reframeado como **no autoevaluable desde el repo**.
- **Asesoría de Interoperabilidad:** retirada la escala inventada "Nivel 2/5"; descrita por los 4 servicios reales de CENS.
- **Apéndice A reescrito contra el código real de `hsc-agent-cli`** (endpoints, OSIRIS, pabellón/patología, `dias_hospitalizacion`, ESI, caché). Ver §A.
- **Métricas recontadas:** aria 86 (era "144+"), índices 173 (era "174+"), tests 538 web + 606 backend = 1.144 casos en 121 archivos (era "517 + ~88 = ~595", mezcla de unidades), componentes 12 spec/16 dir (era "13"), archivos por capa 87/46/47/9/115, contextos reales de IdentityVerification, citas de línea corregidas.
- **ISO 25010:** versión declarada (2011) con nota de obsolescencia (2023 añade *Safety*).
- **Costo y catálogo:** "4 sellos" → 6 certificaciones CENS; 322 UF → estimación con desglose y caveat.

---

## APÉNDICE A — CARACTERIZACIÓN DE LA RED ASISTENCIAL DEL SS ÑUBLE Y EL HSC

Fuente: `/home/felix/projects/hsc-agent-cli` — vitrina clínica de **solo lectura** que los agentes AI usan para leer los sistemas reales del HSC (DAU, SGH, LIS) y el ESB Salud En Red mediante scraping HTML + parseo, exponiéndolos como *handles* identity-safe en JSON. **Esta versión del Apéndice fue verificada endpoint por endpoint contra el código del CLI (2026-05-30).** No es una sonda de monitorización; es asistencia conversacional sobre datos de producción.

### A.1 Mapa de sistemas de la red asistencial

| Sistema | Tipo | Rol en la red | Protocolo | Auth |
|---|---|---|---|---|
| **SGH** | PHP legacy, HTML server-rendered | Hospitalización: censo, camas, servicios, evoluciones, indicaciones, documentos, recetas, epicrisis | HTTP interno vía proxy `100.77.30.26` | Cookie PHPSESSID + form login (`usuario`/`contrasena`) |
| **DAU** | PHP legacy, HTML server-rendered | Urgencia: triage, signos, anamnesis, exámenes, órdenes, medicación, altas | HTTP interno vía proxy `100.77.30.26` | Cookie PHPSESSID + form login |
| **LIS** | PHP legacy | Laboratorio: resultados por RUT, histórico, PDFs de detalle | HTTP interno vía proxy `100.77.30.26` | Cookie PHPSESSID + form login |
| **HCC** (Historia Clínica Compartida) | Bridge DAU+SGH → ESB | APS, especialidades, interconsultas, epicrisis de otros establecimientos | HTTPS a `esb.saludenred.cl:{8201,8095,8096,8097,8099}` | Token vía bridge (DAU+SGH→ESB), sin credenciales propias |
| **OSIRIS** (en este CLI) | Subsistema de **documentos ambulatorios** del SGH | Atenciones previas ambulatorias + listado de documentos del paciente | HTTP interno vía proxy | Indirecto (sesión SGH) |
| **Pabellón / A. Patológica** | Sistemas quirúrgicos/anatomopatológicos | — | **Externos al proxy** (p. ej. pabellón en `http://10.6.85.124:8085`, IP distinta) | No accesibles desde `100.77.30.26` |

*Corrección de la versión previa: OSIRIS no es "imagenología `not_implemented_yet`" — en este CLI es el subsistema de documentos ambulatorios del SGH y **está implementado** (handle `paciente:ambulatorias-osiris/<rut>`). Pabellón/Patología no están marcados `not_implemented_yet`: se declinaron por vivir en sistemas externos a la IP del proxy.*

### A.2 Arquitectura de red del SS Ñuble

```
                  MINSAL / MPI / SNRE / REM
                           |  [Internet / HTTPS]
              ┌─────────────────────────┐
              │   ESB Salud En Red       │  ← interoperabilidad regional
              │   esb.saludenred.cl       │     (token :8201, datos :8095-8099)
              └───────────┬──────────────┘
                          │
    ┌─────────────────────┼──────────────────────┐
    │          proxy interno 100.77.30.26          │
    │  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐    │
    │  │ SGH  │  │ DAU  │  │ LIS  │  │HCC/  │    │
    │  └──┬───┘  └──┬───┘  └──┬───┘  │ESB   │    │
    │     │    H_SGH_HOSPITAL_ID=2 (San Carlos)   │
    │     │    H_SGH_HOSPITAL_ID=1 (H. Martín)    │
    └─────┼─────────┼─────────┼─────────┼─────────┘
    ┌─────┴─────────┴─────────┴─────────┴─────────┐
    │          hd-hsc-os (greenfield)              │
    │   → coexiste con SGH/DAU/LIS                  │
    │   → primer productor FHIR de la red           │
    │   → interopera hacia MINSAL/ESB               │
    └─────────────────────────────────────────────┘
```
(Sistemas externos al proxy — pabellón `10.6.85.124:8085`, patología — quedan fuera de este plano.)

### A.3 SGH (sistema que hd-hsc-os reemplaza para HODOM) — endpoints reales

| Característica | Detalle (verificado en código) | Implicancia para hd-hsc-os |
|---|---|---|
| **Modelo de datos plano** | Pacientes por `cp` (código paciente) e `ingreso_id`. Tablas HTML scrapeadas, sin normalización | La migración Σ_F reconstruye entidades desde un modelo no relacional |
| **Identidad frágil** | `evolucion_id` frecuentemente "0" en HODOM (`censo_pointer_invalid`); el censo no siempre apunta a la última evolución | hd-hsc-os debe tolerar datos inconsistentes del legacy en coexistencia |
| **Censo (fuente de verdad)** | `funciones/listado/listado_datos_camas_pacientes.php` (precedido de `listado_servicios2.php` + `listado_salas3.php`). Campos: `cp`, `nombre`, `rut`, `ingreso_id`, `dias_hospitalizacion`, `diagnostico`, `evolucion_id`. `find --hospitalizados --hodom` consulta esta grilla filtrando `servicio_id=72` | El censo es canónico para saber qué pacientes están activos |
| **HODOM = servicio 72, no módulo aparte** | HODOM es `servicio_id=72` (salas 286/287/288; 635 "HODOM HSC" como default), misma tabla de evoluciones/indicaciones/documentos que hospitalización general | El dominio HODOM de hd-hsc-os es una abstracción que no existe en el legacy; la migración proyecta el subconjunto HODOM desde tablas genéricas |
| **Documentos como PDF** | Servidos por `ingreso/ver_pdf.php?form=<form>&id=<ingreso_id>`. Sin metadatos estructurados | La migración extrae texto vía `pdftotext` y asigna metadatos por heurística (pérdida aceptada) |
| **Auth por sesión PHP** | `funciones/autenticacion.php` (form `usuario`/`contrasena`), cookie PHPSESSID, sin 2FA ni roles por endpoint | hd-hsc-os introduce RBAC/ABAC donde no existía; mapear usuarios SGH → roles HODOM |
| **Multi-establecimiento** | `H_SGH_HOSPITAL_ID=1` (Herminda Martín), `=2` (San Carlos, default). `vistas/cambiar_hospital.php` cambia contexto | El RLS por `establishment_id` (D8) debe contemplar que ambos hospitales comparten el mismo SGH físico como tenants lógicos distintos |

### A.4 DAU (urgencia) — relevante para derivación a HODOM

| Característica | Detalle (verificado) | Implicancia |
|---|---|---|
| **Triage 5 niveles** | Campo `Categoria` con valores `C1..C5` (de `triageprueba/listadoTriage.php`). *Suele rotularse "ESI" por convención clínica, pero el código nombra `C1..C5`, no "ESI".* | La derivación urgencia→HODOM (U3) debe capturar el nivel de triage como contexto clínico |
| **Evoluciones no estructuradas** | Anamnesis/indicaciones/observaciones en texto libre HTML, sin vocabulario controlado | La solicitud de ingreso HODOM extrae diagnóstico/estabilidad desde texto libre — brecha de terminología |
| **Medicación de urgencia** | `atencion/obtener_lista_indicaciones.php` (fármaco, dosis, vía, frecuencia) | El esquema farmacológico inicial del episodio HODOM puede originarse aquí; requiere conciliación |

### A.5 LIS (laboratorio)

| Característica | Detalle (verificado) | Implicancia |
|---|---|---|
| **Resultados por RUT** | `resultadoseleccion.php` devuelve el listado de exámenes; el CLI filtra pendientes y expone handles | hd-hsc-os puede consultar resultados vía el mismo proxy en coexistencia, o migrar el histórico |
| **PDFs de detalle** | `detalleexamenes.php?id=<id>` genera el PDF | Si se requiere LOINC, el mapeo desde códigos internos del LIS se hace en el adaptador |
| **Histórico** | Vía `resultadoseleccion.php` (no hay endpoint `historial_examenes.php` separado) | Fuente para el Pasado (timeline) clínico previo al ingreso HODOM |

### A.6 ESB Salud En Red (HCC)

| Característica | Detalle (verificado) | Implicancia |
|---|---|---|
| **APS y especialidades** | DAU `atencion/obtener_visor_aps.php?rut=&dv=` devuelve URL bridge; el ESB entrega consultas APS/interconsultas/epicrisis de otros establecimientos | La continuidad post-HODOM (derivación a APS) debe notificarse vía ESB; el alta HODOM genera un documento que viaja al CESFAM de origen |
| **Token vía bridge** | Token de ESB `:8201 /VISOR_CL/ObtenerTokenSesion` obtenido tras autenticarse en DAU+SGH; sin auth directa al ESB | hd-hsc-os necesitará un mecanismo de autenticación ante el ESB; si el ESB expone FHIR, ese es el camino natural |
| **Cobertura parcial** | Algunos subsistemas (pabellón, patología) no son alcanzables (externos al proxy) | La interoperabilidad con la red completa depende de la madurez del ESB, no solo de hd-hsc-os |

### A.7 HODOM operacional hoy (lo que revela el CLI)

Del censo real del SGH vía `scripts/smoke-hodom.sh` (ejecuta `find --hospitalizados --hodom`):

| Indicador | Origen | Significado |
|---|---|---|
| `total_pacientes`, `rooms_with_people` | **nativos del CLI** (`HospitalizadosResult`) | Pacientes activos en HODOM (servicio 72) y salas ocupadas (286/287/288/635) |
| `evolucion_id_zero`, `long_stay_14d`, `long_stay_30d`, distribución `dias_hospitalizacion` (buckets), `handle_ready`, `handle_missing` | **derivados por el script smoke** (Python sobre la salida del CLI) | Dato sucio (censo sin evolución), estancias prolongadas, recuperabilidad de datos clínicos |

**Implicancia:** el HODOM del HSC ya tiene indicadores operacionales medibles. Esto es insumo para que B-PRACSIS evalúe "Capacidad de Gestión de la Información" del HSC (con su instrumento, no por inferencia). hd-hsc-os debe preservar y mejorar esta capacidad de medición.

### A.8 Riesgos de interoperabilidad descubiertos

| Riesgo | Origen | Impacto en certificación |
|---|---|---|
| **FHIR es greenfield total en la red** | Ningún sistema del HSC expone FHIR; el ESB usa protocolos propios; el MPI nacional está en draft | hd-hsc-os será el productor FHIR sin consumidores FHIR locales; la conformidad se valida contra perfiles MINSAL, no contra tráfico real |
| **Identidad por RUT, no por MPI** | SGH/DAU/LIS usan RUT (módulo 11); el MPI (PIXm/PDQm) no está en producción en el SS Ñuble | La integración con MPI es contrato futuro; mientras tanto, RUT + identificador interno opaco |
| **PDFs sin estructura** | Documentos SGH (`ver_pdf.php`) sin metadatos FHIR | La migración documental (D10) acepta pérdida de metadatos; los documentos nuevos sí serán FHIR-nativos |
| **Caché clínica en disco sin cifrar** | El CLI cachea en `~/.cache/hsc-agent-cli/<rut>/...` JSON **sin cifrado**, aunque con permisos `0600`/`0700` y **TTL por tipo** (wrapper `stored_at`/`ttl_seconds`) | hd-hsc-os debe elevar el estándar: IndexedDB con expiración (y cifrado si aplica). El déficit es la falta de cifrado, no la ausencia total de control |
| **Proxy único como punto de fallo** | `100.77.30.26` es la entrada única a DAU/SGH/LIS | hd-hsc-os con PostgreSQL local + PWA offline no depende del proxy para operar (mejora de disponibilidad S4 RCE); la migración sí lo necesita, con ventana acotada |

### A.9 Implicancias para la estrategia de certificación

1. **Interoperabilidad en dos fases:** hacia afuera (MINSAL/MPI/REM/SNRE, hd-hsc-os como productor FHIR) y hacia adentro (SGH/DAU/LIS/ESB, consumo legacy vía adaptadores no-FHIR durante la coexistencia).
2. **La migración es el gate del Sello RCE:** la calidad del dato migrado (PDFs, evoluciones HTML, `evolucion_id=0`) determina la integridad del RCE.
3. **B-PRACSIS al HSC real, no inferido:** los indicadores del censo HODOM son el tipo de evidencia que B-PRACSIS evalúa; recolectarlos sistemáticamente fortalece la postura, pero el nivel lo asigna el instrumento.
4. **La topología fuerza arquitectura:** hd-hsc-os no puede depender del proxy para operar (lo resuelve el PWA offline); el adaptador de migración sí lo necesita, como riesgo aceptado con ventana temporal acotada.
