# Auditoría normativa e interoperabilidad

Estado: borrador controlado
Tipo: auditoría transversal inicial
Fecha: 2026-05-26

## Propósito

Auditar `hd-hsc-os` desde cumplimiento normativo e interoperabilidad en salud,
revisando cada componente actual del repo: canon, dominio, datos, experiencia,
arquitectura, specs, puertos y capas de código.

Esta auditoría no certifica cumplimiento legal. Traduce obligaciones y
estándares vigentes en brechas de diseño, gates y artefactos para que el repo
absorba esta dimensión antes de implementar.

## Fuentes Consultadas

| Fuente | Hallazgo aplicable |
|---|---|
| Ley 20.584 | ficha clínica, confidencialidad, acceso, portabilidad, consentimiento, conservación mínima |
| Ley 21.541 | telemedicina/salud digital, seguridad, registros, medios técnicos, consentimiento |
| Ley 21.719 | datos de salud como datos sensibles, portabilidad, programa de cumplimiento y delegado |
| Ley 21.663 | salud como servicio esencial, seguridad por diseño, incidentes y resiliencia |
| Resolución Exenta ANCI 7/2025 | reporte de incidentes significativos al CSIRT Nacional |
| Decreto Exento MINSAL 9/2023 | Norma Técnica 231/EIS como marco de estándares de información |
| Interoperabilidad MINSAL | FHIR R4, SNOMED CT, CIE-10, LOINC, MPI, HPD, servicios terminológicos |
| NID MINSAL 0.4.8 | Core CL, MPI, PIXm/PDQm y dependencias nacionales |
| SNRE MINSAL 0.9.6 | guía draft para prescripción/dispensación interoperable |

## Resultado Ejecutivo

El repo tiene una base arquitectónica correcta: dominio separado del legado,
FHIR declarado como borde externo, REM derivado desde core, experiencia clínica
con auditoría visible y migración con proveniencia.

La brecha principal era documental y contractual: cumplimiento normativo,
interoperabilidad, terminología, identidad nacional, portabilidad, SNRE,
incidentes y datos sensibles aparecían como menciones dispersas, no como gates
obligatorios.

Esta pasada deja esa dimensión anclada en:

- `02-datos/contrato-interoperabilidad-salud.md`;
- `05-especificaciones/puertos/interoperabilidad-salud.md`;
- `05-especificaciones/evals/cumplimiento-normativo-interoperabilidad.md`;
- actualización de fuentes, memoria, roadmap, gates y specs.

## Auditoría Por Componente

| Componente | Estado encontrado | Brecha | Acción |
|---|---|---|---|
| `CLAUDE.md` | arquitectura por capas correcta; FHIR vive en adaptadores | no explicita normativa como gate transversal | no se modifica; se baja a docs operativos |
| `00-canon/` | precedencia clara; Drive sensible ya reconocido | faltaban fuentes oficiales normativas/interoperabilidad | actualizar precedencia y lectura recomendada |
| `01-dominio/` | dominio no se contamina con FHIR; invariantes D13/D14 existen | faltan obligaciones de ficha clínica/consentimiento como constraints de aplicación | cubrir por datos, puertos y evals, no por dominio puro |
| `02-datos/` | fuerte en migración, REM, RLS, eventos | no tenía contrato FHIR/Core CL/NID/SNRE/terminología | crear contrato de interoperabilidad |
| `03-experiencia/` | buen soporte a identidad, auditoría, offline, tele | faltan referencias explícitas a portabilidad y consentimiento normativo | cubrir por eval y futuros componentes |
| `04-arquitectura/` | roadmap impide tecnología prematura | no exigía gate normativo/interoperabilidad antes de ADR | agregar gate al roadmap |
| `05-especificaciones/` | usuarios/requerimientos muy sólidos; puertos mínimos de persistencia | falta puerto de interoperabilidad y eval de cumplimiento | crear puerto y eval |
| `90-referencias/` | buena evidencia de `hdos-app` | no gobierna | sin cambios |
| `dominio/` | vacío, correcto en greenfield | sin guardia técnica todavía | futuro: tests o lint de dependencia |
| `aplicacion/` | vacío | falta contrato de puertos al implementar | puerto documentado antes de código |
| `adaptadores/` | vacío | no hay implementación FHIR/terminología aún | gate antes de crear adaptador |
| `interfaces/` | vacío | no hay superficie de portabilidad/consentimiento aún | cubrir en slices |

## Brechas Priorizadas

### B1. Identidad Paciente / EMPI

Riesgo: usar `RUT` como clave primaria universal o resolver deduplicación por
matching informal.

Decisión requerida:

- identificador interno opaco;
- RUN/RUT como identificador sensible;
- soporte para pacientes sin RUN, extranjeros o identidad provisoria;
- matching con proveniencia;
- política de merge/unmerge.

### B2. Ficha Clínica, Portabilidad Y Acceso

Riesgo: que `Portal` y export FHIR sean features UX, no cumplimiento de acceso y
portabilidad.

Decisión requerida:

- formato estructurado exportable;
- control de solicitudes de titular/representante/tercero autorizado;
- mínima información necesaria para continuidad de cuidado;
- auditoría visible;
- retención y custodia.

### B3. Terminología

Riesgo: perpetuar texto libre para diagnósticos, prestaciones, medicamentos,
procedimientos y hallazgos.

Decisión requerida:

- SNOMED CT para conceptos clínicos cuando aplique;
- CIE-10 para reportería/estadística;
- LOINC para observaciones/laboratorio;
- EIS/DEIS para datos administrativos y geoespaciales;
- catálogo local versionado más `ConceptMap`.

### B4. Prescripción, Medicamentos Y SNRE

Riesgo: modelar receta/dispensación localmente y descubrir tarde que SNRE exige
otro ciclo de vida.

Decisión requerida:

- `MedicationRequest` y SNRE antes de prescripción interoperable;
- separación entre esquema farmacológico, receta, medicamento físico,
  dispensación y administración;
- validación de prescriptor, paciente y fármaco.

### B5. Teleatención Y Consentimiento Digital

Riesgo: tratar teleatención como videollamada embebida.

Decisión requerida:

- consentimiento registrado;
- medio y condiciones de prestación;
- identidad verificada;
- registro clínico equivalente a atención presencial;
- caída de conexión y no grabación por defecto.

### B6. Ciberseguridad E Incidentes

Riesgo: dejar seguridad como tarea de infraestructura tardía.

Decisión requerida:

- clasificación de activos;
- RTO/RPO;
- cifrado;
- logs inmutables;
- procedimiento de reporte de incidentes;
- pruebas de restauración;
- control de terceros.

### B7. REM Y Reportería

Riesgo: confundir reporte agregado con fuente clínica.

Decisión requerida:

- REM derivado desde core;
- conciliación contra periodos;
- numerador, denominador, filtro y fuente por indicador;
- exportes agregados sin identificadores salvo base legal.

## Gates Antes De ADR Tecnológico

Antes de elegir stack o base física:

1. `02-datos/contrato-interoperabilidad-salud.md` debe estar aceptado.
2. `05-especificaciones/puertos/interoperabilidad-salud.md` debe cubrir el slice.
3. `05-especificaciones/evals/cumplimiento-normativo-interoperabilidad.md` debe
   estar aplicado al slice.
4. Cada slice debe declarar:
   - recursos FHIR tocados;
   - terminologías;
   - datos sensibles;
   - reglas de consentimiento;
   - auditoría;
   - portabilidad;
   - incidentes o continuidad si aplica.
5. Ningún adaptador FHIR puede implementarse sin versión de perfil y validación.

## Estado De Cumplimiento Del Repo

| Dimensión | Estado |
|---|---|
| Dominio no contaminado por FHIR | fuerte |
| FHIR como borde externo | inicial, ahora contractualizado |
| Core CL/NID | pendiente de mapping detallado por slice |
| SNOMED/LOINC/CIE/EIS | pendiente de política terminológica ejecutable |
| Identidad/EMPI | pendiente |
| Consentimiento digital | parcial en UX, falta contrato |
| Portabilidad ficha clínica | parcial en portal, falta spec |
| Auditoría | fuerte en intención, falta modelo/eventos concretos |
| Ciberseguridad/incidentes | inicial, falta plan y puertos |
| SNRE | reconocido como futuro gate |
| REM | fuerte como derivación, falta eval normativo final |

## Próximo Trabajo Recomendado

1. Refinar `docs/02-datos/modelo-datos-hd-hsc-os.md` en identidad física, consentimiento,
   auditoría, documentos y terminología antes de DDL.
2. Extender `Ingreso HODOM` con mapping FHIR mínimo: `Patient`,
   `ServiceRequest`, `Encounter`, `RelatedPerson`, `Consent`,
   `DocumentReference`.
3. Definir fixture de portabilidad y fixture de acceso delegado.
4. Antes de prescripción: crear spec SNRE/medicación.
