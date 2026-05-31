# Auditoría de Seguridad — hsc-agent-cli / Red SS Ñuble-HSC
## Desde perspectiva de hacker ético (código solamente, sin conexiones activas)

Fecha: 2026-05-31
Fuente: /home/felix/projects/hsc-agent-cli
Alcance: análisis estático de código Go, configuración, red y patrones operacionales
Límite ético: sin escaneo activo, sin conexiones a sistemas vivos

---

## HALLAZGOS CRÍTICOS (6)

### CR-1 | HTTP plano para todos los servidores PHP del hospital
100.77.30.26:8080/8085/8084 — DAU, SGH, LAB viajan en HTTP sin TLS. PHPSESSID,
credenciales de login y toda la ficha clínica en texto plano por la red local.
`config.go:59-61`

### CR-2 | TLS deshabilitado para ESB Salud En Red
`InsecureSkipVerify: true` en `hcc.go:392`. Cualquier MITM en la ruta de red puede
suplantar `esb.saludenred.cl` e interceptar/manipular datos clínicos del ESB nacional.

### CR-3 | Caché clínica en texto plano sin cifrado
`~/.cache/hsc-agent-cli/<rut>/*.json` contiene diagnósticos, medicamentos, signos
vitales, evoluciones, nombres de pacientes, RUTs, PDFs clínicos (hasta 24h).
`cache.go:52-56, 119-155`

### CR-4 | RUTs de pacientes logueados a stderr
Cada comando `catalog`, `get`, `find`, `bundle` registra el RUT en texto plano
vía slog a stderr. `commands.go:53-57, 307-312, 369, 461`

### CR-5 | Acceso multi-hospital con una sola sesión
`--establecimiento` permite cambiar `H_SGH_HOSPITAL_ID` en runtime sobre la misma
PHPSESSID. Un usuario autenticado en HSC=2 puede acceder a Herminda Martin=1.
`commands.go:589-590`

### CR-6 | Exfiltración masiva con sesión válida
Sin rate limits, sin RBAC, sin auditoría. `find --hospitalizados` vuelca el censo
completo. Iterar RUTs secuencialmente permite drenar toda la base clínica del hospital.

---

## HALLAZGOS ALTOS (8)

| ID | Hallazgo | Archivo:Línea |
|----|----------|---------------|
| HI-1 | Credenciales en texto plano en credentials.env | `config.go:126-150` |
| HI-2 | Credenciales visibles vía /proc/<pid>/environ | `main.go:43-45` |
| HI-3 | PHPSESSID viaja en HTTP plano → capturable en red | `session.go:55-57` |
| HI-4 | Directorio de caché indexado por RUT → enumeración trivial | `cache.go:80-86` |
| HI-5 | Caché expirada nunca se borra → datos clínicos persisten indefinidamente | `cache.go:90-108` |
| HI-6 | Datos clínicos en mensajes de error | `support.go:110-115` |
| HI-7 | Sin auditoría de quién ejecutó qué comando contra qué paciente | (*) |
| HI-8 | Binario instalado con 0755 → world-executable | `install-local.sh:26` |

---

## HALLAZGOS MEDIOS (8)

| ID | Hallazgo | Archivo:Línea |
|----|----------|---------------|
| ME-1 | IDs internos hardcodeados (usuario_id=3225, servicio=4, institucion=4) | `config.go:49-57` |
| ME-2 | Token de sesión ESB en memoria de proceso | `hcc.go:284` |
| ME-3 | Mapa completo de red interna en código fuente (IPs, puertos, endpoints) | `config.go`, `hcc.go`, `catalog.go` |
| ME-4 | `pdftotext` ejecutado sobre PDFs de servidor potencialmente comprometido | `documents.go:476-501` |
| ME-5 | Parseo HTML con regex, no parser HTML robusto | `dau.go:228-245`, `sgh.go:220-241` |
| ME-6 | RUT cero en 15+ handlers DAU → bypass de identity check | `fetchers.go:397+` |
| ME-7 | IDRyF (identificador nacional) expuesto en JSON | `hcc.go:85-92` |
| ME-8 | Sin minimización de datos en salida JSON | (*) |

---

## TOPOLOGÍA DE RED RECONSTRUIDA

```
                    Internet
                       │
              ┌────────┴────────┐
              │  esb.saludenred.cl  :8201 :8095-8099 (HTTPS, TLS roto)
              │  visor.saludenred.cl :443
              └────────┬────────┘
                       │
    ┌──────────────────┼──────────────────┐
    │       Proxy interno 100.77.30.26     │
    │                                      │
    │  :8080 → DAU (Urgencia)         HTTP │
    │  :8085 → SGH (Hospitalización)  HTTP │
    │  :8084 → LIS (Laboratorio)      HTTP │
    │                                      │
    │  :8085 → 10.6.85.124 (Pabellón) HTTP │
    │  Anatomía Patológica (iframe)        │
    └──────────────────────────────────────┘

    Hospital ID 1 = Herminda Martin
    Hospital ID 2 = San Carlos (default)
```

---

## VECTORES DE ENTRADA PRIORITARIOS (hebras para explorar)

1. **Captura de PHPSESSID en red local** → con eso, sesión clínica completa. El HTTP plano (CR-1) hace esto trivial para cualquiera en el mismo segmento de red.

2. **Lectura de ~/.cache/hsc-agent-cli/** → si un atacante obtiene acceso al filesystem del servidor donde corre el CLI, todos los RUTs consultados + su ficha clínica completa están en texto plano (CR-3).

3. **MITM contra ESB Salud En Red** → TLS deshabilitado (CR-2). Un atacante que controle el proxy o la ruta de red puede inyectar datos falsos en el historial clínico compartido nacional.

4. **Iteración de RUTs** → sin rate limiting (CR-6), un script simple puede barrer el espacio de RUTs chilenos y extraer datos de cualquier paciente que haya pasado por el hospital.

5. **Cambio de establecimiento** → con credenciales de San Carlos, acceso a datos de Herminda Martin (CR-5). Sin registro de auditoría (HI-7).

6. **Inyección vía PDFs maliciosos** → `pdftotext` procesa PDFs del servidor SGH (ME-4). Si un atacante compromete el SGH y sirve un PDF con exploit de poppler, obtiene ejecución de código en la máquina del CLI.

---

## CONTROLES REQUERIDOS POR LEY 21.663 QUE FALLAN

| Control | Ley | Estado |
|---------|-----|--------|
| Cifrado en tránsito | Art. 8 | ✗ HTTP plano en red local |
| Cifrado en reposo | Art. 8 | ✗ Caché clínica en texto plano |
| Control de acceso mínimo necesario | Art. 8 | ✗ Sin RBAC, acceso total con credenciales |
| Auditoría de accesos | Art. 8 | ✗ Sin registro de quién accedió a qué |
| Gestión de incidentes | Art. 9 | ✗ Sin runbook de incidentes |
| Reporte al CSIRT | Art. 9 | ✗ Sin canal de reporte |
| Seguridad por diseño | Art. 7 | ✗ Código sin revisión de seguridad |

---

## RECOMENDACIONES PRIORIZADAS

1. **Cifrar caché en reposo** — AES-256-GCM con clave derivada de entorno, no del código
2. **Habilitar TLS entre proxy y sistemas** — o tunelizar sobre WireGuard si el proxy no soporta TLS
3. **Eliminar InsecureSkipVerify** — configurar cadena de certificados del ESB correctamente
4. **Redactar RUTs de logs** — usar hash o simplemente no loguear identificadores
5. **Implementar auditoría append-only** — registro inmutable de (timestamp, usuario, comando, RUT, resultado)
6. **Agregar RBAC mínimo** — separar al menos rol clínico de rol administrativo
7. **Sandbox para pdftotext** — ejecutar en contenedor efímero o con seccomp
8. **Rate limiting** — máximo N consultas por minuto por usuario
9. **Auto-limpieza de caché** — borrar entradas expiradas, no solo ignorarlas
10. **Parser HTML robusto** — reemplazar regex por golang.org/x/net/html
