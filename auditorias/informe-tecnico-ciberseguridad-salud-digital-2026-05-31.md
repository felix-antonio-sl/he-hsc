# Informe Técnico — Brecha de Ciberseguridad y Compliance · Salud Digital Chile

Para: equipo de desarrollo (backend, frontend, datos) + Dirección Técnica HODOM-HSC
Fecha: 2026-05-31
Alcance: **ciberseguridad y compliance completos** de hd-hsc-os como sistema de salud digital de un hospital público chileno (servicio esencial, Ley 21.663). Superconjunto del informe CENS (`informe-tecnico-cierre-brechas-cens-2026-05-31.md`), que cubre solo los sellos de calidad.
Método: estado verificado contra el código (exploraciones dirigidas + verificación de paths). Integra y **corrige** los informes-fuente en `_TEMP_BORRAR/informe_ciber/` (informe de requisitos + crítica salubrista + investigación de compliance). Cada path citado existe.

---

## 0. Cómo leer este informe — tres categorías que NO se deben mezclar

La distinción que ordena todo lo demás (y que el plan debe respetar):

| Categoría | Pregunta | Urgencia |
|---|---|---|
| 🔴 **EXPOSICIÓN ACTUAL** | ¿Hay datos reales de pacientes en riesgo *hoy*, en un activo que ya existe? | **Inmediata** — no es deuda futura |
| 🟠 **DEUDA DE IMPLEMENTACIÓN** | ¿Está diseñado/contratado pero sin construir? | Antes del cutover productivo |
| 🟡 **AUSENCIA DE GOBERNANZA** | ¿Falta un documento operativo, rol institucional o decisión? | Antes de operar / dependencia HSC |

El error de los informes-fuente es presentar todo como "deuda de diseño". La verificación contra código muestra que **dos frentes ya son exposición actual de PII real** (§1). Esos se contienen primero; lo demás es secuenciable.

---

## 1. 🔴 EXPOSICIÓN ACTUAL — lo urgente (verificado contra código)

### 1.1 — Datos clínicos sin cifrar en el dispositivo (PWA offline)

**Confirmado.** La cola offline escribe datos clínicos en **texto plano** en el navegador del equipo de terreno.

- `interfaces/web/src/offline/indexeddb-outbox-store.ts` — `store.put(entry)` serializa el `OutboxEntry` completo sin cifrar (IndexedDB `hodom-outbox`/`entries`).
- Payloads clínicos en claro: **narrativa del acto clínico** y decisión (`acto-clinico-firmado`, en `shell/app-shell.tsx`), **notas de visita** (`registro-visita`, en `superficies/visita.tsx`), **coordenadas del domicilio** (`domicile-georef`, lat/lng + `capturedBy`).
- **Borradores en `localStorage`** sin cifrar: `hd-acto-clinico:<episodeRef>:borrador` (autosave de la narrativa) en `pulso/acto-clinico-module.tsx`.
- **Cero cifrado en cliente:** no hay `crypto.subtle`, `libsodium` ni `dexie-encrypted`; `package.json` (web) no incluye ninguna librería de cifrado. El único `crypto.*` es `crypto.randomUUID()` para IDs.
- **Sin wipe ni TTL:** `logout` (`auth/auth-bar.tsx` → `auth-gateway.ts` → `client.ts: postLogout`) invalida la cookie en el servidor pero **no limpia IndexedDB ni localStorage**. No hay purga por expiración ni wipe remoto.
- **SyncEngine.flush no es automático:** el listener de `online` en `shell/app-shell.tsx` solo hace `setOnline(true)`; `sync-engine.ts:flush()` no se invoca al recuperar red → la cola con datos clínicos persiste más de lo necesario.

**Estado normativo:** las ADRs 0011/0013 marcan el cifrado del store local como "se decide con la ADR de seguridad" y el `contrato-seguridad-informacion-salud.md` pide explícitamente "cola offline **cifrada y borrable**". O sea: **deuda reconocida en diseño, pero exposición real en el código** — un equipo en San Carlos que pierde el teléfono expone narrativa clínica, decisiones y la ubicación del domicilio del paciente, en claro. Severidad: **crítica** (Ley 21.719 datos sensibles + S6 del propio contrato).

**Mitigación inmediata (sprint actual):**
1. Cifrar payloads antes de `store.put` con WebCrypto (AES-GCM, clave derivada de la sesión) — o `dexie-encrypted`.
2. `wipe()` de IndexedDB + localStorage en `logout` y al expirar sesión.
3. `SyncEngine.flush()` en el listener `online` + TTL de la cola alineado a la sesión (≤8h, ADR 0016).
4. Aunque la implementación del cifrado se difiera, la **política de wipe/expiración debe quedar escrita ya**.

### 1.2 — BD de cutover persistente sin cierre de cadena de custodia

**Confirmado — y más grave que "dry-run".** Los informes-fuente describen la migración como "dry-run sobre datos reales". La realidad verificada: el **cutover real se ejecutó el 2026-05-30** y persiste **733 pacientes, 799 episodios, 733 domicilios y ~2.998 `source_identifier` con RUT real** en el contenedor `hd-hsc-os-pg:5556`, **activo hoy**.

Lo que está **bien hecho** (no alarmar de más): extract `BEGIN TRANSACTION READ ONLY` (`adaptadores/migracion/extract-hdos.ts`), **minimización de columnas** (`EXTRACT_CONTRACT` — nunca `SELECT *`; no extrae nombre/sexo/fecha de nacimiento), staging cifrable con `age`, manifest sin filas, PII efímera en runner Testcontainers, staging gitignored, y **cero RUN/RUT real en el repo** (fixtures `SYN-`).

Lo que es **exposición actual:**
- El cutover persistente se ejecutó **sin la ceremonia de autorización formal** que el propio `docs/02-datos/cadena-custodia-extract-hdos.md` §3 exige (autorización escrita, base legal, llaves, ventana). Se hizo de modo informal.
- La BD destino **no tiene log de cierre de custodia**: no hay evento `destroyed`, ni retención definida, ni registro de quién accede. Bajo Ley 21.719 (acceso/destrucción auditables) y Ley 20.584, esto es una custodia "abierta" sobre datos reales.
- Credenciales en `.env.target` (gitignored, pero password en claro); passphrase de backups en `~/.config/hd-hsc-os/backup-pass`; volumen Docker **sin cifrado de disco** (el `age` solo protege los backups, no la BD viva).

**Mitigación inmediata:** ceremonia de cierre documentada (autorización + base legal + retención + destrucción auditable); log de custodia del cutover (`authorized`/`backup`/`destroyed`); decisión de cifrado en reposo de la BD viva o destrucción si era solo validación; passphrase a bóveda.

### 1.3 — PII clínica real en un documento del working tree

**Confirmado.** `docs/02-datos/2026-05-30-dictamen-clinico-cuarentena.md` (hoy **untracked**, en el árbol de trabajo) contiene **17 `stay_id` reales + diagnósticos/patologías reales** (ACV, cáncer, demencia vascular, enfermedad pulmonar intersticial…) **+ fechas reales** de ingreso/egreso. No tiene nombres ni RUT directos, pero **stay_id + diagnóstico + fecha permite reidentificación** cruzando con el legacy → es dato sensible de salud bajo Ley 21.719.

**Acción:** decidir explícitamente si este archivo (y `2026-05-30-revision-clinica-cuarentena.md`) puede versionarse. Recomendación: **no commitearlo** con contenido reidentificable; moverlo a un store con custodia o seudonimizar los `stay_id` y agregar las rutas al `.gitignore`. (Nota operativa: estos archivos pertenecen a un carril paralelo del operador — no los toqué; se reportan como hallazgo, la decisión es del operador/DPO.)

---

## 2. Mapa normativo completo (Chile salud digital)

| Norma / marco | Ámbito | Exigencia clave para hd-hsc-os |
|---|---|---|
| **Ley 20.584** | Ficha clínica | Confidencialidad, acceso del titular, **conservación mínima 15 años**, portabilidad, consentimiento |
| **Ley 21.541** | Telemedicina | Registro de identidad/medio/condiciones, consentimiento, seguridad de plataforma |
| **Ley 21.719** | Datos personales (vigencia **1-dic-2026**) | Datos de salud = sensibles; **EIPD**, **delegado de protección de datos**, derechos ARSOP, base de licitud, supresión al cesar finalidad |
| **Ley 21.663** | Ciberseguridad | Salud = **servicio esencial**; seguridad por diseño (Art. 8 SGSI); **reporte de incidentes** al CSIRT Nacional (Art. 9) |
| **DS 295/2024** | Reglamento de reporte de incidentes | Clasificación y canal de notificación |
| **Res. ANCI 7/2025** | Taxonomía de incidentes | Incidentes significativos, canal al CSIRT |
| **Ley 21.180 + NTs 7-12** | Transformación Digital del Estado | NT7 Seguridad/Ciber · NT8 Notificaciones · **NT9 Autenticación (Clave Única)** · **NT10 Documentos/Expedientes (firma avanzada → Ley 19.799)** · NT11 Calidad de plataformas (**WCAG 2.1 AA**) · NT12 Interoperabilidad |
| **DE MINSAL 9/2023 (NT 231)** | Estándares de información en salud (EIS) | Interoperabilidad sintáctica/semántica |
| **DS 6/2022 MINSAL** | Atención de salud a distancia | Reglamento de telemedicina (con ISO 13131) |
| **ISO/IEC 27001:2022** | SGSI | Sistema de gestión: riesgo, controles Anexo A, mejora continua |
| **NIST CSF 2.0** | Marco de ciberseguridad | Gobernar · Identificar · Proteger · Detectar · Responder · Recuperar |
| **Política Nacional de IA / CTCI 2021** | IA responsable | Transparencia, trazabilidad, supervisión humana, no discriminación, responsabilidad |
| **Sellos CENS** (Software/RCE/Telemedicina) + B-PRACSIS | Calidad / madurez | Ver `cens-certificacion-virtual.md` (remediado) |

> Corrección a los informes-fuente: la atribución de NT9/NT10 **ya está bien** en la investigación de compliance (NT9=Autenticación, NT10=Documentos), pero el eval CENS las tenía cruzadas (corregido). La firma electrónica avanzada se rige por **Ley 19.799**, soportada por NT10.

---

## 3. Estado por dominio de ciberseguridad (verificado contra código)

| Dominio | Estado real | Categoría | Path / evidencia |
|---|---|---|---|
| **Identidad y acceso (RBAC)** | **~80%**: `auth.identity/identity_role/session/policy` (mig. 0062-0066), `PgIdentityService` (Argon2id), middleware `req.actor`, `/auth/login`. Falta: `PgPolicyAccessControl` que **lea** `auth.policy` (hoy solo `PgAllowAll*`), enforcement (54 `PG_ACTOR_*` simulados), `/auth/logout`+`/auth/yo`+MFA, seed de policy | 🟠 Deuda | `adaptadores/auth/identidad-pg.ts`, `interfaces/api/middleware/identidad.ts`, `adaptadores/postgres/soporte-pg.ts:971` |
| **Auditoría / no repudio** | `audit_event` **INSERT-only real** + RLS + REVOKE físico (mig. 0068). Falta: **sello lógico encadenado** (`sello_logico` siempre null), `correlation_id`, audit-panel conectado a datos reales | 🟠 Deuda | `adaptadores/postgres/seguridad-pg.ts`, `migrations/0068-append-only-revoke.sql` |
| **Cifrado en tránsito** | TLS = deployment-concern (Nginx/proxy), sin ADR ni config en repo | 🟡 Gobernanza | sin ADR de TLS |
| **Cifrado en reposo (servidor)** | **0%** — sin KMS, sin `pgcrypto`, PII en claro en PostgreSQL | 🟠 Deuda + 🔴 (BD viva §1.2) | ningún ADR menciona KMS |
| **Cifrado en cliente (PWA)** | **0%** — IndexedDB/localStorage en claro | 🔴 **Exposición actual** | §1.1 |
| **Migración / custodia** | extract minimizado y read-only **bien**; cutover persistente **sin cierre de custodia** sobre 733 pacientes reales | 🔴 **Exposición actual** | §1.2, `adaptadores/migracion/extract-hdos.ts`, `cadena-custodia-extract-hdos.md` |
| **Interoperabilidad FHIR** | **0%** — 3 puertos en `.md`, sin tipos TS ni adaptador | 🟠 Deuda (no toca OPM) | `docs/05-especificaciones/puertos/interoperabilidad-salud.md` |
| **Identidad de paciente / MPI** | UUID v7 + `source_identifier` **sí**; matching/merge **no** | 🟠 Deuda (merge **toca OPM**) | ADR 0003, mig. 0002/0067 |
| **Continuidad (RTO/RPO)** | Requisito sin valores; sin plan de modo degradado ni prueba de restauración | 🟡 Gobernanza (dep. HSC) | `contrato-seguridad…md` §continuidad |
| **Runbook de incidentes** | **No existe** (solo intención + puerto `IncidentClassification`) | 🟡 Gobernanza — **bloquea Ley 21.663 Art. 9** | `puertos/seguridad-informacion-salud.md` |
| **Protección de datos (EIPD/DPO/retención)** | EIPD no existe; DPO no designado; retención vs supresión sin matriz | 🟡 Gobernanza — **obligatorio Ley 21.719** | `contrato-seguridad…md` |
| **IA responsable** | Principio "IA auxiliar, trazable y descartable; el humano decide" en spec; **responsabilidad (quién responde si la IA falla) no especificada** | 🟡 Gobernanza | spec del repo |
| **Seguridad clínica** | Fuerte: PatientBand, ActionGuard, ConfirmIrreversible, IdentityVerification (5 contextos), alertas estratificadas, MAR append-only (D22) | ✅ Cubierto | `interfaces/web/src/componentes/` |
| **Firma electrónica avanzada** | **0%** (sin `document_signature`, sin paso firmar) | 🟠 Deuda (**toca OPM**; recomendado diferir V2) | — |
| **SGSI / inventario de activos** | Contrato declarativo; sin dueño, ciclo, KPIs, matriz de riesgos, inventario con responsables | 🟡 Gobernanza | `contrato-seguridad-informacion-salud.md` |

---

## 4. Cobertura por marco (diseño vs implementación vs brecha principal)

| Marco | Diseño | Implementado | Brecha principal |
|---|---|---|---|
| **Ley 21.663 (Ciberseguridad)** | Arts. 8 y 9 mapeados | ✗ | **Sin SGSI operativo, sin runbook de incidentes** (no se podría reportar en <3h) |
| **Ley 21.719 (Datos personales)** | Principios en contratos | ◐ | **Sin EIPD, sin DPO, sin política de supresión**; + exposición §1 |
| **Ley 20.584 (Ficha clínica)** | Acceso/conservación referenciados | ◐ | Retención 15 años vs supresión sin resolver |
| **Ley 21.180 (NTs 7-12)** | NTs mapeadas | ◐ | NT7 (ciber) y NT10 (firma) sin implementar; NT11 (WCAG) sin auditoría formal |
| **ISO 27001:2022** | Controles del Anexo A referenciados | ✗ | Sin inventario de activos, sin ciclo PDCA, sin mapeo control-a-control |
| **NIST CSF 2.0** | "Gobernar/Identificar" parcial | ✗ | **Proteger/Detectar/Responder/Recuperar sin implementación** |
| **Sellos CENS** | 3 sellos evaluados | ✗ | Gate de seguridad + interop (ver informe CENS) |

---

## 5. Plan de acción — tres olas

```
🔴 OLA 0 — CONTENER EXPOSICIÓN ACTUAL (sprint actual, no negociable)
  0.1 Cifrar IndexedDB/localStorage (WebCrypto AES-GCM) + wipe en logout + flush en `online` + TTL ≤8h
  0.2 Cerrar cadena de custodia del cutover persistente: ceremonia escrita (autorización + base legal),
      log destroyed/retención, decisión cifrado-en-reposo de la BD viva, passphrase a bóveda
  0.3 Resolver PII real en docs: seudonimizar stay_id del dictamen de cuarentena o sacarlo del árbol
      → decisión del operador/DPO; gitignore de docs/02-datos/2026-05-30-*cuarentena*.md

🟠 OLA 1 — GATE DE SEGURIDAD TÉCNICO (no pasa por OPM; arrancable ya)
  1.1 RBAC productivo: PgPolicyAccessControl (lee auth.policy) + enforcement req.actor + seed + /auth/logout,/yo,MFA
  1.2 Auditoría fuerte: sello lógico encadenado + correlation_id + audit-access-panel con datos reales
  1.3 Cifrado en reposo servidor: ADR 0017 (secretos+KMS) → columnas sensibles + respaldos cifrados con restauración probada
  1.4 A2 Adaptador FHIR (dominio limpio): puertos TS + mappers Patient/Encounter/ServiceRequest/Consent + validación Core CL

🟡 OLA 2 — GOBERNANZA (algunas dependen del HSC; arrancables en paralelo)
  2.1 Runbook de incidentes (Ley 21.663 Art.9 / DS 295 / ANCI 7): matriz severidad, árbol CSIRT sí/no,
      plazos <3h/<72h/<15d, canal con oficial de enlace HSC, tabletop probado
  2.2 EIPD ejecutada (disparada por: datos sensibles + tratamiento masivo + geolocalización + teleatención)
  2.3 Designar DPO (Ley 21.719) + dueño del SGSI + ciclo de revisión + matriz de riesgos + inventario con responsables
  2.4 Política retención/supresión: matriz tipo-de-dato → plazo → quién suprime → auditoría
  2.5 RTO/RPO cuantificados + plan de modo degradado + clasificación OIV/servicio esencial (con HSC)
  2.6 Mapeo control-a-control NIST CSF 2.0 / ISO 27001:2022
  2.7 IA responsable: declarar responsabilidad (quién responde si la IA falla)

DOMINIO (pasa por hd-opm antes — OPM MANDA):
  A1 Consentimiento digital (proceso otorgar/revocar) · A3 merge de identidad · A4 firma (diferir V2)
```

**Racional de orden:** Ola 0 son datos reales en riesgo hoy → primero. Ola 1 cierra el gate que reprueba los sellos CENS y es técnica pura. Ola 2 es gobernanza, parcialmente dependiente del HSC, pero **el runbook y la EIPD bloquean operar legalmente** y deben empezar ya en paralelo.

---

## 6. Correcciones a los informes-fuente (las imágenes)

Para evitar arrastrar errores a decisiones:

| Afirmación en los informes-fuente | Corrección verificada |
|---|---|
| "migración: dry-run sobre datos reales" | **Es cutover persistente real**: 733 pacientes vivos en `:5556` sin cierre de custodia (más grave) |
| "517 tests web" | **538 web + 606 backend = 1.144 casos** en 121 archivos (la suite reporta ~1.178) |
| "13/13 componentes" | spec define **12**; directorio tiene 16 (4 no clínicos) |
| "matriz de acceso = puertos fake en P0" | RBAC está al **~80%** (tablas+identidad+middleware); falta leer `auth.policy` + enforcement |
| "Total ~322 UF" certificación | Estimación interna, **no tarifa de paquete cotizada** por CENS (RCE sin precio público) |
| IndexedDB "deuda de diseño" | Es **exposición actual** (datos clínicos en claro, sin wipe) — confirmado en código |
| NT9/NT10 (en el eval CENS) | Cruzadas en el eval (corregido); la investigación de compliance ya las tiene bien |

Lo que los informes-fuente **acertaron** y se mantiene: el mapa normativo completo, los plazos de incidentes (<3h/<72h/<15d), los disparadores de EIPD, los flujos FHIR por recurso, la atribución de NTs en la investigación de compliance, y el veredicto cualitativo de la crítica salubrista ("distancia entre lo declarado y lo implementado").

---

## 7. Reglas operativas

- **Exposición actual ≠ deuda de diseño.** No diferir la Ola 0 con el argumento "está en el contrato/ADR como pendiente": mientras no se implemente, hay datos reales en riesgo.
- **OPM MANDA.** A1/A3/A4 tocan dominio → `hd-opm` primero. El gate de seguridad (RBAC, auditoría, cifrado), interop FHIR y la gobernanza son realización/proceso, no dominio clínico.
- **No inventar.** Todo path aquí está verificado; al implementar, calcar el patrón de slice existente (§5 del informe CENS).
- **Repo multi-agente.** Commit por ruta explícita, nunca `git add -A`. Los archivos de cuarentena (§1.3) son de un carril paralelo del operador.
- **Servicio esencial.** Bajo Ley 21.663, hd-hsc-os es infraestructura crítica de salud: el estándar no es "cumple un sello" sino "opera sin exponer al paciente".

---

## 8. Artefactos relacionados

- `informe-tecnico-cierre-brechas-cens-2026-05-31.md` — subconjunto CENS (sellos de calidad).
- `cens-certificacion-virtual.md` (remediado) + `auditoria-cens-certificacion-virtual-2026-05-30.md`.
- `docs/02-datos/contrato-seguridad-informacion-salud.md` · `docs/05-especificaciones/evals/seguridad-informacion-salud.md` · `docs/04-arquitectura/auditoria-seguridad-informacion-salud.md`.
- `docs/05-especificaciones/puertos/seguridad-informacion-salud.md` (puerto IncidentClassification).
- `docs/02-datos/cadena-custodia-extract-hdos.md` · `docs/04-arquitectura/handoff-cutover-persistente-2026-05-29.md`.
- ADRs 0003 (identidad), 0005 (append-only), 0007 (RLS), 0011/0013 (offline/PWA — cifrado pendiente), 0016 (auth/RBAC).
- Fuente externa: `_TEMP_BORRAR/informe_ciber/` (informe de requisitos + crítica salubrista + investigación de compliance, 2026-05-29).
