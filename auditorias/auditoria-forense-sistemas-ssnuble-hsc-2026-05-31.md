# Auditoría Forense 360° — Sistemas del SS Ñuble y Hospital de San Carlos

Fecha: 2026-05-31
Fuente: `/home/felix/projects/hsc-agent-cli` como sonda forense
Alcance: SGH, DAU, LIS, HCC/ESB Salud En Red — reconstruction completa desde el código
Método: ingeniería inversa pasiva de endpoints, modelos de datos, autenticación, red y vulnerabilidades

---

## 1. ARQUITECTURA DE LA RED DEL SS ÑUBLE

```
                         ┌─────────────────────────────────┐
                         │     ESB Salud En Red (MINSAL)   │
                         │     esb.saludenred.cl (HTTPS)   │
                         │                                 │
                         │  :8201  Token Exchange           │
                         │  :8095  Resumen Primaria (APS)   │
                         │  :8096  Resumen Secundaria       │
                         │  :8097  Detalle Primaria         │
                         │  :8099  Detalle Secundaria       │
                         │         (XML epicrisis SGH)      │
                         └──────────────┬──────────────────┘
                                        │
          ┌─────────────────────────────┼──────────────────────────┐
          │                Proxy interno 100.77.30.26              │
          │                                                        │
          │  :8080 ── DAU  (Urgencia)          HTTP plano          │
          │  :8085 ── SGH  (Hospitalización)   HTTP plano          │
          │  :8084 ── LIS  (Laboratorio)       HTTP plano          │
          │                                                        │
          │  Todos comparten:                                      │
          │  · mismo proxy IP                                      │
          │  · PHPSESSID como mecanismo de sesión                  │
          │  · login por formulario (usuario/contrasena)           │
          │  · PHP legacy (5.x/7.x) con HTML server-rendered       │
          │  · sin API REST, sin JSON, sin FHIR, sin HL7           │
          └────────────────────────────────────────────────────────┘
```

### Multi-establecimiento (7 hospitales, 1 instancia SGH)

| ID | Hospital |
|----|----------|
| 1 | Hospital Herminda Martin (Chillán) |
| 2 | Hospital de San Carlos (default) |
| 3 | Hospital de Quirihue |
| 4 | Hospital de Coelemu |
| 5 | Hospital de El Carmen |
| 6 | Hospital de Yungay |
| 7 | Hospital de Bulnes |

Todos comparten la misma instancia SGH. El `cambiar_hospital.php` cambia una variable de sesión PHP. No hay segregación de base de datos por hospital — es una base única con discriminador `hospital_id`.

---

## 2. SGH — SISTEMA DE GESTIÓN HOSPITALARIA

### Perfil técnico

| Atributo | Valor |
|----------|-------|
| URL base | `http://100.77.30.26:8085/SGH/` |
| Tecnología | PHP legacy, HTML4 server-rendered |
| Sesión | PHPSESSID, login por `funciones/autenticacion.php` |
| Multi-hospital | `cambiar_hospital.php` + `renovar_sesion.php` |
| HODOM | servicio_id=72, salas 286/287/288/635 |

### Endpoints expuestos (14 descubiertos)

| Endpoint | Método | Función clínica |
|----------|--------|-----------------|
| `funciones/autenticacion.php` | POST | Login (usuario+contraseña). Retorna 200 con login_form si falla |
| `funciones/renovar_sesion.php` | POST | Fijar contexto de hospital en sesión |
| `vistas/cambiar_hospital.php` | POST | Cambiar hospital activo |
| `ingreso/obt_paciente.php` | POST | Buscar paciente por RUT |
| `ingreso/ver_paciente.php` | GET | Ficha completa (13 tabs, históricos) |
| `funciones/listado/listado_servicios2.php` | POST | Lista de servicios por hospital |
| `funciones/listado/listado_salas3.php` | POST | Lista de salas por servicio |
| `funciones/listado/listado_datos_camas_pacientes.php` | POST | Censo de camas ocupadas |
| `ingreso/cargar_historial_evolucion.php` | POST | Lista de evoluciones de un ingreso |
| `ingreso/cargar_detalle_evolucion.php` | POST | Detalle JSON de una evolución |
| `ingreso/ver_pdf.php` | GET | Documento PDF (epicrisis, ingreso, receta...) |
| `ingreso/atenciones_previas.php` | POST | Historial de hospitalizaciones previas |
| `ingreso/atenciones_previas_ambulatorias.php` | POST | Atenciones ambulatorias (OSIRIS) |
| `funciones/listado/listado_recetas_evolucion.php` | POST | Recetas de hospitalización |

### Modelo de datos reconstruido

```
Patient: cp(PK), nombre, rut+dv, ingreso_id(activo)
Census: cama, nombre, rut, fecha_ingreso, diagnostico, dias_estada,
        evolucion_id (puede ser "0" en HODOM), ingreso_id, servicio, sala
Evolution: evolucion_id, fecha, profesional, tipo,
           historia, evolucion, plan, indicacion, farmacos,
           examenes, infofamiliar, infotraslado
Document: ver_pdf.php?form={ingreso|epicrisis|receta|consentimiento}&id=X
Medication: id, fecha, detalle, items[]{medicamento, indicacion, hora, funcionario}
Intervention: fecha, tipo, descripcion, cirujano, pabellon
```

### Hallazgos de seguridad

- HTTP plano — todo el tráfico clínico sin cifrar
- Auth falla con 200 (login_form en body), no con 401 — patrón PHP clásico
- `evolucion_id=0` frecuente en HODOM — censo roto
- `cargar_detalle_evolucion.php` puede devolver JSON con 8 campos vacíos — inconsistencia accordion vs JSON
- PDFs servidos sin verificación de identidad — cualquier `ingreso_id` válido accesible
- MoJibake sistemático en nombres (Latin-1 mal interpretado como UTF-8)
- Inestable bajo carga — documentado explícitamente, requiere 3 retries
- Sin CSRF tokens, sin headers de seguridad, sin rate limiting

---

## 3. DAU — DEPARTAMENTO DE ATENCIÓN DE URGENCIA

### Perfil técnico

| Atributo | Valor |
|----------|-------|
| URL base | `http://100.77.30.26:8080/dau/vista/` |
| Tecnología | PHP legacy, Bootstrap glyphicons + jQuery tooltips |
| Sesión | PHPSESSID independiente de SGH (cookie jar separado) |
| Identidad | `atencion/index.php?a=X` → hidden fields (run, dv, codPacie, codAdmision) |
| Board | `listadoPacientesBox.php` — censo de urgencia SIN RUT expuesto |

### Endpoints expuestos (16 descubiertos)

| Endpoint | Método | Función clínica |
|----------|--------|-----------------|
| `autenticacion.php` | POST | Login independiente |
| `atencion/index.php` | GET | Ancla de identidad (RUT, codPacie, codAdmision) |
| `listadoPacientesBox/listadoPacientesBox.php` | GET | Board/censo de urgencia |
| `triageprueba/listadoTriage.php` | GET | Triage ESI C1-C5 + signos vitales |
| `atencion/obtener_listado_signos_vitales.php` | GET | Serie temporal de signos vitales |
| `atencion/obtener_anamnesis.php` | GET | Notas de anamnesis |
| `atencion/obtener_examen_fisico.php` | GET | Examen físico |
| `atencion/obtener_hipotesis.php` | GET | Hipótesis diagnóstica |
| `atencion/obtener_examen_observacion.php` | GET | Evolución + observaciones |
| `atencion/obtener_cie.php` | GET | Diagnósticos CIE-10 (SOLO GET) |
| `atencion/obtener_lista_exa_laboratorio.php` | GET | Órdenes de laboratorio |
| `atencion/obtener_lista_exa_rayo.php` | GET | Órdenes de rayos |
| `atencion/obtener_lista_exa_scanner.php` | GET | Órdenes de scanner (params `c`/`cp`) |
| `atencion/obtener_lista_sic.php` | GET | Interconsultas |
| `atencion/obtener_lista_indicaciones.php` | GET | Medicación activa |
| `atencion/obtener_indicaciones_alta.php` | GET | Indicaciones de alta |
| `atencion/obtener_lista_recetas.php` | POST | Recetas (SOLO POST) |
| `atencion/dau_p.php` | GET | Documento imprimible HTML |

### Flujo clínico

```
Board → Identity (atencion/index.php) → Triage (ESI) → Anamnesis + ExFisico + Hipotesis
→ Órdenes (Lab/Rayos/Scanner/SIC) → Medicación → Evolución/Observaciones
→ CIE-10 Diagnósticos → Alta (indicaciones + recetas) → dau_p.php
```

### Hallazgos de seguridad

- HTTP plano
- Board sin RUT — obliga a N consultas de identidad para resolver pacientes
- DAU cerrado pierde identidad (hidden fields vacíos) — imposible verificar RUT post-alta
- `obtener_cie.php` solo funciona con GET (POST = vacío) — falso negativo silencioso
- `obtener_lista_exa_scanner.php` rompe convención de parámetros (`c`/`cp` vs `a`/`u`)
- `obtener_lista_recetas.php` solo funciona con POST
- HTML scraping frágil — basado en `<tr class="dato">` y regex sobre onclick
- Sin CORS, sin CSRF, sin rate limiting

---

## 4. LIS — LABORATORY INFORMATION SYSTEM

### Perfil técnico

| Atributo | Valor |
|----------|-------|
| URL base | `http://100.77.30.26:8084/WEB_SANCARLOS/` |
| Tecnología | PHP legacy |
| Sesión | PHPSESSID independiente de DAU y SGH |
| Resultados | HTML table → filtrado (V)alidados + PDF por examen |

### Endpoints expuestos (3 descubiertos)

| Endpoint | Método | Función |
|----------|--------|---------|
| `autenticacion.php` | POST | Login |
| `resultadoseleccion.php` | POST | Listado de exámenes por RUT (solo dígitos, sin DV) |
| `detalleexamenes.php` | GET | PDF con resultados, valores de referencia, unidad |

### Flujo de datos

```
DAU (orden) → RUT → LIS resultadoseleccion.php (POST rut + BotonAccion=Buscar)
→ HTML table con exam_id, nombre, fecha, (V)/(P), link PDF
→ FILTRA pendientes → detalleexamenes.php?id=X → PDF binario
→ pdftotext -layout → parseKeyValues + parseStructuredResults
→ ResultValue{examen, resultado, unidad, referencia}
```

### Modelo de datos

```
Exam: id, nombre, fecha (DD-MM-YYYY HH:MM), estado (validado|pendiente), userParam
ResultValue (desde PDF): examen, resultado, unidad, referencia
PDF metadata: Fecha Toma, Muestra, etc.
```

### Hallazgos de seguridad

- RUT sin dígito verificador — el LIS no valida el DV
- Acceso por RUT sin binding a episodio — cualquiera con sesión LIS ve resultados de cualquier RUT
- Sin trazabilidad de quién consultó qué resultados
- PDFs sin marca de agua ni protección
- Sin LOINC, sin SNOMED, sin HL7 — exámenes identificados por nombre libre
- `pdftotext` ejecutado como subproceso con PDFs de fuente no confiable
- Cookie jar independiente pero mismo proxy host — posible colisión de dominio

---

## 5. HCC/ESB — SALUD EN RED (puente nacional)

### Perfil técnico

| Atributo | Valor |
|----------|-------|
| Host | `esb.saludenred.cl` |
| Protocolo | HTTPS (con TLS roto: InsecureSkipVerify=true) |
| Puertos | 8201 (token), 8095-8099 (clínicos) |
| Auth | Sin login propio — bridge DAU+SGH → visor iframe → tokens |

### Flujo de autenticación (4 pasos)

```
1. DAU: obtener_visor_aps.php?rut=X&dv=Y → URL puente SGH
2. SGH: atenciones_previas_aps2.php → HTML con <iframe> a visor.saludenred.cl
3. Parse: iframe URL → Identification, IdentificationType, IDRyF, AccessToken
4. ESB :8201: ObtenerTokenSesion?Parametro={"TokenAcceso":"<token>"} → TokenSesion
```

### Endpoints clínicos

| Puerto | Método | Función | Ventana |
|--------|--------|---------|---------|
| 8095 | GET | Resumen atención primaria (APS) | 35 meses |
| 8096 | GET | Resumen atención secundaria | 35 meses |
| 8097 | GET | Detalle atención primaria | Por ID |
| 8099 | GET | Detalle atención secundaria (XML epicrisis SGH) | Por ID |

### Datos expuestos

- Fecha, establecimiento, servicio, tipo de atención
- Diagnóstico principal (CIE-10)
- Motivo de consulta / anamnesis
- Epicrisis / alta hospitalaria (XML anidado en JSON en puerto 8099)
- Identificador único de paciente (IDRyF — Red y Ficha)
- RUT, tipo de identificación

### Hallazgos de seguridad

- TLS completamente deshabilitado (`InsecureSkipVerify: true`) — MITM trivial
- TokenSesion viaja en query string — logueable por proxies
- AccessToken viaja en HTML de SGH sobre HTTP plano
- IDRyF (identificador nacional) expuesto en output JSON
- Token de sesión autoriza acceso a cualquier paciente de la red — sin RBAC por paciente
- Toda la cadena de identidad (DAU→SGH→visor→ESB) viaja sobre HTTP excepto el último salto
- Sin refresh tokens — sesión vive hasta que expira el PHPSESSID

---

## 6. HALLAZGOS TRANSVERSALES DE LA RED

### 6.1 Cero interoperabilidad estándar

Ningún sistema del HSC expone FHIR, HL7 v2, DICOM, LOINC, SNOMED o cualquier estándar internacional. La interoperabilidad es exclusivamente vía RUT como llave compartida entre sistemas que no se comunican entre sí.

### 6.2 Tres silos de autenticación

DAU, SGH y LIS tienen logins independientes con PHPSESSID separados. El HCC/ESB no tiene login propio — requiere bridge DAU+SGH. Un atacante necesita comprometer 3 credenciales para acceso clínico completo.

### 6.3 HTTP plano en toda la capa interna

Los 3 sistemas clínicos (DAU :8080, SGH :8085, LIS :8084) operan sobre HTTP. Solo el ESB (:8201, :8095-:8099) usa HTTPS, pero con validación de certificados deshabilitada. Toda credencial, cookie de sesión y dato clínico viaja en texto plano por la red local.

### 6.4 Proxy único como punto de fallo y superficie de ataque

`100.77.30.26` concentra el acceso a los 3 sistemas clínicos y el bridge al ESB. Quien controle el proxy (o el segmento de red) captura todo el tráfico clínico del hospital.

### 6.5 Sin auditoría ni trazabilidad

Ningún sistema deja registro de quién accedió a qué paciente. El PHPSESSID es la única credencial de sesión. No hay logs de acceso, no hay append-only audit trail, no hay non-repudiation.

### 6.6 Sin separación real multi-establecimiento

Los 7 hospitales del SS Ñuble comparten la misma instancia SGH. La segregación es por variable de sesión PHP (`cambiar_hospital.php`), no por base de datos, no por red, no por autenticación. Un usuario con credenciales de San Carlos puede cambiar a Herminda Martin con un POST.

### 6.7 Inconsistencia de parámetros entre endpoints

Cada endpoint del DAU usa su propia convención de nombres de parámetros (`a` vs `atencion`, `u` vs `usuario`, `c` vs `a`). No hay contrato de API. El código del CLI debe conocer cada excepción individualmente.

---

## 7. IMPLICANCIAS PARA hd-hsc-os

### 7.1 hd-hsc-os será el primer sistema con FHIR en toda la red

No hay nada que interoperar en FHIR hacia adentro. Todo el valor de interoperabilidad de hd-hsc-os es hacia afuera: MINSAL, REM, SNRE, MPI nacional. Hacia adentro, la interoperabilidad será contra sistemas PHP sin API.

### 7.2 La migración es desde un modelo plano no relacional

El SGH no tiene entidades separadas para HODOM. Pacientes, evoluciones, documentos y medicación de HODOM están mezclados con los de hospitalización general en las mismas tablas. La migración debe proyectar el subconjunto HODOM desde tablas genéricas.

### 7.3 El cifrado en reposo y tránsito es diferenciador

hd-hsc-os con PostgreSQL + PWA offline con IndexedDB cifrada + HTTPS representa un salto de seguridad frente al estado actual de HTTP plano y cookies en texto plano. Esto es un argumento fuerte ante CENS para los sellos RCE y Telemedicina.

### 7.4 La identidad es RUT, no MPI

El MPI nacional (NID v0.4.8, PIXm/PDQm) no está en producción en el SS Ñuble. Todos los sistemas usan RUT con módulo 11 como identificador. hd-hsc-os debe operar con RUT + identificador interno opaco, con MPI como integración futura.

### 7.5 La red no está lista para Clave Única (NT 9)

Los 3 sistemas usan login por formulario con usuario/contraseña. Implementar Clave Única del Estado en hd-hsc-os lo convertiría en el único sistema con autenticación moderna de la red, pero sin integración con el resto. Esto requiere un IdP puente.

---

## 8. REFERENCIAS CRUZADAS

- `hsc-agent-cli/internal/upstream/sgh/` — reconstrucción SGH
- `hsc-agent-cli/internal/upstream/dau/` — reconstrucción DAU
- `hsc-agent-cli/internal/upstream/lab/` — reconstrucción LIS
- `hsc-agent-cli/internal/upstream/hcc/` — reconstrucción ESB
- `hsc-agent-cli/internal/upstream/config/` — URLs y credenciales
- `hsc-agent-cli/internal/identity/` — validación RUT módulo 11

---

*Documento generado por ingeniería inversa forense desde código Go. Sin conexiones activas a sistemas vivos.*
