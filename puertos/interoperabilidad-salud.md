# Spec puerto: interoperabilidad en salud

Estado: borrador controlado

## Propósito

Definir el puerto de aplicación para interoperar con sistemas externos de salud
sin acoplar el dominio a FHIR, Core CL, NID, SNRE, servicios terminológicos ni
un proveedor tecnológico específico.

## Fuente Canónica

- `CLAUDE.md`
- `02-datos/contrato-interoperabilidad-salud.md`
- `05-especificaciones/evals/cumplimiento-normativo-interoperabilidad.md`
- `01-dominio/categoria-dominio-hodom.md`
- `03-experiencia/flujos-criticos.md`

## Reglas

1. El dominio no importa FHIR ni SDKs externos.
2. El puerto habla en conceptos de aplicación/dominio.
3. El adaptador traduce a recursos FHIR y valida perfiles.
4. Toda operación clínica sensible deja auditoría.
5. Toda exportación declara propósito, destinatario y mínimo necesario.
6. Los errores distinguen falta de dato, identidad ambigua, autorización,
   terminología inválida, perfil inválido y falla técnica.

## Operaciones Iniciales

```text
HealthInteroperabilityPort
  receiveReferral(input) -> AdmissionReferral | InteroperabilityError
  exportEpisodeSummary(episodeId, requester, purpose) -> HealthExchangeBundle | InteroperabilityError
  exportPatientPortableRecord(patientId, requester, scope) -> PortableRecord | InteroperabilityError
  publishClinicalDocument(documentId, requester, purpose) -> PublishedDocumentRef | InteroperabilityError
  validateResource(resourceEnvelope) -> ValidationReport | InteroperabilityError

PatientIdentityPort
  resolvePatientIdentity(identityQuery) -> PatientIdentityMatch | IdentityError
  linkExternalIdentifier(patientId, externalIdentifier, evidence) -> IdentityLink | IdentityError
  recordMergeDecision(command) -> MergeDecision | IdentityError

TerminologyPort
  validateCode(coding, valueSet) -> TerminologyValidation | TerminologyError
  translateCode(coding, targetSystem) -> ConceptMapping | TerminologyError
  listAllowedValues(valueSet, version) -> ValueSetSnapshot | TerminologyError
```

## Objetos De Entrada/Salida

| Objeto | Descripción |
|---|---|
| `AdmissionReferral` | solicitud de ingreso normalizada desde sistema externo |
| `HealthExchangeBundle` | paquete de intercambio clínico para continuidad de cuidado |
| `PortableRecord` | export estructurado para titular/representante/tercero autorizado |
| `PublishedDocumentRef` | referencia auditable a documento clínico publicado |
| `ValidationReport` | resultado de validación de perfil, terminología y reglas locales |
| `PatientIdentityMatch` | match exacto, ambiguo, ausente o bloqueado |
| `IdentityLink` | vínculo entre identidad interna e identificador externo |
| `ConceptMapping` | traducción entre catálogo local y sistema oficial |

## Recursos FHIR Esperados Por Operación

| Operación | Recursos probables |
|---|---|
| `receiveReferral` | `ServiceRequest`, `Patient`, `Condition`, `Observation`, `DocumentReference`, `Organization`, `Practitioner` |
| `exportEpisodeSummary` | `Patient`, `Encounter`, `CarePlan`, `Condition`, `Observation`, `Procedure`, `MedicationRequest`, `DocumentReference` |
| `exportPatientPortableRecord` | `Bundle`, `Patient`, `Encounter`, `DocumentReference`, `CarePlan`, `Consent`, `AuditEvent` |
| `publishClinicalDocument` | `DocumentReference`, `Composition`, `Binary`, `Provenance` |
| `validateResource` | recurso FHIR envuelto con perfil, versión y finalidad |

## Errores Esperados

- `UnauthorizedRequester`
- `MissingPurpose`
- `PatientNotFound`
- `AmbiguousPatientIdentity`
- `ExternalIdentifierConflict`
- `ConsentRequired`
- `ConsentRevoked`
- `MinimumNecessaryViolation`
- `UnsupportedProfile`
- `ProfileValidationFailed`
- `TerminologyValidationFailed`
- `TerminologyServiceUnavailable`
- `DestinationUnavailable`
- `AuditWriteFailed`
- `InteroperabilityInvariantViolation`

## Auditoría Obligatoria

Cada operación exitosa o fallida debe emitir evento auditable con:

- actor;
- rol;
- paciente/episodio cuando aplique;
- propósito;
- destinatario;
- recurso o documento afectado;
- resultado;
- timestamp;
- razón de rechazo si falla;
- identificador de correlación.

## Criterios De Aceptación

- Ningún contrato menciona librería FHIR, endpoint real, ORM ni proveedor.
- Cada recurso exportado tiene mapping desde objeto de dominio o aplicación.
- Cada código clínico pasa por `TerminologyPort` o queda marcado como texto no
  codificado con deuda explícita.
- Toda operación sensible exige auditoría.
- El primer slice `Ingreso HODOM` puede declarar qué parte de este puerto usa o
  deja fuera de alcance.
