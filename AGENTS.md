# AGENTS.md

## Misión

Mantener el corpus de seguridad y evaluación ofensiva de HSC como evidencia responsable, reproducible y orientada a mitigación. La seguridad del paciente y la continuidad asistencial dominan sobre la curiosidad técnica.

## Autoridad y frontera

- Lee `README.md`, `HANDOFF.md` solo si existe y retomas trabajo material inconcluso, y únicamente la evidencia relacionada con el objetivo.
- El contenido histórico documenta lo observado en su fecha; verifica de nuevo antes de afirmar vigencia.
- No establezcas conexiones activas, explotes vulnerabilidades, exfiltres datos, alteres sistemas, escanees terceros ni pruebes producción sin autorización HSC explícita, superficie exacta y límites acordados.
- Usa datos sintéticos. No copies secretos, PHI/PII, tokens, respuestas sensibles o material explotable innecesario.

## Evidencia

- Ancla cada hallazgo a ruta y línea, comando seguro o artefacto observable.
- Separa hecho, inferencia, severidad, impacto clínico-operacional y recomendación.
- Verifica rutas citadas contra `../hd-hsc-os` o `../hsc-agent-cli` cuando esos repositorios sean la fuente.
- No eleves una coincidencia de texto a vulnerabilidad explotable ni una mitigación propuesta a control implementado.

## Edición y cierre

- Actualiza el informe autoritativo o el único `HANDOFF.md` raíz; no crees duplicados, continuidades fechadas, `MEMORY.md`, bitácoras ni archivos de sesión.
- Conserva cadena de evidencia y redacta material sensible al mínimo necesario.
- Ejecuta `git diff --check`, comprueba referencias y declara `NOT_RUN` para toda prueba activa no ejecutada.
- No publiques ni remitas hallazgos fuera del alcance autorizado.
