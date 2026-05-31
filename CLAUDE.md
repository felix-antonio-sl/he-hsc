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

Fecha: 2026-05-31
Fase: reconocimiento pasivo completado (4 sistemas perfilados)
Próximo: escaneo de vulnerabilidades activo (requiere autorización del HSC)

## Artefactos

| Directorio | Descripción |
|------------|-------------|
| `contratos/` | Contratos de seguridad e interoperabilidad (fuente: hd-hsc-os) |
| `auditorias/` | Auditorías de seguridad, forenses, cumplimiento y hacking ético |
| `evals/` | Checklists y evaluaciones de seguridad (SGSI, interoperabilidad) |
| `puertos/` | Puertos de seguridad e interoperabilidad (IAM-agnostic) |
| `certificacion/` | Evaluación virtual de sellos CENS |
| `experiencia/` | Seguridad en UX clínica |
| `sistemas/` | Perfiles forenses de los sistemas objetivo |
| `vectores/` | Vectores de ataque por sistema |
| `escenarios/` | Escenarios de ataque compuestos |
| `remediacion/` | Planes de acción y métricas |
| `handoff/` | Handoffs de sesión |

## Fuentes

- `hsc-agent-cli` — sonda forense en Go que lee los sistemas reales
- `hd-hsc-os` — sistema greenfield que reemplazará HODOM
- SGH, DAU, LIS — sistemas PHP legacy del hospital
- ESB Salud En Red — puente de interoperabilidad nacional
- Ley 21.663, Ley 21.719, ISO 27001, NIST CSF 2.0

## Reglas de enfrentamiento

1. **Sin conexiones activas** a sistemas vivos sin autorización explícita del HSC
2. **Sin explotación** de vulnerabilidades en producción
3. **Sin exfiltración** de datos reales
4. **Sin modificación** de sistemas objetivo
5. **Divulgación responsable** — hallazgos se comparten primero con el equipo del HSC
6. **Evidencia trazable** — cada hallazgo referencia archivo y línea del código fuente
7. **Clasificación de severidad** — Crítico/Alto/Medio/Bajo con impacto clínico explicitado
