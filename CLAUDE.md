# CLAUDE.md — Canon operativo he-hsc

Documento unico y fuente de verdad (SSOT) del repositorio. Reune contexto del
proyecto, estado, arquitectura, reglas de trabajo, convenciones y comandos
accionables para cualquier colaborador o agente. `README.md` y `AGENTS.md`
apuntan aqui.

## Que es

**he-hsc** es el carril de ciberseguridad del ecosistema HSC: hacking etico,
auditoria ofensiva controlada, inteligencia de amenazas, vectores de ataque,
evaluacion de cumplimiento normativo y planes de remediacion para los sistemas
del **Hospital de San Carlos** y el **Servicio de Salud Nuble**, previo al
cutover de `hd-hsc-os`.

Este repositorio **NO es** `hd-hsc-os` (el sistema greenfield). Es el carril de
auditoria ofensiva que alimenta el diseno de seguridad de hd-hsc-os con evidencia
concreta de vulnerabilidades del ecosistema legacy.

## Proposito

Auditar la postura de seguridad de los sistemas de informacion del Hospital de
San Carlos y el Servicio de Salud Nuble desde una perspectiva ofensiva
controlada, sin conexiones activas a sistemas vivos. El objetivo es identificar
vulnerabilidades explotables antes de que lo haga un atacante real, y alimentar
el diseno de `hd-hsc-os` con evidencia concreta de lo que **NO debe replicar**
del ecosistema legacy.

## Estado

- **Fecha:** 2026-06-09
- **Fase:** reconocimiento pasivo completado (4 sistemas perfilados: SGH, DAU, LIS, ESB)
- **Normativa:** corpus SGSI MINSAL incorporado (63 documentos, 2026-06-04)
- **Certificacion CENS:** evaluacion virtual completada, auditada y remediada (2026-05-30)
- **Auditoria categorial:** cerrada
- **Proximo:** escaneo de vulnerabilidades activo (requiere autorizacion del HSC)

## Alcance dual

El repositorio contiene dos tipos de artefactos:

1. **Produccion propia de he-hsc:** auditorias ofensivas, perfiles forenses,
   vectores de ataque, escenarios compuestos, plan de remediacion, handoffs de
   sesion, corpus normativo MINSAL. **Fuente de verdad de este repo.**

2. **Referencia de hd-hsc-os:** contratos, specs de puertos, evals, diseno
   visual, certificacion CENS y auditorias de diseno/cumplimiento. Producidos en
   el contexto del sistema greenfield; almacenados aqui como fuente de verdad
   para los hallazgos y recomendaciones de este carril. Sus paths internos
   (`02-datos/`, `05-especificaciones/`, `01-dominio/`, `03-experiencia/`,
   `04-arquitectura/`) refieren al repo `hd-hsc-os`, **no a este repo**.

## Sistemas objetivo

| Sistema | Puerto | Funcion | Criticidad |
|---------|--------|---------|------------|
| SGH | :8085 | Hospitalizacion, censo, evoluciones, recetas | Critica |
| DAU | :8080 | Urgencia, triage ESI, diagnosticos CIE-10 | Critica |
| LIS | :8084 | Resultados de laboratorio | Alta |
| ESB | :8201, 8095-8099 | Bus de interoperabilidad nacional (Salud En Red) | Critica |

Hallazgos transversales:

- HTTP plano en toda la capa interna — credenciales y datos clinicos sin cifrar
- Tres sesiones PHPSESSID independientes sin SSO ni RBAC
- Proxy unico como SPOF y concentrador de trafico
- Sin auditoria de accesos en ningun sistema
- Multi-tenancy por variable de sesion sin segregacion real
- TLS deshabilitado para ESB (`InsecureSkipVerify: true`)
- Cero interoperabilidad estandar — sin FHIR, HL7, LOINC, SNOMED

## Reglas de enfrentamiento (para agentes y humanos)

1. **Sin conexiones activas** a sistemas vivos sin autorizacion explicita del HSC.
2. **Sin explotacion** de vulnerabilidades en produccion.
3. **Sin exfiltracion** de datos reales.
4. **Sin modificacion** de sistemas objetivo.
5. **Sin datos identificables reales de pacientes** en este repositorio.
6. **Divulgacion responsable** — los hallazgos se comparten primero con el equipo
   del HSC.
7. **Evidencia trazable** — cada hallazgo referencia archivo y linea del codigo
   fuente.
8. **Clasificacion de severidad** — cada hallazgo se clasifica Critico/Alto/Medio/Bajo
   con impacto clinico explicitado.
9. **Artefactos de referencia hd-hsc-os** — no modificar sus paths internos sin
   verificar que existen en el repo destino.
10. **OPM MANDA** — cambios que tocan dominio, estado o procesos nuevos (A1/A3/A4)
    deben modelarse primero en `hd-opm`. Esto aplica a los artefactos de
    hd-hsc-os, no a este repo.

## Convenciones de trabajo

- Idioma: **espanol (es-CL)** para prosa; ingles para identificadores y terminos
  tecnicos.
- Cada documento nuevo debe declarar: **estado** (borrador/canon/supersedido),
  **fecha**, **proposito**, **alcance** y **fuentes**.
- Los handoffs de sesion van en `handoff/` con formato `handoff-YYYY-MM-DD.md`.
- Las auditorias fechadas que queden supersedidas deben llevar nota explicita en
  el encabezado y referenciar al documento que las reemplaza.
- Paths internos `02-datos/`, `05-especificaciones/`, `01-dominio/`,
  `03-experiencia/`, `04-arquitectura/` → repo `hd-hsc-os`, no este repo.
- Paths de codigo Go (`hsc-agent-cli/internal/...`) → repo `hsc-agent-cli`.
- Paths de codigo TypeScript (`interfaces/web/src/`, `adaptadores/`,
  `migrations/`) → repo `hd-hsc-os`.

## Navegacion

| Quiero... | Voy a... |
|---|---|
| Entender el proyecto y operar como agente | Este documento (`CLAUDE.md`) |
| Ver hallazgos criticos de seguridad del legacy | `auditorias/hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md` |
| Ver la reconstruccion forense de los sistemas | `auditorias/auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md` |
| Ver la seguridad de red y CLI | `auditorias/auditoria-seguridad-red-ssnuble-hsc-2026-05-31.md` |
| Ver la postura de ciberseguridad de hd-hsc-os | `auditorias/informe-tecnico-ciberseguridad-salud-digital-2026-05-31.md` |
| Ver el cierre de brechas CENS | `auditorias/informe-tecnico-cierre-brechas-cens-2026-05-31.md` |
| Ver el estado de certificacion CENS | `certificacion/cens-certificacion-virtual.md` |
| Ver el resumen ejecutivo de los 4 sistemas | `sistemas/perfiles-forenses.md` |
| Ver los vectores de ataque por sistema | `vectores/` |
| Ver los escenarios de ataque compuestos | `escenarios/escenarios-compuestos.md` |
| Ver el plan de remediacion priorizado | `remediacion/plan-remediacion.md` |
| Ver la normativa MINSAL SGSI | `auditorias/minsal-seguridad-info/README.md` |
| Ver los contratos de seguridad/interop | `contratos/` |
| Ver las specs de puertos de aplicacion | `puertos/` |
| Ver handoffs y contexto de sesiones previas | `handoff/` |

## Plan de remediacion (vigente)

La fuente de verdad de la remediacion es `remediacion/plan-remediacion.md`: 17
acciones (R1–R17) en 3 prioridades (esta semana / este mes / proximos 3 meses)
mas la tabla de metricas de seguridad linea base vs meta cutover.

## Corpus normativo MINSAL

El SGSI completo del Ministerio de Salud de Chile esta en
`auditorias/minsal-seguridad-info/`: 63 documentos (1 politica general, 23
politicas secundarias, 14 procedimientos, 6 instructivos, 19 resoluciones)
obtenidos de `minsal.cl/seguridad_de_la_informacion/` el 2026-06-04, en PDF
original y transcripcion markdown. (Espejo de corpus — no editar su contenido.)

## Fuentes canonicas

| Fuente | Tipo | Uso |
|---|---|---|
| `hsc-agent-cli` | Sonda forense Go | Reconstruccion de sistemas legacy |
| `hd-hsc-os` | Sistema greenfield | Destino de recomendaciones de seguridad |
| `hd-opm` | Modelo OPM | Fuente de verdad del dominio HODOM |
| `minsal.cl/seguridad_de_la_informacion/` | Normativa oficial | Marco SGSI MINSAL |
| Ley 21.663 | Ley | Marco de Ciberseguridad |
| Ley 21.719 | Ley | Proteccion de Datos Personales |
| Ley 21.459 | Ley | Delitos Informaticos |
| Ley 20.584 | Ley | Ficha clinica, derechos del paciente |
| ISO 27001:2022 (NCh-ISO) | Norma | Requisitos SGSI |
| NIST CSF 2.0 | Framework | Gobernanza de ciberseguridad |

## Relacion con otros repositorios

| Repo | Relacion |
|---|---|
| `hd-hsc-os` | Sistema greenfield — he-hsc audita el legacy y alimenta el diseno de seguridad |
| `hsc-agent-cli` | Sonda forense en Go — he-hsc la usa como lente para reconstruir los sistemas |
| `hd-opm` | Modelo OPM del dominio HODOM — fuente de verdad de dominio para hd-hsc-os |
| `deep-opm-pro` | Proyecto padre — he-hsc es un carril de ciberseguridad independiente |

Al leer o escribir documentos que referencien paths de hd-hsc-os (`02-datos/`,
`05-especificaciones/`, `01-dominio/`, `03-experiencia/`, `interfaces/web/src/`,
`adaptadores/`, `migrations/`), verificar que el path existe en el repo
`hd-hsc-os` antes de darlo por valido.

Al leer o escribir documentos que referencien paths de hsc-agent-cli
(`internal/upstream/`, `config.go`, `commands.go`, `cache.go`, `hcc.go`),
verificar que el path existe en el repo `hsc-agent-cli`.

Los documentos de este repo que auditan hd-hsc-os referencian ADRs del repo
hd-hsc-os (ej. ADR 0003, 0005, 0007, 0011, 0013, 0016).

## Mapa del repositorio

```
he-hsc/
├── README.md                 # Puntero a CLAUDE.md
├── AGENTS.md                 # Puntero a CLAUDE.md
├── CLAUDE.md                 # Este documento — SSOT
├── contratos/                # Contratos de seguridad e interop (ref. hd-hsc-os)
│   ├── contrato-seguridad-informacion-salud.md
│   └── contrato-interoperabilidad-salud.md
├── auditorias/               # Auditorias de seguridad, forenses y hacking etico
│   ├── hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md       # Analisis ofensivo pasivo (SSOT)
│   ├── auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md   # Reconstruccion forense 360 (SSOT)
│   ├── auditoria-seguridad-red-ssnuble-hsc-2026-05-31.md      # Seguridad del CLI y red (SSOT)
│   ├── informe-tecnico-ciberseguridad-salud-digital-2026-05-31.md  # Informe integral (SSOT, superconjunto)
│   ├── informe-tecnico-cierre-brechas-cens-2026-05-31.md     # Cierre brechas CENS (subconjunto)
│   ├── auditoria-seguridad-informacion-salud.md              # Auditoria seguridad hd-hsc-os (ref. cruzada)
│   ├── auditoria-normativa-interoperabilidad.md              # Auditoria normativa hd-hsc-os (ref. cruzada)
│   ├── auditoria-cumplimiento-2026-05-29.md                  # Cumplimiento frontend (SUPERSEDIDO)
│   ├── auditoria-cumplimiento-2026-05-29-cierre.md           # Cierre cumplimiento frontend (ref. cruzada)
│   └── minsal-seguridad-info/   # Corpus normativo SGSI MINSAL (63 PDFs + 63 markdowns)
├── certificacion/            # Evaluacion virtual CENS (ref. hd-hsc-os)
│   ├── cens-certificacion-virtual.md               # Evaluacion principal (remediada)
│   ├── auditoria-cens-certificacion-virtual-2026-05-30.md  # Auditoria de la evaluacion
│   └── handoff-cens-certificacion-2026-05-30.md    # Handoff de la evaluacion
├── evals/                    # Checklists de evaluacion (ref. hd-hsc-os)
├── puertos/                  # Specs de puertos de aplicacion (ref. hd-hsc-os)
├── experiencia/              # Diseno visual y seguridad UX (ref. hd-hsc-os)
├── sistemas/                 # Perfiles forenses — resumen ejecutivo
├── vectores/                 # Vectores de ataque por sistema
├── escenarios/               # Escenarios de ataque compuestos
├── remediacion/              # Plan de remediacion priorizado
├── handoff/                  # Handoffs de sesion y desarrollo
└── historico/                # Documentos obsoletos conservados por trazabilidad
```

## Documentos vigentes (fuente de verdad)

### Produccion propia he-hsc

| Documento | Proposito |
|---|---|
| `auditorias/hacking-etico-sistemas-ssnuble-hsc-2026-05-31.md` | Analisis ofensivo pasivo de los 4 sistemas legacy |
| `auditorias/auditoria-forense-sistemas-ssnuble-hsc-2026-05-31.md` | Reconstruccion forense completa (endpoints, datos, auth) |
| `auditorias/auditoria-seguridad-red-ssnuble-hsc-2026-05-31.md` | Auditoria de seguridad del CLI y la red |
| `auditorias/informe-tecnico-ciberseguridad-salud-digital-2026-05-31.md` | Informe integral ciberseguridad + CENS (superconjunto) |
| `auditorias/informe-tecnico-cierre-brechas-cens-2026-05-31.md` | Traduccion CENS a ingenieria concreta (subconjunto) |
| `sistemas/perfiles-forenses.md` | Resumen ejecutivo de los 4 sistemas |
| `vectores/*.md` | Vectores de ataque por sistema (sgh, dau, lis, esb) |
| `escenarios/escenarios-compuestos.md` | 4 escenarios compuestos |
| `remediacion/plan-remediacion.md` | 17 acciones en 3 prioridades + metricas cutover |
| `handoff/handoff-ola-b1-seguridad-clinica.md` | Handoff desarrollo backend Ola B-1 (ref. trazabilidad hd-hsc-os) |
| `handoff/handoff-cens-certificacion-2026-05-30.md` | Handoff evaluacion CENS (ref. hd-hsc-os) |
| `auditorias/minsal-seguridad-info/` | Corpus normativo SGSI MINSAL |

### Referencia de hd-hsc-os (almacenados aqui como fuente de verdad)

| Documento | Proposito |
|---|---|
| `contratos/contrato-seguridad-informacion-salud.md` | Obligaciones minimas de seguridad |
| `contratos/contrato-interoperabilidad-salud.md` | Reglas de interoperabilidad FHIR |
| `puertos/seguridad-informacion-salud.md` | Spec de puertos de seguridad |
| `puertos/interoperabilidad-salud.md` | Spec de puertos de interoperabilidad |
| `evals/seguridad-informacion-salud.md` | Checklist de evaluacion de seguridad |
| `evals/cumplimiento-normativo-interoperabilidad.md` | Checklist de evaluacion normativa |
| `experiencia/sistema-visual-seguridad.md` | Diseno visual y reglas de seguridad UX |
| `certificacion/cens-certificacion-virtual.md` | Autoevaluacion CENS (remediada) |
| `certificacion/auditoria-cens-certificacion-virtual-2026-05-30.md` | Auditoria de la autoevaluacion CENS |
| `auditorias/auditoria-seguridad-informacion-salud.md` | Auditoria transversal de seguridad hd-hsc-os |
| `auditorias/auditoria-normativa-interoperabilidad.md` | Auditoria transversal normativa hd-hsc-os |

### Documentos historicos o supersedidos

| Documento | Estado | Motivo |
|---|---|---|
| `auditorias/auditoria-cumplimiento-2026-05-29.md` | SUPERSEDIDO | Reemplazado por `auditoria-cumplimiento-2026-05-29-cierre.md` |
| `historico/handoff-2026-05-31.md` | OBSOLETO | Handoff de sesion inicial. Contenido promovido a documentos independientes (ver `historico/README.md`). |

Para el indice completo de documentos archivados, ver `historico/README.md`.
