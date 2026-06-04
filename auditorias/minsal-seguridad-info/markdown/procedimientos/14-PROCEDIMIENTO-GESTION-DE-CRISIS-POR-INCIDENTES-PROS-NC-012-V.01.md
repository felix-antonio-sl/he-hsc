<!-- pág. 1 -->

MO
VINISTERIODE SALUD
PROS-NC- PROS-NC-012
PROCEDIMIENTO GESTIÓN DE CRISIS POR
INCIDENTES DE SEGURIDAD
E Á _—
Ñ_c—R— e
Sistema de Gestión de Seguridad de la Información — Nivel Central ¡xEE _ _—_— __ —_ Versión Oficial Actual vO1 — Agosto 2021 a
Rodrigo
Vidal
Unidad
de
Ñ
Elaborado
Seguridad TIC
Agosto 2021
a
Ricardo Pardo / Andrés Muñoz
NAO!
Y)
Revisado
l
Agosto 2021
### 4. LL ESA
YSL
a
Unidad Operaciones
TIC
ZA41 4
ON
José
Villa
Encargado
ST
y
VÍ
Ciberseguridad
A GOUAA
Gino Paolo Peirano Alvarado
A ESDEN
i
Aprobado |efe Departamento Tecnologías Agosto 2021 ¡SA
A
eos
- |de
la
Información
y
£: $ bar AENTO DE E
E
Comunicaciones
A: Ol
A
Lo Aroración y
ez, COMUNICACIONES )

<!-- pág. 2 -->

o . O
CONTENIDO
PROPÓSITOcicoccococonicoooonocoroononaonoronrnoncorcononnononnn conocooronnnono nnonconnnoa nana ntornonconotocancniana 3
TERMINOLOGÍA... ciocococcicccociocioccocoorocrnconocconorononcnnconconononroncnncnnoncoinnrno rociar cancion
DOCUMENTOS APLICABLES...oocococconcncononocccocnoncononoccnonoconono ononooo nono non nronononoronn conca cancarcnnanc GESTIÓN DE INCIDENTES CRÍTICOScocciondd
6.3.
COMITÉ DE CRISIS cooocicciiccionninnocccononononinnoncononccnono conocio canina
PREPARACIÓNcooocococconaninniconocororooncnnorcnoncnnoconacionocnon conocen rana cocnocanonanincaacas Y
6.4.1
Instalaciones y comunicación para la gestión de incidentes.....oooooconnnocnonnconnono..9
6.4.2
Hardware y software para la gestión de incidentes......ooonoconocconioonicnnconnococncocananannnnnoTO
6.4.3
Recursos para el análiSiS......ooooooccnnncnncnnnnnnninnnoncacicncnonononcon nono naornro nrnnnnar cnn ronca 11
6.4.4
Software para Mitigación ...ooooooconononioncmonoocorenoannononn rocio nconcancnn cnn conano nc nonrocnonranronn cancnnnn 11
IDENTIFICACIÓN4
AS A
6.7.
PLANDE COMUNICACIÓN.cooncinccnconornnconicconorininocicconnonnonnononoonononronnnnnononconcnoconcnn conoci ccacc
A AAA
A E
A SO
REVISION Y MEDICION..ooooccocccocccccccoconccconcccccononononnnonncnn cornconrcnnnnnc corno ronccorcanoa EXCEPCIONES AL CUMPLIMIENTO DEL PROCEDIMIENTO cocoa ooo. 14
CONTROL DE VERSIONEScoocococcoococcccccconcoonconococononnonnconronoroncancnconn noncnrronr conanconocancan can 14 ANEXO: CHECKLIST GESTIÓN DE INCIDENCIAS ..0occocicoccococnococinoncocnoninincononcononnann 15 ANEXO: Orientaciones sobre nivelesy criterio de evaluación y clasificación de crisis... 18

<!-- pág. 3 -->

MU"
ONINISTERIODE SALUD
PROPÓSITO
Establecer las actividades necesarias en la Subsecretarías de Salud Pública y Redes Asistenciales, para el tratamiento de incidencias mayores que requieran de un Comité de Crisis para su gestión.
ALCANCE
Este procedimiento aborda la gestión de incidentes mayores y requieran la activación de
Comités de Crisis,
y que afecten a los activos de información del tipo: base de datos, documento, equipo, expediente, formulario, infraestructura física, persona, sistema de información, software, en cuantoa la;
Confidencialidad: acceso no autorizado a la información, Integridad: Modificación no autorizada, destrucción o pérdida de información Disponibilidad: Inaccesibilidad a la información.
Este procedimiento es aplicable a todos los funcionarios: (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para las Subsecretarías de Salud Pública y de Redes Asistenciales y que tengan derechos de accesoa la información que puedan afectar los activos de información del Ministerio de Salud.
Este procedimiento abarca los siguientes controles definidos en la norma NCh-ISO
27001.0f2013:
Alcance de Dominios y Controles de Seguridad de la Información (Nch-1SO 27001:2013)
Nombre del | 1D Control!
o o
ISO 27001
Nombre del Control
a
Organización | A.06.01.03 | Contacto con autoridades de la und de A.06.01.04 | Contacto con grupos especiales de interés información A.16.01.01 | Responsabilidades y procedimientos A.16.01.02 | Informe de eventos de seguridad de la información A.16.01.03 | Informe de las debilidades de seguridad de la información
Gestión de
Evaluación y decisión sobre los eventos de seguridad de la
A.16.01.04
Incidentes
información
A.16.01.05 | Respuesta ante incidentes de seguridad de la información A.16.01.06 | Aprendizaje de los incidentes de seguridad de la información A.16.01.07 | Recolección de evidencia
1 A lo largo del procedimiento cada vez que se mencione funcionario se refiere a: funcionarios (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.).
SE

<!-- pág. 4 -->

O VINISTERIO DE SALUD
TERMINOLOGÍA
MINSAL: Ministerio de Salud.
SGSI: Sistema de Gestión de Seguridad de Información.
CSIRT: Equipo de Respuesta ante Emergencias Informáticas.
DOCUMENTOS APLICABLES Documentos del Sistema de Gestión de Seguridad de la Información (SGSI) de MINSAL Política Nacional de Ciberseguridad (PNCS)
El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior:
Decretos Supremos y Normas Internacionales de Seguridad de la Información y
Ciberseguridad: https://www.csirt.gob.cl/decretos/
Leyes relacionadas: https://www.csirt.gob.cl/leyes/
ROLES Y RESPONSABILIDADES Miembros comité de Crisis y sus Subrogantes:
o Ver tabla del punto 6.1 con el detalle de las responsabilidades.
Funcionarios
o
Informar cualquier evento o debilidad que pueda afectar la seguridad de la información.
PROCEDIMIENTO
GESTIÓN DE INCIDENTES CRITICOS La Institución llevará adelante la respuesta a incidentes a través de sus instancias técnicas y se coordinará con el equipo de respuesta a Incidentes y el Comité de Crisis, en la medida que el impacto de los incidentes afecte a los activos vitales de la organización.
Los problemas relacionados a los incidentes de seguridad de la información dentro de la organización serán manejados por el Encargado de Seguridad de la Información y Ciberseguridad y/o quien asigne el Jefe Departamento Tecnologías de la Información y Comunicaciones, el que se apoyará en el personal equipo de respuesta a Incidentes y el Comité de Crisis, con atención al resguardo de los principios de la Política General y las leyes vigentes. A su vez, el Encargado de Seguridad de la información y Ciberseguridad mantendrá los contactos correspondientes con las autoridades, grupos de interés externos o foros que manejen los problemas relacionados con los incidentes de seguridad de la información.
NAE mi

<!-- pág. 5 -->

a oO
A —————
Cabe destacar que en la medida que los incidentes hayan sido judicializados, se requerirán de especiales cuidados, en orden a convocar a los expertos policiales para que accedan a la información necesaria para la investigación.
FLUJO GENERAL DEL PROCESO La gestión de crisis se realizará de acuerdo con lo indicado en el siguiente flujo:
j O
: Declarar Chsis
y Oasis
ed >
Ed |
E
¿Incidente bajo
E
E
AA
é
zontrol?
SE
E
e a A
ria e a
Q)
COMITÉ DE CRISIS
El Comité de Crisis es responsable de la gestión de los Incidentes dentro de la organización, este debe estar previamente definido. Sus principales responsabilidades son; acelerar los procesos para la toma de decisiones en la resolución de incidentes, definir las prioridades, establecer la estrategia, asignar recursos y táctica a seguir.
Este es presidido por la figura máxima con capacidad de decisión (responsable máximo del organismo y/o representante del Gabinete de Ministro o Subsecretarias. Junto con ello debe tener representación y subrogante de a lo menos las siguientes áreas del Organización: Encargado de Ciberseguridad, Infraestructura Física, TIC (Operaciones, Infraestructura, Desarrollo, Explotación), Dueños de los Procesos, Recursos Humanos, Finanzas, Jurídica y Comunicaciones. La gestión de crisis no es algo exclusivo del equipo de seguridad o tecnología, sino que implica a toda la organización.
Será el presidente del comité el responsable de definir si se está ante una crisis o no, su nivel de criticidad, definición de medidas y asignación de responsabilidades, así como los Y
A Ys

<!-- pág. 6 -->

EEES| PROCEDIMIENTO GESTIÓN DE CRISIS POR INCIDENTES DE .O e — distintos responsables en cada caso, desde lo operativo para la contención y resolución del incidente, hasta la coordinación y comunicación que velará por la imagen de la institución, estableciendo la política de información, con los comunicados más adecuados y canales oportunos.
O. UM
a a oeN Corao
A continuación, se presenta un cuadro resumen de los actores del Comité de Crisis y sus responsabilidades:
[Representante | — Responsabilidades
CEO/Representante
Inicia la gestión de crisis y preside el comité de crisis.
| Dirección
General
Delega responsabilidades.
¡Presidente
"Se mantiene permanentemente informado.
i
Actúa como portavoz si las circunstancias lo exigen.
Encargado
de = Eselprimeroen conocer el incidente y debe determinar nivel.
Ciber/Seguridad de
decriticidad (Impacto y Urgencia), si es preciso trasladarlo o la Información no al comité de Crisis.
Notifica al CSIRT de referencia.
"Determina
cuáles son las primeras acciones operativas para
|su contención.
| TIC
e
Gestiona la continuidad de los servicios, utilizando según
E
sea el caso, los respaldos o sitios de contingencia para los Toda versión impresa de este documento se considera como Copia No Controlada,
MEN Y

<!-- pág. 7 -->

PEE
T|
MT
O VINISTERIO DE SALUD _Representante_______
Responsabilidades__________22—
Revisa
el entorn común
de
todas
las
aplicaciones
i
(comunicaciones,
firewall,
DNS,
etc..),
así como
los
específicos de cada aplicación.
Gestionará de forma rápida servidores virtuales en caso de ser necesario.
Activar Política de copias de seguridad.
Activar infraestructura de contingencia.
PMO o Encargado
Coordinar con
los proveedores todas las acciones de del Proyecto contención, erradicacióny cierre de los incidentes.
| Jurídica
'=» Determina
las
responsabilidades
legales
directas
provocadas por el incidente.
Da seguimiento a las acciones a seguir de acudoa la leyes y normas aplicables.
Orienta sobre todos los asuntos legales.
¡Comunicaciones
Integra
el Comité de
Crisis y adopta
el Manual de
comunicaciones de crisis previamente elaborado.
Decide cuáles son los mensajes clave, el formato y canal más adecuado, en función de los grupos de interés.
= Activa el seguimiento y percusión de la crisis en los.
diferentes medios de comunicación y redes sociales.
|" Mantiene contacto con los medios de comunicación.
Administración
y
* Analiza los recursos necesarios para la resolución de la
| Finanzas
Crisis.
Recopila información, evalúa los hechos y plantea opciones.
Infraestructura
¡»Mantiene comunicación con las compañías aseguradoras (si
Física_______
1. aplica.
Recursos Humanos
Portavoz ante los funcionarios y en caso de ser aplicable, los representantes.
Gestiona las acciones operativas en caso de incidentes relacionados con personas.
Comunica, llegado el caso, con los afectados y facilita información o asistencia básica (por ejemplo, en caso de una i lesión de un funcionario).
Evalúa el ánimo de los funcionarios y recomienda acciones para evitar decaimiento o una evolución no prevista.
Ce
Toda
versión impresa de este documento se considera como Copia No Controlada.
a T

<!-- pág. 8 -->

Bo...
A
OVINISTERIO DE SALUD
Declaración de crisis y equipo responsable según el nivel de criticidad (Impacto y
Urgencia):
Gestión Operativa
Comité de Crisis
g
E
A
i
BAJO
“0 MEDIO
' o
Ago
MUYALIO.
A Aa
(yg
oOO ao
e
Noregulere comida
— Psoe aerecamienecias Remiescomidcasa y e.
e
TOSIi
o
LL
Gobierno deGsis. ——.
SS.
Responde EncargadoáÁrea AO aos y...
Preside Representente o, o. Responde sduno a A sd o. Aco, '
A
a
A
gn
e
rr o a
on o e a a e
RS
e e
E
a
e a ss o o
Ante incidentes con peligrosidad baja y media no deberían requerir la convocatoria de un Comité de Crisis, porque no se encuentra ante una situación que se pueda definir como tal. Bajo la responsabilidad de directa del Encargado de Ciberseguridad y/o quien asigne el Jefe Departamento Tecnologías de la Información y Comunicaciones, los equipos técnicos tienen el conocimiento para solucionar el problema en el nivel operativo.
__ _—_——
EL  _K_ E _ _Á_AA
Atributo
Ñ
Nivel de criticidad
o
_Bajo
Medio
Alto
MuyAlto
MM
e
emtninin¡qq gg/qqg/II
OO Cd[q]
V<-.D
RO AS
Declaración
nn
ON
aA 1
e NO
NO
-. CDPCIONAL—
Sl
Si
| - de Crisis...
OA
¡Norequiere
No
requiere Requiere Comité
Requiere
MiNaS
|comité
de crisis Comité de Crisis de sis
Comitéde
Mei
Drerao ToyNegoc
Ámbito de
quien asigne JefeAOS Representan a O o «Departame:mio Seguridad y/o | te Dirección o
- Tecnologías
de la
quien asigne
¡Gobierno
toman .TS
de crisis oO
E omuicaciones . Departamento ooo
OOOO acecnologías |
e
A
cs
OOOO AE —
Era
a
o o A
ca(qOes
NE

<!-- pág. 9 -->

M7UU
OVINISTERIODE SALUD
En función del nivel del incidente actuarán distintos niveles o actores del Comité de crisis:
Baja y Media
Comitéde
Nivel Operativo
crisis
¡No
se
requiere
del
| Ciber/Encargado
de
nivel Ot
Seguridad, ni del CEO/DG/P (para estos casos será.
| presidido por el encargado del
¡área Tl y responsable de los
| activos afectados).
Alta y Muy Alta
Comité de
Comité de Crisis
o
omsis
| Comité
de
Crisis
sin
el.
o CEO/DG/P (para estos casos
| nivel2-3
el comité será presidido por el.
| Ciber/Encargado
de
¡Seguridad y/o quien asigne
Jefe
Departamento
| Tecnologías de la Información |
| y Comunicaciones).
o
Comitéde
Estratégico
A
A CE
O
PREPARACIÓN
A continuación, se establecen las herramientas y recursos que deben estar disponibles antes de la gestión de cualquier incidente, deben ser mantenidas y actualizas por el representante que preside el Comité, de acuerdo con el nivel de Criticidad establecido en punto anterior:
6.4.1 Instalaciones y comunicación para la gestión de incidentes
Información de contacto:
Registro de
partes interesadas dentro y fuera de la organización (titular y subrogante), tales como Equipo de Respuesta ante Incidentes, Autoridades, Comunicaciones, Jurídica, Recursos Humanos y Administración y Servicios.
Los datos de contacto deben incluir a lo menos los números de teléfono y correos electrónicos.
Mecanismos de reporte de incidentes: Todos los funcionarios, el personal a honorarios y terceras partes deben informar, tan pronto como sea posible, debilidades, eventos y/o o , Toda versión impresa de este documento se considera como Copia No Controlada, , ANENS

<!-- pág. 10 -->

MU
incidentes que pueda tener un impacto en la seguridad de los activos de la organización. Al respecto, Minsal dispone los siguientes canales de comunicación únicos de contacto:
O
Através del contacto telefónico CA +(562) 800 123 573 = Mediante los siguientes correos Para temas técnicos (requerimientos, Incidencias) mdasOminsal.cl
En
temas
de
(Eventos,
debilidades
de
seguridad,
Incidentes, amenazas, riesgos) seguridadticOminsal.cl Sistema de registro de incidentes: debe existir un sistema de gestión de incidentes para el monitoreo y seguimiento del estado de los incidentes.
" Teléfonos móviles: para ser utilizados por el personal que sea asignadoa la gestión de incidentes en terreno o fuera de las dependencias principales.
Software de encriptación de comunicaciones: para las comunicaciones sensibles entre los miembros del equipo de respuesta a incidentes, partes internas y externas, PDI, Ministerio del Interior, etc.
Sala de Crisis: sala (fija o temporal) para la centralización de las comunicaciones y coordinación.
Lugar de almacenamiento seguro: para el almacenamiento de la evidencia u otro material sensible.
6.4.2 Hardware y software para la gestión de incidentes Estaciones de trabajo para actividades forenses y dispositivos de respaldo: para crear imágenes, conservar logs y guardas otros datos relevantes.
Notebooks: para actividades de análisis de datos, analizar paquetes y escribir reportes.
Extra de estaciones de trabajo, servidores, equipamiento de red (físico o virtualizado): para ser utilizado con diversos propósitos tales como restaurar respaldo o gestionar Malware.
Medios extraíbles (pendrive, discos duros, etc.) en blanco.
Impresora.
Analizadores de tráfico: para capturar y analizar el tráfico de red.
Software de análisis forense: para analizar imágenes de disco.
Medios extraíbles con software confiable: con versiones confiables de programas para la obtención de evidencia desde los sistemas.
_.
c>EN y

<!-- pág. 11 -->

BO
Accesorios para recopilar evidencias: tales como notebooks, cámaras digitales, grabadoras de audio, formularios de cadena de custodia, etiquetas y bolsas de custodia, cinta adhesiva de custodia, para las posibles acciones legales.
6.4.3 Recursos para el análisis Listado de puertos: incluidos los usados comúnmente por trojanos.
Documentación:
sistemas
operativos,
aplicaciones,
protocolos y manuales de antivirus.
Diagrama de red y listado de activos críticos: tales como aplicaciones, bases de datos, servidores, etc.
Línea base: de la red, sistema y actividades de las aplicaciones.
Arquitectura del Sistema afectado.
6.4.4 Software para mitigación = Acceso a imágenes: de sistemas operativos y aplicaciones para recuperación y restauración.
IDENTIFICACIÓN
Si se determina que corresponde a un incidente que requiere la actuación de uno de los Comité de Crisis, se debe dar aviso de inmediato a sus miembros, y el Encargo del Comité según el nivel que corresponda debe coordinar las acciones de contención y erradicación.
A partir de este momento se debe mantener registro de todas las actividades y comunicaciones realizadas, estos registros deben permitir dar respuesta a las siguientes preguntas: ¿quién?, ¿qué?, ¿dónde?, ¿por qué? y ¿cómo?
En esta etapa se activan las actividades de comunicación al interior de la organización y con terceras partes, dependiendo del tipo y nivel del incidente.
Una vez determinado el alcance del incidente, la activación del comité de crisis y el registro de lo ocurrido se debe avanzara la siguiente fase.
Nota 1: en cualquiera de las fases si el comité de crisis determina que el alcance del incidente es mayor a lo definido inicialmente, el presidente del comité debe escalar al Comité Superior de gestión de incidencias.
CONTENCIÓN
El Comité de Crisis en conjunto dirigidos por el presidente respectivo, coordinan la contención del incidente, tratando de minimizar los daños, dependiendo del tipo de
E
AO)
—TIWSe

<!-- pág. 12 -->

POE
SEGURIDAD - PROS-NC-012
O
VINISTERIODESALUD
incidencia, serán distintos los responsables de las acciones de contención (ver punto 6.1 de este procedimiento).
Los pasos para la contención son:
a) Acciones inmediatas de contención: destinadas a detener de inmediato el incidente y contener los daños. Un ejemplo de estas acciones es la aislación de un segmento de red con estaciones infectadas, sacar de producción servidores que se encuentren comprometidos, apagar switch, etc.
Las acciones inmediatas de contención no pretenden ser soluciones a largo plazo o soluciones definitivas, solamente limita el incidente a que sea peor.
b) Respaldo de la información: se deben realizar respaldos de los activos afectados, para preservar la evidencia, para el posterior análisis forense y las acciones legales pertinentes.
c) Acciones de contención para restablecer las operaciones: en este paso se deben implementar las acciones de remediación para restablecer las operaciones, por ejemplo: levantar respaldos, activar sites de contingencia, activar procesos manuales, etc.
En esta etapa básicamente se remueven las cuentas comprometidas, puertas traseras instaladas por los atacantes, instalación de parches de seguridad, y cualquier acción destinada a evitar que el incidente escale.
PLAN DE COMUNICACIÓN
Para la notificación de los incidentes de seguridad se utilizará como criterio de referencia el Nivel de peligrosidad que se asigne a un incidente, sin perjuicio de que, a lo largo del desarrollo, mitigación o resolución de este, se categorice con un determinado Nivel de impacto que requiera de un
Plan de Comunicaciones del incidente a los actores involucrados, que considera las comunicaciones, tanto entre equipos de trabajo (árbol de llamadas) como con clientes, proveedores.
Los que deberán ser informados al Encargado de Seguridad de la Información y Ciberseguridad, quien a su vez informaráa los al Jefe del Departamento de Tecnologías, los incidentes cuyo nivel de severidad sea Rojo. El plan de comunicación podrá considerar las siguientes instancias de comunicación:
Encargado de Seguridad de la Información y Ciberseguridad Jefe del Departamento de Tecnologías
Jete Gabinete Ministro
Jefe Gabinete SRA
Jefe Gabinete SSP
Director Operativo CSIRT
Director General CSIRT Consejo Nacional de Ciberseguridad (CNC)
A
Subsecretario del Interior > Wa
ANNA

<!-- pág. 13 -->

### 0. UU O VINISTERIODE SALUD
Ministro de Interior
y Seguridad Pública
Presidente de la República Es importante que de acuerdo con el nivel de severidad del incidente este sea comunicado en forma preventiva al Coordinador SOC, quien a su vez será la persona que informe en detalle del incidente a el director Operativo y General de CSIRT.
De ser requerida una comunicación oficial hacia medios públicos esta deberá ser coordinada con el Jefe del Departamento de Comunicaciones quien visará el texto a publicar y los medios que serán utilizados.
ERRADICACIÓN
En esta etapa el Comité de Crisis gestiona la restauración de los activos afectados, se deben ejecutar todas las acciones necesarias para remover cualquier contenido malicioso o ilícito, asegurando que los sistemas o procesos se encuentran “limpios”. En esta etapa se deben implementar todas las protecciones necesarias para evitar que el incidente nuevamente ocurra, en base de lo aprendido durante las etapas anteriores (por ejemplo:
instalación de parches, actualización de sistemas, compra de equipamiento, etc.).
RECUPERACIÓN
El comité de crisis gestiona la recuperación de los procesos, una vez las vulnerabilidades han sido erradicadas, asegurando que el incidente no se repetirá. Se debe mantener el testeo, monitoreo y validar que la solución ha sido efectiva.
Durante esta etapa se debe definir:
Fechay hora de la restauración de las operaciones.
Metodología de testeo para verificar que los activos afectados no son vulnerables y son completamente funcionales.
La duración del monitoreo de los activos para verificar cualquier comportamiento anómalo.
Las herramientas para el monitoreo y validación del comportamiento de los activos afectados.
6.10 LECCIONES APRENDIDAS En esta etapa el presidente del Comité de Crisis según corresponda, debe gestionar que todas las actividades realizadas en la gestión de la incidencia estén correctamente documentadas, junto con registrar cualquier otra información que sea de beneficio para futuros incidentes. El informe debe dar cuenta de quién, qué, dónde, por qué y cómo de la incidencia.
El informe no debe tardar más de dos semanas en su confección y aprobación.
r
Los campos mínimos del informe deberían contener:
,ae: e
e

<!-- pág. 14 -->

POTES]
1 OVINISTERIO DE SALUD Cuando fue detectado el problema y por quién.
El alcance de la incidencia.
= Cómo fue contenido y erradicado.
Trabajos realizados durante la recuperación.
= Áreas en donde el Comité fue efectivo.
Areas en los que se necesita mejorar.
Recomendaciones de mejora para la gestión de incidencias.
REGISTROS
Informe de gestión de la incidencia.
Evidencia recopilada durante el proceso.
Registros de las actividades ejecutadas durante la gestión de la incidencia.
DIFUSION
La comunicación del presente procedimiento se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en la intranet de Minsal http://isalud.minsal.cl/
Correo informativo.
REVISION Y MEDICION
El presente procedimiento deberá ser revisado a lo menos cada dos años o cuando ocurran cambios significativos para asegurar su continua idoneidad, eficiencia y efectividad.
EXCEPCIONES AL CUMPLIMIENTO DEL PROCEDIMIENTO Frente a casos de especiales, el Comité de Seguridad de Información evaluará la situación y podrá establecer condiciones puntuales de excepción en el cumplimiento del presente procedimiento, siempre que no infrinja las políticas internas existentes. Toda excepción debe ser documentada y generar un proceso de revisión del procedimiento, que determine si se deben agregar condiciones de operación particulares.
CONTROL DE VERSIONES
¡Versión  Fechade
Motivodelcambio
Secciones
O.
Diciembre
Creación del documento
N/A
A
dsAN

<!-- pág. 15 -->

EE
rr
UOONIDNNISTERIODESALUD ANEXO: CHECKLIST GESTIÓN DE INCIDENCIAS
PREPARACIÓN
Todos los miembros del Comité son conscientes de las políticas de Seguridad Todos los miembros del Comité tienen claro a quién contactar en caso de incidentes.
Todos los miembros del comité tienen acceso a herramientas, equipamiento y registros para la ejecución del proceso de gestión de incidentes.
Todos los miembros tienen experiencia o han realizado simulacros de incidentes.
IDENTIFICACIÓN
Dónde ocurrió el incidente.
Quién reporto o descubrió el incidente.
Cómo fue descubierto.
Hay más de un área comprometida en el incidente, si es así cuáles y cuando fue descubierto.
Cuál es el impacto del incidente.
"Las fuentes del incidente se encuentran identificadas (dónde, cuándo y cuáles son)
CONTENCIÓN
Acciones inmediatas de contención:
e
¿El problema puede ser aislado?
o
Sies así, asilar el problema.
o
Si no, gestionar con los dueños y encargados de los activos, y terceras partes relevantes, para determinar las acciones necesarias para contener el problema e ¿Todos los activos comprometidos están aislados de los activos no comprometidos?
o
Sies así, continuar al siguiente paso.
o
Si no, continuar con
el proceso para aislar el problema, para evitar escalamiento a otros activos.
Respaldo de la información:
e
¿Las copias forenses de los activos afectados han sido creados y resguardados para futuros análisis?
e
¿Todos los comandos y otra documentación relevante, desde que ocurrió el incidente se mantiene actualizada?
,aa

<!-- pág. 16 -->

aO
o
Sinoes así, documentar todas las acciones tomadas lo más pronto posible, para asegurar que toda la evidencia se retenga para análisis futuros (técnicos y regales) y/o lecciones aprendidas.
¿Las copias forenses se encuentran almacenadas en lugares seguros?
o
Sies así continuar al siguiente paso.
o
Si
no,
resguardarlas en un
lugar seguro,
para
prevenir perdida o
manipulación indebida.
Acciones de contención para restablecer las operaciones:
e
Si el activo puede ser aislado del proceso y continuar con las operaciones, proceder a la fase de erradicación.
e
Si el activo debe continuar en el proceso, proceder con las acciones para restablecer las operaciones, removiendo cualquier vulnerabilidad que afecte al activo (remover malware, hardening, etc.).
ERRADICACIÓN
e
¿Los activos afectados puedes ser rediseñados o fortalecidos (hardening), mediante parches, u otras contramedidas para reducir el riesgo de ataques?
o
Sino, responder ¿por qué?
e
¿Todas las vulnerabilidades y otros artefactos utilizados por el atacante han sido removidos, y los activos fortalecidos contra esas vulnerabilidades?
o
Sino, responder ¿por qué?
RECUPERACIÓN
e
¿Todos los activos afectados han sido parchados fortalecidos frente al ataque reciente, existen posibilidades de un ataque futuro?
e
Fecha y hora en que los procesos pueden ser restablecidos.
e
¿Qué herramientas se utilizarán para testar, monitorear y verificar que los procesos han sido restablecidos y no son vulnerables a los mismos métodos de ataque del incidente original?
e
¿Durante cuanto tiempo se monitoreará los procesos restablecidos?
e
¿Existen indicadores que permitan definir una línea base, para medir el grado de cumplimiento de los procesos restaurados?
LECCIONES APRENDIDAS
e
¿Existe toda la documentación del incidente?
o
Sies así, generar el Informe de Incidente.
o
Si no, generar la documentación lo más pronto posible, antes que la información sea olvidada o perdida.
| 2AA

<!-- pág. 17 -->

### 1. UU
ONINISTERIODE SALUD
Asumiendo que el informe de gestión de incidentes existe, ¿responde a las siguientes preguntas: ¿qué?, ¿dónde?, ¿por qué? y ¿cómo?
e
¿Es posible generar
el
informe de incidentes dentro de las dos semanas posteriores al incidente?
o
Explicar por qué, y cuando estará disponible el informe.
e
En la reunión de lecciones aprendidas:
o
Analizar el proceso de respuesta al incidente con todos los miembros del comité.
o
¿Existen áreas en las que sea necesario mejorar?
Sino existen, explicar por qué.
DA

<!-- pág. 18 -->

O
ANEXO: Orientaciones sobre niveles y criterio de evaluación y clasificación de crisis
E
E
—Bajo— Medio
—Aló MuyAlto
Melia
t
mpacto
o cl
PS COa
o
oCO
A
Ateca
Afectación ala
Oa
la
Externo
e .L
OO actividades [Eoubea
E
nacional O
a ea nacional
o
a
O
O...
extraniero.
A
aaCo ala DS
a AS
, o seguridad
.  AEeliice
Afectación a la (o
:O ciudadana con MEM
Externo
a (¡Dg
¡5IEI$CIKIA|... OOO mote o potencial ciudadana ca : OOOO pelioro para ¡lee
A
Oreco. | personas.
Interno
ón
aO
o O
a le
infraestructuras
IIS
ofaestuciura
críticas/servicio. "1 e XX e...
crítica
esencial
oa
: oo
a
Afecla
a los Afecta a más Aaa másdo Aleta a a sistemas de la | del 20 % de [ME (0 [E ssems:
AA
Afectación a
LO.) Sistemasdela organico
RESERVADO
[Sea
Interno
sistemas O> Organización OOO sa o : CL Afecta a más del MACecE tool o CO
3... 75% delo 00.
o
OA
Os.
de
dE.
OS
Is
¡q¿30€éáá;áAa sistemas de la ASCO eb o
RO
1.s
O
A
rrISI
IS
lee
eorganización
Interrupción de interrupción Inietrupción en interrupción en CU OL .. prestación| en la lo pescó la Mec la prestación
Interrupción del o
prestación. dl sendo «del
Semicio
Meal
servicio
Interno
Oe
servicio easupere
a
1 superor a E superior a 8 servicio o : O a
O
stperoral5% heray suoener
| horas
y superior [WENO
Po...
de usuam
.. .% a
ALCAE 0. das
4 Pm
.oo
de UStanos a
a 35 % de .
de
h
O
o Mc
los Usuarios
(El
incidente
El
incidente Emédeme
El
incidente [IO
Recursos en
: pararesolverse. para
- ¿para fésolese
para tesolverse
[mier
interno
jornadas
menos
de 1. resolverse
eMe o y eL. ente
50 y Mud
personas
Ea.o ] éntte
1 y 5 aa
100 Jornadas- Hd
aoA
persona —.. | jemadasE...
| N
o
[Aoa econ. a o DA
¡Entre 0.0001 %
Entre
el A...
Entre el0,07%y Mr
Interno
| Impacto económico De
q 0,001
y 995 a
o
el
9,1 +
.]]— 5
del
dePlBacua]| delPiBacual UL
E
a.
MA
—Supeñor a Superior
a ...
Supeñor aIAE
Externo
Afectación
ao Eo e
: a oa prensión
geográfica
| TReg. ———2Reg
e
UU 4Reg.
MRiecie
: mediático.| reputacionales es acionales| reputacionales a MS oee]; 5 dao con eto.a a imagen del país MLELAS y o...O mediático. “separación on. (marca
Meda
nda (amplia.
a
España)
y Aida
en
. O cobertura II
medios
de
Externo
Impacto reputacional |...
E
: A.
a
a
a
emos medios
ampliacontinua en Mee eo
| coponra medios
de [MAGNO
O comunicación)  enios mediosde comunicación
|o
| comunicación y ñacionales
O
o...
o
AFAN

<!-- pág. 19 -->

PONE
PU
vinisTERIODESALUD
AAA
Sin afectación | Con
eciperadón | Recuperación
Aca
| oticos.
procesos.
ata
cidad: Ml actividad
Interno /
Afectación alos... 1 criticos.
y
a interrumpida por
activida /
Drocesos O recuperación tgerasnentopor encima de su Cons operaciones críticos aaa nidad :
la BICa. (UU a. A
d
por
OS
A...
E encima.
de
su
Oa interrumpida. OO o... IV oo dentro de suo a a crA
TI
5E”
id
|Lasexpectalivas| Las
aa Las expectativas MECACINES
|confianza
de los | la
O IO confianza delos
Sp
_ ¿Ecomfanza de EOLCOUouoos de E
Afectación a las
=3Ínterés no se los grupos e re interés se verán HICE
Social
relaciones
|WenBleciadas| interés no se |mMeamEne
| afectadas [ECN
con los grupos de IO afectadas adas de manera
ACA.
oca
interés
coado O considerable
MICA
o
O O O
atectadas
Pl
Es O
a
fl durante úun largo
o
qQxXxGOÓIuUOx0xqx0?$?$Íbii.. LD —_
A
A III
a] A MUa
] oa
e,
población
Muveceldn
Social
Alarma social o a
a ón
E conisin
O
oa $.
causa justificada
Mea justificada
A
A
a.
O A
Económico
¡Daños aterceros / tasaoA : moderados TO ve
Ll
¡Sin pérdidas o | Pérdidas por Pérdidas par. Pérdidas — por MA
|pérdidas.| valor
hasta delos haa valor hasta WE hasta o
Pérdidas
' insignificantes.
«coste
de ¿sede coste
de a
de
Económico
económicas
|Coste
dentro | reposición
eposcón
reposición
M
ició
oa Sin
E e
O Reclamaciones. Ao
e
nani
implicaciones implicaciones implicaciones|aisladas de MW hasta implicaciones o
A...
o.
_.—_A
e
e
Legal
legales a
: O Terceros
y/o
MG
de
Ooa
: a indiciosdeMG eel
qxIA—A— o
o) delto..... *RA
O A
MUYALTO.
ARAU
2 RTO Tiempo objetivo de recuperación
SN
NENA