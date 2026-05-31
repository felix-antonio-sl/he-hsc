# Contrato de seguridad de información en salud

Estado: canon operativo
Fecha: 2026-05-26

## Propósito

Fijar las obligaciones mínimas de seguridad de información para `hd-hsc-os`
antes de implementar base de datos, autenticación, adaptadores, migración o
portal.

Este contrato no certifica cumplimiento legal. Convierte normativa sanitaria,
protección de datos y ciberseguridad en reglas de diseño verificables para el
futuro sistema HODOM HSC.

## Fuentes Normativas Y Técnicas

| Fuente | Uso en este contrato |
|---|---|
| Ley 20.584 | ficha clínica, reserva, acceso, conservación, continuidad, confidencialidad |
| Ley 21.541 | salud digital, telemedicina, seguridad de plataformas y consentimiento |
| Ley 21.719 | datos personales, datos sensibles de salud, derechos ARSOP, portabilidad, modelo de cumplimiento |
| Ley 21.663 | ciberseguridad, servicios esenciales, gestión de incidentes, ANCI/CSIRT |
| Decreto Supremo 295/2024 | reglamento de reporte de incidentes de ciberseguridad |
| Resolución Exenta ANCI 7/2025 | taxonomía y canal de reporte de incidentes significativos |
| ISO/IEC 27001:2022 | SGSI, riesgo, controles, mejora continua |
| NIST CSF 2.0 | gobernar, identificar, proteger, detectar, responder y recuperar |

Nota temporal: Ley 21.719 tiene vigencia diferida al 1 de diciembre de 2026.
Para `hd-hsc-os` se trata como requisito de diseño desde el inicio, no como
deuda futura.

URLs de referencia:

- `https://nuevo.leychile.cl/navegar?idNorma=1039348`
- `https://www.leychile.cl/navegar?idNorma=1190336`
- `https://nuevo.leychile.cl/navegar?idNorma=1209272`
- `https://www.bcn.cl/leychile/navegar?i=1202434`
- `https://www.bcn.cl/leychile/Navegar?idNorma=1211466`
- `https://www.leychile.cl/navegar?idNorma=1211464`
- `https://www.iso.org/standard/27001`
- `https://www.nist.gov/cyberframework`

## Activos De Información

| Activo | Clasificación mínima | Riesgo dominante |
|---|---|---|
| identidad paciente, RUN/RUT, domicilio, teléfono | sensible salud / identificable | exposición, suplantación, uso secundario |
| ficha clínica, documentos, epicrisis, indicaciones | sensible salud | acceso indebido, alteración, pérdida |
| episodio, plan, visitas, prestaciones, eventos | sensible salud | alteración clínica, pérdida de continuidad |
| cuidador/representante y permisos delegados | confidencial / sensible contextual | acceso delegado indebido |
| geolocalización, ruta, domicilio operativo | sensible contextual | riesgo físico, exposición territorial |
| credenciales, sesiones, tokens, llaves, secretos | secreto operacional | compromiso sistémico |
| logs de auditoría y seguridad | confidencial crítico | manipulación, borrado, no repudio fallido |
| respaldos, exports, bundles FHIR, migración | sensible salud masivo | fuga de gran escala |
| métricas agregadas, REM, analítica | interno / agregado | reidentificación si granularidad insuficiente |
| código fuente, configuración, infraestructura | secreto operacional | explotación técnica |

Regla: ningún fixture, log, screenshot, documento o prompt de trabajo puede
contener datos identificables reales salvo autorización explícita, canal seguro y
necesidad operacional documentada.

## Clasificación De Datos

| Clase | Ejemplos | Reglas |
|---|---|---|
| público | documentación técnica sin datos reales | publicable |
| interno | roadmap, specs, métricas no sensibles | acceso staff/proyecto |
| confidencial | operación, agenda, capacidad, configuración | mínimo necesario |
| sensible salud | ficha, diagnósticos, medicamentos, documentos | acceso por finalidad asistencial o base legal |
| secreto operacional | credenciales, llaves, tokens, configs, hashes | nunca en repo ni logs; rotación y bóveda |

## Principios De Seguridad

1. Seguridad por diseño antes de stack.
2. Mínimo necesario por defecto.
3. Acceso condicionado por actor, rol, episodio, establecimiento, finalidad y
   situación clínica.
4. Ficha clínica y datos de salud son sensibles aunque estén en sistemas de
   prueba, exports, respaldos o logs.
5. Todo acceso relevante es auditable y resistente a manipulación.
6. Toda acción irreversible o de alto riesgo requiere ceremonia proporcional.
7. Toda exportación, migración o integración cruza un gate de privacidad,
   autorización, auditoría y cifrado.
8. Continuidad operacional es requisito clínico, no tarea de infraestructura
   tardía.

## Controles Mínimos

### Gobierno Y SGSI

- inventario de activos;
- matriz de riesgos;
- responsables de tratamiento y seguridad;
- evaluación de impacto de protección de datos cuando haya tratamiento masivo,
  datos sensibles, perfilamiento, interoperabilidad o teleatención;
- política de terceros/encargados;
- revisión periódica de controles y deuda.

### Identidad Y Acceso

- autenticación fuerte para staff;
- 2FA para acciones clínicas, administrativas o de seguridad críticas;
- autorización por rol, objeto, episodio, establecimiento y contexto;
- separación entre rol clínico, coordinación, administración y soporte;
- acceso excepcional `break-glass` con razón obligatoria, expiración y auditoría;
- revocación inmediata de acceso ante salida de equipo o cambio de función;
- sesiones con expiración, bloqueo y registro de dispositivo.

### Protección De Datos

- cifrado en tránsito;
- cifrado en reposo para datos sensibles y respaldos;
- gestión explícita de llaves y secretos;
- seudonimización para análisis cuando no se requiere identidad directa;
- anonimización irreversible para fixtures públicos o documentación;
- retención alineada con ficha clínica y obligaciones regulatorias;
- minimización de logs, trazas, errores y telemetría.

### Auditoría

- log append-only o equivalente resistente a manipulación;
- evento por lectura, escritura, exportación, firma, override, break-glass,
  acceso delegado, importación, migración y error de autorización;
- correlación entre actor, sesión, paciente, episodio, objeto, finalidad,
  timestamp y resultado;
- revisión de accesos anómalos;
- evidencia exportable para auditoría interna, titular o autoridad cuando
  corresponda.

### Continuidad Operacional

- RTO/RPO explícitos por slice y por activo;
- respaldos cifrados;
- restauración probada;
- modo degradado para atención domiciliaria;
- cola offline cifrada y borrable;
- runbook de indisponibilidad;
- priorización clínica si sistema, red o proveedor externo cae.

### Incidentes

- clasificación por confidencialidad, integridad, disponibilidad y uso legítimo;
- severidad y responsable de triage;
- preservación de evidencia;
- comunicación interna y escalamiento;
- ruta de reporte CSIRT/ANCI cuando aplique;
- postmortem sin culpa, con acciones correctivas y cierre verificable.

## Gates Antes De Implementar

1. Clasificación de activos y datos tocados por el slice.
2. Actor, finalidad y base de autorización por operación sensible.
3. Matriz de acceso y excepción `break-glass`.
4. Eventos de auditoría definidos.
5. Política de logs sin datos sensibles innecesarios.
6. RTO/RPO y modo degradado si el slice afecta continuidad asistencial.
7. Tratamiento de exports, adjuntos, respaldos y migración.
8. Gestión de secretos y configuración fuera de repo.
9. Plan de incidente para fuga, alteración, indisponibilidad y credenciales.
10. Eval `05-especificaciones/evals/seguridad-informacion-salud.md` aplicado.

## Decisiones Abiertas

| Decisión | Estado |
|---|---|
| proveedor de identidad | futura ADR |
| modelo RBAC/ABAC concreto | futura ADR |
| bóveda de secretos y KMS | futura ADR |
| RTO/RPO institucional | pendiente con HSC |
| clasificación OIV/servicio esencial aplicable al sistema | pendiente institucional |
| política de acceso de soporte técnico | pendiente |
| política de retención de logs de seguridad | pendiente |
| procedimiento de derechos ARSOP | pendiente |
| certificación/acreditación de plataforma de salud digital | pendiente normativa/ADR |
