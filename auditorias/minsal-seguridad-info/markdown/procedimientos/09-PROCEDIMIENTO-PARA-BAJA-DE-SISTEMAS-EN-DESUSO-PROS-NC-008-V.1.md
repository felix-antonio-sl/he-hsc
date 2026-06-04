<!-- pág. 1 -->

¿0h
Mindstorio de
¿RO DES
e
a
a
CI
ENCARGADO
Versión oficial
v1.0
a
os
cons ¡2 DE SEGURIDAD c
Fecha de laversión:
15.01.2024
2000
i
JS
DEIA,
Y
Elaborado por:
Pablo Fabres /Jose Villa C.
| Firma:
>AD
Jose Villa C.
Firma:
Ñ
(MN
Catalina Arenas A. /Rodrigo Baeza
Firma: (Vis
Carlos Maldonado P./ Any Castillo
Firma:
Fica
Aprobado por:
Jorge Herrera R./Rodrigo ZamoranoAE

<!-- pág. 2 -->

mm
ina
2 de
da
SALUD
Contenido
PROPÓSITO qeria
md
TERMINOLOG lAoiniinnaa rc
ANA AN RANA
SSA

<!-- pág. 3 -->

ns
Ñ
1D: PROS-NC-008
Versión:
o
### 1. PROPOSITO
El presente procedimiento tiene como propósito atender los requerimientos de retiro o baja de los sistemas publicados a internet, por cese de prestación de su servicio o su no uso en ningún servidor o equipos informáticos del Ministerio de Salud (Minsal). La baja se llevará a cabo con el objeto de garantizar la seguridad de la información, cumplir con los estándares de la organización y mitigar cualquier riesgo potencial asociado con este tipo de activos.
### 2. ALCANCE
Se aplica a todos los sistemas publicados a internet que se encuentran bajo la propiedad y/o gestión de Minsal, Subsecretarias de Salud Pública y de Redes Asistenciales. Abarca los siguientes controles definidos en la norma NCh-ISO 27001.0f2022:
A.8.1.3 Uso aceptable de los activos.
A.12.1.2 Gestión de cambios.
A.12.3.1 Respaldo de la información.
A.18.1.2 Derechos de propiedad intelectual.
### 3. TERMINOLOGÍA
Sistema: Para efectos del presente procedimiento entiéndase como sistema, los activos de información que se encuentran bajo el alcance, el cual incluye los siguientes conceptos (desarrollados en cualquier tecnología):
e
Página, Sistema o Portal web.
e
Aplicativo.
e
Software.
e
Servicios Web (categorías SOAP y RESTu otra).
e
Tokenso Certificados de seguridad (SSL).
e
API (Interfaz de Programación de Aplicaciones).
e
Servicio Informático.
Baja de Sistema: Corresponde al proceso de retirar un sistema de operación activa y poner fin a su funcionalidad. Esto implica su desactivación, la interrupción de los servicios asociados y la eliminación de los datos almacenados en él. Para dar de baja el sistema se deben realizar diversas actividades con el objeto de proteger la seguridad de la información o garantizar el buen uso de los recursos involucrados.
4 DOCUMENTOS APLICABLES.
Dentro de la normativa, marcos de trabajo y documentos relacionados, y que son aplicables al presente procedimiento, se asocian los siguientes:
Nch-ISO 27001.0f2022, Sobre los requisitos de la seguridad de la información.
Decreto 1 del año 2015, del Ministerio de la Secretaría General de la Presidencia, que aprueba la norma técnica sobre sistemas y sistemas web de los órganos de la administración del estado.
Decreto 83 del año 2004, del Ministerio de la Secretaría General de la Presidencia, que aprueba la norma técnica para los órganos de la administración del estado sobre la seguridad y confidencialidad de los documentos electrónicos.
Decreto 7 del año 2023, del Ministerio de la Secretaría General de la Presidencia, que establece la norma técnica de seguridad de la información y ciberseguridad.

<!-- pág. 4 -->

5 ROLES Y RESPONSABILIDADES.
e
Nivel Directivo: responsable de generar las condiciones adecuadas para la ejecución y comunicación de presente procedimiento.
e.
Encargado de Seguridad de la Información / Encargado de Ciberseguridad: Velar por la aplicación del presente procedimiento y brindar asesoramiento en la identificación de las amenazas que puedan afectar a los sistemas, producto de la obsolescencia tecnológica, S.O.
no soportados por el fabricante o vulnerabilidades reportadas por la comunidad de investigadores de seguridad y los factores de riesgo a considerar en la evaluación de estas.
Informar al Comité de Seguridad de la Información sobre sistemas en desuso o revocaciones de sistemas que se tramiten.
e
Dueños de los sistemas: Deben dar aplicación al presente procedimiento y solicitar, oportunamente, cuando se requiera dar de baja un sistema.
e
Departamento de Tecnologías de Información y Comunicaciones: Debe establecer el control sobre los dominios de los sistemas Ministeriales y reglas para garantizar la seguridad y privacidad de la información. Así como la baja de los sistemas, siendo el responsable de su custodia, administración, desinstalación y control de los sistemas, pudiendo disponer la baja de un sistema si verifica que ya no se encuentra en uso.
e
Unidad
de
Operaciones:
Debe
gestionar
las
actividades
técnicas
que
permitan
la
desactivación y decomiso del sistema de manera controlada y segura. Asimismo, será responsable de la extracción, custodia y eventual migración de datos a los nuevos sistemas que se dispongan para los procesos a los que dichos datos correspondan. Adicionalmente, será de su cargo la eliminación segura de los datos, cuando corresponda, de acuerdo con las políticas de retención.
6 PROCEDIMIENTO.
6.1.- CONDICIONES GENERALES.
e
Todo proceso asociado a la baja de un sistema debe quedar documentado, incluyendo al menos la siguiente información:
o
Información del sistema: (Nombre del sistema, número en inventario de activos, fecha de registro, procesos en que se utiliza)
o
Dueño del sistema: Unidad responsable e identidad de la persona que solicita la baja.
o
Decisión de baja: Fundamentos de la decisión de dar de baja del sistema, Fecha de la decisión de baja, fecha prevista para la desactivación.
o
Enrelación con los datos o información: Datos que deberá custodiarse, periodo de retención y destino final de la información (respaldo, migración o eliminación), responsable del proceso de extracción y custodia de datos.
e
Elorigen de baja de sistemas en desuso, puede generarse por monitoreo de no uso por el Departamento de Tecnologías de Información y Comunicaciones o por solicitud directa de los dueños de los activos de información, por estimarse que ya no resultan necesarios para el o los procesos en los cuales se utilizaban.* El sistema que se solicita dar de baja debe estar registrado en el inventario de sistemas existente en Departamento de Tecnologías de Información y Comunicaciones.
l Tratándose de software no autorizado véase lo previsto en el Procedimiento de Pantalla y Escritorio Limpio, punto 6.3, Restricciones sobre el uso de equiposy la instalación de software.

<!-- pág. 5 -->

6.2.- CRITERIOS PARA LA DETERMINACIÓN DE BAJA DE UN SISTEMA.
e
Inactividad Prolongada: Si un sistema ha estado inactivo por más de un trimestre sin una justificación válida, se evaluará su baja para evitar riesgos de seguridad asociados con la falta de mantenimiento y actualización. En el análisis de la decisión de baja se deben verificar las siguientes condiciones:
Que el sistema lleve al menos un trimestre sin utilizarse.
ii.
No existe interoperabilidad o dependencia del sistema con otros sistemas o plataformas. En caso de que exista alguna dependencia o cualquier forma de interoperabilidad, se deben desarrollar las actividades de desacople de los otros aplicativos o plataformas.
iii.
El sistema debe ser dado de baja en todos los ambientes tecnológicos en que se encuentre.
iv.
Si el sistema prestaba algún servicio o trámite a usuarios internos o externos por medio del portal WEB, el dueño del activo será responsable de informar con la debida anticipación a los usuarios, por los medios de comunicación institucionales, tanto la baja del sistema como los motivos y el reemplazo del servicio o tramite.
e
Violación de Seguridad: Se bajará un sistema inmediatamente si se detecta una violación de seguridad que ponga en riesgo la confidencialidad, integridad o disponibilidad de la información.
e
Cambio en la Estrategia Institucional: Si hay un cambio en la estrategia institucional que justifique la eliminación de un sistema, se procederá a su revocación de acuerdo con la planificación establecida.
e.
Incumplimiento de Políticas y Normativas: Cualquier sistema que incumpla las políticas internas de la organización o las normativas legales será sujeto a revocación después de una revisión exhaustiva.
e
Término de periodo de vigencia: Tratándose de sistemas que se implementen para el apoyo de procesos temporales o transitorios, tales como campañas estacionales, otras bajo demanda temporal o de emergencia una vez finalizado su periodo de vigencia se dará de baja el sistema.
6.3.- OTROS CRITERIOS TÉCNICOS PARA DETERMINAR LA BAJA DE UN SISTEMA:
e
Obsolescencia tecnológica: Cuando un software fue adquirido o desarrollado, y es reemplazado totalmente por una nueva versión; cuando el software deja de soportar los procesos de negocio de la institución o cuando el sistema es difícil de integrar con las nuevas soluciones introducidas como parte de las estrategias de transformación digital de gobierno.
e
Reemplazo o
consolidación:
El
sistema
es
remplazado
por
una
nueva
aplicación
(Reemplazo) o los módulos de otra aplicación, pueden cubrir totalmente su funcionalidad (Consolidación).
e
Incompatibilidad con el hardware: Las nuevas versiones de equipos pueden presentar problemas o incompatibilidad con software obsoleto, lo que genera la posibilidad de fallas, la suspensión del soporte y garantía de los dispositivos existentes.
e
Lentitud en la ejecución de los procesos de información: El uso de software obsoleto no asegura el mejor desempeño y no satisface las necesidades del usuario funcional aumentando la carga laboral o generando altos tiempos muertos en los procesos ejecutados sobre el sistema.
e
Alta vulnerabilidad y falta de actualizaciones: Entre más antigua es una versión de software, más vulnerabilidades se presentan. Por lo general cuando se descubren estas

<!-- pág. 6 -->

E
is
SALUD
vulnerabilidades, son parchadas por el fabricante para evitar riesgos, estos parches son liberados con las actualizaciones, utilizar una versión de software obsoleto limita el acceso a estas. Por otro lado, si la aplicación se ejecuta en sistemas operativos obsoletos o no soportados por el fabricante, significa que esta es mucho más vulnerable a amenazas de seguridad aumentando la superficie de riesgo relacionada principalmente con la integridad, confidencialidad y disponibilidad de la información.
e.
Perdida de soporte: Los fabricantes terminan el mantenimiento técnico y generación de parches de seguridad para aplicativos y versiones antiguas, convirtiendo al software en un riesgo para la entidad y su información.
6.4.- PROCESO DE BAJA DE SISTEMA.
a.
Solicitud de baja de sistema en desuso:
El dueño del sistema debe solicitar directamente la solicitud de baja del activo, indicando la causal que lo motiva.
La solicitud se formula por requerimiento a la mesa de ayuda por correo institucional, que escalará a la coordinación del
Departamento
de
Tecnologías
de
Información
y
Comunicaciones que corresponda.
b.
Verificación para dar de baja el sistema:
La
Unidad
de
Operaciones
debe
realizar
actividades de
verificación
que
permitan
determinar el estado operativo del sistema y su infraestructura asociada, para asegurarse de que no haya problemas técnicos o riesgos de seguridad pendientes, revisión de los motivos documentados y comparar con los criterios técnicos establecidos en el presente procedimiento, antes del retiro definitivo del sistema. Esta unidad elaborará un informe y mantendrá registros de los resultados de la evaluación y cualquier acción tomada en consecuencia.
Adicionalmente, llevará a cabo una revisión interna para confirmar la validez de la decisión y abordar posibles implicaciones. Los resultados del análisis serán informados a él o la directora/a de Departamento de Tecnologías de la información y a él o la Encargado/a de Seguridad de la Información.
c.
Notificación y Revisión:
El o la directora/a de Departamento de Tecnologías de la información, en conjunto con él o la encargado/a de seguridad de la información, notificará al dueño del activo sobre la decisión de aceptación o rechazo de la baja y los pasos a seguir d.
Comunicación Externa:
El dueño del activo informará a los usuarios u otras partes interesadas sobre la baja del sistema de manera previa, transparente y clara.
e.
Decomiso del sistema:
El acceso al sistema se desactivará de manera controlada y segura. Para lo cual, las áreas tecnológicas pertinentes deben ajustarse al procedimiento de Gestión de Cambios en Ambientes productivos (CAB) para aprobación de la baja de aplicativo o software.
i.
Copias de Seguridad:
Como primera actividad, se realizarán copias de seguridad completas de todos los datos críticos y configuraciones del sistema.
Las copias de seguridad se almacenarán de manera segura en un entorno controlado, y se documentará la ubicación, fecha y contenido de cada respaldo.

<!-- pág. 7 -->

dm
Ñ
Versión:
ágina
de
mn
SALUD
Paga + ue
li.
Identificación de Recursos Sensibles:
Se identificarán y catalogarán todos los recursos sensibles almacenados en el sistema, como datos de usuarios, información confidencial o propietaria.
Se asignarán responsabilidades claras para la gestión y protección de estos recursos durante el proceso de desactivación.
ñii.
Respaldo y retención de la información contenida en el sistema:
Se realizará un respaldo de los datos críticos antes de la baja, asegurándose de la funcionalidad del respaldo, de su almacenamiento de manera segura y de su eliminación en el sistema que se dará de baja de acuerdo con las políticas de retención.
Los datos respaldados se retendrán de acuerdo con las políticas de retención de datos establecidas por la organización.
Se documentará claramente la política de retención y se garantizará la eliminación segura de los respaldos cuando ya no sean necesarios.
iv.
Desactivación Controlada:
Antes de proceder con la desactivación, se coordinará con la Unidad de Operaciones de TI, Explotación e Infraestructura, la Unidad de Proyectos y la Unidad de Seguridad de la Información, a través de un CAB para garantizar que la desactivación del sistema web se realice de manera controlada y planificada.
Se elaborará un plan de desactivación que incluya los pasos específicos a seguir para garantizar la continuidad operativa y minimizar cualquier impacto negativo.
v.
Desconexión de Accesos Externos:
Se desconectarán los accesos externos al sistema, como dominios, enlaces y servicios de red relacionados.
Se implementarán medidas de seguridad adicionales, como cortafuegos y restricciones de acceso, para prevenir cualquier intento no autorizado de acceder al sistema después de la desactivación.
vi.
Desactivación de Servicios Relacionados:
Se desactivarán o retirarán todos los servicios relacionados con el sistema, como bases de datos, servidores de aplicaciones y servicios de alojamiento.
Se garantizará que cualquier conexión o integración con otros sistemas sea gestionada adecuadamente para evitar interrupciones no planificadas.
vii.
Eliminación de Contenido Sensible:
Se eliminará o protegerá de manera adecuada cualquier contenido sensible o crítico almacenado en el sistema web antes de la desactivación.
Se seguirán
los procedimientos de eliminación segura de datos para garantizar la confidencialidad y cumplir con las políticas de privacidad.
viii.
Verificación de la Desactivación:
Después de la desactivación, se llevará a cabo una verificación exhaustiva para asegurarse de que todos los recursos relacionados con el sistema web se hayan desconectado y desactivado correctamente.
Se realizarán pruebas de seguridad para garantizar que no haya brechas o riesgos de seguridad residuales.
ix.
Sacar del inventario de activos:
Marcar como inactivo el sistema en el inventario de aplicaciones o del inventario de activos.

<!-- pág. 8 -->

dm
"ml
mi
SALUD
6.5.- SOBRE LA CREACIÓN, ELIMINACIÓN DE NOMBRES DE DOMINIO.
a.
Creación de Dominios.
Todo sistema debe cumplir con la obligación de realizar la inscripción del registro vinculado a dominios de gobierno, esto con objeto de evitar malas prácticas, tales como, usurpaciones de identidad, mal uso, abuso de prestigio y marca, y toda aquella acción que corresponda a actividades no pertenecientes al Minsal.
Cumpliendo con lo siguiente:
De acuerdo con los requisitos establecidos en artículo 13 del Decreto Supremo N*1 de la SEGPRES. Todo sitio de gobierno debe hacer uso del dominio “gob.cl”, registrándose previamente ante la División de Informática del Ministerio del Interior de Seguridad Pública, y a través del formulario electrónico https://nic.gob.cl/inscripcion.
hp.
Ogestionar la incorporación del sistema en dominio “minsal.cl” a través del Departamento de Tecnologías de Información y Comunicaciones.
Por lo tanto, la regla general es que no se debe registrar un nombre de dominio para fines institucionales en el sistema de registro de nombres de dominio administrado por Nic Chile.
En el caso de que se registre un nombre de dominio en este sistema, será de responsabilidad de la jefatura de la unidad correspondiente la custodia y mantención del nombre de dominio.
b.
Eliminación de Dominios.
Tratándose de la eliminación de aquellos sistemas Ministeriales inscritos bajo dominio “.cl”, por decisión de la autoridad, término de la estrategia, o por no haberse renovado el dominio en nic.cl, se deberá formalizar dicha decisión por parte del dueño del activo e informar al Departamento T!l y tramitar eliminación en NIC Chile.
El titular que inscribió el dominio deberá requerir a NIC Chile la eliminación del dominio o en su defecto si no lo hiciere en el plazo de 5 días corridos contados desde fecha de expiración, NIC Chile desactivará el dominio.
Es de responsabilidad del dueño del activo anunciar la baja, los motivos y el reemplazo del servicio, si lo hubiera, por los medios de comunicación institucionales.
Si producto de la eliminación del dominio “.cl”, un tercero lo registrará y el dueño de ese activo de información estimara que se ven afectados los derechos de MINSALo la fe pública, deberá hacerse cargo de solicitar a la autoridad que se intente la revocación temprana o tardía del nombre de dominio, según sea el caso lo cual se sujetaráa la Política de Resolución de Controversias por Nombres de dominio “.cl”.
Para iniciar este procedimiento de revocación de un dominio inscrito, será necesario que el dueño del activo lo solicite a NIC Chile por los medios que la entidad dispone, y pague la tarifa respectiva, de acuerdo lo establece su reglamento.2 Para la eliminación de sistemas con nombres de dominio minsal.cl o en gob.cl, gov.cl, se procederá de acuerdo con el punto 6.4e incluir la eliminación del registro DNS asociado con el nombre de dominio que se eliminará. Verificar que se hayan eliminado correctamente todos los registros DNS y que los nombres de dominio ya no estén activos en la infraestructura de DNS.
REGISTROS.
Catastro de Sistemas del Minsal.
Registros de sistemas en decomiso.
2 https://nic.cl/normativa/reglamentacion funcionamiento_registro.cl.pdf

<!-- pág. 9 -->

a
Versión:
el
Catastro de dominios inscritos en NIC Chile.
DIFUSION.
La comunicación del presente documento se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en sitio web Minsal http://www.minsal.cl/seguridad_de la _informacion/ Publicación en la intranet de Minsal http://isalud.minsal.cl/
REVISION.
La revisión del contenido de este documento se efectuará a lo menos cada un año por el Comité de Seguridad de la Información, o atendiendo necesidades de cambios para garantizar versionamientos respectivos recomendables.
10CONTROL DE VERSIONES.
alar
RA ERE
tU
A
15.01.2024
Pablo Fabres/Jose
Todo eldocumento
Creación del documento