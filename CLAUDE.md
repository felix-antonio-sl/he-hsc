# he-hsc — Hacking Ético Hospital de San Carlos / SS Ñuble

Canon operativo para el carril de ciberseguridad del ecosistema HSC.
Repositorio independiente. Produce inteligencia de amenazas, vectores de ataque,
auditorías de cumplimiento, evaluación de sellos CENS, contratos de seguridad,
y planes de remediación para los sistemas del hospital previo al cutover de `hd-hsc-os`.

## Propósito

Auditar la postura de seguridad de los sistemas de información del Hospital de San Carlos
y el Servicio de Salud Ñuble desde una perspectiva ofensiva controlada, sin conexiones
activas a sistemas vivos. El objetivo es identificar vulnerabilidades explotables antes
de que lo haga un atacante real, y alimentar el diseño de `hd-hsc-os` con evidencia
concreta de lo que NO debe replicar del ecosistema legacy.

## Estado

Fecha: 2026-06-04
Fase: reconocimiento pasivo completado (4 sistemas perfilados). SGSI MINSAL incorporado.
Próximo: escaneo de vulnerabilidades activo (requiere autorización del HSC)

## Estructura del repositorio

```
he-hsc/
├── CLAUDE.md                          # Este documento (SSOT)
├── contratos/                         # Contratos de seguridad e interoperabilidad
│   ├── contrato-seguridad-informacion-salud.md
│   └── contrato-interoperabilidad-salud.md
├── auditorias/                        # Auditorías de seguridad, forenses, cumplimiento y hacking ético
│   ├── auditoria-seguridad-informacion-salud.md
│   ├── auditoria-seguridad-red-ssnuble-hsc-2026-05-31.md
│   ├── auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md
│   ├── auditoria-normativa-interoperabilidad.md
│   ├── auditoria-cumplimiento-2026-05-29.md
│   ├── auditoria-cumplimiento-2026-05-29-cierre.md
│   ├── hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md
│   ├── informe-tecnico-ciberseguridad-salud-digital-2026-05-31.md
│   ├── handoff-ola-b1-seguridad-clinica.md
│   └── minsal-seguridad-info/        # SGSI MINSAL: 63 PDFs fuente + 63 transcripciones markdown (v3)
├── evals/                             # Checklists y evaluaciones de seguridad (SGSI, interoperabilidad)
│   ├── seguridad-informacion-salud.md
│   └── cumplimiento-normativo-interoperabilidad.md
├── puertos/                           # Puertos de seguridad e interoperabilidad (IAM-agnostic)
│   ├── seguridad-informacion-salud.md
│   └── interoperabilidad-salud.md
├── certificacion/                     # Evaluación virtual de sellos CENS
│   ├── cens-certificacion-virtual.md
│   ├── auditoria-cens-certificacion-virtual-2026-05-30.md
│   └── handoff-cens-certificacion-2026-05-30.md
├── experiencia/                       # Seguridad en UX clínica
│   └── sistema-visual-seguridad.md
├── sistemas/                          # Perfiles forenses de los sistemas objetivo
│   └── perfiles-forenses.md
├── vectores/                          # Vectores de ataque por sistema
│   ├── sgh-vectores.md
│   ├── dau-vectores.md
│   ├── lis-vectores.md
│   └── esb-vectores.md
├── escenarios/                        # Escenarios de ataque compuestos
│   └── escenarios-compuestos.md
├── remediacion/                       # Planes de acción y métricas
│   └── plan-remediacion.md
└── handoff/                           # Handoffs de sesión
    └── handoff-2026-05-31.md
```

## SGSI MINSAL (`auditorias/minsal-seguridad-info/`)

Corpus normativo completo del Sistema de Gestión de Seguridad de la Información del
Ministerio de Salud de Chile, obtenido de `minsal.cl/seguridad_de_la_informacion/`
el 2026-06-04.

| Categoría | PDFs | Markdowns | Método extracción |
|-----------|------|-----------|-------------------|
| Política General | 1 | 1 | OCR (pymupdf + Tesseract spa_best, DPI 350) |
| Políticas Secundarias | 23 | 23 | 9 texto estructurado (pymupdf con headings + tablas), 14 OCR |
| Procedimientos | 14 | 14 | 7 texto estructurado, 7 OCR |
| Instructivos | 6 | 6 | 4 texto estructurado, 2 OCR |
| Resoluciones | 19 | 19 | 19 OCR |
| **Total** | **63** | **63** | **18 texto nativo, 45 OCR** |

Pipeline de transcripción (3 pasadas):
- **V1** (pdftotext/markitdown): 79/100, ~0 headings, 0 tablas
- **V2** (estructurado pymupdf + OCR best): 84/100, 292 headings detectados
- **V3** (tablas markdown + join párrafos + listas + limpieza): 87/100, 175 headings, tablas formateadas, 399 listas

Marco normativo referenciado en los documentos:
- NCh-ISO 27001:2022 — Requisitos SGSI
- Ley 21.663 — Marco de Ciberseguridad
- Ley 21.719 — Protección de Datos Personales
- Ley 21.459 — Delitos Informáticos (Convenio de Budapest)

## Fuentes

- `hsc-agent-cli` — sonda forense en Go que lee los sistemas reales
- `hd-hsc-os` — sistema greenfield que reemplazará HODOM
- SGH, DAU, LIS — sistemas PHP legacy del hospital
- ESB Salud En Red — puente de interoperabilidad nacional
- MINSAL — `minsal.cl/seguridad_de_la_informacion/` (SGSI institucional)
- Ley 21.663, Ley 21.719, ISO 27001, NIST CSF 2.0

## Relación con otros repositorios

| Repo | Relación |
|------|----------|
| `hd-hsc-os` | Sistema greenfield — he-hsc audita el legacy y alimenta el diseño de seguridad de hd-hsc-os |
| `hsc-agent-cli` | Sonda forense — he-hsc usa el CLI como lente para reconstruir los sistemas objetivo |
| `deep-opm-pro` | Proyecto padre — he-hsc es un carril de ciberseguridad independiente |

## Reglas de enfrentamiento

1. **Sin conexiones activas** a sistemas vivos sin autorización explícita del HSC
2. **Sin explotación** de vulnerabilidades en producción
3. **Sin exfiltración** de datos reales
4. **Sin modificación** de sistemas objetivo
5. **Divulgación responsable** — hallazgos se comparten primero con el equipo del HSC
6. **Evidencia trazable** — cada hallazgo referencia archivo y línea del código fuente
7. **Clasificación de severidad** — Crítico/Alto/Medio/Bajo con impacto clínico explicitado
