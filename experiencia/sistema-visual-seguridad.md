# Sistema visual y seguridad por diseño

Estado: canon operativo

## Color

Color comunica información clínica, no decoración.

Los tokens y assets canónicos viven en
`03-experiencia/assets/manifest-ui.md`. Cualquier implementación visible debe
consumir esos assets o declarar una actualización explícita del manifest.

### Severidad Clínica

| Token | Uso |
|---|---|
| `--clinical-critico` | alergia, alerta crítica, voluntad anticipada crítica, fallecimiento, dosis bloqueante |
| `--clinical-atencion` | caída, dolor, úlcera, dispositivo vencido, estadía prolongada, signo vital ámbar |
| `--clinical-normal` | signo vital en rango, plan al día, paciente estable |
| `--clinical-info` | riesgo social, historial relevante, conocimiento contextual |

Reglas:

- solo estos cuatro tokens comunican severidad;
- rojo nunca es decorativo;
- verde nunca es decorativo;
- gradientes prohibidos en superficies clínicas;
- no depender solo de color.

## Tipografía

Reglas:

- escala `rem`;
- números tabulares en signos vitales, dosis, fechas, RUT y teléfonos;
- A/A+/A++ disponible también para staff;
- cursiva prohibida salvo razón terminológica real;
- texto clínico con line-height suficiente para lectura bajo estrés.

## Densidad

| Contexto | Densidad |
|---|---|
| Coordinación desktop | tabular alta |
| Paciente desktop | cards medianas |
| Paciente mobile | cards grandes |
| Visita mobile | controles táctiles amplios, narrativa primero |
| Tele | controles grandes y calidad de conexión visible |

## Mobile Clínico

Las superficies mobile son dispositivos de terreno, no maquetas de marketing.

Reglas:

- reservar safe area superior e inferior;
- notch/status bar nunca pisa título, identidad, paso ni acción primaria;
- home indicator nunca tapa `Firmar`, `Enviar`, `Escalar` o texto clínico;
- la acción primaria puede quedar fija abajo sólo si el contenido mantiene
  padding inferior suficiente;
- todo control principal mide al menos 44px de alto;
- no hay scroll horizontal;
- `PatientBand` compacto muestra identidad, día de episodio y banderas críticas.

## Movimiento

Animación decorativa prohibida en superficies clínicas.

Motion permitido solo si comunica:

- estado;
- foco;
- speaking indicator;
- carga;
- éxito;
- error;
- cambio crítico.

## Accesibilidad

Piso: WCAG 2.2 AA.

Requisitos mínimos:

- contraste texto normal >= 4.5:1;
- contraste UI/iconos >= 3:1;
- foco visible;
- labels persistentes;
- target táctil mínimo 24px, preferir 44px en mobile clínico;
- mensajes de error accionables;
- orden de tab lógico;
- soporte de reducción de movimiento.

## Seguridad Visible

La UI debe hacer visibles:

- paciente correcto;
- episodio correcto;
- finalidad de acceso cuando la acción lo requiera;
- estado offline/sync;
- rol y permisos activos;
- borradores no enviados;
- firma o ausencia de firma;
- auditoría de acceso;
- razones de botones deshabilitados;
- consecuencias de acciones irreversibles.

Regla: una acción clínica deshabilitada sin explicación visible es un defecto de
seguridad. Debe existir una causa y una salida: corregir, completar, cancelar,
escalar o solicitar override documentado.

## Estados Que No Son Alertas

No se usa `ClinicalAlert` para comunicar:

- ausencia de alertas;
- operación exitosa;
- estado clínico estable;
- plan al día;
- sincronización normal.

Esos estados usan `ClinicalStateNotice`, texto inline o resumen de estado. Las
alertas se reservan para riesgos o interrupciones con salida clínica u
operacional.

## Acciones Irreversibles

Requieren `ConfirmIrreversible`:

- alta clínica;
- cierre por fallecimiento;
- eliminación de registro firmado;
- contrarreferencia definitiva;
- cancelación irreversible de decisión clínica.

La confirmación debe ser proporcional: re-tipeo de RUT, verbo explícito, razón y
auditoría.

## Prevención De Paciente Equivocado

Antes de visita, teleatención o acción crítica:

- mostrar foto si existe;
- mostrar nombre/RUT/edad;
- confirmar cuidador cuando participe;
- registrar resultado;
- bloquear continuidad si falla identidad.

## Offline

El estado offline no puede ser sorpresa.

Reglas:

- autosave local en formularios críticos;
- cola de envío visible;
- conflicto de sincronización resoluble;
- borrador recuperado con decisión explícita: enviar, editar o descartar.

## Guía Institucional Y Automatización

La guía just-in-time se permite sólo si reduce carga cognitiva en el punto de
decisión.

Reglas:

- mostrar fuente, versión, vigencia y razón de aparición;
- permitir ver detalle sin abandonar el flujo clínico;
- permitir descartar o no mostrar en ese contexto;
- si usa AI, marcar el resultado como sugerido, revisable y descartable;
- ninguna automatización ejecuta, firma, cierra ni prescribe por el usuario.

## Información Sensible En Pantalla

Reglas:

- mostrar sólo los datos necesarios para la tarea actual;
- no revelar ficha completa en superficies agregadas;
- no exponer domicilio, teléfono o RUN si basta identificador parcial;
- ocultar por defecto secretos, tokens, identificadores técnicos y trazas;
- avisar cuando una acción será auditada o visible para revisión posterior;
- `break-glass` requiere razón visible y revisión posterior, no es un botón de
  conveniencia.

## Lo Que No Entra Al Canon Visual

- landing pages;
- heroes de marketing;
- gradientes en data clínica;
- orbes o decoración atmosférica;
- cards estéticas sin tarea;
- replicar navegación histórica de `hdos-app` por memoria muscular.

## Assets UI

El sistema visual se materializa inicialmente en:

- `assets/tokens/hd-hsc-os.tokens.json`;
- `assets/tokens/hd-hsc-os.tokens.css`;
- `assets/tokens/hd-hsc-os.tailwind-preset.cjs`;
- `assets/svg/hd-hsc-os-mark.svg`;
- `assets/svg/hd-hsc-os-lockup.svg`;
- `assets/svg/clinical-severity-dots.svg`;
- `assets/svg/surfaces-map.svg`.

Reglas:

- `tokens.json` es la fuente semántica;
- `tokens.css` es consumible por prototipos e implementación web;
- el preset Tailwind es referencia opcional, no decisión tecnológica;
- los SVG de marca no comunican severidad clínica;
- un asset nuevo exige propósito, uso permitido y restricción clínica en el
  manifest.
