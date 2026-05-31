# Eval: cumplimiento normativo e interoperabilidad

Estado: canon operativo
Tipo: eval transversal inicial
Fecha: 2026-05-26

## Propósito

Evaluar si un slice, componente, puerto o adaptador de `hd-hsc-os` cumple las
condiciones mínimas de normativa sanitaria, protección de datos, ciberseguridad e
interoperabilidad antes de considerarse listo para implementación o cutover.

## Entradas Obligatorias

| Entrada | Condición |
|---|---|
| objeto de dominio | explícito y vigente en `01-dominio/` |
| datos sensibles | clasificados y minimizados |
| propósito de tratamiento | declarado |
| actor y destinatario | identificados |
| base de autorización | consentimiento, continuidad de cuidado, obligación legal u otra |
| mapping FHIR | requerido si cruza frontera de interoperabilidad |
| terminologías | sistemas y value sets declarados |
| auditoría | evento esperado y retención |
| fallback | comportamiento ante red caída, servicio externo caído o perfil inválido |

## Checklist Normativo

| Dimensión | Pregunta |
|---|---|
| Ficha clínica | ¿El registro preserva completitud, acceso oportuno, confidencialidad y conservación? |
| Acceso titular | ¿Paciente/representante/tercero autorizado tienen flujo definido cuando aplica? |
| Portabilidad | ¿La información exportable usa formato estructurado y utilizable por otro sistema? |
| Consentimiento | ¿La aceptación/rechazo queda registrado con medio, fecha, actor y alcance? |
| Telemedicina | ¿La prestación remota registra identidad, medio, condiciones, consentimiento y nota clínica? |
| Datos sensibles | ¿RUT, dirección, teléfono, salud, biometría y menores tienen tratamiento explícito? |
| Minimización | ¿La vista/export usa solo lo necesario para su propósito? |
| Secreto/confidencialidad | ¿El acceso se limita a equipo tratante, titular o autorizados? |
| Retención | ¿El documento/registro declara política de custodia? |
| Seguridad por diseño | ¿Hay control de acceso, cifrado esperado, logs, backup y restauración? |
| Incidentes | ¿Existe clasificación y ruta de reporte si compromete confidencialidad, integridad o disponibilidad? |

## Checklist De Interoperabilidad

| Dimensión | Pregunta |
|---|---|
| FHIR R4 | ¿El intercambio usa recursos FHIR R4 o justifica excepción? |
| Perfil chileno | ¿Se valida contra Core CL/NID/SNRE u otro perfil aplicable? |
| Recurso correcto | ¿El objeto se mapea al recurso FHIR apropiado? |
| Identidad | ¿RUN/RUT, identificador local y fuente tienen `system` y proveniencia? |
| EMPI | ¿Paciente ambiguo queda bloqueado o en revisión, no fusionado por defecto? |
| Terminología | ¿SNOMED CT, CIE-10, LOINC, EIS o catálogo local están declarados? |
| ValueSet | ¿Los códigos están activos y dentro del value set esperado? |
| ConceptMap | ¿Existe mapa si se traduce desde catálogo local? |
| Provenance | ¿El recurso exportado conserva autor, fuente y fecha? |
| AuditEvent | ¿La lectura/export/import queda auditada? |
| Versionado | ¿Se fija versión de perfil, value set o guía usada? |

## Checklist De Recursos FHIR Por Slice

| Recurso | Cuándo exigirlo |
|---|---|
| `Patient` | cualquier flujo con identidad paciente |
| `Encounter` | episodio, visita o atención |
| `ServiceRequest` | derivación, solicitud de ingreso, exámenes/interconsultas |
| `RelatedPerson` | cuidador/representante/delegado |
| `Consent` | teleatención, acceso delegado, portabilidad, tratamiento específico |
| `CarePlan` | plan terapéutico y de cuidados |
| `Condition` | diagnóstico, problema, condición principal |
| `Observation` | signos vitales, hallazgos, resultados |
| `Procedure` | prestación/procedimiento ejecutado |
| `MedicationRequest` | prescripción |
| `MedicationDispense` | dispensación |
| `MedicationAdministration` | administración de medicamento |
| `DocumentReference` | documento clínico o adjunto |
| `Composition` | documento clínico estructurado |
| `Provenance` | autoría, fuente, firma, migración |
| `AuditEvent` | acceso, exportación, importación, firma, override |

## Gates Para `Ingreso HODOM`

El primer slice queda aceptable si:

1. declara si recibe derivación externa o solo ingreso interno;
2. si recibe derivación externa, define mapping mínimo a `ServiceRequest` y
   `Patient`;
3. abre episodio con equivalente futuro `Encounter`;
4. modela cuidador como `RelatedPerson` cuando haya delegado;
5. registra documentos mínimos como candidatos a `DocumentReference`;
6. todo acceso/cambio queda auditable;
7. no exporta ficha ni FHIR todavía si está fuera de alcance;
8. deja deuda explícita para EMPI, Core CL/NID y portabilidad si no se implementa
   en el corte.

## Gates Para Prescripción/Medicamentos

No implementar prescripción productiva sin:

- spec SNRE;
- validación de prescriptor;
- validación de paciente;
- terminología farmacológica definida;
- `MedicationRequest`;
- separación receta/dispensación/administración;
- auditoría y firma.

## Resultado

Estados permitidos:

- `cumple-para-slice`;
- `cumple-con-deuda-declarada`;
- `bloqueado-por-normativa`;
- `bloqueado-por-identidad`;
- `bloqueado-por-terminologia`;
- `bloqueado-por-seguridad`;
- `bloqueado-por-interoperabilidad`;
- `fuera-de-alcance-del-slice`.

## Regla

Una deuda normativa puede diferirse solo si:

1. no afecta seguridad del paciente;
2. no expone datos sensibles;
3. no bloquea continuidad de cuidado;
4. queda registrada como pérdida o alcance negativo;
5. tiene gate antes de producción o cutover.
