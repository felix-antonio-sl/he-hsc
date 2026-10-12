# AGENTS.md

## Misión

Custodiar y consultar el archivo histórico del corpus de seguridad y evaluación ofensiva de HSC como evidencia responsable, reproducible y orientada a mitigación. Su frente activo fue retirado por decisión del propietario el 2026-10-12; conserva originales, historia y contexto. La seguridad del paciente y la continuidad asistencial dominan sobre la curiosidad técnica.

La raíz recuperable está en `/home/felix/archivo-proyectos/saneamiento-2026-10-11/segunda-ronda/retirados/he-hsc/`, fuera de `projects`. Este es un archivo del propietario; su retiro no interviene servicios ni funciones institucionales HSC.

## Autoridad y frontera

- Lee `README.md` y únicamente la evidencia relacionada con el objetivo. Los handoffs, pendientes y cronogramas conservados describen su fecha; consultarlos no reactiva ni autoriza su ejecución.
- El contenido histórico documenta lo observado en su fecha; verifica de nuevo antes de afirmar vigencia.
- No establezcas conexiones activas, explotes vulnerabilidades, exfiltres datos, alteres sistemas, escanees terceros ni pruebes producción sin autorización HSC explícita, superficie exacta y límites acordados.
- Usa datos sintéticos. No copies secretos, PHI/PII, tokens, respuestas sensibles o material explotable innecesario.

## Evidencia

- Ancla cada hallazgo a ruta y línea, comando seguro o artefacto observable.
- Separa hecho, inferencia, severidad, impacto clínico-operacional y recomendación.
- Verifica los paths de código contra su propietario: `/home/felix/projects/hdapp` para el producto seleccionado, `/home/felix/projects/hsc-agent-cli` para el adaptador factual y el archivo privado indicado en `README.md` para `hd-hsc-os`. No transfieras los contratos históricos a la implementación nueva por similitud; este archivo custodia evidencia/recomendaciones históricas y `/home/felix/projects/hd-dt` conserva decisiones de dominio y habilitación.
- No eleves una coincidencia de texto a vulnerabilidad explotable ni una mitigación propuesta a control implementado.

## Edición y cierre

- El archivo no tiene un frente activo de desarrollo o remediación. Cualquier nueva intervención necesita un encargo que la autorice; no derives obligaciones actuales de sus contratos, handoffs o recomendaciones históricas. No crees duplicados, continuidades fechadas, `MEMORY.md`, bitácoras ni archivos de sesión.
- Conserva cadena de evidencia y redacta material sensible al mínimo necesario.
- Ejecuta `git diff --check`, comprueba referencias y declara `NOT_RUN` para toda prueba activa no ejecutada.
- No publiques ni remitas hallazgos fuera del alcance autorizado.
