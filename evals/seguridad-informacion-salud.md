# Eval: seguridad de información en salud

Estado: canon operativo
Tipo: eval transversal inicial
Fecha: 2026-05-26

## Propósito

Evaluar si un slice, componente, puerto, adaptador, migración o ADR de
`hd-hsc-os` cumple las condiciones mínimas de seguridad de información en salud
antes de implementación, exposición a datos reales o cutover.

## Entradas Obligatorias

| Entrada | Condición |
|---|---|
| activo de información | explícito y clasificado |
| dato sensible | identificado, minimizado y protegido |
| actor | rol, responsabilidad y relación con episodio |
| finalidad | declarada por operación sensible |
| base de autorización | continuidad de cuidado, consentimiento, obligación legal u otra |
| política de acceso | regla allow/deny/review/break-glass |
| auditoría | evento, retención y consulta esperada |
| logs y errores | sin datos sensibles innecesarios |
| continuidad | RTO/RPO o justificación de no aplicar |
| incidente plausible | clasificación y ruta de respuesta |

## Checklist De Gobierno

| Dimensión | Pregunta |
|---|---|
| Activos | ¿El slice declara qué información crea, lee, modifica, exporta o elimina? |
| Clasificación | ¿Cada dato está clasificado como público, interno, confidencial, sensible salud o secreto operacional? |
| Finalidad | ¿Cada tratamiento sensible tiene propósito explícito? |
| Minimización | ¿La operación usa sólo lo necesario? |
| Responsable | ¿Hay dueño funcional del dato/control? |
| Terceros | ¿Se declara proveedor, encargado o sistema externo si aplica? |

## Checklist De Acceso

| Dimensión | Pregunta |
|---|---|
| Autenticación | ¿La operación requiere identidad de actor? |
| Autorización | ¿La decisión usa acción, objeto, episodio, establecimiento, rol y contexto? |
| Acceso delegado | ¿Paciente/cuidador/representante tienen alcance y vigencia? |
| Break-glass | ¿Existe razón, expiración, auditoría y revisión posterior? |
| Sesión | ¿La operación crítica considera expiración o segundo factor? |
| Denegación | ¿El error no revela datos clínicos ni existencia de paciente? |

## Checklist De Protección

| Dimensión | Pregunta |
|---|---|
| Cifrado | ¿Datos sensibles, adjuntos, exports y respaldos se cifran cuando aplique? |
| Secretos | ¿No hay credenciales, tokens ni llaves en repo, logs o fixtures? |
| Logs | ¿Errores y telemetría minimizan datos personales? |
| Offline | ¿Cache, borradores, fotos y cola local están protegidos? |
| Retención | ¿La conservación o eliminación está declarada? |
| Anonimización | ¿Datos reales usados para prueba tienen manifest de anonimización o síntesis? |

## Checklist De Auditoría

| Dimensión | Pregunta |
|---|---|
| Lectura | ¿Se audita lectura de ficha/documento cuando corresponde? |
| Escritura | ¿Se audita cambio clínico o administrativo relevante? |
| Exportación | ¿Se audita descarga, envío, bundle FHIR o portabilidad? |
| Consentimiento | ¿Se audita aceptación, rechazo y revocación? |
| Integridad | ¿El log es resistente a manipulación o sellado por lotes? |
| Consulta | ¿Existe forma autorizada de consultar auditoría? |

## Checklist De Continuidad E Incidentes

| Dimensión | Pregunta |
|---|---|
| RTO/RPO | ¿El slice declara tolerancia a indisponibilidad y pérdida de datos? |
| Modo degradado | ¿Qué se hace si sistema, red o proveedor cae? |
| Backup | ¿La información crítica tiene respaldo esperado? |
| Restauración | ¿Hay evidencia o gate de prueba de restauración? |
| Incidente | ¿Se clasifican fuga, alteración, indisponibilidad y credenciales? |
| Reporte | ¿Existe ruta CSIRT/ANCI si el incidente es significativo? |

## Gates Para `Ingreso HODOM`

El primer slice queda aceptable si:

1. clasifica paciente, RUN/RUT, domicilio, contacto, cuidador, solicitud,
   documento y episodio;
2. define quién puede crear, leer, aceptar, rechazar y abrir episodio;
3. exige finalidad para lectura o cambio de información clínica;
4. registra auditoría de solicitud, decisión, apertura, documento y denegación;
5. no guarda datos reales en fixtures, screenshots, logs ni docs;
6. declara manejo de sesión o segundo factor para decisión crítica si aplica;
7. define comportamiento si red o sistema caen durante ingreso;
8. declara incidente plausible y ruta de escalamiento.

## Resultado

Estados permitidos:

- `cumple-para-slice`;
- `cumple-con-deuda-declarada`;
- `bloqueado-por-acceso`;
- `bloqueado-por-datos-sensibles`;
- `bloqueado-por-auditoria`;
- `bloqueado-por-secretos`;
- `bloqueado-por-continuidad`;
- `bloqueado-por-incidente`;
- `fuera-de-alcance-del-slice`.

## Regla

Una deuda de seguridad puede diferirse solo si:

1. no expone datos sensibles reales;
2. no permite acceso clínico indebido;
3. no bloquea continuidad asistencial;
4. no impide auditoría de una acción crítica;
5. queda registrada con gate antes de producción, migración o cutover.
