# Auditoría de la Evaluación Virtual CENS

Fecha: 2026-05-30
Objeto auditado: `cens-certificacion-virtual.md` (eval) + `handoff-cens-certificacion-2026-05-30.md` (handoff)
Método: triple verificación independiente — (1) reproducción aritmética del scoring, (2) verificación factual contra el código del repo, (3) verificación de la topología del Apéndice A contra `hsc-agent-cli` real, (4) verificación normativa contra fuentes oficiales (CENS, BCN/LeyChile, MINSAL, ISO, ANCI).
Veredicto del objeto: **estructuralmente sólido, factualmente contaminado. No enviable a CENS sin una pasada de corrección.**
Estado: **REMEDIADO el 2026-05-30.** Los 17 hallazgos (C1-C4, M1-M6, m1-m7) fueron corregidos en `cens-certificacion-virtual.md` (ver su §9) y en el handoff. Este documento se conserva como registro de la auditoría y de la metodología de verificación.

---

## Resumen ejecutivo

El documento acierta en dos planos difíciles: la **caracterización macro de la red asistencial** (verificada contra código) y un **conjunto grande de referencias normativas duras** que resultaron reales pese a parecer sospechosas (Fonasa obligatorio en Telemedicina, DS 876/2025, contacto Eric Rojas, leyes, versiones MINSAL). El esqueleto analítico es bueno y la cobertura es amplia.

Pero el trabajo está atravesado por el mismo anti-patrón que este proyecto declara combatir — **"dato sin fuente jamás como valor plausible"**: rellena con cifras concretas, nombres de endpoints y atribuciones normativas que *aparentan* precisión y no resisten verificación. La capa de cuantificación (el titular "89% CUMPLE") no es reproducible y enmascara seguridad reprobada. Un documento cuyo propósito es certificar rigor reproduce el defecto que su propio dominio vigila.

| Severidad | Hallazgos | Efecto |
|---|---|---|
| **CRÍTICO** | 4 | Destruyen credibilidad ante un evaluador CENS o inducen decisión errónea |
| **MAYOR** | 6 | Inflan o distorsionan el veredicto; metodología no defendible |
| **MENOR** | 7 | Erosionan confianza por imprecisión acumulada |
| **SÓLIDO** | — | Lo que sí está bien verificado (no todo es crítica) |

---

## CRÍTICOS

### C1 — Atribución normativa cruzada: NT 9 y NT 10 (Ley 21.180)
El eval afirma "NT 9 exige MPI/identidad" (línea 65 handoff §A3) y "NT 10 exige firma electrónica avanzada" (líneas 36, 254), y sobre esa base levanta el veredicto `✗` de la subcaracterística 6.4 (Autenticidad).
**Realidad verificada:** **NT 9 = Norma Técnica de *Autenticación*** (no MPI); **NT 10 = *Documentos y Expedientes Electrónicos*** (no firma avanzada). La materia está cruzada. Un evaluador de CENS o de la Secretaría de Gobierno Digital lo detecta de inmediato, y arrastra un veredicto bloqueante apoyado en la norma equivocada.
**Fuente:** wikiguias.digital.gob.cl/Normas/Decreto9 y /Decreto10; PDF oficial NT-10 en cens.cl.

### C2 — Escala inventada: "Asesoría de Interoperabilidad Nivel 2/5"
El eval cierra con "Madurez actual: Nivel 2 — Diseño documentado" y consolida "Nivel 2/5" (líneas 229, 241).
**Realidad verificada:** CENS estructura su Asesoría de Interoperabilidad en **4 servicios secuenciales nombrados** (Evaluación de mensajería, Diagnóstico, Propuesta, Implementación). **No existe un framework numerado 1-5.** El veredicto cita una escala que no es pública.
**Fuente:** cens.cl/asesorias-en-interoperabilidad.

### C3 — Apéndice A: 7 de 9 endpoints PHP están fabricados
El Apéndice A es el activo que el handoff destaca como "topología real de la red, sondeada vía `hsc-agent-cli`". Su capa macro es correcta (ver SÓLIDO). Pero su **capa de detalle de endpoints está mayormente inventada**: contra el código real de `hsc-agent-cli`, solo `autenticacion.php` y `cambiar_hospital.php` existen.

| Citado en Apéndice A | Existe | Endpoint real en el código |
|---|---|---|
| `obt_grilla.php` | NO | `listado_datos_camas_pacientes.php` |
| `mostrar_documento.php?gg=` | NO | `ingreso/ver_pdf.php?form=…&id=…` |
| `listado_medicamentos.php` | NO | `atencion/obtener_lista_indicaciones.php` |
| `buscar_resultados.php?rut=` | NO | `resultadoseleccion.php` |
| `detalle_examen.php` | NO | `detalleexamenes.php` |
| `historial_examenes.php?rut=` | NO | (no existe; histórico vía `resultadoseleccion.php`) |
| `ficha_clinica/?rut=` | NO | `obtener_visor_aps.php` → bridge → ESB `/VISOR_CL/ObtenerTokenSesion` |
| `autenticacion.php` | SÍ | `funciones/autenticacion.php` |
| `cambiar_hospital.php` | SÍ | `vistas/cambiar_hospital.php` |

Errores fácticos adicionales del Apéndice (no interpretación, hechos): **OSIRIS** se describe como "sistema de imagenología, `not_implemented_yet`" — falso: en este CLI es el subsistema de **documentos ambulatorios del SGH y está implementado** (`ambulatorias-osiris`). **Pabellón/Patología** no se marcan `not_implemented_yet`: se declinaron por vivir en sistemas **externos al proxy** (pabellón en `10.6.85.124:8085`). El campo del censo es **`dias_hospitalizacion`**, no `dias_estada`. **"ESI (Emergency Severity Index)"** es un rótulo agregado por el autor: el código usa `Categoria C1..C5` y nunca menciona "ESI".
**Patrón:** el autor capturó bien la estructura del ecosistema y luego rellenó nombres verosímiles sin abrir el código. Para un documento que irá a CENS, un solo endpoint inventado descubierto invalida la credibilidad de todo el Apéndice.

### C4 — El scoring no es reproducible y aparenta una objetividad que no tiene
Reproducción aritmética del Sello "Software en Salud":

- **Los pesos no suman 100%.** La tabla de subcaracterísticas suma **200%**; la tabla de características suma **185%**. Además **no concuerdan entre sí** (p. ej. "Adecuación funcional" pesa 35% en una tabla y 20% en la otra).
- **El titular "89%" no se reproduce.** Con promedio ponderado normalizado de la tabla de características da **90.4%**, no 89%.
- **El valor implícito de `◐` cambia según convenga.** Resolviendo qué puntaje numérico haría cuadrar cada característica (con `/`=100, `✗`=0): Seguridad implica `◐`≈74, Compatibilidad ≈80, Usabilidad ≈58, Fiabilidad ≈50; en RCE ≈57 y ≈62; en Telemedicina ≈75. **No hay constante.** Los puntajes por característica son asignaciones a ojo presentadas como si salieran de una fórmula.

Telemedicina (73% / 63%) sí se reproduce limpiamente con `◐`=75 — lo que confirma que *cuando* hay método, cuadra; el problema es que el Sello headline y el RCE no lo siguen.

---

## MAYORES

### M1 — El promedio enmascara seguridad reprobada (inversión de la jerarquía del proyecto)
`CLAUDE.md` ordena **"seguridad clínica > estética > conveniencia técnica"**. El scoring hace lo contrario:
- **RCE:** Seguridad **68%** (bajo el umbral inferido de 70%) se promedia con Usabilidad 81% → **"75% CUMPLE CON OBSERVACIONES"**. Una dimensión de seguridad reprobada se rescata con una de usabilidad aprobada.
- **Software en Salud:** Seguridad **71%** (la más baja, con firma electrónica `✗`) se diluye contra Mantenibilidad 100% y Portabilidad 100% → **89%**. Características de ingeniería no clínicas enmascaran el déficit de seguridad.
En un sello clínico, seguridad debe ser **gate**, no sumando. El método debería reportar "reprobado en seguridad" en vez de un promedio que aprueba.

### M2 — Notación contradictoria con la propia leyenda
La leyenda define `◐` = "cumple con observaciones". Pero Telemedicina 67% se etiqueta **`◐` y simultáneamente "NO APROBADO"** (líneas 131, 239). Si 67% está bajo el umbral inferido de 70%, el símbolo correcto es `✗`, no `◐`. El símbolo y el texto se contradicen.

### M3 — Métricas infladas o desactualizadas
| Métrica | Eval | Real (verificado) | Desvío |
|---|---|---|---|
| Usos de `aria-*` | **144+** | **86** | sobreestima ×1.67 |
| Tests web | **517** | 530 (`it()` estático) | desactualizado |
| "Tests totales" | **~595 (517+88)** | mezcla *casos* + *archivos*; handoff-desarrollo dice **878** | unidad incoherente |
| Índices en migraciones | **174+** | **173** | bajo el propio "+" |
| Componentes clínicos | **13** | spec define **12**; directorio tiene 16 (4 no clínicos) | no coincide con nada |
| Archivos por capa | 87/45/44/9/112 | 87/**46**/**47**/9/**113** | subcuenta 1-3 |

Ninguno cambia el veredicto, pero la acumulación de cifras "ligeramente más altas que la realidad" delata un sesgo sistemático al alza — precisamente lo que un auditor externo penaliza.

### M4 — B-PRACSIS: inconsistente entre documentos y mal fundamentado
- **Inconsistencia:** el handoff reporta **3.8/6** ("2.8→3.8 tras hallazgos de red"), pero el eval nunca recalcula y se queda en **2.8/6** en cuerpo y consolidado. Los dos documentos del mismo entregable se contradicen.
- **Método:** B-PRACSIS evalúa la **institución (HSC)**, pero todo el "hallazgo" se **infiere desde un repo de software externo**. La ausencia de evidencia en el repo se convierte en "Nivel 1 — Básica" (un valor de madurez), cuando lo correcto es **"no evaluable desde esta fuente"**. Esto es exactamente "ausente ≠ normal" invertido: ausencia tratada como dato. El propio doc admite que infiere; debería entonces declarar *no evaluable*, no asignar nivel.

### M5 — Diseño-no-implementado presentado como evidencia de cumplimiento
Verificado contra código: **no existe** consentimiento informado, **no existe** adaptador FHIR, **no existen** los puertos de interoperabilidad como tipos TypeScript (solo prosa en `.md`), **no existe** firma electrónica. El eval *a veces* lo reconoce (`✗`, `◐`) pero en varias celdas de evidencia cita el diseño documental como si sostuviera el criterio (p. ej. puertos "definidos", consentimiento "diseñado en modelo-datos"). La frontera diseño↔implementación debe ser explícita en cada celda; hoy se difumina a favor del score.

### M6 — ISO/IEC 25010 citada en versión 2011 (vigente 2023)
El eval evalúa contra "25010:2011" (8 características). La norma fue **revisada a ISO/IEC 25010:2023** (9 características: añade *Safety*, renombra Usabilidad→*Interaction capability* y Portabilidad→*Flexibility*). Atenuante: CENS usa "ISO 25010" sin declarar versión y de facto el modelo clásico. Conviene una nota; *Safety* es especialmente pertinente para software clínico y hoy queda fuera del marco usado.

---

## MENORES

- **m1 — Citas de línea desplazadas:** `flujos-criticos.md` F6 está en 156-178 (no 162-193); `auditoria-normativa` en 178 (no 176); `contrato-interoperabilidad` 42-56 es la tabla de decisiones, no el mapeo FHIR (que está en 77-96); `modelo-datos:133` no dice "UUID v7 PK" (eso está en ADR 0003); `db-client.ts:10-18` es Pool+wrapper Kysely, no solo Pool. Verosímiles pero verificables y erróneas.
- **m2 — Nombres de los 5 contextos de `IdentityVerification` erróneos:** el eval dice "visita, medicación, cierre, escalamiento, teleatención"; el código define `visita | tele | prescripcion | acceso-delegado | irreversible`. El conteo (5) es correcto; los nombres no. Y la subcaracterística U3 dice "2 de 5 contextos" mientras 4.4 dice "5 contextos" sin reconciliar diseño↔uso.
- **m3 — "7 superficies diseñadas con IFML textual":** solo existen **4** archivos `superficie-*.md`; las 7 ViewContainers viven consolidadas en `ifml-hodom.md`. Sobreconteo de archivos.
- **m4 — "4 sellos CENS":** CENS ofrece **6 certificaciones/programas**. B-PRACSIS, contado como "4º sello", no es un sello de software sino herramienta de madurez institucional (el cuerpo lo aclara; el encabezado de alcance induce a error).
- **m5 — Costo "322 UF + IVA":** no verificable como cifra cerrada. Tarifas públicas: Telemedicina 99 UF, B-PRACSIS (informe) 25 UF, Software 89-99 UF (discrepan fuentes), **RCE sin precio público**. Presentar como estimación con desglose y fuentes, no como total oficial.
- **m6 — "Clave Única como alternativa a MPI":** confusión conceptual. Clave Única es autenticación de acceso ciudadano; el MPI (NID, PIXm/PDQm) resuelve identidad/matching clínico. Resuelven problemas distintos; no son alternativas.
- **m7 — Caché en `~/.cache` "en texto plano sin cifrar":** cierto que no cifra, pero el CLI aplica permisos `0600`/`0700` + TTL por tipo. El Apéndice presenta media verdad como déficit total.

---

## SÓLIDO / BIEN VERIFICADO (no todo es crítica)

**Arquitectura macro de red (Apéndice A) — verificada contra `hsc-agent-cli`:**
- Proxy `100.77.30.26` (config default), exacto.
- `H_SGH_HOSPITAL_ID` 1=Herminda Martin / 2=San Carlos + `cambiar_hospital.php`, exacto.
- ESB `esb.saludenred.cl` con los **5 puertos exactos** {8201,8095,8096,8097,8099}.
- `servicio_id=72` HODOM + salas 286/287/288 (+635 default), exacto.
- Auth PHPSESSID + form `usuario`/`contrasena`; HCC sin credenciales propias vía bridge DAU+SGH→ESB.
- `evolucion_id=0` / `censo_pointer_invalid` como dato sucio real del censo — bien caracterizado.
- `smoke-hodom.sh` + `find --hospitalizados --hodom` existen y hacen lo descrito.

**Normativa dura — confirmada como real (varias parecían inventadas y no lo son):**
- **Fonasa obligatorio en el Sello Telemedicina** — confirmado en la página oficial. Acierto fuerte.
- **DS 876/2025** modifica el DS 12/2023 — ambos existen (BCN). La fecha "futura" resultó genuina.
- **Eric Rojas (erojas@cens.cl)** y contacto@cens.cl — datos públicos reales, no inventados.
- Leyes **20.584 / 21.541 / 21.719 / 21.663** — numeración y materia correctas en las cuatro.
- **Res. ANCI N°7/2025** (taxonomía de incidentes) — existe.
- **Core CL v1.9.4, SNRE v0.9.6, EIS v0.1.0** — versiones exactas verificadas (hl7chile / interoperabilidad.minsal.cl).
- **ISO 13131:2021** — título y año exactos.
- **B-PRACSIS** — escala /6, niveles y 6 dimensiones coinciden con la fuente oficial.
- Estructura del **Sello RCE en 2 ejes** (Seguridad + Usabilidad) — correcta.

**Hechos del repo — verdaderos:** 16 ADRs (0001-0016), 68 migraciones SQL, `tsconfig` strict + noUncheckedIndexedAccess + exactOptionalPropertyTypes, `argon2` en package.json, `hd_session` httpOnly, `audit_event` INSERT-only ("NUNCA UPDATE/DELETE"), 87 archivos de dominio, `vite-plugin-pwa`, `mobile-clinical-shell.tsx` con safe-area-inset.

**Honestidad metodológica:** declara explícitamente que los umbrales (≥70/≥75%) son inferidos y que CENS no los publica — correcto y bien señalado.

---

## Recomendaciones de corrección (orden de prioridad antes de cualquier contacto con CENS)

1. **Corregir C1 (NT 9/NT 10):** reasignar materias (NT 9 = Autenticación; NT 10 = Documentos/Expedientes) y rehacer el sustento normativo de la firma electrónica (su base correcta es la Ley 19.799, no NT 10). Es el error más dañino y el más fácil de arreglar.
2. **Eliminar C2 (escala 1-5 inventada):** describir la Asesoría como los 4 servicios reales de CENS; quitar "Nivel 2/5".
3. **Sanear C3 (Apéndice A):** reemplazar los 7 endpoints fabricados por los reales del código, corregir OSIRIS/pabellón/patología/`dias_hospitalizacion`, y marcar "ESI" como interpretación. Re-derivar todo el Apéndice directamente del código de `hsc-agent-cli`, no de memoria.
4. **Rehacer C4/M1/M2 (scoring):** normalizar pesos a 100%, publicar la fórmula y un valor fijo de `◐`, tratar **Seguridad como gate** (no promediable), y reconciliar símbolo↔texto. Si el método no es reproducible, es preferible un veredicto cualitativo honesto a un porcentaje falsamente preciso.
5. **Reconciliar M4 (B-PRACSIS):** un solo número entre handoff y eval; y reetiquetar como "no evaluable desde el repo" lo que hoy figura como "Nivel 1 — Básica".
6. **Trazar M5 (diseño vs implementación):** en cada celda, separar "diseñado en `.md`" de "implementado en código" (verificado: consentimiento, FHIR, puertos, firma = solo diseño).
7. **Refrescar M3 (métricas):** recontar todo automáticamente al cierre (aria=86, tests=530 web, índices=173, componentes=12) y elegir **una** definición de "total de tests".
8. **Nota M6:** declarar versión ISO 25010 usada y advertir que 2023 añade *Safety*.

**Conclusión:** el documento es un buen *borrador de trabajo interno* y una base de cobertura amplia, pero **no debe enviarse a CENS en su estado actual**. Su fortaleza (estructura + normativa dura real) queda anulada por relleno verificable como falso (endpoints, escalas, métricas). La corrección es acotada: la mayoría de los hallazgos críticos se arreglan editando, no re-investigando.
