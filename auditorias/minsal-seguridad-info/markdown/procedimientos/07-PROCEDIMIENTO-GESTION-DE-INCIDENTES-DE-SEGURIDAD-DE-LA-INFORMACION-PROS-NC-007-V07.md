<!-- pág. 1 -->

Po] Ministerio de
Gabiermna
de Chis
PROS-NC-007
PROCEDIMIENTO GESTIÓN DE INCIDENTES DE SEGURIDAD DE LA INFORMACION Versión Oficial Actual vO7 - Noviembre del 2024 a oR bl
F
o
¡rm
VIE e
echa cas o ir>
Elaborado
Vado
|Aa_
le Za INS
10 Y Y
p
yA
p
CAR
Ó
Revisado Ni y VA! A
“49. LO A 43IIA O
RO DEN O ECURIDAD
Aprobado
LAZAL Q0_ > 4
a
Documento Controlado. Prohibida su reproducción parcial o total sin autorización.
ES "
y
E EM

<!-- pág. 2 -->

de 7
MONTA,
ministerio DESALUD | ID:PROS-NC-07 | Versión:7 | Página2de28
PANA
CONTENIDO
PROPÓSITO .ccccocconenentononaneenoconinaononoonononnenanenannoconcoloconconondo anno cnncoloscnnonononco conancaladas corasticciÓ
TERMINOLOGÍAcoooooccococcococcoconcnnonononnnoncononcnnnonnnnnonnonnnnononarnococnorororononarncrncnc raranannannonoris A MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS ...occcccncccccnnccnononroccncnccnnncaccnnnnacncccDd Notificación de un incidente de Seguridad ........oooocccccccconcccnonononenononononnnccnoncnnaroconannnnO
Gestión de INCIeNtes........occooonccncoccnncnnnnnononnnnnnonnncnnonoconnnnocrnnnacononorononacccnnnacoconanoccno Reporte de eventos y debilidades en la Seguridad de la Información ........................ 10 Procedimiento para gestión de Incidentes. .........cccccoooncnncccnoniononnnncnonoronnononaninocnnnnnaso 12 Equipo de respuesta aincidentes y Comité de CTiSiS............oooccooccoccnnnoncninnoronaronosrono 19 Declaración del Nivel de crisis y equipo responsable según el nivel de criticidad (Impacto y Urgencia): ...cooocccononococinoccccnooacccononnnoronnnconananoconnnncannnnccconcncconancnccnnc acc canonoronnncccnn o ZO
Proceso Disciplinario ............ooocccooccooncnnoccnnnnrnonancnarnnnnnronorononocnnacononcconaconanoconoccnnicano Continuidad de la Seguridad de la Información .........ooocccccccnoncccnnnononocccononinanicocinnano22
Recolección de evidencia....occcccoonnnnnnccnnoonncnnononannccconononoronononononnnnn nonororonononoccccncn o Z
6.10
Comunicación alos involucradoS........cccccccccnnonocoonnccnncocccnnnnononanionoccccnacacononanencaninicnnZO
6.11
Análisis de causa y cierre del incidente .........oocccccnooncncccnnnononcccnnnonccccnononanicicinininicicZO
6.12
— Aprender de los incidentes en la seguridad de la información .......coocncncnnnnnnnnnnnnnnnnn.ZO PLAZOS DE NOTIFICACIÓN DE INCIDENTES DE SEGURIDAD ..cococccnccccccccnoninncnncnnncnconocooZA PERÍODO DE REVISIÓN. cocoocococoooonononococnonconocororonnnconococononononcnconorororanaconcnoncocnacocononZO EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA....ooccccccccccincccononocconccnnconccnnaniccnooZO , AA TON reproducción parcial ototal sin autorización.
(en

<!-- pág. 3 -->

PROCEDIMIENTO DE GESTIÓN DEINCIDENTES DE SEGURIDAD DE LA INFORMACIÓN ae
MÍ
Página3de28
PROPÓSITO.
Establecer las actividades necesarias en la Subsecretarías de Salud Pública y Redes Asistenciales, para la detección oportuna y tratamiento de vulnerabilidades o eventos que comprometan la seguridad de los Activos de Información de la Institución.
Establecer responsabilidades de las distintas Unidades con relación a la seguridad de los datos institucionales (integridad, disponibilidad y confidencialidad), ya sea se encuentren en la plataforma informática como en su manipulación a cargo de los funcionarios en general.
Responder en forma rápida, eficaz y ordenada ante la ocurrencia de incidentes de seguridad que afecten los activos de información institucionales.
Asegurar un enfoque consistente y eficaz sobre la gestión de los incidentes de seguridad de la información, incluida la comunicación sobre eventos de seguridad y debilidades.
ALCANCE.
Este procedimiento aborda la gestión de incidentes de seguridad que afecten a los activos de del tipo:
base
de
datos,
documento,
equipo,
expediente,
formulario,
infraestructura física, persona, sistema de información, software, en cuantoa la:
Confidencialidad: acceso no autorizado a la información.
Integridad: Modificación no autorizada, destrucción o pérdida de información.
Disponibilidad: Inaccesibilidad a la información.
Este procedimiento es aplicable a todos los funcionarios' (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para las Subsecretarías de Salud Pública y de Redes Asistenciales y que tengan derechos de accesoa la información que puedan afectar los activos de información del Ministerio de Salud.
En cuanto a las temáticas de protección abordadas, el ámbito de aplicación de esta política corresponde al (a los) Dominio(s) de Seguridad de la Información y Controles de Seguridad respectivos, detallados a continuación:
Alcance de Dominios y Controles de Seguridad de la Información
Estándar
ID Control
Nombre del Control
A05.5
Contacto con las autoridades
ISO
A 05.6
Contacto con grupos de interés especial
27001:2022
A 06.8
Notificación de los eventos de seguridad de la información ' Alo largo del procedimiento cada vez que se mencione funcionario se refiere a: funcionarios (planta, contrata, reemplazo dlE, y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.).
jse e
E |
J
SAS

<!-- pág. 4 -->

am
Alcance de Dominios y Controles de Seguridad de la Información
A06.8
Notificación de puntos débiles de la seguridad
A 05.09
inventario de información y otros activos asociados
A 05.13
Etiquetado de la información
A 05.24
Responsabilidades y procedimientos
A 05.26
Respuesta a incidentes de seguridad de la información
A 05.27
Aprendizaje de los incidentes de seguridad de la
A 05.28
Recopilación de evidencias
3 TERMINOLOGÍA.
Amenaza: Potencial causa de un incidente que podría dañar la organización o sus activos de información. Las amenazas pueden ser internas o externas, intencionales o accidentales.
Ciberataque: Actividad intencional realizada por actores internos o externos que busca explotar vulnerabilidades para acceder, modificar, interrumpir o destruir información, sistemas o servicios.
Clasificación de Incidentes: Proceso de evaluación del incidente para determinar su severidad y priorización, utilizando criterios como impacto operativo, alcance, activos afectados y probabilidad de recurrencia.
CSIRT: Grupo designado responsable de coordinar y ejecutar las actividades de respuesta a incidentes, compuesto por especialistas en seguridad,
Tl
y, según
corresponda, representantes.
Evento de Seguridad: Ocurrencia identificada de un sistema, servicio o estado de red que indica un posible incumplimiento de la política de seguridad de la informacióno falla de los controles o una situación desconocida que puede ser relevante para la seguridad.
Gestión de Incidentes: Proceso estructurado para identificar, analizar, responder y aprender de los incidentes de seguridad con el objetivo de minimizar daños y prevenir su recurrencia.
Incidente de Seguridad: Un evento o una serie de eventos de seguridad de la información no deseados o inesperados que tienen una probabilidad significativa de comprometer las operaciones institucionalesyamenazar la seguridad de la información.
Lecciones Aprendidas: Análisis posterior a un incidente que identifica oportunidades técnicas o administrativas de mejora en los procesos, controles y respuesta para prevenir futuros incidentes o mejorar la gestión.
Notificación de Incidentes: Proceso formal de comunicar a las partes interesadas internas y externas sobre la ocurrencia de un incidente, su impacto y las medidas de mitigación implementadas, conforme a los requisitos legales y contractuales. E
SH

<!-- pág. 5 -->

de eli
Recuperación: Etapa del proceso de gestión de incidentes enfocada en restaurar las operaciones normales de los sistemas y servicios afectados, garantizando la seguridad y estabilidad.
Registro de Incidentes: Documento o sistema utilizado para registrar, rastrear y gestionar incidentes de seguridad, incluyendo detalles como la naturaleza del incidente, su clasificación, impacto y acciones tomadas.
Resiliencia Cibernética: Capacidad de los sistemas y servicios de la organización para resistir, recuperarse y adaptarse frente a incidentes de seguridad, minimizando el impacto en las operaciones.
Respuesta a Incidentes: Conjunto de acciones específicas ejecutadas para contener, mitigar, investigar y resolver un incidente de seguridad, asegurando la continuidad de negocio.
Riesgo de Seguridad: Combinación de la probabilidad de que ocurra un incidentey las consecuencias negativas asociadas.
Vulnerabilidad:
Debilidad en un sistema, proceso o configuración que puede ser explotada para comprometer la seguridad de la información o los sistemas.
4 MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS.
e.
Marco Normativo.
o
NCh I5027001:2022: Seguridad de la información, ciberseguridad y protección de la privacidad - Controles de seguridad de la información.
o
El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior.
Decretos Supremos y Normas Internacionales de Seguridad de lalnformación y Ciberseguridad.
Normas relacionadas:
LeyN*18.845, de 1989, que establece sistema de mocrocopia o micrograbación de documentos.
LeyN”19.799, sobre documentos y firmas electrónicas LeyN”19.880 de bases de los procedimientos administrativos que rigen los actos de los órganos de la administración del Estado.
Ley N* 20.217, que modifica el Código de Procedimiento Civil y la ley N? 19.799, sobre documento electrónico, firma electrónicay los servicios de certificación de dichas firmas.
Ley N* 20.584, de derechos y deberes de los pacientes frente a las acciones y prestaciones de salud.
LeyN*21.180 Ley de Transformación Digital del Estado, establece directrices para la modernización de los procesos y servicios digitales en instituciones pública ESA o al
A

<!-- pág. 6 -->

de
MÍ
MINISTERIO DESALUD | 1D:PROS-NC-07 | Versión:7 | Págima6de28 PAM Tiene implicaciones en la privacidad y la protección de datos personales, ya que establece estándares para la seguridad de la en servicios y plataformas digitales, fomentando la eficiencia sin comprometer la confidencialidad y la integridad de los datos de los ciudadanos.
LeyN” 21.663 sobre Marco de Ciberseguridad, esta ley proporciona un marco para asegurar la ciberseguridad de infraestructuras críticas, que indirectamente impacta en la protección de datos.
Ley 21.668 establece la interoperabilidad de las fichas clínicas, sobre protección de datos establece un marco legal para salvaguardar la privacidad y los derechos de los ciudadanos en relación con sus datos personales.
Decreto N? 181, de 2002, del Ministerio de Economía, Fomento y Reconstrucción, Subsecretaría de economía, que aprueba el Reglamento de la ley N” 19799 sobre documentos electrónicos, firma electrónicay la certificación de dicha firma.
Decreto N* 14, de 2014, del Ministerio de Economía, Fomento y Turismo, Subsecretaría de Economía y empresas de menor tamaño, que modifica el decreto N? 181, de 2002, que aprueba Reglamento de la ley N” 19.799 sobre documentos electrónicos, firma electrónica y la certificación de dicha firma y deroga los decretos que indica.
DFL N? 1, de 15 de marzo de 2021, del Ministerio de las Culturas, las artes y el patrimonio, que determina los requisitos del método de elaboración, conservación y uso de las microformasy de aquellos a emplear en la destrucción de documentos originales en virtud de la ley N” 18.845.
Decreto N*23, de 21 de octubre de 2021, que aprueba el reglamento que establece los medios y procedimientos técnicos y administrativos que se utilizarán en la generación de microformas.
DFLN?*1, 2005, Ministerio de Salud.
Decreto N? 41, de 2012, del Ministerio de Salud, Reglamento de ficha clínica.
DFLN*725, de 31 de enero de 1968, Código Sanitario.
Decreto 273, de 2022, que establece la obligación de reportar incidentes de ciberseguridad a los organismos del Estado al CSIRT de gobierno.
El Decreto N* 533 establece el marco regulatorio en ciberseguridad para las instituciones públicas en Chile, que incluye normas para la protección de la información, la gestión de incidentes de ciberseguridad y la protección de infraestructuras críticas, en las que se procesan datos personales.
El Decreto Supremo N* 7 establece una Norma Técnica de Seguridad de la Información y Ciberseguridad, en concordancia con la Ley
N*2 21.180 sobre
Transformación Digital del Estado. Que tiene el objetivo de definir estándares mínimos de seguridad y ciberseguridad para todos los órganos de la administración pública en Chile, contribuyendo a la protección de los datos personales y a la seguridad de la información en los sistemas digitales A Documento Controlado. Prohibida su reproducción parcial o total sin autorización.
X ez e
a

<!-- pág. 7 -->

_|
a E”
gubernamentales.
Documentos Relacionados.
o
Documento del Sistema de Gestión de Seguridad de la Información,disponibles en isalud.minsal.cl.
5 ROLES Y RESPONSABILIDADES.
Funcionarios.
o
Manejar, utilizar y proteger el acceso a los documentos institucionales, asegurando su integridad, disponibilidad y confidencialidad en los procesos y sistemas institucionales.
o
Informar de manera oportuna cualquier evento, debilidad o sospecha de incidente de seguridad que pueda comprometer la información institucional, a través de los canales oficiales establecidos por el MINSAL.
Encargado de Seguridad de la información y Ciberseguridad.
o
Diseñar, actualizar y garantizar el cumplimiento del procedimiento de gestión de o Supervisar la implementación de acciones correctivas y preventivas.
o
Actuar como enlace principal entre la alta dirección, partes interesadas internas y externas, y otras áreas relevantes.
o
Informar
a
la
alta
dirección
sobre
incidentes
críticos
y
coordinar
respuestas
estratégicas.
o
Gestionar y priorizar eventos e incidentes, liderando la ejecución de medidas para mitigar riesgos y prevenir recurrencias.
o
Encargado de Informar a CSIRT de Gobierno, Incidentes de Seguridad de acuerdo con lo indicado en Decreto 273, de 2022 y Ley N* 21.180.
Departamento de Tecnologías.
o
Proporcionar soporte técnico en la gestión de incidentes que afecten los sistemasy la infraestructura tecnológica de su administración.
o
Identificar y remediar vulnerabilidades explotadas en incidentes.
o
Proporcionar logs, configuraciones y otros datos técnicos para el análisis de los o Coordinar a las unidades internas de Infraestructura, Operaciones y Desarrollo de
Sistemas, Seguridad.
o
Implementar medidas de recuperación y restauración de servicios afectados.
Unidades responsables de los datos.
o
Dar cumplimiento a las políticas de seguridad de la información, aplicar el presente procedimiento y gestionar los incidentes en lo que se refiere al uso, manipulaciónL
Documento
Controlado. Prohibida su reproducción parcial o total sin autorización.
PS
o;
ES:

<!-- pág. 8 -->

PROCEDIMIENTO DE GESTIÓN DE INCIDENTES DE
SEGURIDAD
_|
il
protección de acceso a datos institucionales de modo de garantizar su integridad, disponibilidad y confidencialidad.
o
Representar los intereses de las áreas afectadas y colaborar en la gestión del impacto de los incidentes en los procesos de unidades responsables.
o
Informar sobre incidentes detectados en sus áreas.
o
Apoyar en la evaluación del impacto del incidente en sus procesos.
o
Implementar las recomendaciones para mitigar riesgos futuros en su ámbito.
Equipo de Respuesta de Incidentes.
o Supervisar que los Equipos o Áreas Resolutoras gestionen los incidentes de manera adecuada y conforme a su nivel de criticidad.
o
Gestionar los incidentes de acuerdo con el nivel de criticidad.
o
Coordinar la respuesta a incidentes de alto impacto con apoyo de las siguientes áreas:
Infraestructura física.
Y” Operaciones TIC.
Y” Recursos Humanos.
Y” Unidad Jurídica.
y” Servicios Generales o División de Administración.
Y” Unidades responsables de los datos afectados.
Equipos o Áreas resolutoras designadas para la gestión de incidentes.
o
Seráresponsable de:
Y” Coordinar la activación de los equipos de respuesta ante incidentes.
Y” Identificar la causa raíz de los incidentes y proponer medidas correctivas.
y” Generar y mantener reportes documentados sobre la gestión de incidentes.
v” Realizar el seguimiento de las medidas de mitigación hasta su cierre.
Mantener comunicación activa con CSIRT de Gobierno u organismos relevantes para la gestión de incidentes.
Nota: El personal designado deberá contar con un respaldo que lo reemplace en caso de ausencia.
Todos los usuarios, Administradores de Seguridad, Custodio de las Datos, las Unidades de Informática, Jefes de Servicio, Directores, Jefes de División, Jefes de Departamento y Gestión de Personas son responsables del cumplimiento de este procedimiento.
E
ES:

<!-- pág. 9 -->

_|
a
MÍ
Página9 de 28
PROCEDIMIENTO.
Notificación de un incidente de seguridad.
Todo el personal, incluidos funcionarios, personala honorarios y terceros, debe informar de manera inmediata cualquier debilidad, evento, incidente, amenaza o riesgo que pueda comprometer la seguridad de los activos de la organización. Para ello, el MINSAL dispone de los siguientes canales de comunicación únicos:
Contacto Telefónico:
o
+562)800 123573
Correo Electrónico:
o
Temastécnicos (requerimientos e incidencias): mdseminsal.cl.
o
Temas de seguridad (eventos, debilidades de seguridad, incidentes, amenazas, riesgos): seguridadticeminsal.cl.
Es obligatorio utilizar estos canales oficiales para garantizar una gestión oportuna, segura y eficiente de los incidentes reportados.
Gestión de Incidentes.
La institución llevará adelante la respuesta a incidentes a través de sus instancias técnicas y se coordinará con el equipo de respuesta a Incidentes y/o el Comité de Crisis, en la medida que el impacto de los incidentes afecte a los activos vitales de la organización.
Los problemas relacionados a los incidentes de seguridad de la información dentro de la organización serán manejados por el Encargado de Seguridad de la Información y Ciberseguridad, el que se apoyará en el personal equipo de respuesta a Incidentes y/o el Comité de Crisis, con atención al resguardo de los principios de la Política General y las leyes vigentes. A su vez, el Encargado de Seguridad de la información y Ciberseguridad mantendrá los contactos correspondientes con las autoridades, grupos de interés externos o foros que manejen los problemas relacionados con los incidentes de seguridad de la información.
Cabe destacar que en la medida que los incidentes hayan sidojudicializados, se requerirán de especiales cuidados, en orden a convocar a los expertos policiales para que accedana la información necesaria para la investigación.
(ENS
AA

<!-- pág. 10 -->

a alí
GÍA
| Versión:7
| TLP: BLANCO |
BLANCO
Reporte de eventosy debilidades en la Seguridad de la Información.
6.3.1 Flujo de la notificación.
E
A
Peporia porcores
S
al Encargado de
$---- seguridadticminsalo
A
Seguridad
S
Detecta un
Los
El
informa
i
vunerarilidadies
a
l
resultado del
plo
O
Á
a
a
z
Acciones preventivas
E
co.
Dad
e:
z
E:
E
o;
lá:
a
E
Y;
Contacta persona que
7 e
informa areas
a
al
reporia y Fecolecta
afectadas persona
informacion
A
que repona
E
E
NZ
0 incidente?
Registro Je
arnatisiz
Todo el personal de ambas Subsecretarías, en coordinación con su jefatura, es responsable de notificar cualquier tipo de evento que pueda afectar el funcionamiento normal del Sistema de Seguridad de la Información de la Institución.
Cada evento o incidente de relevancia se consignará en el sistema de tickets dispuesto por Minsal como herramienta central de registro y gestión de los incidentes, con objetivo central de concentrador y notificador de éstos, y, en consecuencia, disponer de un registro central de los incidentes.
En la herramienta centralizada de reporte y notificación de incidentes quedarán registradas también las actividades de administración de incidentes para poder evaluar los procesos involucrados (mejora continua) incorporandoa ella aprendizajes obtenidos ante errores y/o ciertos de los planes de acción ejecutados.
2QME
a
de los p
j
EN
mE YADO S'
Mi
a
SAS ES

<!-- pág. 11 -->

aEl
MN —muusteriooesaluo
1D:PROS-NC-07
Páginatide28
PAM
Esta función es importante para la institución, pues en la medida que los funcionarios están alertas a estos detalles se maximiza la vigilancia y resguardo de los activos institucionales.
En este sentido todos los funcionarios deberán siempre estar alertas tanto a los temas de respetoa las políticas de seguridad de la información como a señales que parezcan extrañas o poco habituales, teniendo en consideración que cada uno de ellos puede ser blanco u objetivo de un ataque cibernético mediante el cual se puede acceder ainformación personal o institucional relevante, entre la que destaca en primera instancia:
Credenciales o contraseñas.
Direcciones de correo electrónico.
Perfiles de usuario o gustos personales de compras y/o navegación web.
Información confidencial(documentos sensibles institucionales, tarjetas de crédito, entre otros).
Recursos del sistema (CPU, USB y disco externos), para almacenar malware o utilizar equipos institucionales sin autorización.
Según el impacto del evento, el Encargado de Seguridad de la Información debe contactar a la persona que reporta y Jefatura del área relevante en un plazo no superior a 24 h, para recolectar toda la información necesaria para el análisis del evento, registrando todos los antecedentes.
Hecha la recolección de información sobre el incidente, el Encargado de Seguridad de la Información y Ciberseguridad debe analizar los antecedentes. El resultado de dicho análisis puede tener las siguientes opciones:
a) Elevento no corresponde a una amenaza: se cierra el registro de eventos, informando a la persona que reportó.
b) El evento corresponde a una vulnerabilidad: se gestiona las actividades de mitigación (con los dueños de los activos comprometidos, el área o unidad de competencia y/o Comité de Seguridad), dejando registro de la gestión de la vulnerabilidad.
c) Elevento ocurrió y debe ser gestionado como incidente: se activa el proceso de Gestión de Incidentes de Seguridad.
Identificar Equipos/Áreas Resolutoras por tipo de Incidentes.
Se deben asociar Equipos particulares o Áreas generales, como resolutores para abordar incidentes según su naturaleza, lo que debe quedar documentado para servir de guía de asignación de los incidentes una vez declarados.
ER,
hd
h
n VI
Sl
sl
A
a

<!-- pág. 12 -->

Do”
MÍ) — MINISTERIODESALUD
Versión:7
Páginal2de28
MAN
Procedimiento para gestión de Incidentes.
A continuación, se presentan los procedimientos que debe ejecutar las Áreas Técnicas para cumplir con el resguardo de la plataforma y datos que le competen, de acuerdo con niveles de resolución dependiendo de la clasificación del Incidente de Seguridad.
6.4.1
Flujo General del proceso.
Dependiendo del impacto y severidad del Incidente, existirán tres niveles de escalamiento, de acuerdo con el siguiente flujo:
y
Ñ
1i
. Síoea ]
|¿O
Nipata Canada
EO
a
e_
o
d

<!-- pág. 13 -->

eie
: dl
1D: PROS - NC- 07
6.4.2
Flujo resolución de incidencias Nivel 1 y Nivel 2 iSP pure E Pa Aaa z
A
deere
N3
o
Prony
ER
de Cuss
6.4.3
Registro y Clasificación del Incidente.
e
Registro:
Y” La Mesa de ayuda, Resolutor Nivel 1 y el Encargado de Seguridad de la Información debe registrar el Incidente, según corresponda.
e
Clasificación:
Y” La Mesa de ayuda, Resolutor Nivel 1 y el Encargado de Seguridad de la Información, según corresponda, deben clasificar el incidente, de acuerdo con el origen, tipoy nivel de criticidad.
APME SS
S
e

<!-- pág. 14 -->

ae
A — MINISTERIODESALUD
ID:PROS-NC-07 | Versión:7
Páginal4de28
PAINT
6.4.4 Tipo de Incidente.
Tipo
Ejemplos
] Todos aquellos
E = Denegación de servicios computacionales S o lastecnologías dela" Código malicioso a) Informático ome ción "Accesos no autorizados a los sistemas de
| continuidad de las
E
operaciones
Infraestructura TIC
Po
Violacionesala confidencialidad, integridad |
| ptes aquellos
y disponibilidad (documento)
'b) Noinformático ESO Filtración de información reservada ae contempladosenel Incidentes provocados por la naturaleza
| punto anterior
Acceso físico no autorizado En general dependiendo del tipo de incidente los responsables de ejecutar la respuesta inmediata serían:
| =po de Activo eirds a, el
Jefatura responsable de la respuesta
Ñ i
| incidente
Ingea
Base de datos
| Formulario
asu
Departamento TIC
Infraestructura TIC
| Sistema
| Software
¡Documento
A
Departamento donde se desarrolla el proceso
Expediente
: Otros equipos
Departamento Administración y Servicios
Infraestructura física
E
Persona
Departamento de RRHH
ES
Pa
¿ VISKO
E
ES

<!-- pág. 15 -->

da >
Ó) — MINISTERIODESALUD
| Versión:7
Páginal5de28
MAIN
6.4.5
Nivel de criticidad.
Una vez que se recibe la información sobre las causas del incidente, identifica alternativas de solución y, en caso de que la solución implique costos, se debe cuantificarlos para gestionar su aprobación.
Asimismo,
deberá
registrarse
la
recopilada
(Anexo
N*%),
descripción,
responsables, análisis de la ocurrencia del incidente, tiempo de respuesta y solución al incidente, finalmente cuantificarymonitorear el tipo, volumen y costo del incidente. En caso de que haya implicancias legales o de otro tipo, deberá poner antecedentes en conocimiento de la División Jurídica y jefe de servicio para acordar curso a seguir. Toda respuesta a eventos y/o incidentes significativos deberá al menos incluir los siguientes aspectos para un mejor desempeño y atención del incidente:
Recopilar la evidencia lo más pronto posible después de la verificación;
Clasificar
el
de
acuerdo
con
su
tipo
de
taxonomía:
https://www.enisa.europa.eu/publications/reference-incident-classificationtaxonomy Clasificar la severidad del incidente de acuerdo con la siguiente tabla:
Bajo
Impacto bajo sobre los activos: daño desde la amenaza no tiene consecuencias relevantes.
Medio
Impacto medio sobre
los activos: daño desde la amenaza tiene consecuencias importantes.
Alto
Impacto
alto
sobre
los
activos:
daño desde
la amenaza
tiene
consecuencias graves sobre los activos.
Impacto muy alto: daño desde la amenaza tiene consecuencias catastróficas sobre los activos.
Crítico
Impacto crítico: daño desde la amenaza tiene consecuencias críticas y/o los procesos de negocio de la Institución.
Efectuar escalamiento Nivel 2, según la pertinencia y relevancia del incidente;
Asegurarse de que todas las actividades de respuesta se registren correctamente para el posterior análisis;
e
o
Ne
N

<!-- pág. 16 -->

PROCEDIMIENTO DE GESTIÓN DE INCIDENTES DE SEGURIDAD DE LA INFORMACIÓN
De”
inde
¡D: PROS- NC- 07
Comunicación de la existencia del incidente de seguridad de la información o cualquier detalle pertinente a otras personas u organizaciones internas o externas que deban ser informadas o advertidas sobre estos incidentes;
Manejar las debilidades de la seguridad de la información que causan o contribuyen al incidente;
6.4.6
Análisis y Evaluación de un Incidente de Seguridad Nivel 2 (Evaluación 2)
En el caso de que el incidente sea considerado por el evaluador nivel 2 como incidente relevante, este deberá realizar las siguientes actividades:
Analizar toda la información relevante recopilada.
Validar oreclasificar la severidad del incidente de acuerdo con la siguiente tabla:
Bajo
Impacto
bajo
sobre
los
activos:
daño
desde
la
amenaza
no
tiene
consecuencias relevantes.
Medio
Impacto
medio
sobre
los
activos:
daño
desde
la
amenaza
tiene
consecuencias importantes.
Alto
impacto alto sobre los activos: daño desde la amenaza tiene consecuencias graves sobre los activos.
Impacto
muy
alto:
daño
desde
la
amenaza
tiene
consecuencias
catastróficas sobre los activos.
Crítico
Impacto crítico: daño desde la amenaza tiene consecuencias críticas y/o los procesos de negocio de la institución.
Gatillar Respuesta Inmediata.
Iniciar cadena de custodia.
Realizar análisis forenses de seguridad de la información, según sea necesario;
Ejecutar Plan de Comunicaciones Interna.
Documentar
el incidente.
"Una vez que se ha manejado el incidente correctamente, se deberá cerrar y registrar formalmente.
SES
y
L,
Ea
A

<!-- pág. 17 -->

_|
iii
MÍ — MINISTERIODESALUD
Versión:
Página17 de 28
Este nivel establecerá los procedimientos de respuesta específicos que permitan de una manera ordenada, estandarizada, segura y eficaz, responder a estas anomalías en la seguridad institucional.
Todos los incidentes de seguridad, incluyendo los falsos positivos, que hayan sido evaluados por el nivel 2 deberán ser revisados mediante análisis post-incidente, para identificar el origen de este, sus posibles implicancias, impacto en la organización, estudio de tendencias de incidentes analizados, así como también con el propósito de realizar una mejora continua sobre las acciones de control realizadas por esta unidad.
En caso de que el incidente de seguridad sea considerado relevante (Nivel de severidad 3 o superior)y no haya podido ser resuelto, es decir, que el incidente pese al plan de respuesta inmediata aplicado NO esté bajo control, deberá activarse el Proceso de Gestión de Crisis (Ver procedimiento de Gestión de Crisis por Incidentes de Seguridad).
6.4.7
Respuesta Inmediata.
El responsable del o los activos involucrados designados para la respuesta inmediata del incidente es o son responsables del desarrollo de las siguientes acciones inmediatas:
Contener el daño y minimizar el riesgo Evitar que se propaguen los daños o efectos del incidente, coordinando las actividades necesarias para su disminución, probabilidad y consecuencia.
Reclasificar
el
si
fuera | Reclasificar según punto 6.4.5 necesario
Protección de evidencias Resguardar las evidencias recopiladas durante la gestión.
Notificacióna los organismos externos | Cuando sea necesario notificar a organismos externos como por ejemplo (carabineros, PDI, Bomberos, etc.).
Recuperación de los sistemas Contactar al administrador de el o los sistemas a fin de gestionar la recuperación de éstos.
Escalar con proveedores externos Contactar a los proveedores expertos en el Activo Vital y en conjunto con ellos se deberá gatillar el plan de acción para resolver el incidente a la brevedad posible.
Lu
al
e
py

<!-- pág. 18 -->

MTS — MINISTERIO DE SALUD
ID: PROS-NC-07
Compilación
y
organización
de
la | Recopilar todos los antecedentes relacionados con el documentación del incidente En esta etapa el Encargado de Seguridad de la Información debe entregar lineamientos para la respuesta ante un incidente.
6.4.8
Activación de resolución de incidencias Nivel 3.
Si un incidente se agrava en su nivel de severidad o impacto en las personas o procesos, la propiedady la infraestructura (Activos Ministeriales Vitales), y que además sea probable que continúe por un tiempo más prolongado de lo previsto, se entiende que este incidente pasa a ser una crisis y tratado de acuerdo con la siguiente organización.
Equipo de respuesta a incidentes y Comité de Crisis.
Elequipo de respuesta a Incidentes y el Comité de Crisis serán los responsables de la gestión de los Incidentes dentro de la organización. Sus principales responsabilidades son: acelerar los procesos para la toma de decisiones en la resolución de incidentes, definir las prioridades, establecer la estrategia, asignar recursosy táctica a seguir.
Este es presidido por la figura máxima con capacidad de decisión (responsable máximo del organismo y/o representante del Gabinete de Ministro/a o Subsecretarios/as. Junto con ello debetener representación y subrogante de alo menos las siguientes áreas del Organización:
Encargado de Seguridad de la Información y Ciberseguridad, Infraestructura Física, TIC (Operaciones, Infraestructura, Desarrollo, Explotación), Dueños de los Procesos, Recursos
Humanos, Finanzas, Jurídica y Comunicaciones. La gestión de crisis no es algo exclusivo del equipo de seguridad o tecnología, sino que implica a toda la organización.
Será el presidente del comité el responsable de definirsise está ante una crisis o no, su nivel de criticidad, definición de medidas y asignación de responsabilidades, así como los distintos responsables en cada caso, desde lo operativo para la contención y resolución del incidente, hasta la coordinación y comunicación que velará por la imagen de la institución, estableciendo la política de información, con los comunicados más adecuados y canales oportunos.
A continuación, se presenta un cuadro resumen de los actores del Comité de Crisis y sus responsabilidades:
RS
S
éS
y Y
Z,
W
_

<!-- pág. 19 -->

a
A
—miisTERIODESALUD
Página19 de 28
o:
Iniciala gestión de crisis y preside el comité de crisis.
CEO / Representante.
Delega responsabilidades.
Dirección General /
Presidente
Semantiene permanentemente informado.
Actúa como portavoz si las circunstancias lo exigen.
Es el primero en conocer el incidente y debe determinar nivel de criticidad (Impacto y Urgencia), si es preciso trasladarlo o no al comité de Crisis.
i
Sr aaqundaa Hola
Notifica al CSIRT de referencia.
Información
E
Determina cuáles son
las primeras acciones operativas para su:
contención.
Gestiona la continuidad de los servicios, utilizando según sea el caso, los respaldos o sitios de contingencia para los servicios críticos.
Revisa el entorno común de todas las aplicaciones (comunicaciones,
TIC
firewall, DNS, etc..), así como los específicos de cada aplicación.
Gestionará de forma rápida servidores virtuales en caso de ser necesario.
Activar Política de copias de seguridad.
PMO o Encargado del
Coordinar con los proveedores todas las acciones de contención,
Proyecto
erradicación y cierre de los incidentes.
E
Determina las responsabilidades legales directas provocadas por el i
Jurídica
Da seguimiento a las acciones a seguir de acudo a la leyes y normas aplicables.
Orienta sobre todos los asuntos legales.
Integra el Comité de Crisis y adopta el Manual de comunicaciones de crisis previamente elaborado.
Decide cuáles son los mensajes clave, el formato y canal más adecuado,
Comunicaciones
en función de los grupos de interés.
"Activa el seguimiento y percusión de la crisis en los diferentes medios de comunicacióny redes sociales.
Mantiene contacto con los medios de comunicación.
Administración y
Analiza los recursos necesarios para la resolución de la crisis.
Finanzas
Recopila información, evalúa los hechos y plantea opciones.
Mantiene comunicación con las compañías aseguradoras (si aplica).
A:
II
AA
IO
EA
A
A,
(tm
P
Y

<!-- pág. 20 -->

db =
1D: PROS - NC- 07
Infraestructura Física Portavoz ante los funcionarios y en caso de ser aplicable, los representantes.
i
Gestiona las acciones operativas en caso de incidentes relacionados con personas.
Recursos Humanos
o
o
Comunica, llegado el caso, con los afectados y facilita información o asistencia básica(por ejemplo, en caso de una lesión de un funcionario).
"Evalúa el ánimo de los funcionarios y recomienda acciones para evitar decaimiento o una evolución no prevista.
Declaración del Nivel de crisis y equipo responsable según el nivel de criticidad (Impacto y Urgencia):
Gestión Operativa
Comité de Crisis
Ñ f
Te
hi
E
BAJO
MEDIO
ALTO
MUY ALTO
CRITICO
Declaración qe
hi
z
ité
No requiere Comiéde lo, á isis Requiere Comite de Crisis o j pue decesión 1
70]AE
A Ep
Le A, preside e CibesJEncrgado
Preside Representante
E
ierno
de
Crisis
a
escon
argado
área |
dE
Presias Representante
Ñ
noeEno
, Tic y Negocio
de Seguridad
de Seguridad
Dirección
E
Ante incidentes con peligrosidad baja y media no deberían requerir la convocatoria de un Comité de Crisis, porque no se encuentra ante una situación que se pueda definir como tal.
Bajo la responsabilidad de directa del Encargado de Ciberseguridad, los equipos técnicos tienen el conocimiento para solucionar el problema en el nivel operativo.
Ol
5 VO
e
2yy

<!-- pág. 21 -->

dE
El
MINISTERIO DESALUD
En función del nivel del incidente actuarán distintos niveles o actores del Comité de crisis y procedimientos a seguir:
Atributo
Nivel de criticidad
Bajo
Medio
Alto
Muy Alto
Crítico
pecateción de
NO
NO
OPCIONAL
Ss
s|
Crisis
Ss
Nivel
a
No requiere
No
requiere
comité de crisis
Comité de Crisis
Ámbito de
Estratégico
Gestión
/Gobiernode
Responde equipo
Responde
Preside el
Preside el
crisis
Operativo
Encargado
Área
Preside
TIC y Negocio
Seguridad /Ciber
Seguridad /Ciber
HoESEiS
Dirección
PROCEDIMIENTO GESTIÓN DE
Procedimiento
INCIDENTES DE SEGURIDAD DE LA PROCEDIMIENTO GESTIÓN DE CRISIS
INFORMACIÓN
Proceso Disciplinario.
Si elincidente es de mayor gravedad o se sospecha la comisión de algún delito, el Comité de
Seguridad de
la
Información, asesorándose por el integrante de la
División jurídica
designado para las materias de Seguridad de Información, informará al Jefe Superior del Servicio y, de precisarse, a carabineros, bomberos, ambulancias, Ministerio Público, etc.
En el caso que existan eventuales responsabilidades administrativas, y dependiendo de la gravedad del incidente, el Comité de Seguridad de la Información solicitará a quien corresponda la instrucción de un procedimiento disciplinario para la investigación de las eventuales responsabilidades en los términos previstos en el Estatuto Administrativo.
Cuando el incidente involucre a personal contratado a honorarios o terceros, se evaluará solicitar el término anticipado del contrato o, en caso de que exista, la aplicación de la sanción que establezca el propio contrato, Política General de Seguridad de la Información u otras políticas ministeriales para el incidente detectado.
e
Si

<!-- pág. 22 -->

Continuidad de la Seguridad de la Información.
En caso de que el incidente no pueda ser controlado y ponga en riesgo las operaciones y entrega de productos y servicios del Ministerio, el Comité de Seguridad de la Información, evaluará la activación de los procesos de continuidad del negocio (Ver procedimiento de Gestión de Crisis por Incidentes de Seguridad, Política de Seguridad para la Continuidad).
Recolección de evidencia.
La recolección de
la evidencia es responsabilidad del responsable del activo involucrado, designado para la resolución del incidente, la que debe ser reportada al Encargado de Seguridad para su revisión, ésta debe ser clara y suficiente. Para ello se deberá:
Paralos documentos en papel:
Y” Se debe levantar inventario de los documentos.
El original es incluido en la cadena de custodia, y se guarda de manera segura con un registro del individuo que encontró el documento, dónde y cuándo fue encontrado el documento, y quién fue testigo del descubrimiento. En cualquier investigación se debe asegurar que los originales no son alterados.
Y” Para los análisis se utilizarán copias numeradas de circulación controlada.
Parala información sobre medios computacionales:
El proceso se inicia con la generación de una imagen espejo en presencia del ministro de fe de la institución. Se levanta inventario y se inicia la cadena de custodia.
Y” Elolos archivos originales y copias espejo se deben guardar de manera segura e intactos (se utilizan mecanismos de protección e incluso encriptación para que nadie adultere la evidencia).
Y” En el caso de que no sea factible aislar y sacar de producción el original, la copia 1 será considerada original a estos efectos, en la medida que se resguarde el procedimiento anterior.
Y” Las imágenes o copias espejo (dependiendo de los requisitos aplicables) de cualquier medio removible, información en discos duros o en memorias, deben ser numeradas y retenidas para asegurar su disponibilidad.
Y” De todas las operaciones de análisis sobre estas copias se levantará acta identificando las personas que las manipulan, detalle de las operaciones realizadas y sus hallazgos o resultados.
Y” El registro de todas las acciones durante el proceso de copiado se debería guardary el proceso se debería efectuar ante testigos.
US

<!-- pág. 23 -->

Ml PROCEDIMIENTO DE GESTIÓN DE INCIDENTES DE SEGURIDAD DE LA INFORMACIÓN
DE
A — MINISTERIO DE SALUD
1D:PROS-NC-07
Cualquier trabajo forense se debe realizar sólo sobre copias del material de evidencia. Se debe supervisar y registrar cuándo y dónde fue ejecutado el proceso de copiado, quién realizó las actividades de copiado y qué herramientas y programas se han utilizado.
Si corresponde esta evidencia debe ser entregada al Comité de Seguridad de la Información para la evaluación de procesos disciplinarios.
6.10
Comunicacióna los involucrados.
Una vez contenido el incidente, el Encargado de Seguridad de la Información debe informar a los involucrados en el Incidente.
6.11
Análisis de causay cierre del incidente.
En esta etapa el Responsable del activo, designado para la resolución del incidente debe:
Realizar un análisis de las causas del Incidente.
Cuando el incidente no esté cerrado, seleccionar e implementar un plan de acción adecuado, además de definir el plazo para su implementación, dejando registro de las actividades.
El seguimiento de este plan será responsabilidad del Encargado de Seguridad de la Información.
Registrar el cierre del Incidente en un informe de cierre del incidente.
6.12
Aprender de los incidentes en la seguridad de la información A lo menos cada seis meses el Encargado de Seguridad de la Información, debe revisar los incidentes de seguridad del período analizando:
Posibles tendencias.
Eficacia de los tratamientos implementados.
Cuantificación de los tipos, volúmenes y costos de los incidentes de seguridad.
Incidentes recurrentes o de alto impacto.
Problemas subyacentes y medidas correctivas desarrolladas.
Necesidades de mejorar o implementación de nuevos controles para limitar la frecuencia, daño y costo de futuras ocurrencias.
Con los antecedentes aportados por esta revisión, el Encargado de Seguridad de la Información debe proponer al Comité de Seguridad de la Información medidas que sean necesarias para que no vuelvan a ocurrir, además de detectary promover los aprendizajes de cada uno de ellos.
ANSa ES
e
e

<!-- pág. 24 -->

_|
D ea
7 PLAZOS DE NOTIFICACIÓN DE INCIDENTES DE SEGURIDAD.
De acuerdo con lo establecido en la Ley N” 21.663, Ley Marco de Ciberseguridad, se deben reportar al CSIRT Nacional los incidentes de ciberseguridad o ciberataques que puedan tener efectos significativos.
Todo incidente de seguridad debe ser notificado dentro de los siguientes plazos:
Dentro de las 3 horas siguientes a conocer el incidente, se debe enviar una alerta temprana.
Dentro de las 72 horas, se debe enviar una actualización con la evaluación inicial del incidente, su gravedad e impacto.
Dentro de los 1b días corridos, se debe enviar un informe final sobre el incidente y las medidas adoptadas.
Nota: Se deberán informar a CSIRT Nacional aquellos Incidentes que provoquen la interrupción de la continuidad de un servicio esencial, afectar la integridad física o la salud de las personas, afectar sistemas informáticos que contengan datos personales.
El incumplimiento de estos plazos será considerado una falta grave, de conformidad con las normativas internas y los estándares legales, y podrá derivar en acciones disciplinarias o contractuales según corresponda.
REGISTROS:
Registros cadena de custodia Registro de análisis de incidentes.
Registro de gestión de vulnerabilidades.
Acta de análisis de hallazgos Planilla registro de incidentes.
Plan de acción.
Informe de incidentes.
Registro de cumplimiento del deber de notificar incidente Registro de cumplimiento de obligación de denuncia (si procede)
Registro de Evidencias.
DIFUSION:
La comunicación
del
presente procedimiento se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, alo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en la intranet de Minsal http://isalud.minsal.cl/
Correo informativo.
Publicación en sitio web Minsal http://www.minsal.cl/seguridad_de_la_informacion/
FAME
ja
Sl
o 20 -,
S

<!-- pág. 25 -->

_|
Sistema de Gestión de Seguridad de la información - Nivel Central
10 PERÍODO DE REVISIÓN.
El presente procedimiento deberá ser revisado cada dos años o cuando ocurran cambios significativos para garantizar que:
o
Sigue siendo adecuado para su propósito y preciso.
o
Refleja los cambios en las tecnologías.
o
Está alineado con la legislación vigente, los estándares internacionales y las mejores prácticas.
11 EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA.
En situaciones excepcionales, el Jefe de Departamento TIC, el CISO o el Comité de Seguridad de la Información tendrán la facultad de evaluar y establecer condiciones específicas para la excepción al cumplimiento de las directrices establecidas en esta política, siempre que tales excepciones no infrinjan la legislación vigente ni comprometan la seguridad de la información.
Cada excepción deberá ser debidamente documentada, y se deberá iniciar un proceso de revisión de la política en el que se determinará si es necesario incorporar directrices adicionales o realizar modificaciones específicas.
12 CONTROL DE VERSIONES:
Versión
Fecha
Pág. o Sección modificada
Motivo delcambio
Diciembre
N/A
Creación del documento
Octubre
ti
los
flujos
2014
Puntos: 6-1, 6.2
| A
| Se define como vía de contacto
A | Soportefminsalel
Octubre 2017
| Todo el documento
| Se actualiza:
Formato del procedimiento.
Diagramas de flujo.
Se reemplaza el uso de planilla de registro por el aplicativo de gestión de incidentes.
Se
modifican
los
registros
del
procedimiento.
Octubre 2019 |Todo el documento [Seactualiza:
Alcance del documento.
¡Correo de contacto para informar a a su Documento Controlado. Prohibida su reproducción parcial ototal sin autorización.
fe

<!-- pág. 26 -->

MA
misterioDESALUD
| ID:PROS-NC-07 | Versión:7 | Página26de28
PANAMA
Versión
Fecha
Pág. o Sección modificada __
Motivodelcambio
a
¡Flujos puntos 6.1 y 6.2.
¡Punto 6.2.5.
Punto 7.
E
Punto 8.
Registros.
Responsabilidades
A
Agosto 2021 Todo eldocumento.
Clasificación de losincidentes, según su nivel y responsables de la gestión.
Noviembre
Pag.2,3,4,5,6, 24, 25,
Actualización
Normativa
ISO:
2027
127.001:2022 y
2 Alcance:3 Terminolegía;4 Normativa de
Gobierno.
sobre
Normativa;s
Roles
y c'Perseguridad
Responsabilidades; 7 Plazos
Notificación;
Periodo
AA
Revisión; 11Excepciones, _
| a. EN
Mi
Ad
us
o*
o
he

<!-- pág. 27 -->

_|
a E
er
1D: PROS
- NC- 07
### 13. ANEXOS
Anexo 1: Datos mínimos que deben ser registrados en el informe de incidentes.
Campo
Campo
Estado
"Estado del
Responsable de
| Responsable de la Acción
| Incidente (Abierto,
la Acción
E
| Acciones
: Inmediatas,
- Acciones
correctivas /
| Preventivas,
: Cerrado)
: Número de Evento
Acción
Descripción de las
: / Incidente
[Inmediata
acciones inmediatas
E
realizadas para contener el
Origen
Origen del Evento /
Fecha Acción
Fecha Acción inmediata : Incidente inmediata
Fecha Reporte
| Fecha Reporte
Hora Acción
Hora Acción Inmediata e
Hora Reporte
Hora Reporte
E
Se activa
Indicar si se activa la
|Continuidaddel | continuidad del negocio
Negocio(S/N)
Identificación de quien
| Datos de la
Registros y
Identificación de los reporta
| persona que
evidencia
registros y evidencias que
| reporta (nombre,
E
respaldan el proceso
cargo,
E
disciplinario
- organización,
¡ datos de contacto)
E
Activos / Sistemas
Descripción de los
Análisis de
Registrar las causas de raíz afectados
| activos oSistemas
causas
que produjeron el Incidente : afectados(N*de
- serie, marca, tipo,
- soporte, etc.)
Corresponde a un
Indicar si
Acción
Acciones correctivas O
Incidente o Debilidad
- Correspondeaun
Correctiva/
preventivas realizadas para
- Incidente o
Preventiva
eliminar las causas de raíz
Debilidad
del incidente
PNA
o
ST
ES

<!-- pág. 28 -->

de E”
MA
Versión:7
Página28de28
PAINT
Tipo de Incidente
| Indicar el Tipo de
Costos
Costos asociados al
- Informático
(NI)No
- Incidente
Asociados
Informático”
Nivel de criticidad
E Registrar el nivel
E
Respuesta y
Resumen de las
: de criticidad en
Cierre
actividades de cierre del ' base ala urgencia incidente y conclusiones pe impacto
Descripción del
. Descripción del
Fecha Cierre
Fecha Cierre
Registro de Evidencias
| Identificación de
los registros y
| evidencias que
e
: respaldan las
- acciones
- realizadas
i
laVGA 5
Ly