# he-hsc

**Archivo histórico recuperable. Frente activo retirado por decisión del
propietario el 2026-10-12.** Se conserva el corpus completo, su historia Git y
sus originales; los pendientes, cronogramas y handoffs describen su contexto
histórico y no constituyen encargos actuales.

La raíz completa se custodia en H289 fuera de `projects`, en
`/home/felix/archivo-proyectos/saneamiento-2026-10-11/segunda-ronda/retirados/he-hsc/`.
La recuperación verificada del estado previo y la historia final se conservan
en la carpeta privada `../../checkpoints/he-hsc/` desde esa raíz. El repositorio
remoto conserva su visibilidad pública previa y queda archivado; no sustituye
la custodia privada de los originales locales.

Corpus de seguridad y evaluación ofensiva del ecosistema HSC, orientado a evidencia,
mitigación y continuidad asistencial. No autoriza pruebas activas contra producción ni
terceros.

Empieza por `AGENTS.md` y limita cada intervención a la superficie y autoridad exactas.

## Orientación humana

- Resumen de sistemas observados: `sistemas/perfiles-forenses.md`.
- Auditorías y corpus normativo: `auditorias/`.
- Escenarios y vectores documentados: `escenarios/` y `vectores/`.
- Plan de remediación: `remediacion/plan-remediacion.md`.
- Contratos, puertos y evaluaciones del producto relacionado: `contratos/`, `puertos/`
  y `evals/`. Conservan referencias de diseño de `hd-hsc-os` con corte de mayo
  de 2026; sus requisitos y paths no se transfieren al producto actual por copia.

La evidencia histórica describe su fecha de observación. No demuestra que un hallazgo
siga vigente ni autoriza conexión, escaneo, explotación o divulgación.

## Propietarios de los frentes activos relacionados

Este archivo conserva evidencia y recomendaciones históricas. En
`/home/felix/projects/hd-dt`, `hd-dt` conserva decisiones de dominio y las
condiciones de habilitación; en `/home/felix/projects/hdapp`, `hdapp` es el único
producto técnico seleccionado por el propietario el 2026-10-11 y gobierna
código, contratos implementados y pruebas propias. Ninguna de esas fronteras
concede adopción institucional o convierte una revisión histórica en control
implementado.

La alternativa `hd-hsc-os` tiene retiro técnico autorizado. Su código y
documentación se recuperan desde la custodia privada del saneamiento; en H289,
`/home/felix/archivo-proyectos/saneamiento-2026-10-11/retirados/hd-hsc-os/`.
Comprueba el archivo antes de resolver sus paths. En
`/home/felix/projects/hsc-agent-cli`, `hsc-agent-cli` conserva el adaptador factual
y se contrasta en su raíz cuando el mandato exija actualidad.

La revisión de estas entradas y referencias es documental. Las conexiones,
escaneos, explotación y pruebas de producción permanecen `NOT_RUN`; no se
ha revalidado la vigencia o explotabilidad de los hallazgos.
