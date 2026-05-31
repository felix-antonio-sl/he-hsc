# Análisis de Hacking Ético — Sistemas SS Ñuble / Hospital de San Carlos

Fecha: 2026-05-31
Tipo: análisis ofensivo pasivo (sin conexiones activas, sin escaneo)
Fuente: reconstrucción forense desde `hsc-agent-cli` — el código documenta el comportamiento real de los sistemas
Clasificación: CONFIDENCIAL — contiene vectores de ataque explotables contra sistemas de salud en producción

---

## RESUMEN EJECUTIVO

Tres sistemas clínicos PHP legacy (SGH, DAU, LIS) + un ESB nacional operan sobre HTTP plano
detrás de un proxy único (`100.77.30.26`). La superficie de ataque es amplia y las defensas
son inexistentes para estándares modernos. Un atacante con acceso al segmento de red del
hospital puede comprometer la confidencialidad, integridad y disponibilidad de todos los datos
clínicos sin necesidad de explotar vulnerabilidades de software — el protocolo de transporte
por sí solo es la vulnerabilidad.

---

## 1. SUPERFICIE DE ATAQUE

```
                         INTERNET
                            │
              ┌─────────────┴─────────────┐
              │  esb.saludenred.cl        │  ← MITM trivial (TLS deshabilitado)
              │  :8201 token              │
              │  :8095-8099 clínicos      │
              └─────────────┬─────────────┘
                            │
              ┌─────────────┴─────────────┐
              │    100.77.30.26 (proxy)   │  ← SPOF + sniffer central
              │                           │
              │  :8080 DAU  HTTP plano    │  ← captura de sesiones
              │  :8085 SGH  HTTP plano    │  ← inyección de datos clínicos
              │  :8084 LIS  HTTP plano    │  ← exfiltración masiva
              └───────────────────────────┘
```

### Activos en riesgo

| Activo | Sistema | Superficie |
|--------|---------|------------|
| PHPSESSID (sesión clínica activa) | SGH, DAU, LIS | Capturable en red, texto plano en disco |
| Credenciales (usuario+contraseña) | SGH, DAU, LIS | Envío HTTP POST sin cifrar, `/proc/<pid>/environ` |
| Fichas clínicas completas | SGH, DAU | HTML sin cifrar en tránsito |
| Resultados de laboratorio | LIS | PDFs + HTML sin cifrar |
| TokenSesion ESB (acceso nacional) | HCC/ESB | Query string HTTP, logueable |
| AccessToken ESB | HCC/ESB | Viaja en HTML de SGH sobre HTTP |
| IDRyF (identificador nacional) | HCC/ESB | Expuesto en JSON de salida |
| Censo de pacientes | SGH | Un solo endpoint vuelca todos los pacientes |
| Board de urgencia | DAU | Sin autenticación adicional por paciente |

---

## 2. VECTORES DE ATAQUE POR SISTEMA

### 2.1 SGH (Sistema de Gestión Hospitalaria — :8085)

#### V-SGH-1 [CRÍTICO] Captura de sesión por sniffing de red
- **Vector:** HTTP plano. PHPSESSID viaja en texto claro en cada request.
- **Explotación:** tcpdump/Wireshark en el segmento `100.77.30.0/24` captura la cookie.
- **Impacto:** sesión clínica completa. El atacante puede:
  - Consultar cualquier paciente por RUT (`obt_paciente.php`)
  - Leer evoluciones, diagnósticos, medicación, documentos PDF
  - Volcar el censo completo de pacientes hospitalizados
  - Acceder a datos de los 7 hospitales del SS Ñuble (`cambiar_hospital.php`)
- **Detección:** Ninguna. Sin logs de acceso.

#### V-SGH-2 [CRÍTICO] Fuerza bruta de credenciales sin protección
- **Vector:** `funciones/autenticacion.php` no tiene rate limiting visible. Responde 200 con `login_form` en body en caso de falla — sin delay, sin lockout.
- **Explotación:** diccionario de usuarios comunes (`admin`, `medico`, `enfermera`) + contraseñas débiles.
- **Indicio:** el CLI implementa 3 retries con backoff porque el SGH "es inestable bajo carga" — esto sugiere que el servidor ya está al límite. Un ataque de fuerza bruta podría causar DoS incidental.

#### V-SGH-3 [ALTO] Acceso cross-hospital sin control
- **Vector:** `cambiar_hospital.php` acepta `hh=<hospital_id>` sin verificar que el usuario tenga permisos en ese hospital.
- **Explotación:** POST `hh=1` cambia de San Carlos a Herminda Martin. Misma PHPSESSID.
- **Impacto:** un usuario legítimo de San Carlos accede a datos de Herminda Martin. O un atacante que compromete credenciales de un hospital pequeño (Coelemu, ID=4) pivotea a San Carlos (ID=2) donde hay más pacientes.

#### V-SGH-4 [ALTO] Enumeración de pacientes por RUT
- **Vector:** `obt_paciente.php?rut=<num>&v=<dv>` no tiene rate limiting. Responde 200 con HTML (con o sin datos).
- **Explotación:** iterar RUTs secuencialmente (los RUT chilenos son predecibles: ~8M a ~27M). Un script puede identificar qué RUTs tienen ficha en el hospital.
- **Impacto:** enumeración de pacientes del hospital + determinación de quién está hospitalizado (el censo revela estado activo).

#### V-SGH-5 [MEDIO] Inyección de parámetros en `ver_pdf.php`
- **Vector:** `ver_pdf.php?form=<tipo>&id=<ingreso_id>`. `ingreso_id` es incremental y predecible.
- **Explotación:** iterar `id` y acceder a documentos (epicrisis, ingresos, recetas) de cualquier paciente.
- **Mitigante parcial:** el CLI implementa verificación de identidad extrayendo RUT del PDF vía `pdftotext`. Pero el SGH mismo no protege el endpoint — cualquier sesión válida accede a cualquier documento.

#### V-SGH-6 [MEDIO] HTML injection en evoluciones
- **Vector:** `cargar_historial_evolucion.php` retorna HTML con contenido clínico libre. Si el SGH no sanitiza la entrada de texto de evoluciones, un usuario malicioso podría inyectar HTML/JS.
- **Explotación:** un médico o enfermera con acceso de escritura al SGH inyecta `<script>` en una evolución. El HTML se sirve a otros usuarios y al CLI (que lo parsea con regex).
- **Impacto:** XSS persistente. Robo de PHPSESSID de otros clínicos que vean la evolución.

### 2.2 DAU (Departamento de Atención de Urgencia — :8080)

#### V-DAU-1 [CRÍTICO] Exfiltración del board de urgencia
- **Vector:** `listadoPacientesBox.php` expone nombre, edad, motivo de consulta, box, categoría ESI, médico tratante y tiempo de espera de todos los pacientes en urgencia. Sin RUT, pero con nombre completo.
- **Explotación:** una sola request GET con sesión válida.
- **Impacto:** violación de privacidad de todos los pacientes en urgencia. Datos vendibles (seguros, empleadores, prensa).

#### V-DAU-2 [ALTO] Triage endpoint sin control de acceso por paciente
- **Vector:** `listadoTriage.php?c=<codAdmision>` — `codAdmision` es secuencial.
- **Explotación:** iterar `codAdmision` y acceder a triage de cualquier paciente: signos vitales, alergias, antecedentes mórbidos, medicación crónica, motivo de consulta.
- **Impacto:** historia clínica de urgencia de cualquier paciente que haya pasado por el servicio.

#### V-DAU-3 [ALTO] Silent data loss en endpoint CIE-10
- **Vector:** `obtener_cie.php` responde con `<tbody></tbody>` vacío si se llama por POST en vez de GET.
- **Explotación:** si un integrador (o el CLI) usa POST por error, los diagnósticos aparecen como "sin datos" — falso negativo con consecuencias clínicas.
- **Impacto:** decisión clínica basada en datos incompletos. Un atacante que pueda forzar el método HTTP (e.g., proxy inverso mal configurado) puede ocultar diagnósticos.

#### V-DAU-4 [MEDIO] Fuga de identidad en atención cerrada
- **Vector:** `atencion/index.php?a=<id>` retorna hidden fields vacíos cuando la atención está cerrada (paciente ya hospitalizado o dado de alta).
- **Explotación:** no es explotable directamente, pero es un punto ciego que un atacante puede usar para evadir correlación de identidad.
- **Impacto:** pérdida de trazabilidad forense. Un atacante que manipule una atención cerrada borra el rastro de identidad.

#### V-DAU-5 [MEDIO] HTML injection en notas clínicas
- **Vector:** `obtener_anamnesis.php`, `obtener_examen_fisico.php`, `obtener_hipotesis.php` retornan texto libre en `onclick="mostrar_*(id,'<texto>')"`. Si el DAU no sanitiza el input, el texto puede contener `'` que rompa el atributo HTML e inyecte JS.
- **Explotación:** un clínico con acceso de escritura inyecta `'); alert(document.cookie); //` en una nota.
- **Impacto:** XSS persistente. Robo de sesiones de otros usuarios del DAU.

### 2.3 LIS (Laboratory Information System — :8084)

#### V-LIS-1 [CRÍTICO] Acceso a resultados de cualquier paciente por RUT
- **Vector:** `resultadoseleccion.php` acepta `rut=<num>&BotonAccion=Buscar`. Sin verificación de relación clínico-paciente, sin registro de acceso.
- **Explotación:** con una sesión LIS válida, consultar cualquier RUT y obtener todos los exámenes validados. Sin límite de rate.
- **Impacto:** violación masiva de privacidad. Resultados de VIH, drogas, embarazo, marcadores tumorales — todo accesible sin trazabilidad.

#### V-LIS-2 [ALTO] RUT sin dígito verificador — colisión de identidad
- **Vector:** el LIS recibe `rut` sin DV (`12345678` sin el `-5`).
- **Explotación:** un error de tipeo en el RUT (12345678 vs 12345679) devuelve resultados de otro paciente. El LIS no detecta ni previene esto.
- **Impacto:** resultado de laboratorio atribuido al paciente equivocado → decisión clínica errónea.

#### V-LIS-3 [MEDIO] PDF sin protección de identidad
- **Vector:** `detalleexamenes.php?id=X&user=Y` sirve PDFs sin DRM, sin marca de agua, sin registro de descarga.
- **Explotación:** iterar `id` (secuencial) descarga todos los PDFs de laboratorio del hospital.
- **Impacto:** exfiltración masiva de resultados de laboratorio en formato imprimible.

#### V-LIS-4 [MEDIO] Ejecución de `pdftotext` sobre PDFs del servidor
- **Vector:** el CLI ejecuta `pdftotext` sobre PDFs servidos por `detalleexamenes.php`. Si el LIS es comprometido y sirve un PDF malicioso, el ataque se propaga al host del CLI.
- **Explotación:** comprometer el LIS → servir PDF con exploit de poppler → ejecución de código en la máquina donde corre el CLI.
- **Impacto:** pivoteo de LIS a infraestructura de agentes AI.

### 2.4 HCC / ESB Salud En Red (esb.saludenred.cl)

#### V-ESB-1 [CRÍTICO] TLS deshabilitado — MITM completo
- **Vector:** `InsecureSkipVerify: true` en `newESBHTTPClient`. Cualquier certificado es aceptado.
- **Explotación:** ARP spoofing + certificado autofirmado. El atacante se interpone entre el proxy `100.77.30.26` y `esb.saludenred.cl`.
- **Impacto:** captura de TokenSesion y AccessToken → acceso a la red nacional de salud. Lectura y modificación de resúmenes clínicos, epicrisis, diagnósticos. Inyección de datos falsos en el historial clínico compartido.

#### V-ESB-2 [ALTO] Token en query string — logueable
- **Vector:** `?ParametroFUC={"TokenSesion":"<token>",...}`. Los query strings son logueados por default en proxies, load balancers y servidores web.
- **Explotación:** acceder a logs del proxy `100.77.30.26` o del ESB → extraer TokenSesion de líneas de log.
- **Impacto:** reuso de token por cualquier persona con acceso a los logs.

#### V-ESB-3 [ALTO] AccessToken viaja en HTML sobre HTTP
- **Vector:** el bridge de identidad DAU→SGH→visor coloca el AccessToken en el HTML del SGH (`visor.saludenred.cl/#/rut/tipo/idryf/access%2Ftoken`). Este HTML viaja sobre HTTP plano desde :8085.
- **Explotación:** sniffing de red en el segmento del proxy captura el AccessToken en texto claro.
- **Impacto:** con AccessToken, el atacante obtiene TokenSesion (paso 4 del bridge) y acceso clínico nacional.

#### V-ESB-4 [MEDIO] Token de sesión sin scope por paciente
- **Vector:** `TokenSesion` autoriza acceso a cualquier endpoint clínico (8095-8099) para cualquier paciente cuyo IDRyF sea conocido.
- **Explotación:** una vez obtenido el token, iterar IDRyF o usar RUTs conocidos.
- **Impacto:** acceso irrestricto a la red Salud En Red. El token no está atado a un paciente ni episodio específico.

#### V-ESB-5 [BAJO] IDRyF expuesto como identificador nacional
- **Vector:** `IdentityCheck` en la respuesta JSON del CLI incluye `idryf`. Aunque el CLI es interno, este dato está en outputs que pueden ser logueados o cacheados.
- **Impacto:** correlación de pacientes entre sistemas usando un identificador nacional.

---

## 3. ESCENARIOS DE ATAQUE COMPUESTOS

### Escenario A: Compromiso del segmento de red
```
Atacante con acceso a 100.77.30.0/24 (empleado, contratista, dispositivo IoT comprometido)
  │
  ├─ tcpdump puerto 8085 → captura PHPSESSID de SGH
  ├─ tcpdump puerto 8080 → captura PHPSESSID de DAU
  ├─ tcpdump puerto 8084 → captura PHPSESSID de LIS
  │
  ├─ Con PHPSESSID de SGH:
  │   · listado_datos_camas_pacientes.php → censo completo
  │   · obte_paciente.php por cada RUT → fichas
  │   · cambiar_hospital.php hh=1..7 → datos de toda la red SS Ñuble
  │   · ver_pdf.php iterando ingreso_id → todos los PDFs
  │
  ├─ Con PHPSESSID de DAU:
  │   · listadoPacientesBox.php → board de urgencia
  │   · obtener_cie.php, obtener_anamnesis.php... → fichas clínicas
  │
  ├─ Con PHPSESSID de LIS:
  │   · resultadoseleccion.php para cada RUT → resultados de lab
  │   · detalleexamenes.php iterando id → PDFs de resultados
  │
  └─ Con tráfico hacia ESB:
      · TokenSesion del query string → acceso nacional
      · AccessToken del HTML de SGH → renovación de token
```
**Resultado:** exfiltración completa de datos clínicos de los 7 hospitales del SS Ñuble
+ acceso a la red nacional Salud En Red. Tiempo estimado: horas. Detección: ninguna.

### Escenario B: Compromiso de credenciales débiles
```
Atacante con acceso a un endpoint del proxy (sin estar en la red)
  │
  ├─ Fuerza bruta a funcionales/autenticacion.php (SGH)
  │   · sin rate limiting, sin lockout, sin CAPTCHA
  │   · 200 con login_form en body = más rápido que 401 (no hay overhead de error HTTP)
  │
  └─ Con credenciales válidas de SGH:
      · Mismo alcance que Escenario A para SGH + cross-hospital
```
**Resultado:** compromiso remoto sin necesidad de acceso físico a la red.

### Escenario C: Pivoteo desde un hospital pequeño a toda la red
```
Atacante compromete credenciales del Hospital de Coelemu (ID=4, el más pequeño)
  │
  ├─ Login en SGH (misma instancia para los 7 hospitales)
  ├─ cambiar_hospital.php hh=2 → San Carlos
  ├─ Acceso a datos de San Carlos (hospital principal)
  ├─ cambiar_hospital.php hh=1 → Herminda Martin (hospital base del SS Ñuble)
  │
  └─ Acceso a datos de los 7 hospitales con credenciales del más débil
```
**Resultado:** el eslabón más débil de la cadena (hospital pequeño con menos recursos de seguridad) compromete toda la red asistencial.

### Escenario D: MITM contra ESB — inyección de datos clínicos falsos
```
Atacante en posición MITM entre 100.77.30.26 y esb.saludenred.cl
  │
  ├─ ARP spoofing + certificado autofirmado (TLS no verifica)
  ├─ Intercepta respuestas de ESB :8099 (detalle secundaria con epicrisis)
  ├─ Modifica XMLDetalleHistoria:
  │   · cambia diagnósticos (agrega/elimina condiciones)
  │   · modifica medicación (alergias, dosis)
  │   · altera epicrisis de alta
  │
  └─ Reenvía respuesta modificada al visor clínico
```
**Resultado:** datos clínicos falsos inyectados en el historial compartido. Decisiones
médicas basadas en información adulterada. Potencial de daño clínico directo a pacientes.

---

## 4. CLASIFICACIÓN DE RIESGOS POR IMPACTO CLÍNICO

| Riesgo | Probabilidad | Impacto clínico | Severidad |
|--------|-------------|-----------------|-----------|
| Exfiltración masiva de fichas | Alta (HTTP plano, sin detección) | Confidencialidad total | **Crítico** |
| Acceso cross-hospital | Alta (cambiar_hospital.php sin control) | Confidencialidad 7 hospitales | **Crítico** |
| MITM ESB — inyección de datos | Media (requiere posición MITM) | Integridad de historial nacional | **Crítico** |
| Enumeración de pacientes por RUT | Alta (sin rate limiting) | Privacidad + ingeniería social | **Alto** |
| Resultados de lab sin trazabilidad | Alta (sin binding a episodio) | Privacidad + error clínico | **Alto** |
| Acceso a documentos por ID secuencial | Alta (ver_pdf.php sin control) | Confidencialidad | **Alto** |
| RUT sin DV en LIS | Media (requiere error de tipeo) | Error diagnóstico | **Alto** |
| CIE-10 falso negativo por método HTTP | Baja (requiere error de integración) | Decisión clínica errónea | **Medio** |
| XSS en evoluciones/notas | Baja (requiere acceso de escritura) | Robo de sesiones | **Medio** |
| TokenSesion en logs | Media (logs típicamente accesibles) | Reuso de sesión | **Medio** |

---

## 5. VULNERABILIDADES ESTRUCTURALES (no parcheables sin redesign)

### 5.1 HTTP como protocolo de transporte clínico
Los 3 sistemas usan HTTP. Migrar a HTTPS requiere cambios en los servidores PHP, no en el
proxy. Esto no es un parche — es un redeploy de los sistemas legacy con certificados.

### 5.2 PHPSESSID como único mecanismo de sesión
No hay refresh tokens, no hay segundo factor, no hay firmas de request. El PHPSESSID es
simultáneamente autenticación y autorización. Su robo equivale a acceso total.

### 5.3 Identidad por RUT, no porMPI
No hay un master patient index que correlacione identidad entre sistemas. El RUT es la
llave compartida, pero el LIS ni siquiera valida el dígito verificador.

### 5.4 Multi-tenancy por variable de sesión PHP
La segregación entre hospitales depende de `$_SESSION['hospital_id']`. No hay RLS a nivel
de base de datos, no hay segregación de red, no hay controles de acceso por establecimiento.

### 5.5 Proxy único como punto de fallo y concentrador de tráfico
100.77.30.26 concentra las conexiones a DAU, SGH, LIS y ESB. Un compromiso del proxy
(o del segmento de red) expone todo el tráfico clínico del SS Ñuble.

### 5.6 Cero estándares de interoperabilidad
Sin FHIR, sin HL7, sin DICOM, sin LOINC, sin SNOMED. La integración entre sistemas
depende de scraping HTML con regex. Cada cambio de UI en un PHP rompe la integración.

---

## 6. QUÉ ES DEFENDIBLE Y QUÉ NO

### Lo que hd-hsc-os PUEDE resolver (y debe)

| Problema | Cómo lo resuelve hd-hsc-os |
|----------|---------------------------|
| HTTP plano | HTTPS + TLS 1.3 desde el día 1 |
| PHPSESSID como única sesión | Argon2 + sesiones httpOnly + 2FA |
| Sin RBAC | RBAC por action×object×episode×establecimiento (ADR 0016) |
| Sin auditoría | Audit event append-only (F6 immutability, ADR 0005) |
| RUT sin validación | UUID v7 interno + RUT como source_identifier |
| Caché en texto plano | IndexedDB con cifrado |
| Sin cifrado en reposo | PostgreSQL con pgcrypto/KMS |
| Sin segregación multi-tenant | RLS PostgreSQL por establishment_id (ADR 0007, D8) |
| Sin interoperabilidad estándar | FHIR R4 + Core CL + NID como borde externo |
| Dependencia del proxy | PWA offline, PostgreSQL local |

### Lo que hd-hsc-os NO puede resolver

| Problema | Por qué |
|----------|---------|
| ESB con TLS roto | El ESB es gestionado por MINSAL/Salud En Red |
| SGH/DAU/LIS en HTTP | Son sistemas legacy del hospital. hd-hsc-os los reemplaza solo para HODOM |
| Cross-hospital en SGH legacy | El SGH legacy seguirá operando para hospitalización general |
| TokenSesion en query string | Diseño del ESB, no del hospital |
| Fuerza bruta en sistemas legacy | Sin acceso al código PHP del SGH/DAU/LIS |
| XSS en evoluciones del SGH | Sin acceso al código PHP del SGH |
| RUT sin DV en LIS legacy | Sin acceso al código PHP del LIS |

---

## 7. PLAN DE ACCIÓN INMEDIATO (cosas que sí dependen del HSC/equipo)

### Prioridad 1 (esta semana)
1. **Habilitar HTTPS en el proxy** — aunque los backends sean HTTP, al menos el tráfico
   entre el CLI y el proxy debe estar cifrado. Configurar nginx/apache como reverse proxy
   con TLS, certificado de LetsEncrypt o interno.
2. **Deshabilitar `cambiar_hospital.php` para roles no administrativos** — restringir el
   cambio de hospital a usuarios con privilegios explícitos. Agregar log de cada cambio.

### Prioridad 2 (este mes)
3. **Implementar rate limiting en endpoints de búsqueda** — `obt_paciente.php` y
   `resultadoseleccion.php` no deben permitir más de N consultas por minuto por sesión.
4. **Agregar logging de acceso** — cada consulta a `obt_paciente.php`, `ver_pdf.php`
   y `cargar_historial_evolucion.php` debe registrar (timestamp, usuario, RUT consultado,
   IP origen). Aunque sea un archivo de texto, es mejor que nada.
5. **Forzar DV en LIS** — modificar `resultadoseleccion.php` para que reciba y valide
   el dígito verificador del RUT antes de buscar.

### Prioridad 3 (siguientes 3 meses)
6. **Segmentar la red** — separar el tráfico de los sistemas clínicos en una VLAN
   dedicada, inaccesible desde la red administrativa o de invitados.
7. **Rotar credenciales y eliminar defaults** — cambiar las contraseñas de los usuarios
   del SGH/DAU/LIS. Eliminar usuarios genéricos. Implementar política de contraseñas.
8. **Preparar runbook de incidentes** — ¿qué hacer si se detecta exfiltración? ¿a quién
   notificar? ¿cómo preservar evidencia? Alineado con Ley 21.663 y CSIRT.

---

## 8. MÉTRICAS DE RIESGO PARA EL CUTOVER

| Indicador | Estado actual | Meta antes del cutover |
|-----------|--------------|----------------------|
| Endpoints clínicos sobre HTTPS | 0 de 30+ | Todos los que toque hd-hsc-os |
| Sistemas con rate limiting | 0 de 4 | SGH + LIS |
| Sistemas con logs de acceso | 0 de 4 | SGH + DAU |
| Sistemas con validación de identidad | 1 de 4 (DAU parcial) | Todos |
| Sesiones con expiración forzada | 0 de 4 | SGH + DAU |
| Cifrado en reposo para datos clínicos | 0 de 4 | hd-hsc-os (PostgreSQL) |
| Segregación multi-hospital real | 0 | hd-hsc-os (RLS) |
| Plan de respuesta a incidentes | No existe | Documentado y probado |

---

*Análisis realizado desde código fuente del CLI como documentación del comportamiento de los sistemas. Sin conexiones activas a sistemas vivos. Sin explotación de vulnerabilidades.*
