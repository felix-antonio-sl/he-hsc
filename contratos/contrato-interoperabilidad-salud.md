# Contrato de interoperabilidad en salud

Estado: canon operativo
Fecha: 2026-05-26

## Propósito

Fijar cómo `hd-hsc-os` interoperará con sistemas clínicos, regulatorios y
territoriales sin convertir FHIR, REM, SNRE, MPI ni otras arquitecturas externas
en el dominio interno del sistema.

El dominio sigue gobernado por `hd-opm`. La interoperabilidad vive como borde:
puertos en `aplicacion/`, adaptadores en `adaptadores/`, contratos verificables
en `docs/`.

## Fuentes Normativas Y Técnicas

| Fuente | Uso en este contrato |
|---|---|
| Ley 20.584 | ficha clínica, reserva, acceso, conservación, portabilidad y consentimiento |
| Ley 21.541 | salud digital y telemedicina |
| Ley 21.719 | datos personales, datos sensibles de salud, portabilidad y programa de cumplimiento |
| Ley 21.663 | ciberseguridad, servicios esenciales y seguridad por diseño |
| Resolución Exenta ANCI 7/2025 | reporte de incidentes significativos al CSIRT Nacional |
| Decreto Exento MINSAL 9/2023 | Norma Técnica 231 de Estándares de Información en Salud |
| Interoperabilidad MINSAL | arquitectura, FHIR R4, MPI, HPD, servicios terminológicos |
| Core CL / NID MINSAL | perfiles base para interoperabilidad nacional |
| SNRE MINSAL | receta electrónica cuando el slice implemente prescripción/dispensación |

URLs de referencia:

- `https://nuevo.leychile.cl/navegar?idNorma=1039348`
- `https://www.leychile.cl/navegar?idNorma=1190336`
- `https://nuevo.leychile.cl/navegar?idNorma=1209272`
- `https://www.leychile.cl/navegar?idNorma=1202434`
- `https://www.leychile.cl/navegar?idNorma=1211464`
- `https://www.bcn.cl/leychile/navegar?i=1189880`
- `https://interoperabilidad.minsal.cl/docs/especificacion-de-la-arquitectura/estandares-perfiles.html`
- `https://interoperabilidad.minsal.cl/fhir/ig/nid/0.4.8/index.html`
- `https://interoperabilidad.minsal.cl/fhir/ig/snre/0.9.6/index.html`

## Decisiones

| Decisión | Estado | Regla |
|---|---|---|
| FHIR | requerido como borde externo | usar FHIR R4 y perfiles chilenos vigentes cuando aplique |
| Core CL / NID | requerido para intercambio nacional | versionar perfiles usados y validar recursos |
| SNOMED CT | requerido para conceptos clínicos cuando exista binding | no persistir texto libre como código clínico |
| CIE-10 | requerido para reportería/estadística cuando aplique | usar como clasificación, no reemplazo de terminología clínica |
| LOINC | requerido para laboratorio/observaciones cuando aplique | activar al implementar resultados u observaciones codificadas |
| REM | derivado desde core | no usar planilla paralela como verdad primaria |
| SNRE | borde externo futuro | requerido antes de prescripción/dispensación interoperable |
| MPI/EMPI | abierto | debe resolverse antes de migración productiva o intercambio nacional |
| HPD/RNPI | abierto | requerido para interoperar prestadores individuales |
| Consent | requerido | consentimiento y revocación deben ser trazables y auditables |
| AuditEvent/Provenance | requerido | todo acceso, exportación o intercambio clínico sensible deja evidencia |

## Principios

1. El modelo interno habla HODOM; los adaptadores hablan FHIR.
2. Cada recurso FHIR exportado o importado debe tener mapping explícito.
3. Cada código clínico debe indicar `system`, `code`, `display`, versión cuando
   corresponda y estado de validación terminológica.
4. Toda operación de intercambio debe declarar propósito, base de licitud,
   destinatario, mínimo necesario y evidencia de auditoría.
5. Toda exportación por portabilidad debe producir formato estructurado y
   utilizable por otro sistema.
6. El paciente, su representante o tercero autorizado accede solo bajo las reglas
   de ficha clínica y consentimiento.
7. La salud digital y teleatención registran consentimiento, medio utilizado,
   identidad verificada y condiciones de la prestación.

## Mapeo Inicial Dominio -> FHIR

| Dominio `hd-hsc-os` | Recurso FHIR R4 esperado | Perfil/guía | Nota |
|---|---|---|---|
| `Paciente` | `Patient` | Core CL / NID `MINSALPaciente` cuando aplique | RUN/RUT como identificador chileno, más identificadores locales |
| Identidad paciente cruzada | `Patient`, `Person`, operaciones MPI | NID, PIXm/PDQm cuando aplique | no resolver con merge manual sin proveniencia |
| `Episodio HODOM` | `Encounter` | Core CL + perfil local HODOM futuro | unidad de atención longitudinal en modalidad domiciliaria |
| Solicitud de ingreso | `ServiceRequest` | Core CL o perfil local | derivación/admisión desde hospital/APS |
| Domicilio | `Patient.address`, `Location` | Core CL/EIS | dirección sensible; no exponer sin finalidad |
| Establecimiento | `Organization` | Core CL / MINSAL | responsable institucional del episodio |
| Profesional | `Practitioner`, `PractitionerRole` | HPD/Core CL | validar RNPI cuando se implemente |
| Colaborador de cuidado | `RelatedPerson`, `Consent` | Core CL + perfil local | permisos delegados con vigencia |
| Plan terapéutico y de cuidados | `CarePlan`, `Goal`, `Task` | Core CL + perfil local | plan por categorías de prestación |
| Atención profesional programada | `Encounter`, `Appointment`, `Task` | perfil local | la visita puede ser encounter operativo o actividad de plan |
| Prestación/procedimiento | `Procedure` | SNOMED CT / EIS / catálogo local | procedure solo si se ejecutó |
| Diagnóstico/problema | `Condition` | SNOMED CT + CIE-10 cuando aplique | CIE-10 para reportería/estadística |
| Signos vitales y hallazgos | `Observation` | LOINC/SNOMED CT | validar unidades y rangos |
| Prescripción | `MedicationRequest` | SNRE cuando aplique | no implementar prescripción interoperable sin SNRE gate |
| Dispensación/administración | `MedicationDispense`, `MedicationAdministration` | SNRE/local | separar medicamento físico de esquema farmacológico |
| Documento clínico | `DocumentReference`, `Composition`, `Binary` | Core CL/local | metadatos, hash, autor, custodia y acceso |
| Consentimiento | `Consent` | Core CL/local | incluye teleatención, acceso delegado y portabilidad |
| Evento adverso | `AdverseEvent` | FHIR R4/local | severidad, causalidad, cierre |
| Auditoría | `AuditEvent`, `Provenance` | FHIR R4 | acceso, exportación, firma, intercambio y reparación |
| REM | `MeasureReport` o export regulatorio específico | local/MINSAL | derivado desde core; no autoridad interna |

## Flujos De Intercambio

### Hospital/APS -> HODOM

Entrada esperada:

- `ServiceRequest` o payload equivalente de derivación;
- `Patient` identificable;
- antecedentes clínicos mínimos: `Condition`, `Observation`, `MedicationRequest`
  o documento adjunto;
- profesional/institución solicitante;
- base de contacto y consentimiento cuando corresponda.

Resultado:

- solicitud recibida;
- solicitud aceptada, rechazada o postergada;
- episodio abierto si cumple condiciones;
- auditoría de decisión.

### HODOM -> Hospital/APS

Salida esperada:

- resumen de episodio;
- plan vigente o plan de continuidad;
- documentos relevantes;
- estado de alta, reingreso o contrarreferencia;
- condiciones y medicamentos relevantes.

### HODOM -> Paciente/Cuidador

Salida esperada:

- información comprensible;
- documentos autorizados;
- auditoría de accesos;
- descarga/portabilidad FHIR cuando aplique;
- consentimiento y revocación trazables.

### HODOM -> MINSAL/DEIS/REM

Salida esperada:

- agregados derivados desde core;
- numeradores, denominadores, periodo, filtros y fuente declarados;
- ninguna fila identificable salvo obligación normativa específica.

### HODOM -> SNRE

Entrada/salida futura:

- validación de prescriptor y paciente;
- validación terminológica de fármacos;
- registro de prescripción;
- consulta/cambio de estado;
- notificación de dispensación.

Este flujo queda bloqueado hasta que exista spec de prescripción y ADR de
integración SNRE.

## Identidad Y EMPI

El sistema debe distinguir:

| Identidad | Uso |
|---|---|
| identificador interno opaco | claves propias del dominio/modelo |
| RUN/RUT | identificador nacional sensible, no clave primaria universal |
| identificadores fuente | migración, SGH, DAU, Drive, hdos |
| identificadores FHIR | `Patient.identifier` con `system` explícito |
| identidad consolidada | resultado de matching con proveniencia y auditoría |

Reglas:

- ningún merge de paciente sin evidencia y operación auditable;
- soporte para identidad desconocida/provisoria;
- soporte para extranjeros u otros identificadores;
- matching probabilístico nunca promociona sin gate o revisión humana;
- toda deduplicación conserva identificadores fuente.

## Terminología

| Dominio | Sistema esperado |
|---|---|
| diagnósticos, hallazgos, problemas | SNOMED CT; CIE-10 para estadística |
| procedimientos/prestaciones | SNOMED CT, EIS, catálogo local versionado |
| observaciones y laboratorio | LOINC cuando aplique |
| medicamentos | SNRE/terminología farmacéutica chilena cuando esté disponible |
| establecimientos/profesionales | HPD/MINSAL, RNPI cuando aplique |
| comunas/direcciones | EIS/geoespacial oficial |

Los catálogos locales deben publicarse como `CodeSystem`/`ValueSet` internos si
se usan en un adaptador FHIR, con `ConceptMap` hacia terminología oficial cuando
exista.

## Seguridad Y Privacidad Del Intercambio

`02-datos/contrato-seguridad-informacion-salud.md` gobierna los controles de
seguridad transversales. Esta sección sólo fija su aplicación al intercambio
clínico.

Todo intercambio clínico debe declarar:

- propósito;
- actor solicitante;
- paciente/episodio afectado;
- base de autorización o excepción legal;
- mínimo necesario;
- destinatario;
- recurso exportado/importado;
- resultado;
- `AuditEvent`/proveniencia;
- retención y revocación cuando aplique.

Controles mínimos:

- control de acceso por rol, objeto, episodio, establecimiento y situación;
- 2FA para acciones clínicas o administrativas críticas;
- cifrado en tránsito y reposo cuando haya datos sensibles;
- logs inmutables de acceso, exportación, firma y override;
- procedimiento de incidente y reporte;
- respaldo y restauración probada;
- separación entre datos clínicos y métricas agregadas.

## Gates Antes De Implementar Adaptadores FHIR

1. Mapping dominio -> FHIR documentado para los objetos del slice.
2. Versión de perfiles Core CL/NID/SNRE fijada en ADR o spec.
3. Validación de recursos contra perfiles.
4. Terminología validada por `TerminologyPort`.
5. Identidad paciente definida: local, RUN/RUT, fuente, EMPI.
6. Consentimiento y base de licitud definidos para export/import.
7. `AuditEvent`/proveniencia definidos.
8. Tests de no filtración de datos sensibles.
9. Política de portabilidad y formato de entrega definida.
10. Plan de error: recurso inválido, terminología inválida, paciente ambiguo,
    destinatario no autorizado, red caída.
