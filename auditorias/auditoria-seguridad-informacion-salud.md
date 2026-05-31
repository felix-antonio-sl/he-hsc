# Auditoría de seguridad de información en salud

Estado: borrador controlado
Tipo: auditoría transversal inicial
Fecha: 2026-05-26

## Propósito

Auditar `hd-hsc-os` desde seguridad de información en salud, revisando el repo
actual y dejando gates para que el futuro sistema incorpore SGSI, privacidad,
continuidad, gestión de incidentes y controles de acceso desde su diseño.

Esta auditoría no certifica cumplimiento legal ni reemplaza revisión
institucional. Traduce obligaciones y buenas prácticas en arquitectura
documental y criterios implementables.

## Resultado Ejecutivo

El repo parte con una ventaja fuerte: dominio puro, tecnología diferida y capas
separadas. Eso permite diseñar seguridad antes de elegir framework, base de
datos o proveedor de identidad.

La brecha principal era que seguridad aparecía como intención UX o como parte de
interoperabilidad, pero no como contrato propio. Faltaban clasificación de
activos, SGSI, matriz de acceso, auditoría resistente a manipulación, RTO/RPO,
gestión de secretos, incidentes y tratamiento seguro de migración.

Esta pasada deja esa dimensión anclada en:

- `02-datos/contrato-seguridad-informacion-salud.md`;
- `05-especificaciones/puertos/seguridad-informacion-salud.md`;
- `05-especificaciones/evals/seguridad-informacion-salud.md`;
- actualización de canon, roadmap, gates y primer slice.

## Auditoría Por Componente

| Componente | Estado encontrado | Riesgo | Acción |
|---|---|---|---|
| `CLAUDE.md` | capas limpias y dominio sin dependencias | no explicita SGSI ni continuidad | bajar reglas a docs sin modificar contrato madre |
| `00-canon/` | precedencia y memoria ya ordenadas | ANCI/CSIRT y seguridad no estaban como línea propia | enlazar contrato y auditoría de seguridad |
| `01-dominio/` | dominio clínico no contaminado por infraestructura | tentación de meter permisos como entidad clínica | dejar seguridad en aplicación/adaptadores y docs |
| `02-datos/` | modelo de datos y migración fuertes | faltaba clasificación, cifrado, retención, backup y logs | crear contrato de seguridad |
| `03-experiencia/` | seguridad visible, paciente correcto, offline | faltaba conectar UX con control de acceso y auditoría | cubrir por eval y puertos |
| `04-arquitectura/` | roadmap bloquea tecnología prematura | no exigía gate de seguridad antes de ADR | agregar gate de seguridad |
| `05-especificaciones/` | slices, puertos y evals ya existen | faltaba puerto/eval específico de seguridad | crear puerto y eval |
| `dominio/` | vacío, correcto | futuro riesgo de importar auth/roles | mantener dominio libre de seguridad técnica |
| `aplicacion/` | vacío | deberá definir puertos de acceso, auditoría y privacidad | puerto documentado |
| `adaptadores/` | vacío | futuro riesgo de acoplar proveedor IAM/DB al dominio | gate antes de adaptar |
| `interfaces/` | vacío | riesgo UX de fuga por pantallas/logs/export | eval de seguridad por slice |
| migración desde `hdos` | auditoría preparatoria existe | extracts con datos reales, logs o fixtures identificables | gate de anonimización, cifrado y cadena de custodia |

## Brechas Priorizadas

### S1. Inventario Y Clasificación De Activos

Riesgo: implementar tablas, logs o exports sin clasificar si contienen ficha
clínica, identidad, geolocalización, credenciales o secreto operacional.

Gate: cada slice declara activos y clasificación antes de persistencia.

### S2. Identidad, Acceso Y Mínimo Necesario

Riesgo: autorización por rol plano, sin episodio, establecimiento, finalidad ni
situación clínica.

Gate: matriz de acceso por acción, objeto, actor, finalidad y contexto.

### S3. Auditoría Resistente A Manipulación

Riesgo: logs útiles para debug pero insuficientes como evidencia de acceso,
exportación, firma, override o incidente.

Gate: evento de auditoría append-only o equivalente para toda operación sensible.

### S4. Migración Y Datos Reales

Riesgo: usar dumps, planillas, screenshots o fixtures con datos identificables
en desarrollo o documentación.

Gate: extracts controlados, cifrados, trazables y minimizados; fixtures
anonimizados o sintéticos.

### S5. Secretos, Configuración Y Proveedores

Riesgo: tokens, credenciales, URLs internas o llaves en repo, logs o variables
sin rotación.

Gate: política de secretos antes del primer adaptador.

### S6. Offline Y Dispositivos En Domicilio

Riesgo: cache local, borradores, fotos o rutas con datos clínicos en dispositivos
perdidos o compartidos.

Gate: cifrado local, expiración, bloqueo, wipe y sincronización auditable.

### S7. Continuidad Operacional

Riesgo: tratar disponibilidad como SLA genérico y no como continuidad de cuidado.

Gate: RTO/RPO por slice, modo degradado y prueba de restauración.

### S8. Incidentes Y CSIRT/ANCI

Riesgo: no tener clasificación ni ruta de reporte ante filtración, alteración,
indisponibilidad, phishing o credenciales comprometidas.

Gate: runbook de incidentes alineado con Ley 21.663, DS 295 y Resolución ANCI 7.

### S9. Derechos Del Titular Y Privacidad Operacional

Riesgo: portal, exportación y rectificación como features, no como derechos con
trazabilidad y límites.

Gate: flujo de acceso, rectificación, oposición, supresión, portabilidad y
bloqueo cuando aplique.

### S10. Terceros Y Encargados

Riesgo: proveedor cloud, mensajería, mapas, FHIR, teleatención o analítica sin
contrato de seguridad ni minimización.

Gate: todo tercero declara datos, finalidad, subencargados, ubicación,
retención, cifrado, auditoría e incidente.

## Gates Antes De ADR Tecnológico

Antes de elegir stack, identidad, nube, base de datos o proveedor:

1. `02-datos/contrato-seguridad-informacion-salud.md` debe estar aceptado.
2. `05-especificaciones/evals/seguridad-informacion-salud.md` debe aplicarse al
   primer slice.
3. Cada slice debe declarar:
   - activos y clasificación;
   - actores y finalidades;
   - matriz de acceso;
   - auditoría;
   - RTO/RPO si afecta continuidad;
   - tratamiento de logs, adjuntos, exports y respaldos;
   - incidente plausible y respuesta mínima.
4. Ningún adaptador puede requerir secretos en repo.
5. Ninguna migración o fixture puede usar datos reales sin cadena de custodia.

## Estado De Seguridad Del Repo

| Dimensión | Estado |
|---|---|
| dominio libre de infraestructura | fuerte |
| capa de seguridad contractual | inicial, ahora creada |
| clasificación de datos | inicial |
| matriz de acceso | pendiente |
| auditoría append-only | pendiente |
| derechos del titular | pendiente |
| continuidad RTO/RPO | pendiente institucional |
| secretos/KMS | pendiente ADR |
| incidentes CSIRT/ANCI | inicial, falta runbook |
| migración segura | inicial, falta cadena de custodia |
| seguridad de dispositivos/offline | parcial en UX, falta spec técnica |

## Próximo Trabajo Recomendado

1. Cerrar matriz de acceso para `Ingreso HODOM`.
2. Definir eventos mínimos de auditoría para `SolicitudRegistrada`,
   `SolicitudAceptada`, `EpisodioAbierto` y lectura de documentos.
3. Abrir ADR futura de identidad/autenticación solo después de matriz de acceso.
4. Definir RTO/RPO institucional para HODOM HSC.
5. Crear runbook mínimo de incidente antes de cualquier dato real o migración.
