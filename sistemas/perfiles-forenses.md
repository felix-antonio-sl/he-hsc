# Sistemas Objetivo — Perfiles Forenses (Resumen Ejecutivo)

**Corte histórico: 2026-05-31.** Este resumen reproduce conclusiones de la
auditoría pasiva de código de esa fecha. No revalida endpoints, topología,
explotabilidad ni ausencia de controles en los sistemas actuales. Las pruebas
activas permanecen `NOT_RUN`; la similitud de código no prueba una vulnerabilidad.

> **Documento completo:** `auditorias/auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md`
> **Análisis ofensivo con vectores detallados:** `auditorias/hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md`
> **Vectores por sistema:** `vectores/sgh-vectores.md`, `vectores/dau-vectores.md`, `vectores/lis-vectores.md`, `vectores/esb-vectores.md`

Reconstrucción desde código del `hsc-agent-cli`. Cada sistema fue perfilado mediante
ingeniería inversa pasiva de sus endpoints, modelos de datos, mecanismos de autenticación,
y patrones de respuesta HTML.

## Inventario

| Sistema | Puerto | URL base | Tecnología | Sesión | Criticidad |
|---------|--------|----------|------------|--------|------------|
| SGH | :8085 | `/SGH/` | PHP legacy, HTML4 | PHPSESSID (form login) | Crítica — hospitalización, censo, evoluciones, documentos, recetas |
| DAU | :8080 | `/dau/vista/` | PHP legacy, Bootstrap+jQuery | PHPSESSID (form login) | Crítica — urgencia, triage ESI, diagnósticos CIE-10 |
| LIS | :8084 | `/WEB_SANCARLOS/` | PHP legacy | PHPSESSID (form login) | Alta — resultados de laboratorio, sin LOINC/SNOMED |
| ESB | :8201,8095-8099 | `esb.saludenred.cl` | HTTPS (TLS roto) | Bridge DAU+SGH→Token | Crítica — historial clínico nacional, epicrisis |

## Topología

```
                    Internet
                       │
              ┌────────┴────────┐
              │  esb.saludenred.cl  :8201 :8095-8099 (HTTPS, TLS roto)
              └────────┬────────┘
                       │
    ┌──────────────────┼──────────────────┐
    │       Proxy interno 100.77.30.26     │
    │  :8080 DAU  :8084 LIS  :8085 SGH    │
    │  (todos HTTP plano)                  │
    └──────────────────────────────────────┘
```

## Hallazgos transversales clave

1. **HTTP plano en toda la capa interna** — credenciales y datos clínicos sin cifrar
2. **Tres sesiones PHPSESSID independientes** sin SSO ni RBAC
3. **Proxy único como SPOF** y concentrador de tráfico
4. **Sin auditoría de accesos** en ningún sistema
5. **Multi-tenancy por variable de sesión** sin segregación real de base de datos
6. **TLS deshabilitado para ESB** (`InsecureSkipVerify: true`)
7. **Cero interoperabilidad estándar** — sin FHIR, sin HL7, sin LOINC, sin SNOMED

Véase la auditoría forense completa para el detalle de endpoints, modelos de datos,
hallazgos de seguridad por sistema e implicancias para hd-hsc-os.
