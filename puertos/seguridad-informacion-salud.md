# Spec puerto: seguridad de información en salud

Estado: borrador controlado

## Propósito

Definir los puertos de aplicación que permitirán aplicar seguridad de
información en salud sin acoplar el dominio HODOM a un proveedor de identidad,
SIEM, bóveda de secretos, base de datos, cloud, librería FHIR o herramienta de
auditoría.

## Fuente Canónica

- `CLAUDE.md`
- `02-datos/contrato-seguridad-informacion-salud.md`
- `05-especificaciones/evals/seguridad-informacion-salud.md`
- `02-datos/contrato-interoperabilidad-salud.md`
- `01-dominio/categoria-dominio-hodom.md`

## Reglas

1. El dominio no conoce usuarios técnicos, sesiones, JWT, OAuth, IAM, SIEM ni
   secretos.
2. La aplicación pregunta si una acción está permitida antes de ejecutarla.
3. Toda operación sensible produce auditoría aunque falle.
4. La política de acceso usa actor, rol, paciente, episodio, establecimiento,
   finalidad, acción y contexto.
5. Los errores de seguridad no filtran datos clínicos ni existencia de pacientes
   a actores no autorizados.

## Operaciones Iniciales

```text
AccessControlPort
  evaluateAccess(request) -> AccessDecision | SecurityError
  requireAccess(request) -> GrantedAccess | SecurityError
  startBreakGlass(command) -> BreakGlassGrant | SecurityError
  revokeAccess(command) -> RevocationResult | SecurityError

SecurityAuditPort
  recordSecurityEvent(event) -> AuditReceipt | SecurityError
  queryAuditTrail(query) -> AuditTrail | SecurityError
  sealAuditBatch(batchId) -> SealReceipt | SecurityError

PrivacyGovernancePort
  classifyDataUse(input) -> DataUseClassification | SecurityError
  registerConsentDecision(command) -> ConsentRecord | SecurityError
  recordDataSubjectRequest(command) -> DataSubjectRequest | SecurityError
  createAnonymizedFixture(sourceRef, scope) -> FixtureManifest | SecurityError

ContinuityIncidentPort
  classifyIncident(candidate) -> IncidentClassification | SecurityError
  openIncident(command) -> IncidentCase | SecurityError
  recordIncidentUpdate(command) -> IncidentUpdate | SecurityError
  requestRestoreDrill(scope) -> RestoreDrillResult | SecurityError
```

## Objetos De Entrada/Salida

| Objeto | Descripción |
|---|---|
| `AccessDecision` | permitido, denegado, requiere break-glass o requiere consentimiento |
| `GrantedAccess` | decisión positiva con alcance, expiración y obligación de auditoría |
| `BreakGlassGrant` | acceso excepcional con razón, responsable, expiración y revisión |
| `AuditReceipt` | recibo de evento auditado con correlación y sello lógico |
| `AuditTrail` | vista filtrada de eventos para auditoría autorizada |
| `DataUseClassification` | clase de dato, finalidad, base de tratamiento y retención |
| `ConsentRecord` | consentimiento, rechazo o revocación con medio y alcance |
| `DataSubjectRequest` | solicitud ARSOP/portabilidad/acceso y estado |
| `FixtureManifest` | evidencia de anonimización o síntesis de datos de prueba |
| `IncidentClassification` | impacto, severidad, taxonomía y ruta de escalamiento |
| `RestoreDrillResult` | evidencia de restauración probada |

## Decisiones De Acceso

Estados esperados:

- `allowed`;
- `denied`;
- `requires-consent`;
- `requires-break-glass`;
- `requires-second-factor`;
- `requires-review`;
- `out-of-scope`;
- `system-degraded`.

## Errores Esperados

- `UnauthenticatedActor`
- `UnauthorizedActor`
- `PurposeRequired`
- `ConsentRequired`
- `ConsentRevoked`
- `PatientScopeMismatch`
- `EpisodeScopeMismatch`
- `TenantScopeMismatch`
- `BreakGlassReasonRequired`
- `AuditWriteFailed`
- `AuditTrailTamperSuspected`
- `SensitiveDataLeakRisk`
- `SecretMaterialDetected`
- `IncidentReportRequired`
- `RestoreEvidenceMissing`

## Eventos De Auditoría Mínimos

| Evento | Cuándo |
|---|---|
| `ClinicalRecordRead` | lectura de ficha, episodio, documento o resumen |
| `ClinicalRecordChanged` | escritura o modificación clínica |
| `AdmissionDecisionChanged` | aceptación, rechazo, espera o apertura de episodio |
| `DocumentExported` | descarga, envío, bundle FHIR o portabilidad |
| `ConsentChanged` | consentimiento, rechazo o revocación |
| `AccessDenied` | denegación por política |
| `BreakGlassStarted` | acceso excepcional |
| `BreakGlassReviewed` | revisión posterior |
| `SecurityIncidentCandidate` | evento que puede constituir incidente |
| `MigrationDataAccessed` | acceso a extract o dato migratorio |

## Criterios De Aceptación

- Ninguna operación menciona tecnología concreta.
- Todo acceso sensible exige `purpose`.
- Toda decisión crítica produce evento auditable.
- `break-glass` no es bypass silencioso.
- Los datos de prueba con origen real requieren `FixtureManifest`.
- El primer slice puede declarar qué operaciones usa y cuáles difiere.
