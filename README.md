# he-hsc — Hacking Ético / Ciberseguridad — Hospital de San Carlos

Repositorio de ciberseguridad ofensiva y defensiva para el ecosistema de sistemas
de información del Hospital de San Carlos y el Servicio de Salud Ñuble.

## Propósito

Auditar, documentar y fortalecer la postura de seguridad de los sistemas que operan
en el HSC, con foco en la transición del ecosistema legacy (PHP, HTTP plano, sin
estándares) hacia `hd-hsc-os` (greenfield con FHIR, RBAC, cifrado, auditoría).

## Estructura

```
he-hsc/
├── CLAUDE.md                          # Canon operativo
├── README.md                          # Este documento
├── contratos/                         # Contratos de seguridad e interoperabilidad
│   ├── contrato-seguridad-informacion-salud.md
│   └── contrato-interoperabilidad-salud.md
├── auditorias/                        # Auditorías de seguridad (internas y forenses)
│   ├── auditoria-seguridad-informacion-salud.md
│   ├── auditoria-seguridad-red-ssnuble-hsc-2026-05-31.md
│   ├── auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md
│   ├── auditoria-normativa-interoperabilidad.md
│   ├── auditoria-cumplimiento-2026-05-29.md
│   ├── auditoria-cumplimiento-2026-05-29-cierre.md
│   ├── hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md
│   ├── informe-tecnico-ciberseguridad-salud-digital-2026-05-31.md
│   └── handoff-ola-b1-seguridad-clinica.md
├── evals/                             # Checklists y evaluaciones de seguridad
│   ├── seguridad-informacion-salud.md
│   └── cumplimiento-normativo-interoperabilidad.md
├── puertos/                           # Puertos de seguridad e interoperabilidad
│   ├── seguridad-informacion-salud.md
│   └── interoperabilidad-salud.md
├── certificacion/                     # Evaluación virtual CENS
│   ├── cens-certificacion-virtual.md
│   ├── auditoria-cens-certificacion-virtual-2026-05-30.md
│   └── handoff-cens-certificacion-2026-05-30.md
├── experiencia/                       # Seguridad en UX clínica
│   └── sistema-visual-seguridad.md
├── sistemas/                          # Perfiles forenses de sistemas objetivo
│   └── perfiles-forenses.md
├── vectores/                          # Vectores de ataque por sistema
│   ├── sgh-vectores.md
│   ├── dau-vectores.md
│   ├── lis-vectores.md
│   └── esb-vectores.md
├── escenarios/                        # Escenarios de ataque compuestos
│   └── escenarios-compuestos.md
├── remediacion/                       # Planes de remediación
│   └── plan-remediacion.md
└── handoff/                           # Handoffs de sesión
    └── handoff-2026-05-31.md
```

## Relación con otros repositorios

| Repo | Relación |
|------|----------|
| `hd-hsc-os` | Sistema greenfield — he-hsc audita el legacy y alimenta el diseño de seguridad de hd-hsc-os |
| `hsc-agent-cli` | Sonda forense — he-hsc usa el CLI como lente para reconstruir los sistemas objetivo |
| `deep-opm-pro` | Proyecto padre — he-hsc es un carril de ciberseguridad independiente |

## Reglas de enfrentamiento

1. Sin conexiones activas a sistemas vivos sin autorización explícita del HSC
2. Sin explotación de vulnerabilidades en producción
3. Sin exfiltración de datos reales
4. Divulgación responsable — hallazgos al equipo del HSC primero
5. Evidencia trazable — cada hallazgo referencia archivo y línea del código fuente
