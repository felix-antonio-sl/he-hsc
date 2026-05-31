# Handoff — Evaluación Virtual CENS para hd-hsc-os

Fecha: 2026-05-30
Origen: investigación de cuerpo normativo completo + sondeo de la red del HSC vía `hsc-agent-cli`
Alcance: autoevaluación pre-sello contra los 3 sellos de software de CENS + B-PRACSIS (madurez institucional) + Asesoría de Interoperabilidad. (CENS ofrece 6 certificaciones en total; aquí se cubren estas 5.)
Estado: evaluación documental terminada y **remediada 2026-05-30** tras auditoría (`auditoria-cens-certificacion-virtual-2026-05-30.md`); implementación de brechas pendiente

## Lo que está terminado

### Artefacto principal
- `docs/05-especificaciones/evals/cens-certificacion-virtual.md` — evaluación completa (~500 líneas) con:
  - 8 subcaracterísticas ISO/IEC 25010 evaluadas contra código del repo
  - Evaluación RCE (seguridad 62.5% gate + usabilidad 75%)
  - Evaluación Telemedicina (clínica 70% + técnica 50%)
  - B-PRACSIS: **no autoevaluable desde el repo** (requiere instrumento CENS aplicado al HSC)
  - Asesoría de Interoperabilidad (diseño documentado, 0 implementaciones; CENS la estructura en 4 servicios, no en niveles 1-5)
  - Apéndice A con caracterización de la red asistencial del SS Ñuble

### Fuentes normativas consultadas (todas vivas a mayo 2026)
- **CENS:** sellos-y-certificaciones, B-PRACSIS, CENS Pharma, bienes públicos (Guía Privacidad, Modelo Competencias 2.0)
- **MINSAL Interoperabilidad:** Estándares y Perfiles, NID v0.4.8 (MPI+HPD), EIS v0.1.0, CLIPS v0.4.0, SNRE v0.9.6
- **Core CL:** v1.9.4 (evolutiva), perfiles nacionales FHIR R4
- **BCN:** Ley 20.584, 21.541, 21.719, 21.663, DS 295/2024, Res. ANCI 7/2025, DE MINSAL 9/2023
- **Transformación Digital del Estado:** Ley 21.180, NT 7-12, DS 12/2023 (modificado por DS 876/2025)
- **ISO:** 25010:2011, 13131:2021, 27001:2022
- **Son**deo operacional: DAU, SGH, LIS, HCC/ESB caracterizados desde `hsc-agent-cli`

### Veredictos consolidados

| Sello | Score | Veredicto |
|---|---|---|
| Software en Salud (ISO 25010:2011) | 86.2% global · Seguridad 57.1% (gate) | **NO OTORGABLE** — gate de seguridad reprobado (firma `✗`) |
| Registro Clínico Electrónico | Usabilidad 75% · Seguridad 62.5% (gate) | **Condicionado** — gate de seguridad bajo umbral |
| Telemedicina | Clínica 70% · Técnica 50% | **No aprobado** — C4 consentimiento + T1 interop/Fonasa `✗` |
| B-PRACSIS (Madurez HSC) | No autoevaluable | Requiere instrumento CENS aplicado al HSC |
| Asesoría Interoperabilidad | Diseño documentado | 0 implementaciones FHIR/Core CL/NID/MPI |

*Scoring con metodología fija reproducible (`◐`=0.5; Seguridad como gate). La versión previa reportaba 89%/75%/67% con un `◐` variable que promediaba seguridad reprobada; corregido en la remediación.*

## Pendientes (por orden de bloqueo)

### Bloque A — Bloqueantes para sellos (4 ítems, dep: backend + institucional)
1. **Consentimiento informado digital** — diseñado en `.md` (`informed_consent`/`consent_record`), sin tabla/dominio/adaptador. Bloquea Sello Telemedicina + RCE
2. **Adaptador FHIR productivo** — puertos documentados (HealthInteroperabilityPort, PatientIdentityPort, TerminologyPort) **solo en `.md`, no como tipos TS**; cero implementación. Bloquea Telemedicina + baja Compatibilidad en Software en Salud
3. **Identidad: MPI clínico vs autenticación** — el MPI nacional (PIXm/PDQm, NID) resuelve matching de paciente; **Clave Única resuelve autenticación de acceso**, no es un MPI. Son problemas distintos; implementar ambos por separado
4. **Firma electrónica avanzada** — marco: **Ley 19.799** (firma electrónica). El soporte de documentos electrónicos del Estado es NT 10 (Documentos y Expedientes); NT 9 es Autenticación. *(La versión previa atribuía firma a NT 10 e identidad a NT 9 — materias cruzadas, corregido.)*

### Bloque B — Mejoras de puntuación (6 ítems, autonomía parcial)
- WCAG 2.1 AA formal
- RTO/RPO con HSC
- Matriz de acceso RBAC productiva
- audit_log por episodio con datos reales (Pasado CA#10)
- CENS Pharma como terminología de medicamentos
- Términos y condiciones de servicio de interoperabilidad

### Bloque C — Madurez institucional (5 ítems, dep: HSC)
- Dueño institucional SGSI
- B-PRACSIS formal con equipo HSC
- Plan de capacitación
- Delegado de protección de datos (Ley 21.719)
- Infraestructura (servidores, dispositivos móviles, VPN)

## Supuestos del diagnóstico

1. Los umbrales de aprobación de CENS son inferidos (≥70% para Software, ≥75% para RCE). CENS no los publica.
2. La evaluación asume que la matriz de acceso RBAC diseñada en ADR 0016 se implementará antes del cutover.
3. Se asume que el MPI nacional (NID v0.4.8) estará disponible cuando hd-hsc-os requiera interoperar.
4. Se asume que el ESB Salud En Red seguirá siendo el puente regional post-cutover.
5. Los pesos de las subcaracterísticas son inferidos del énfasis público de cada sello CENS.

## Riesgos identificados

1. **FHIR es greenfield total en la red:** hd-hsc-os será el primer productor FHIR del HSC. No habrá consumidores FHIR locales para validar en producción.
2. **HODOM existe hoy en SGH:** servicio_id=72, sala=635. La migración no es greenfield puro. Los datos legacy tienen calidad irregular (evolucion_id=0 frecuente).
3. **Identidad es RUT, no MPI:** el SGH/DAU/LIS usan RUT módulo 11. El MPI nacional está en draft. El adaptador de identidad debe ser bidireccional.
4. **Proxy único como punto de fallo:** 100.77.30.26 concentra el acceso a todos los sistemas legacy. hd-hsc-os con PWA offline no depende de él, pero la migración sí.
5. **Caché clínica sin cifrar:** el CLI del ecosistema HSC cachea en `~/.cache/hsc-agent-cli/` JSON **sin cifrado** (aunque con permisos `0600`/`0700` y TTL por tipo). El déficit es la falta de cifrado, no la ausencia de control. hd-hsc-os debe elevar el estándar.

## Lo que NO cubre esta evaluación

- Cumplimiento de cada NT de la Ley 21.180 verificada contra implementación (solo se verificó diseño)
- Pruebas de penetración o seguridad ofensiva
- Validación de Fase 0 con clínico real
- Costos reales de certificación. Estimación interna ~322 UF + IVA (Telemedicina ~99 UF + B-PRACSIS informe ~25 UF + Software ~89-99 UF + RCE sin precio público), **no es una tarifa de paquete cotizada por CENS** — solicitar cotización formal
- Evaluación de proveedores cloud o infraestructura de hosting
- La evaluación oficial de CENS (que requiere pago, contrato y demo funcional)

## Próximo paso recomendado

Contactar a Eric Rojas (erojas@cens.cl) con este documento como pre-evaluación. Solicitar:
1. Confirmación de aplicabilidad de los 3 sellos para un sistema de hospitalización domiciliaria
2. Posibilidad de evaluación temprana (pre-producción) con demo funcional
3. Cotización formal para el paquete completo

## Relación con otros handoffs

- `auditoria-cens-certificacion-virtual-2026-05-30.md` — **auditoría profunda de esta evaluación** (17 hallazgos: 4 críticos, 6 mayores, 7 menores) y registro de la remediación aplicada
- `handoff-desarrollo.md` — estado general del repo (1.144 casos de test, 68 migraciones, ambos ápexes e2e)
- `handoff-cutover-persistente-2026-05-29.md` — estrategia de cutover
- `handoff-migracion-legacy.md` — migración desde hdos
- `auditoria-cumplimiento-2026-05-29-cierre.md` — estado del carril frontend
