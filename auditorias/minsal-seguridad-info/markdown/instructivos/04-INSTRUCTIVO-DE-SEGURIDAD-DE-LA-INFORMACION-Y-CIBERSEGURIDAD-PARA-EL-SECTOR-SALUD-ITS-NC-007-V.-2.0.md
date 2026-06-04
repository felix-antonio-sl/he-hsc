<!-- pág. 1 -->

Po] Ministerio de
Salud
e
INSTRUCTIVO DE SEGURIDAD DE LA INFORMACION Y CIBERSEGURIDAD PARA EL SECTOR SALUD
ITS-NC- 007
Versión Oficial v 2.0 - Abril 2025 gro Le
S
Ñ
ENCARGADO
S DE SEGURIDAD
INFORMACIÓN
v
CIBERSEGURIDA,
Responsable
Fecha
irma
Pablo Fabres F. - José Villa C.
Elaborado
Unidad de Seguridad de la Información y
Marzo 2025
SÍ
l
José Villa C.
al RIDE
Revisado
Encargado de Seguridad dela Informacióny non1202 Qe
A
SA
lO
orge
Herrera
R.
der
_FEENOLOGÍAS DE LA
Aprobado
Jefe Departamento
de
Tecnologías
de
Abril 2025
144 INFORMACIÓNy
eS
Inf
ión
yComunicaciones
Y
COMUNICACIONES 2
nformación y
y S,
E
F
E
SN
Le
EDEN

<!-- pág. 2 -->

INSTRUCTIVO
DE SEGURIDAD DE LA INFORMACIÓN YCIBERSEGURIDADPARA
EL SECTORSALUD|
q
MA
Página 1de 79
LES
n
po
at,
A
E
_
Mi
o
L
eo
rg

<!-- pág. 3 -->

MÍ
tmustenonesacuo | ts-nc-007 | versiónizo |  Páginazde7s
IMBNNAN
Resumen
La acelerada transformación digital del Estado y la creciente adopción de tecnologías avanzadas en el Sector Salud han traído consigo importantes beneficios en términos de eficiencia y acceso. Sin embargo, también han aumentado de manera alarmante la exposición a riesgos y la ocurrencia Incidentes de ciberseguridad, afectando la continuidad operativa de sistemas y la exposición de datos. Dada la importancia de los sistemas de salud y la alta sensibilidad de la información relacionada, es fundamental garantizar una protección prioritaria e ineludible de activos críticos para nuestro sector.
Como antecedente, el Instructivo de Ciberseguridad que fue aprobado mediante la Resolución Exenta N? 785 el 03 de noviembre de 2021 marcó un hito para el sector en esta materia. Sin embargo, con la evolución de la tecnología y las modificaciones legales y reglamentarias surgen nuevos desafíos, que demandan su actualización.
Entre los desafíos técnicos, se pueden mencionar:
la expansión de la telemedicina, la Interoperabilidad de los sistemas, el uso creciente de dispositivos médicos conectados a
Internet
(loT)
la dependencia de proveedores a través de la cadena de suministros, el aumento de los servicios en la nube a través de estrategias híbridas o multicloud, la incorporación de la Inteligencia Artificial en procesos clínicos, la a estandarización e interoperabilidad segura de datos entre los sistemas de salud, la urgencia de fortalecer una arquitectura de seguridad sólida que esté alineada con la Arquitectura de Referencia del Minsal, dada la creciente sofisticación de las amenazas.
A ello se suma los avances de la Ley sobre Transformación Digital del Estado que conlleva la digitalización de los trámites y procedimientos administrativos, lo que involucra desafíos adicionales, en materia de interoperabilidad, en la puesta a disposición de servicios a usuarios finales y gestión de riesgos informáticos que conlleva.
En el ámbito normativo, destacan la entrada en vigor de la Ley N* 21.663, ley Marco de Ciberseguridad y sus reglamentos y demás normas complementarias, que mandatan el establecimiento de normas, instrucciones y directrices de ciberseguridad que sean aplicables a las instituciones que se encuentren bajo el ámbito de cada una de las respectivas competencias institucionales y la ley N* 21.459 que establece normas sobre delitos informáticos, deroga la ley N” 19.223 y modifica otros cuerpos legales con el objeto de adecuarlos al Convenio de Budapest.
En este contexto se pone a disposición de la Red, el nuevo Instructivo de Seguridad de la Información y Ciberseguridad para el Sector Salud, el cual tiene carácter de obligatorio para las instituciones del ecosistema del Ministerio de Salud (Minsal).
EN
Este documento tiene como objetivo principal es, establecer lineamientos, directrices y 6 controles de seguridad que deben ser adoptados por estas instituciones, promoviendo una AE gobernanza de ciberseguridad coordinada en todo el sector, fomentando la adopción de prácticas modernas, sobre los nuevos desafíosy la protección de los derechos de las personas
A

<!-- pág. 4 -->

MN
Versión:20
Página3de79
en el entorno digital, lo cual es fundamental para proteger los sistemas críticos, mantener la integridad de la información y garantizar la continuidad operativa en el Sector Salud, todo lo anterior en línea con estándares internacionales de seguridad.
El cumplimiento de los lineamientos previstos en este instructivo permitirá dar cumplimiento a la legislación nacional vigente y fortalecer la resiliencia del Sector Salud frente a las amenazas cibernéticas.
A
VISADO
S.
oy
rs
ES

<!-- pág. 5 -->

de E
Moo.mez.
| scr | sezo | veses
RENE
INDICE
ELEMENTOS CLAVES PARA LA GESTIÓN DE LA SEGURIDAD DE LA INFORMACIÓN.........7 IMPLEMENTACIÓN SGSI PARA LA SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD ARQUITECTURA DE LA SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD.............18 RESPUESTA ANTE INCIDENTES DE SEGURIDAD DE LA INFORMACION Y
CIBERSEGURIDAD, CONTINUIDAD OPERACIONAL.........ocóicación:occorcooccoccoconocooncocononorcoscoocoonoc1 CIBERSEGURIDAD EN DISPOSIMWOS MEBICOS OTE a ccomocccoccrconocccnoccncoconoracnacar.19 INNOVACION Y TENDENCIAS EN CIBERSEGURIDAD .......oocccccoccccccnccccnccorncccocanicocananacanDÁ CAPACITACION Y CONCIENTIZACION EN CIBERSEGURIDAD .......coococcnncccnncccncoccnnorcnanacIZ INDICADORES DE SEGURIDAD DE LA INFORMACION Y CIBERSEGURIDAD ....................85
A
Ministerio de Salud - Departamento deASES

<!-- pág. 6 -->

se
MA
—VINISTERIODESALUD
Versión:20
Página5de79
INTRODUCCION
El Sector Salud, al manejar información altamente sensible y se operan sistemas críticos para la atención de la población. Salud se encuentra entre los sectores más vulnerables ante estas amenazas. Ataques dirigidos, brechas de datos, interrupciones de servicios y vulnerabilidades explotadas a través de terceros representan riesgos reales que pueden afectar gravemente la confidencialidad, disponibilidad e integridad de la información sanitaria. Casos emblemáticos a nivel internacional, como el ataque a SolarWinds, y experiencias recientes en organismos públicos nacionales han evidenciado la necesidad urgente de reforzar los mecanismos de protección y gobernanza de la información.
En este contexto, en cumplimiento de lo establecido en la Ley Marco de Ciberseguridad N?
21.663, y en concordancia con la Política Nacional de Ciberseguridad y los estándares de seguridad emitidos por la Agencia Nacional de Ciberseguridad (ANCI), el presente Instructivo de Seguridad de la Información y Ciberseguridad para el Sector Salud tiene carácter obligatorio y establece los lineamientos, directrices y controles que deben ser adoptados e implementados por todas las entidades que integran el ecosistema del Ministerio de Salud (Minsal)!.
Esto incluye, de manera explícita a las Secretarías Regionales Ministeriales (Seremis), los Servicios de Salud, los Hospitales de Alta y Mediana Complejidad, los Establecimientos de Atención Primaria y demás organismos públicos o autónomos del sector que se encuentren bajo su dependencia o relación administrativa.
l
La adopción de estas directrices surge del mandato legal de la Ley Marco, que establece la necesidad de crear normas, instrucciones y directrices de ciberseguridad que sean aplicables a los órganos de la Administración del Estado, dentro del ámbito de sus competencias. Esto asegura una gestión que sea coordinada, eficaz y alineada con los estándares internacionales.
Cumplir con estas directrices es fundamental para proteger los sistemas críticos, mantener la integridad de la información y asegurar la continuidad operativa en el Sector de Salud.
### 2. PROPÓSITO
El presente Instructivo de Seguridad de la Información y Ciberseguridad para el Sector Salud establece los lineamientos, directrices y controles de seguridad que deben ser adoptados por las instituciones que integran el ecosistema del Ministerio de Salud (Minsal), Seremis, Servicios de Salud, Hospitales, Establecimientos de Atención Primaria y demás Organismos
Autónomos del sector.
ME
Este instructivo considera lo previsto en la Ley N” 21.663, que establece un marco de
Sismo:
ciberseguridad para fortalecer la protección de la información crítica, asegurar la continuidad
A
operativa y mejorar la resiliencia de los sistemas de información.
* Ley 21.663 Artículo 26.
AA

<!-- pág. 7 -->

INSTRUCTIVO DE SEGURIDAD DE LAINFORMACIÓN Y CIBERSEGURIDAD PARA ELSECTOR SALUD ae
MÍ
misterio nesacuo | trs-n0c-007 | versiómzo | Páginacde7o
IEA
También incluye las disposiciones de la Ley N* 21.180 sobre la Transformación Digital del Estado, lo que garantiza la seguridad en la digitalización de los procesos administrativos y la interoperabilidad segura entre diferentes instituciones.
Además, se alinea con las mejores prácticas de estándares internacionales de seguridad, como ISO/IEC 27001:2022 e ISO/IEC 27002:2022 para la gestión de la seguridad de la información; NIST SP 800-53 y el NIST Cybersecurity Framework (CSF) para la gestión de riesgos y controles de ciberseguridad; CIS Controls v8 para implementar medidas de protección efectivas; y HIPAA (Health Insurance Portability and Accountability Act) para asegurar la seguridad, privacidad y confidencialidad de la información de salud en entornos digitales, entre otros.
El propósito principal de este instructivo es reforzar la seguridad y la privacidad de la información en los sistemas tecnológicos y servicios del sector salud, mediante lineamientos que permitan minimizar los riesgos de afectación a la confidencialidad, integridad, disponibilidad y trazabilidad de los datos, en estricto cumplimiento de la Ley N* 19.628 sobre Protección de la Vida Privada, así como su actualización a través de la Ley N* 21.719 sobre Protección de Datos Personales, la ley N” 20.584 y sus modificaciones, introducidas por la Ley N? 21.541 sobre Telemedicina y la Ley N? 21.668 sobre Interoperabilidad de Fichas Clínicasy las normas reglamentarias que desarrollan estas leyes.
Este instructivo es obligatorio y establece las pautas, directrices y controles técnicos y administrativos que todas las Instituciones del Sector Salud deben seguir e implementar.
También se alinea con la normativa actual del Minsal, especialmente con la Política General de Seguridad de la Información y Ciberseguridad, que fue aprobada por la Resolución Exenta N*
1465/2023. Esta política ofrece un marco de referencia y directrices que buscan proteger de manera integral y efectiva la información y los sistemas tecnológicos de las instituciones, cumpliendo con los estándares internacionales y las exigencias legales nacionales.
### 3. ALCANCE Y APLICABILIDAD
3.1. Alcance
Este instructivo es aplicable a todas las Instituciones del Sector Salud, esto incluye:
e
Ministerio de Salud.
e
Subsecretarías de Salud Pública y Redes Asistenciales.
. Ss Regionales Ministeriales (SEREMI)
PTE
+ Servicios de Salud y sus respectivos establecimientos hospitalarios.
A
+ Centros de Atención Primaria de Salud (APS).
e
Organismos Autónomos de Salud.
e
Entidades externas que operen o administren sistemas de información en salud.
A

<!-- pág. 8 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD PARA ELSECTOR SALUD a MÍ tusremovesacuo | tisnc-007 | versiómzo |  Págine7aezo
MQNRETAIES
3.2. Aplicabilidad
El cumplimiento de este instructivo es esencial para todas las instituciones del sector salud que manejen, procesen o almacenen información sensible, así como para los proveedores de servicios tecnológicos que colaboren con este sector. A estos efectos, todos los procesos de l compra que se realicen por instituciones del sector, deberán contener la obligación del proveedor de ceñirse a los lineamientos previstos en este instrumento.
Las pautas establecidas deben aplicarse en:
e
Infraestructura tecnológica: redes, servidores, plataformas en la nube y dispositivos conectados.
e
Sistemas de información: software de gestión clínica, registros clínicos electrónico (RCE]), sistemas de telemedicina, bases de datos, entre otros.
e
Gestión de accesos: autenticación, control de privilegios y monitoreo de actividad en los sistemas.
e
Protección de datos sensibles: cifrado, seudonimización. anonimización y resguardo de la información de pacientes y profesionales.
Gestión de incidentes de ciberseguridad: detección, respuesta y mitigación de riesgos conforme a marcos normativos y estándares internacionales.
### 4. ELEMENTOS CLAVES PARA LA GESTIÓN DE LA SEGURIDAD DE LA INFORMACIÓN
4.1. Gobernanza
La gobernanza en ciberseguridad se refiere al conjunto de decisiones, directrices y controles que la alta dirección implementa para garantizar que se cumplan los objetivos estratégicos de la institución. Esto no solo apoya la misión organizacional, sino que también ayuda a gestionar los riesgos que podrían poner en peligro su consecución.
En este contexto, la Ley N” 21.663 sobre Ciberseguridad, publicada en abril de 2024, establece que las instituciones públicas deben implementar una estructura de gobernanza que asegure una gestión eficaz para proteger sus sistemas críticos de información.
Por su parte el NIST Cybersecurity Framework 2.0 (CSF 2.0), destaca que la función de gobierno permite que la alta dirección comprenday gestione los riesgos de ciberseguridad en relación con la estrategia organizacional, enfocándose en cómo estas amenazas pueden afectar los objetivos institucionales.
Adicionalmente, la ley N* 21.459 que establece normas sobre delitos informáticos, deroga la ley N* 19.223 y modifica otros cuerpos legales con el objeto de adecuarlos al Convenio de na Budapest exige contar con un marco de gobernanza de la seguridad de la información que
MISADO
permita a
la institución detectar, obtener evidencias y denunciar oportunamente los
AS
incidentes de seguridad de la información que sean producto de acciones que pudieran revestir caracteres de delito.
NN TO

<!-- pág. 9 -->

a,
MÍ
——MINISTERIODESALUD
Página8 de 79
En este contexto y con el objetivo de fortalecer la cultura de seguridad en nuestra institución, es fundamental implementar medidas concretas que aseguren una gobernanza efectiva en cuanto a la Seguridad de la Información y la Ciberseguridad en todos las Instituciones del sector relacionados con el MINSAL.
Esto implica que las instituciones del sector salud deben:
e
Designar a un responsable de ciberseguridad, encargado de coordinar la gestión de riesgos y el cumplimiento normativo.
Implementar políticas y procedimientos de seguridad, alineados con estándares nacionales e internacionales.
e
Conformar Comités de Seguridad de la Información, Ciberseguridad y Protección de Datos Personales, que supervisen la ejecución de estrategias de seguridad y la respuesta ante incidentes.
e
Establecer roles y responsabilidades claras, garantizando una adecuada asignación de funciones dentro de la organización.
e
Implementar una estrategia de monitoreo continuo y mejora de capacidades de ciberseguridad, incluyendo auditorías, capacitaciones y simulacros de respuesta a
4.2. Compromiso del Nivel Directivo El compromiso de la alta dirección es fundamental para el éxito de cualquier estrategia de ciberseguridad. Este compromiso se manifiesta en la creación e implementación de políticas institucionales, que son declaraciones claras de intenciones y directrices estratégicas en el ámbito de la seguridad de la información.
Un ejemplo a nivel nacional es la Política Nacional de Ciberseguridad, que ha contado con el respaldo de tres presidentes de la república, quienes han actuado como patrocinadores de alto nivel, impulsando reformasy medidas clave para mejorar la seguridad digital del país. Este tipo de compromiso debería ser replicado en cada organización, tanto del sector público como del privado.
Por su parte, la Ley N? 21.663 establece que las "Autoridades y directivos de las instituciones tienen un rol fundamental en la gobernanza de la ciberseguridad, debiendo asumir un compromiso activo y vinculante en la gestión de riesgos y protección de la infraestructura crítica”, compromiso que implica:
Incorporar la ciberseguridad en la estrategia institucional, garantizando su alineación con los objetivos organizacionales.
Asignar recursos suficientes y adecuados, incluyendo talento humano, tecnologías y
LE
programas de capacitación.
velos
Fomentar
una
cultura
organizacional
de
seguridad,
mediante
campañas
de
concienciación, liderazgo visible y formación continua.
Í
Supervisar y evaluar regularmente el cumplimiento de las políticas y la eficacia de los controles de seguridad.
A

<!-- pág. 10 -->

a
zm
e
Adoptar un enfoque integral frente a incidentes, priorizando la prevención, detección oportuna y mitigación de impactos.
El compromiso de la dirección no solo refuerza la capacidad de la institución para enfrentar amenazas, sino que también legitima y promueve la implementación de una gobernanza sólida en ciberseguridad.
4.3.
Estrategia de Seguridad y un Plan Director de Seguridad La importancia de usar las tecnologías de la información y comunicación (TIC) de manera responsable no puede subestimarse. Con el aumento de los riesgos y amenazas, como los ciberataques que hemos visto en los últimos años, es crucial que estos escenarios sean controlados y monitoreados de manera profesional, siguiendo normas y mejores prácticas, ya que los procesos de negocioy los servicios de las organizaciones dependen en gran medida de las TIC.
Para resguardar los activos de información y garantizar la continuidad de servicio se debe implementar un conjunto de acciones que gestionen la seguridad de la información y la ciberseguridad en el sector salud, de manera proactiva, para crear un entorno sólido que prevenga cualquier afectación a los servicios informáticos.
En cumplimiento de estos imperativos, la estrategia de seguridad de la información y la ciberseguridad de Minsal queda establecida en su Plan Director?, el que, en línea con los intereses estratégicos de la organización, con un enfoque basado en riesgos y siguiendo los estándares de la industria en esta materia, aborda una serie de iniciativas en apoyo al resguardo de la información, de los activos digitalesyprocesos tecnológicos que son cruciales para las operaciones del Minsal, para crear condiciones de base que otorguen confianza digital en la organización.
Adicionalmente, para llevar a cabo una implementación efectiva de la seguridad de la información y la ciberseguridad en las Instituciones del Sector Salud, se requiere del compromiso individual de la alta dirección de quienes la conforman en su totalidad.
Para ello, es importante que deban tener en cuenta las siguientes consideraciones clave:
Sponsor directivo: Se debe designar un representante de la alta dirección de la institución, con atribuciones suficientes para garantizar el alineamiento de los objetivos de la política de seguridad de la información con el cumplimiento de objetivos estratégicos organizacionales, el carácter vinculante de los lineamientos que se establezcan y la correcta atribución y comunicación de los roles y responsabilidades relacionados con la seguridad de la
ME
O:
ES
o =E
? Plan de Seguridad de la Información y Ciberseguridad para el Sector de Salud (años 2024-2025), aprobada mediante Resolución Exenta N*“969/2024o el vigente.
es

<!-- pág. 11 -->

s
MÍ
rusteronesacuo [| is-nc-007 | versión:zo | Páginaiode7o
PENN
Garantizar recursos adecuados:
La alta dirección de la institución debe asegurar que se asignen los recursos necesarios para respaldar la de la y ciberseguridad, considerando recursos financieros, tecnológicos y humanos.
Compromiso de
instituciones del sector:
Es
esencial
obtener
la
participación
y
el
compromiso activo de las instituciones del sector, su colaboración no solo contribuirá a la eficacia del sistema de gestión de la seguridad de la información y ciberseguridad a nivel sectorial y nacional, sino que también se espera que respalden con otros roles de gestión relevantes, según corresponda a sus áreas de responsabilidad.
Es crucial que cada institución del sector salud desarrolle y mantenga su propio Plan
Director de Ciberseguridad, adaptado a su realidad operativa, contexto de riesgos, infraestructura tecnológica y nivel de madurez en seguridad de la información. Este plan estratégico no solo ayudaa alinear los objetivos de protección con la misión de la institución, sino que también facilita la planificación, ejecución y seguimiento de iniciativas de seguridad de manera sistemática, priorizando acciones según el impacto potencial en los Servicios de Salud. Tener un plan director institucional refuerza la capacidad de respuesta ante incidentes, mejora la gestión del riesgo tecnológico y asegura la continuidad operativa de los sistemas clínicos y administrativos, contribuyendo así a crear un entorno digital confiable y resiliente en beneficio de los pacientes y la comunidad.
DIRECTRICES PARA LA IMPLEMENTACIÓN SGSI PARA LA SEGURIDAD DE LA
INFORMACION Y CIBERSEGURIDAD En el contexto de fortalecer la ciberseguridad en el sector salud, se debe implementar un Sistema de Gestión de Seguridad de la Información (SGSI) que se base en principios de gobernanza, gestión de riesgos, cumplimiento normativo y mejora continua como el núcleo del modelo de protección institucional.
Este sistema, que se alinea con estándares internacionales como ISO/IEC 27001:2022 y la Ley Marco de Ciberseguridad N*21.663, permite establecer, implementar, operar, monitorear, revisar, mantenery mejorar la seguridad de la información de manera sistemática y continua.
La implementación efectiva de este modelo estructurado de gobernanza de la seguridad de la cimentará las bases que permitan asegurar la protección de la confidencialidad, integridad y disponibilidad de los activos críticos de información.
Este modelo debe tener en cuenta los siguientes componentes fundamentales:
5.1.
Gobernabilidad de la seguridad de la información y ciberseguridad La gobernabilidad se encarga de establecer la estructura organizativa, así como los roles y z responsabilidades, y los mecanismos de supervisión que son esenciales para dirigir y
LA
controlar la gestión de la seguridad de la información. Es fundamental definir un modelo
Pe
de gobernanza institucional que incluya:
a
[EEE
II

<!-- pág. 12 -->

BA
emusterioDESaLUD
| trs-N0-007 | Versión:20 [  Páginamde7o
PENN
Designación formal de responsables (Encargado de Seguridad de la Información y Ciberseguridad (CISO), Comité de Seguridad de la Información con los responsables locales en cada Institución o Establecimiento del sector salud).
e
Integración de la seguridad en los niveles estratégicos, tácticos y operativos.
e
Políticas, lineamientos e instructivos formales aprobados por la autoridad institucional.
e
Mecanismos de rendición de cuentas y reporte hacia la alta dirección.
e
Coordinación transversal entre áreas clínicas, administrativas, Tl y jurídicas.
5.2.
Roles y Responsabilidades Bajo el Modelo de Implementación para la Seguridad de la Información y Ciberseguridad, que está alineado con un SGSI y adaptado al contexto del sector salud, es fundamental que los roles y responsabilidades estén bien definidos. Esto garantiza una ejecución efectiva, una rendición de cuentas clara y la sostenibilidad a largo plazo. A continuación, se presentan los roles principales y las responsabilidades que les corresponden:
Alta Dirección Institucional / Dirección del Establecimiento de Salud e Aprobar formalmente la política de seguridad de la información.
Proveer
los
recursos
necesarios (humanos,
tecnológicos,
financieros)
para
la
implementación del SGSI.
e
Asumir la responsabilidad final del tratamiento de riesgos institucionales.
e
Participar en la revisión de informes de impacto y presentación de riesgos críticos.
e
Aprobar planes de tratamientoy priorización de iniciativas.
Encargado de Seguridad de la Información y Ciberseguridad (CISO)
e
Liderar la implementación, mantenimiento y mejora del SGSI a nivel institucional.
Coordinar el Comité de Seguridad de la Información.
e
Supervisar la elaboración del análisis de riesgos, plan de tratamiento y seguimiento de controles.
e
Asegurar el cumplimiento normativo y la implementación de controles alineados a marcos como ISO/IEC 27001, NIST y legislación nacional.
Gestionar incidentes de seguridady liderar la respuesta ante ciberataques.
e
Promover
la
cultura
de
mediante
capacitaciones
y
campañas
de
concientización.
Comité de Seguridad de la Información e Instancia transversal con representación de áreas clínicas, administrativas, legales y de
A
e Analizar riesgos institucionales desde múltiples perspectivas.
XD -
e Evaluar los planes de tratamiento propuestos y sugerir prioridades.
e Apoyar la integración de la seguridad en procesos estratégicos, operativos y clínicos.
Monitorear el cumplimiento de políticas y procedimientos internos.
Ministerio de Salud — Departamento deE

<!-- pág. 13 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD PARAEL SECTOR SALUD an
A
A TLP:BLANCO
Responsables Locales de Seguridad (en cada unidad o establecimiento)
Implementar y mantener controles de seguridad en su área de responsabilidad.
e
Coordinar con el CISO el levantamiento de activos, análisis de riesgos y respuesta a Sensibilizar al personal sobre las políticas y buenas prácticas de seguridad.
e
Participar en auditorías internas o revisiones de cumplimiento.
Encargado de Tecnología / Jefe de Informática Implementar controles técnicos (firewalls, cifrado, autenticación, etc.) conforme a los lineamientos del SGSI.
e
Garantizar la alta disponibilidad, respaldo y continuidad operativa de los sistemas.
e
Colaborar en el levantamiento de activos tecnológicos e integración de medidas de seguridad en nuevos proyectos.
e
Aplicar pruebas de seguridad sobre APIs, plataformasy redes críticas.
Usuarios Finales / Funcionarios de Salud e Cumplir con las políticas, lineamientos y procedimientos institucionales de seguridad.
Participar en capacitaciones obligatorias.
Reportar oportunamente incidentes o eventos sospechosos.
e
Proteger sus credenciales de acceso y manejar la información con responsabilidad.
Auditor Interno / Control Interno e Evaluar periódicamente el nivel de cumplimiento del SGSI.
e
Verificar la eficacia de los controles implementados.
e
Emitirinformes con hallazgos y recomendacionesa la alta dirección.
e
Apoyar la preparación de evidencias para fiscalizaciones externas.
5.3.
Identificación de los activos de información y su orden de criticidad.
El SGS| requiere que se elabore un Inventario de Activos de Información. La gestión de la seguridad debe comenzar identificando, clasificando y valorando los activos de información que respaldan los procesos institucionales. Esto incluye:
e
Elaboración de un Inventario de Activos de Información, tanto digitales como físicos.
e
Clasificación
por
criticidad
(alta,
media,
baja) considerando
el
impacto
en
la
confidencialidad, integridad, disponibilidad y trazabilidad.
e
Inclusión de activos tecnológicos (sistemas HIS, servidores, dispositivos loT, bases de ¿Hz datos)
y activos informacionales (datos clínicos, administrativos, legales).
SNE
e
Asignación de responsables por activo (custodios).
e
Relación entre activos y procesos institucionales, para facilitar el análisis de riesgos. 4

<!-- pág. 14 -->

a
MN
tiisterioDEsaLuD
| rrs-Nc-007 | versión:2o [  Páginaisdeza PAN
5.4.
Gestión de Riesgos.
La gestión de riesgos es un proceso metódico que se encarga de identificar, analizar, evaluar y abordar los riesgos que podrían poner en peligro la seguridad de la información dentro de una organización. Esto implica entender las amenazas y vulnerabilidades que podrían surgir, evaluar la probabilidad de que se materialicen y el impacto que podrían tener, y luego tomar decisiones bien fundamentadas sobre cómo gestionar esos riesgos.
En este sentido, la gestión de riesgos es crucial para las instituciones del sector salud por varias razones:
e
Protección
de
la
del
Paciente:
Se
encarga
de
mantener
la
confidencialidad, integridad y disponibilidad de los datos de los pacientes, cumpliendo con las obligaciones legales y éticas necesarias.
Continuidad del Negocio: Ayuda a identificar y mitigar los riesgos que podrían interrumpir los servicios esenciales, asegurando que las operaciones sigan funcionando sin contratiempos.
Cumplimiento Legal: Facilita el cumplimiento de la Ley 21.663 sobre el Marco de y otras normativas relevantes, evitando así sanciones y responsabilidades legales.
e
Toma de Decisiones Informada: Proporciona una base sólida para tomar decisiones sobre inversiones en seguridad y para asignar recursos de manera eficiente.
Mejora de la Resiliencia: Refuerza la capacidad de la organización para enfrentar y recuperarse de incidentes de seguridad, minimizando daños y pérdidas.
Generación de Confianza: Muestra a los pacientes, al personal y a otros interesados que la organización se toma en serio la seguridad de la información, lo que genera confianza en sus servicios.
5.4.1. Metodologías de Gestión de Riesgos en el Sector Salud La gestión de riesgos en el sector salud es fundamental para proteger la información, asegurar la continuidad de los servicios clínicos y salvaguardar los datos personales sensibles de los pacientes. Para lograrlo, las instituciones de salud deben implementar metodologías de gestión de riesgos que estén alineadas con estándares internacionales como ISO 31000 (Gestión de Riesgos), ISO/IEC 27005 (Gestión de Riesgos en Seguridad de la Información), el Marco de Gestión de Riesgos del NIST (NIST Risk Management Framework - NIST RMF) y MAGERIT*. También pueden seguir las directrices establecidas por el Minsal a través de su
SSEñA
* MAGERIT: Metodología de análisis y gestión de riesgos de seguridad de los sistemas de información, desarrollada por el Consejo Superior de Administración Electrónica (CSAE) del Gobierno de España.
A

<!-- pág. 15 -->

ae
ÍA
Páginal4de79
Política de Gestión de Riesgos de Seguridad de la Información*, complementándolas con lo que indica la Ley N* 21.663 de Ciberseguridad de Chile.
Estas metodologías permiten identificar, analizar, evaluar y tratar de manera sistemática los riesgos que pueden afectar la confidencialidad, integridad, disponibilidad y trazabilidad de la información crítica, lo que contribuye a fortalecer la ciber resiliencia en las organizaciones de salud.
5.4.1.1.
Flujo de Gestión de Riesgos Este flujo describe de manera clara y ordenada las etapas clave para identificar, analizar, evaluar, tratar y monitorear los riesgos que pueden afectar la seguridad de la información en las instituciones de salud.
El objetivo de su implementación es reforzar la protección de los activos críticos de información, asegurar la continuidad de los servicios de atención sanitaria y garantizar el cumplimiento de la Ley N* 21.663 sobre Ciberseguridad, así como otros marcos normativos y estándares internacionales que sean relevantes.
Establecimiento del Contexto:
Definir
los objetivos, alcance, criterios de riesgo y la metodología a utilizar.
Se debe establecer claramente el propósito y los limites del proceso de gestión de riesgos.
e
Sedeben definir los criterios para evaluar los riesgos, considerando el impacto potencial (en la atención al paciente, finanzas, reputación, etc.)y la probabilidad de ocurrencia.
Sedebe seleccionar una metodología de gestión de riesgos (ej., ISO 27005, NIST SP 800-
30)ydocumentarla.
Identificación de Riesgos: En base al inventario de los activos de información identificar las amenazas, las vulnerabilidades que les afectad y se desarrollan escenarios de riesgo.
En base al inventario de los activos de información (datos de pacientes, sistemas, dispositivos, etc.)y clasificarlos según su criticidad.
Sedeben identificar las amenazas relevantes para el sector salud (ej., ransomware, robo de datos)y las vulnerabilidades que podrían ser explotadas.
e
Se deben desarrollar escenarios de riesgo que describan cómo las amenazas podrían afectara los activos.
Análisis de Riesgos: Evaluar el impactoy la probabilidad de los riesgos, y se determina el nivel de riesgo.
Se debe evaluar el daño potencial que cada riesgo podría causar a la organizacióny la probabilidad de que ocurra.
e
Se debe combinar la evaluación del impactoy la probabilidad para determinar el nivel de riesgo (ej., alto, medio, bajo).
A
S
e ¡E
“ https: //www.minsal.cl/seguridad_de_la_informacion/
E

<!-- pág. 16 -->

ae
MA
ITs-NC-007
vVersión:2.0
Páginal5de79
Evaluación de Riesgos: Comparar los niveles de riesgo con los criterios de aceptación y se priorizan los riesgos.
e
Se debe determinar si los niveles de riesgo son aceptableso si requieren tratamiento.
Se deben priorizar los riesgos para su tratamiento, enfocándose en los de mayor impacto y probabilidad.
Tratamiento de Riesgos: Se debe elaborar e implementar un Plan de Tratamiento de los riesgos que detalle las acciones, responsables, plazos y recursos e Desarrollar un Plan de Tratamiento que detalle las acciones, responsables, plazos y recursos.
e
Seleccionar e implementar controles para mitigar o reducir los riesgos a un nivel aceptable, como implementar controles de seguridad, transferir el riesgo a un seguro, evitar la actividad riesgosa.
e
Identificar los riesgos respecto de los que procede transferir (por ejemplo, contratando un seguro) o aceptar los riesgos.
Monitoreo y Revisión: Se debe revisar el proceso de gestión de riesgos y medir la efectividad de los controles en relación con los objetivos de tratamiento de los riesgos.
Se debe realizar un seguimiento continuo de los riesgos y la implementación de los controles.
Se debe revisar periódicamente el proceso de gestión de riesgos para asegurar su eficacia y realizar mejoras.
Un ejemplo de Matriz de Riesgos de Seguridad de la Información en el Sector Salud en Anexo punto N? 21.4.
5.4.2. Plan de Tratamiento Como resultado del análisis de riesgos, es fundamental crear un Plan de Tratamiento formal que defina de manera clara las acciones que se llevarán a cabo para reducir los riesgos a niveles aceptables. Este plan debe incluir:
e
Actividades concretas y responsables designados para su ejecución.
e
Justificación técnica y normativa de cada medida adoptada (por ejemplo, controles técnicos, procedimientos, cambios de configuración).
e
Calendario de implementación con fechas claras para cada acción, y recursos asignados para su cumplimiento.
Criterios de validación o cierre de cada actividad.
a
El Plan de Tratamiento necesita la aprobación de la autoridad correspondiente y debe ser
SU.
monitoreado periódicamente por el Comité de Seguridad de la Información.
Moo
v
Lal
e
o
ES]

<!-- pág. 17 -->

dy E”
MÍ
Página16 de 79
5.4.3. Informe de Impacto y Presentación Directiva Para garantizar una gestión efectiva del riesgo, es fundamental elaborar un Informe de Impacto que reúna los hallazgos más importantes del análisis de riesgos, identificando de manera clara:
e
Riesgos que afectan la continuidad de operación clínica y administrativa.
Vulnerabilidades de mayor impacto en sistemas críticos (HIS, bases de datos, redes internas, etc.).
e
Potenciales consecuencias a la ciudadanía, legales, operativas y reputacionales.
Este informe debe ser presentadoa la dirección del establecimiento de salud o institución a través de una Presentación Directiva. Esto facilitará la comprensión de los riesgos, promoverá decisiones informadasy fortalecerá la rendición de cuentas en lo que respecta a la seguridad de la información.
La retroalimentación recibida en esta presentación debe ser parte del proceso de mejora del SGSI. Esto ayudará a fortalecer la conexión entre la seguridad de la información y los objetivos de la institución.
5.4.4. Mejora continua.
El modelo debe incorporar un enfoque de mejora continua (ciclo PDCA: Planificar - Hacer - Verificar - Actuar), tal como lo establece la ISO 27001:
e
Revisión periódica de políticas y controles.
e
Evaluaciones de madurez y auditorías regulares.
e
Actualización de análisis de riesgos.
e
Reforzamiento de capacidades institucionales a través de formacióny sensibilización.
e
Retroalimentación a partir de incidentes, brechas o hallazgos detectados.
5.5.
Política General, Específicas y Procedimientos De acuerdo con la estructura de gobernanza en ciberseguridad que se ha establecido, cada institución del Sector Salud tiene la responsabilidad de elaborar, formalizar, implementar y mantener una Política General de Seguridad de la Información y Ciberseguridad. Esta política servirá como el marco rector de alto nivel, definiendo las directrices estratégicas y los principios fundamentales para la protección integral y efectiva de todos los activos de información institucionales, asegurando la confidencialidad, integridad y disponibilidad de sus sistemas y datos.
La Política General es una declaración formal del compromiso de la Dirección con la seguridad y
Al
de la información y la ciberseguridad, estableciendo una postura proactiva para garantizar la pe continuidad operativa, el desarrollo seguro de servicios digitales y la mejora continua enla «___4% atención a los usuarios. Este documento estratégico debe ser redactado de manera clara,
AA
IC

<!-- pág. 18 -->

MÍ
utilizando un lenguaje accesible para todos los niveles de la organización, y debe estar completamente alineado con las leyes, decretos y estándares nacionales e internacionales vigentes.
Una vez aprobada y ampliamente difundida esta Política General entre todo el personal, la institución deberá avanzar en el desarrollo e implementación de dos niveles de instrumentos normativos complementarios que permitan llevar a la práctica las directrices estratégicas.
5.5.1.
Políticas Específicas Estas políticas abordarán áreas críticas y específicas de la seguridad de la información, proporcionando lineamientos detallados para la gestión de:
e
Accesos físicos y lógicos a los activos de información.
e
Relaciones con tercerosy la gestión de la seguridad en la cadena de suministro.
e
operativa, incluyendo los procesos de respaldo, recuperación ante desastres y continuidad del negocio.
Clasificación, etiquetado y manejo seguro de la información según su nivel de sensibilidad.
Seguridad de los activos de hardware y software.
Comunicaciones seguras y protección contra malware.
Gestión de incidentes de seguridad.
e
Cumplimiento normativo específico (ej. protección de datos personales, seguridad de la información de salud).
Uso aceptable de los recursos informáticos.
Seguridad en el desarrollo de software. Estas políticas específicas permitirán un tratamiento más granular de los diversos escenarios operativos y los riesgos particulares asociados a cada ámbito.
5.5.2. Procedimientos e Instructivos Operacionales Es crucial que las instituciones del Sector Salud establezcan y mantengan un conjunto normativo interno sólido, que se actualice periódicamente y que sea de cumplimiento obligatorio para todo el personal.
Los procedimientos e instructivos operacionales describirán de manera clara y detallada las etapas de cada proceso, los roles y responsabilidades asignadas en cada fase, los flujos de trabajo, además de los mecanismos técnicos y administrativos necesarios para implementar de manera efectiva los controles de seguridad establecidos en la Política General y en las
Políticas Específicas.
AMES
a
2 1é
Su elaboración debe alinearse estrictamente con las mejores prácticas y estándares
JO
reconocidos tanto a nivel nacional como internacional, como ISO/IEC 27001, las directrices del
LN.
A
NIST, los Controles CIS y las normativas nacionales relevantes (Ley N* 21.663 sobre Ciberseguridad y Ley N” 19.628 sobre Protección de la Vida Privada).
A
OZ

<!-- pág. 19 -->

MA ruusterovesacoo
[ is-nc-007 | versiórzo |
Páginatade7o
AÚQENAO
Para asegurar que
estos
instrumentos
normativos
estén
bien
estructurados
y sean
coherentes, se ofrece un modelo con los componentes mínimos requeridos en el Anexo, punto
ZU:
Su utilización se considera una buena práctica recomendada.
Este marco normativo necesita estar respaldado por una estructura de gobernanza en ciberseguridad que sea efectiva, así como por un Comité de Seguridad de la Información y Ciberseguridad que tenga la autoridad y la responsabilidad de asegurar su cumplimiento. La correcta implementacióny el estricto seguimiento de estos instrumentos vana fortalecer de manera significativa la resiliencia de la organización frente a las amenazas cibernéticas, permitiendo anticipar y mitigar proactivamente los riesgos, además de contribuir directamente a la mejora continua de los servicios y a la consolidación de la confianza de la ciudadanía.
En el marco de la gestión de la seguridad de la información, se recomienda contar, al menos, con procedimientos documentados para los siguientes procesos críticos:
e
Procedimiento de gestión de ficha clínica electrónica y en papel.
e
Procedimiento de gestión de agendas y programación de atenciones.
e
Procedimiento de gestión y control de inventarios de activos tecnológicosy clínicos.
e
Procedimiento de gestión de respaldos y recuperación ante desastres.
Procedimiento de control de accesos físicos y lógicos.
e
Procedimiento de tratamiento de incidentes de seguridad de la información.
e
Procedimiento de alta, modificación y baja de usuarios.
Procedimiento de entrega de información a terceros (por ejemplo, por solicitudes judiciales, auditorías, etc.).
En aquellos casos en que no sea posible documentar todos los procedimientos operativos, se recomienda priorizar según los siguientes criterios:
e
Procesos que involucren el tratamiento de datos personales o sensibles de salud.
e
Procesos que afecten la continuidad operativa del establecimiento.
e
Procesos que incluyan el uso de sistemas informáticos críticos(HIS, RIS, PACS, sistemas de laboratorio, etc.).
Procesos donde intervengan múltiples unidades y/o actores externos.
e
Procesos que hayan sido objeto de incidentes, hallazgos de auditoría o vulnerabilidades anteriores.
DIRECTRICES PARA UNA ARQUITECTURA DE LA SEGURIDAD DE LA
INFORMACIÓN Y CIBERSEGURIDAD Con el fin de reforzar la ciberseguridad en el sector salud, se requiere que cada institución de ado:
este ámbito adopte e implemente de manera proactiva un Modelo de Seguridad por Capaso
*=—..
Defensa en Profundidad (DiD) que garantice una defensa en profundidad, integrando
CE
A

<!-- pág. 20 -->

a
MA
ITS-Nc-007
Página19 de 79
diversos controles técnicos, físicos y administrativos en todos los niveles de la infraestructura tecnológica.
Esta estrategia, que es tanto integral como estructurada, implica la aplicación de diversos controles de seguridad, administrativos, físicos y técnicos, que resultan fundamentales para proteger de manera efectiva activos críticos como información sensible, sistemas operativos e infraestructura tecnológica. La flexibilidad del modelo permite una implementación efectiva y adaptada a las necesidades específicas de cada institución en el sector.
Este modelo se basa en el principio de seguridad y privacidad por defecto y desde el diseño, tal como se establece en la Ley 21.663 sobre el Marco de Ciberseguridad, la ley N* 19.628, de protección de la vida privaday la ley N* 20.584 de Derechos y Deberes de los Pacientes.
Como resultado de lo anterior, todos los sistemas informáticos, aplicaciones y tecnologías de la información deben ser concebidos, implementados y gestionados con la seguridad y la privacidad de los datos como pilares fundamentales desde el principio. Al integrar la seguridad y la privacidad en cada fase del ciclo de vida de los sistemas, se garantiza una protección más sólida y proactiva, lo que complementa la estrategia de defensa en profundidad que caracteriza al Modelo de Seguridad por Capas.
Esta estrategia es crucial en el sector de la salud, donde es fundamental garantizar en todo momento la confidencialidad, integridad y disponibilidad de los datos clínicos y operacionales.
Implementar múltiples niveles de defensa de manera adecuada ayuda a fortalecer la resiliencia digital frente a amenazas tanto internas como externas, además de facilitar el cumplimiento de las normativas nacionales e internacionales relacionadas con la ciberseguridad y la protección de datos personales.
6.1. Capas de Seguridad en Entornos de Salud A continuación, se presentan los controles prioritarios para reforzar la ciberseguridad en el sector salud de manera escalonada:
6.1.1. Capa de Seguridad Física Implemente controles de acceso físico sólidos para limitar el acceso a las instalaciones, centros de datos, salas de servidores críticos y otras áreas sensibles, permitiéndolo solo al personal que esté debidamente autorizado.
Esto debe incluir, al menos:
e
Sistemas de control de acceso biométrico y tarjetas inteligentes: Utilizar el uso de lectores biométricos (huella, iris) y tarjetas RFID personalizadas para permitir acceso solo a personal autorizado.
ARE,
e
Videovigilancia perimetral y en zonas críticas (CCTV) con grabación y monitoreo,
JNE
integrado con sistemas de analítica de videoy alertas.
j
E
e
Zonificación física y separación de áreas: Establecer zonas de seguridad diferenciadas
A
con niveles de acceso específicos. Implementación de barreras físicas, jaulas de racks y rc

<!-- pág. 21 -->

e
US:
salas blancas para infraestructura Tl. Implementar sistemas de detección de intrusos (IDS) físicos para alertar sobre accesos no autorizados Sensores ambientales: Controlar las condiciones ambientales (temperatura, humedad)
y la alimentación eléctrica (SAl/UPS, generadores de respaldo) para garantizar la disponibilidad.
Detectores
de
humo,
humedad,
temperatura
y
fallos
eléctricos
conectados a sistemas de gestión de instalaciones (BMS).
6.1.2.Capa de Seguridad de Red Implemente mecanismos sólidos para controlar el tráfico de red, con el fin de evitar accesos no autorizados a los sistemas y datos de la institución. Además, segmente la red de manera lógica y/o física para limitar la propagación de incidentes de seguridad en caso de que se presenten. Esto debe incluir:
e
Firewalls de última generación (NGFW): Implemente y configure firewalls de última generación entre la red institucional y las redes externas, utilizando inspección profunda de paquetes (DPI), filtrado por aplicación y geo-bloqueo. Configure listas blancas y negras de direcciones IP y puertos para permitir el tráfico necesario y bloquear fuentes de amenazas conocidas.
Active
mecanismos
de
protección
contra
amenazas
avanzadas, como el análisis de tráfico cifrado (inspección SSL/TLS), prevención de intrusiones (IPS) y sandboxing para detectar malware desconocido.
e
|DS/IPS: Implemente sistemas IDS/IPS para monitorear el tráfico de red en busca de
actividades
sospechosas
o
maliciosas,
bloqueando
o
alertando
sobre
posibles
intrusiones.
e
Listas de Control de Acceso (ACLs): Utilice ACLs en enrutadores y switches para controlar el tráfico a nivel de dirección IP y puerto, restringiendo las comunicaciones entre segmentos de red según sea necesario.
e
Segmentación de Red: Implemente la segmentación de la red utilizando VLANSs, subredes o arquitecturas de Zero Trust para aislar sistemas críticos y limitar el movimiento lateral de posibles atacantes. Use microsegmentación para aislar sistemas críticos, redes clínicas, administrativas, loT y visitantes.
e
VPNs seguras: Utilice cifrado IPsec o SSL, autenticación robusta y túneles cifrados por usuario o dispositivo para asegurar las comunicaciones a través de redes no confiables.
e
Políticas de Filtrado de Contenido: Implemente políticas de filtrado de contenido web y de correo electrónico para prevenir el acceso a sitios maliciosos y la descarga de archivos peligrosos.
e
Monitoreo del Tráfico de Red: Establezca un sistema de monitoreo continuo del tráfico de red para detectar anomalías, patrones sospechosos y posibles incidentes de seguridad en tiempo real.
6.1.3.Capa de Seguridad del Perímetro a
E
VISA
implemente una capa de seguridad perimetral que controle y proteja de manera rigurosa todos x___2 los puntos de entradaa la red institucional, ya sea desde Internet o cualquier otra red externa.
Esta capa de seguridad debe incluir:
A

<!-- pág. 22 -->

A
Página21de79
e
Firewalls
de
Aplicación Web (WAF):
Implemente WAF
para
proteger
nuestras
aplicaciones web de amenazas como inyecciones SQL y cross-site scripting (XSS).
e.
Protección contra DDoS (Distributed Denial of Service): Utilice sistemas dedicados o servicios en la nube que ayuden a mitigar ataques de denegación de servicio distribuidos.
e
Filtrado de Contenido Web: Implemente soluciones de filtrado de contenido web para bloquear el accesoa sitios maliciosos conocidos, categorías de contenido inapropiadas o cualquier sitio que pueda poner en riesgo la seguridad de la institución.
Gestión de Amenazas Unificada (UTM): Considere la implementación de soluciones UTM que integren diversas funciones de seguridad perimetral (como firewall, IPS, antivirus de gateway, filtrado web, etc.) para una gestión centralizada y una protección más efectiva.
e
Políticas de Acceso Remoto Seguro: Defina e implemente políticas estrictas para el acceso remotoa la red institucional (por ejemplo, a través de VPNs con autenticación fuerte y cifrado), controlando quién puede accedery desde dónde.
Monitoreo y Alertas: Establece un sistema de monitoreo y alertas. Intégrelos con un
SIEM.
6.1.4. Capa de Aplicación:
Desarrolle
y
configure
todas
las
aplicaciones
institucionales
de
manera
segura,
implementando medidas proactivas para prevenir vulnerabilidades y proteger los datos que procesan. Esto implica adoptar las siguientes prácticas obligatorias:
e
Ciclo de Vida de Desarrollo de Software Seguro(SSDLC): Se debe implementar un SSDLC que incluya medidas de seguridad a nivel de aplicaciones, como autenticación, autorización y pruebas de seguridad, para salvaguardar la integridad y confidencialidad de los datos. Adoptar estándares de desarrollo seguro reconocidos, como los que propone OWASP o NIST, y aplicar marcos de trabajo como el SSDLC es una excelente práctica.
Validación de Entradas: Implemente mecanismos sólidos para validar todas las entradas de usuario y así prevenir ataques de inyección, como SQL Injection, XSS (Cross-Site Scripting) y CSRF (Cross-Site Request Forgery). Al realizar consultas a bases de datos, es recomendable utilizar procedimientos almacenados y consultas preparadas para evitar inyecciones SQL. Además, es importante emplear librerías y frameworks de terceros que sean confiables y que integren mecanismos de seguridad robustos.
e
Codificación Segura: Adopte prácticas que sigan guías y estándares reconocidos, como el OWASP Top Ten, para evitar vulnerabilidades comunes en el software.
e
Control de Acceso a
la Aplicación: Implemente mecanismos de autenticación y autorización sólidos, basados en roles, ayudará a gestionar quién puede accedera las
PUE.
a
0A
E
funcionalidades y datos dentro de la aplicación.
### 5. SADO -
Gestión Segura de Sesiones: Asegúrese de que las sesiones de usuario se manejen de
A
manera segura, generando identificadores de sesión robustos, protegiendo contra el secuestro de sesiones y asegurando la invalidación adecuada al cerrar la sesión.
A

<!-- pág. 23 -->

a
MA
e.
Realizar pruebas de penetración (pentesting) especificas para las aplicaciones y realización de análisis de seguridad estáticos (SAST) y dinámicos(DAST).
Manejo Seguro de Errores y Excepciones: Configure las aplicaciones para manejar errores y excepciones de forma segura, evitando la divulgación de información sensible o detalles internos del sistema.
e
Utilizar cifrado para datos sensibles dentro de la aplicación. Implemente cifrado para proteger los datos sensibles dentro de la aplicación. También es importante implementar registros de auditoría detallados que registren la actividad de la aplicación (logs).
e
Protección de Datos Sensibles: Implemente medidas de seguridad para los datos sensibles que maneja la aplicación. Esto incluye cifrado tanto en tránsito como en reposo, así como la anonimización o seudonimización cuando sea necesario, y el enmascaramiento de datos en entornos que no son de producción.
Gestión segura de APIs: Las APIs, tanto internas como externas, deben ser desarrolladas siguiendo principios de seguridad desde el diseño, implementando autenticación robusta (como OAuth
2.0) autorización
granular,
cifrado TLS
o superior y
protecciones contra las vulnerabilidades más comunes que se encuentran en el OWASP API Top 10. Además, es esencia! incluir la validación de entradas, limitar las tasas de consumo, mantener una trazabilidad completa de los accesos y contar con documentación actualizada.
e
Parala exposición de los servicios API REST: Utilice mecanismos de autenticación para su uso privado, ya sea mediante tokens (como JWT u otros), certificados, llaves criptográficas, o cualquier otro método de autenticación cuya efectividad se haya Comprobado por métodos fiables entre puntos.
6.1.5.Capa de Seguridad de los Datos Implemente medidas de seguridad sólidas para salvaguardar la información, tanto cuando está almacenada en los sistemas como cuando se está utilizando, protegiéndola de accesos no autorizados, modificaciones inapropiadas o eliminaciones accidentales o maliciosas. Esto significa seguir las siguientes directrices obligatorias:
e
Autenticación Fuerte: Utilice mecanismos de autenticación robustos (incluyendo la Autenticación Multifactor - MFA cuando sea posible) para verificar la identidad de los usuarios antes de permitir el acceso alos datos.
e
Cifrado de Datos en Reposo: Cifre la información sensible almacenada en bases de datos, servidores, dispositivos de almacenamiento y cualquier otro medio utilizando algoritmos de cifrado fuertes y estándares reconocidos por la industria como AES-256.
Además de implementar una gestión de claves criptográficas segura.
e
Cifrado de Datos en Tránsito: Asegure la protección de la información sensible durante su transmisión a través de redes internas y externas mediante el uso de protocolos de cifrado seguros TLS 1.2 o superior para datos en tránsito.
e
Firmas Digitales: Utilice firmas digitales basadas en criptografía de clave pública, en AMS atención a que esta tecnología permite verificar la autenticidad e integridad de los datos ; Vs a y documentos, asegurando el no repudio. Tenga en cuenta que, tratándose de ES instrumentos públicos, éstos deben ser firmados con Firma Electrónica Avanzada.
AA
A

<!-- pág. 24 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN YCIBERSEGURIDAD PARA EL SECTOR SALUD a
MÍ
Irs-NC-007
Página23de79
e
Prevención de Pérdida de Datos(DLP): Implemente herramientasy políticas de DLP para monitorear y controlar el movimiento de información sensible, previniendo su fuga o extracción no autorizada.
e
Anonimización y Seudonimización: Cuando sea apropiado y legalmente permitido, aplique técnicas de anonimización o seudonimización a los datos sensibles para reducir el riesgo de identificación directa.
Políticas de Retención y Eliminación Segura de Datos: Defina e implemente políticas claras para la retención de datos según los requisitos legales y del negocio, y establezca procedimientos seguros para la eliminación de datos que ya no sean necesarios, evitando su recuperación no autorizada.
e
Auditoría de Acceso a Datos: Implemente un sistema de auditoría que registre los accesos, las modificaciones y las eliminaciones de datos sensibles, permitiendo el seguimiento y la detección de actividades sospechosas. Clasificación y etiquetado de la información: Uso de etiquetas automatizadas y manuales para categorizar y aplicar políticas.
Autenticación: Verificar laidentidad de los usuariosantes de otorgar acceso a sistemas y datos. Utilizando mecanismos robustos como autenticación multifactor (MFA), uso de contraseñas complejas y políticas de rotación, e idealmente, autenticación basada en certificados o biometría. Técnicamente, se deben implementar protocolos seguros como OAuth 2.0 y SAML 2.0 para la autenticación y federación de identidades.
e
Autorización: Definir qué recursos y datos pueden acceder los usuarios autorizados, mediante la implementación de listas de control de acceso (ACLs, RBAC y ABAC)
aplicadas consistentemente en la capa de aplicacióny la infraestructura, e DLP(Data Loss Prevention): Prevención de fuga de datos vía correo, USB, impresión o nube.
e
Sistemas de respaldo automatizados: Realizar copias de seguridad (backups) periódicas y seguras de los datos, con almacenamiento local y en la nube, pruebas regulares de recuperación (DRP - Plan de Recuperación ante Desastres /BIA - Análisis de Impacto al
Negocio).
6.1.6.Capa de Seguridad de Dispositivos y Endpoints implemente medidas de seguridad integrales para proteger todos los dispositivos de los usuarios finales, como estaciones de trabajo, portátiles, dispositivos móviles y tablets, que accedena los recursos de la Institución. Esta protección debe incluir los siguientes aspectos obligatorios:
e
Implementación de Antimalware Avanzado: Instale y mantenga actualizado software antimalware robusto en todos los endpoints, con capacidades de detección en tiempo real, análisis heurístico y protección contra amenazas emergentes (virus, spyware, ransomware, etc.). Se recomienda el uso de tecnologías de protección avanzada(NGAV),
AA
que incorporen detección basada en comportamiento y análisis heurístico para anticipar hi.
mE
nuevas variantes de malware.
5e
EDR(Endpoint Detection and Response)
/ XDR (Extended Detection and Response): Se
NA
deberá implementar una solución de EDR, que permita el monitoreo continuo de la actividad en los endpoints, la detección temprana de amenazas y una respuesta e

<!-- pág. 25 -->

E
e
MÍ)
HMINISTERIODESALUD
Página24de79
automatizada ante incidentes. Para entornos más complejos, se sugiere la adopción de plataformas XDR, que correlacionen eventos entre múltiples vectores como red, correo electrónico y nube. Estas soluciones deben integrarse con el sistema de gestión de eventos e información de seguridad (SIEM) institucional.
e.
Firewall Personal: Active y configure correctamente firewalls personales en todos los dispositivos para controlar el tráfico de red entrante y saliente a nivel del endpoint.
e.
Gestión Centralizada de Dispositivos Móviles (MDM/UEM): Implemente una solución de Gestión de Dispositivos Móviles (MDM) o Gestión Unificada de Endpoints (UEM) para aplicar políticas de seguridad, gestionar la configuración, realizar inventario, controlar el acceso a aplicaciones y datos, y habilitar el borrado remoto en caso de pérdida o robo de dispositivos móviles.
Control de Acceso al Dispositivo: Exija el uso de mecanismos de autenticación fuertes (contraseñas complejas, PINs, biometría) para acceder a los dispositivos y configure el bloqueo automático por inactividad.
e
Cifrado de Disco Completo: Implemente el cifrado de disco completo en los portátiles y otros dispositivos que puedan contener información sensible y puedan ser extraviados o robados.
e.
Gestión
de Parches
y
Actualizaciones:
Establezca
un
proceso
centralizado
y
automatizado para
la aplicación oportuna de parehes de seguridad del sistema operativo, las aplicacionesy el firmware de los dispositivos.
e
Control de Aplicaciones: Implemente políticas para controlar la instalación y ejecución de aplicaciones en los dispositivos, permitiendo solo software autorizado y bloqueando aplicaciones potencialmente riesgosas.
Prevención de Pérdida de Datos (DLP) en el Endpoint: Considere la implementación de soluciones DLP en los endpoints para monitorear y controlar la transferencia de información sensible, previniendo su fuga accidental o intencional.
e
Control de dispositivos extraíbles: Es obligatorio establecer políticas de control sobre el uso de dispositivos extraíbles, como unidades USB. Estas políticas deben restringir el uso de medios no autorizados, registrar los eventos de conexión y exigir cifrado en los dispositivos permitidos. Además, los puertos USB deben ser deshabilitados por defecto, salvo cuando exista una justificación funcional documentada.
Paralos dispositivos móviles institucionales o personales autorizados (BYOD), se debe implementar una solución de gestión centralizada como MDM (Mobile
Device
Management) o UEM (Unified Endpoint Management). Estas plataformas deben permitir aplicar políticas de seguridad como el cifrado de datos, la autenticación reforzada, la instalación controlada de aplicaciones y el borrado remoto en caso de pérdida o robo.
e
Políticas de Uso Seguro de Dispositivos: Defina y comunique claramente las políticas de uso seguro de los dispositivos, incluyendo las restricciones sobre la instalación de software no autorizado, la conexión a redes no seguras y el almacenamiento de información sensible en dispositivos personales no gestionados.
se
Cá
E

<!-- pág. 26 -->

a
MÍA
6.1.7. Capa de Seguridad Operacional y de Monitoreo Implemente un conjunto de acciones y herramientas que permitan detectar, responder y contener amenazas de seguridad de manera oportuna. Esta capa de seguridad operativa y de monitoreo debe incluir los siguientes elementos esenciales:
Implementación de un Centro de Operaciones de Seguridad (SOC) o Funciones Equivalentes: Establezca un equipo o funciones dedicadas para el monitoreo continuo de la seguridad, el análisis de alertas y la gestión de incidentes.
e
Sistemas de Gestión de Eventos e Información de Seguridad(SIEM): Implemente un SIEM para la recopilación, correlación y análisis de logs de seguridad de diversas fuentes (firewalls, IDS/IPS, servidores, endpoints, aplicaciones, etc.) con el fin de detectar actividades sospechosasy posibles incidentes en tiempo real.
e
Monitoreo Continuo de la Infraestructura: Establezca un monitoreo constante de la salud, el rendimiento y la seguridad de la infraestructura tecnológica, incluyendo la red, los servidores, las aplicaciones ylas bases de datos.
e
Alertas y Notificaciones en Tiempo Real: Configure sistemas de alerta para notificar de manera inmediata al personal de seguridad sobre eventos sospechosos o incidentes detectados.
e
Procesos de Gestión de Incidentes Definidos: Desarrolle e implemente procedimientos claros y documentados para la identificación, análisis, contención, erradicación, recuperación y lecciones aprendidas de los incidentes de seguridad.
Equipos de Respuesta a Incidentes (IRT): Designe y capacite equipos de respuesta a incidentes con roles y responsabilidades definidos para actuar con rapidez y eficacia ante las amenazas.
e
Inteligencia de Amenazas (Threat Intelligence): Integre fuentes de inteligencia de amenazas en los procesos de monitoreo y análisis para comprender mejor el panorama de amenazasy anticipar posibles ataques.
e
Análisis Forense: Desarrolle capacidades de análisis forense para investigar incidentes de seguridad, identificar sus causas raíz, determinar el alcance del daño y recopilar evidencia para acciones futuras.
e
Ejercicios y Simulacros de Respuesta a Incidentes: Realice simulacros periódicos de respuesta a incidentes para probar la efectividad de los procedimientos y la preparación del personal.
Comunicación de Incidentes: Establezca protocolos claros para la comunicación de de seguridad a las partes interesadas relevantes, incluyendo la alta dirección y, según la normativa, la Agencia Nacional de Ciberseguridad (ANCI).
e
Inteligencia de amenazas Tl / CTI (Threat Intelligence / Cyber Threat Intelligence):
Información contextualizada para anticiparse a campañas y vectores emergentes.
IN
e
Pruebas de seguridad: Evaluaciones periódicas de vulnerabilidades, realizar pruebas de
7: Sl
penetración (pentesting) análisis de vulnerabilidades automatizados, revisiones de io seguridad del código fuente (SAST/DAST), auditorías y simulacros de incidentes.
A
E

<!-- pág. 27 -->

sE”
MA mmusterovesacuo
[| is-nc-007 | versiórzo | Páginazode7o
AÚQENAO
6.1.8.Capa de Seguridad en la Nube Para las instituciones del sector salud que utilicen o que están pensando en usar servicios en la nube (como laaS, PaaS o SaaS), es fundamental incorporar una Capa de Seguridad enla Nube dentro de su Modelo de Defensa en Profundidad. Esta capa se centra en los controles y servicios específicos que son necesarios para salvaguardar los activos, aplicaciones y datos que se encuentran en estos entornos, teniendo en cuenta el modelo de responsabilidad compartida con el proveedor de la nube.
En este contexto, las instituciones del sector salud tendrán que implementar controles de seguridad sólidos y específicos para reducir los riesgos que conlleva el uso de servicios en la nube. Esto es crucial para garantizar la confidencialidad, integridad y disponibilidad de la información en este ámbito.
Gestión de Identidades y Accesos en la Nube (IAM): Para asegurar un acceso seguro y controlado a los recursos de la nube, configure y gestione de manera centralizada las identidades de usuarios, la agrupación en roles y los permisos de acceso utilizando los servicios de lAM provistos por su proveedor de nube, tales como AWS AM, Azure Active Directory o Google Cloud lAM. Es fundamental aplicar rigurosamente el principio de mínimo privilegio, asignando a cada usuario o servicio únicamente los permisos estrictamente necesarios para llevar a cabo sus funciones específicas. Adicionalmente, implemente la Autenticación Multifactor (MFA) de forma obligatoria para todas las cuentas que tengan acceso a recursos sensibles o con privilegios elevados en su entorno de nube, añadiendo una capa adicional de seguridad.
e
Gestión
de
la
Postura de Seguridad en la Nube (CSPM):
Despliegue
e
integre
herramientas y servicios de Gestión de la Postura de Seguridad en la Nube (CSPM) para establecer un monitoreo continuo de la configuración de todos sus recursos en la nube.
Configure estas soluciones para que identifiquen y generen alertas automáticas ante configuraciones inseguras, vulnerabilidades conocidas y cualquier desviación de las mejores prácticas de seguridad y los estándares de cumplimiento normativo aplicables al sector salud en Chile. Es crucial establecer flujos de trabajo claros y asignar responsabilidades para la revisión y la ejecución oportuna de acciones de remediación para cualquier alerta generada por el sistema CSPM, manteniendo así una postura de seguridad sólida.
e.
Seguridad de la Red en la Nube: Defina, configure y gestione sus Redes Privadas Virtuales (VPC/VNet), subredes lógicas y firewalls virtuales (Grupos de Seguridad, Listas de Control de Acceso) utilizando las funcionalidades que ofrece su proveedor de servicios en la nube para establecer un perímetro de red seguro en el entorno cloud.
Implemente una segmentación lógica robusta de sus cargas de trabajo en la nube mediante la creación de subredes aisladas y aplique reglas de firewall estrictas para controlar el flujo de tráfico permitido entre estos recursos, basándose en el principio de necesidad. Para la conectividad híbrida con su infraestructura local, en caso de ser requerida, establezca conexiones segurasy cifradas utilizando Redes Privadas Virtuales (VPN) o conexiones directas (Direct Connect u otras soluciones equivalentes) para proteger la comunicación.
E)
e
Protección de Datos en la Nube: Implemente el cifrado robusto de los datos sensibles em__5 y reposo utilizando los servicios de cifrado que proporciona su proveedor de nube, como
E

<!-- pág. 28 -->

a
MN—uisrerionesaruo
| iswc-o07 | versiónizo |  Páginaz7ae7o
PIMNAA
. AWSKMS, Azure Key Vault o Google Cloud KMS, asegurándose de gestionar las claves de cifrado de forma segura y conforme a las mejores prácticas. Asimismo, asegúrese de que todos los datos que se transmiten hacia y desde su entorno de nube estén protegidos mediante protocolos de cifrado fuertes, como TLS/SSL versión 1.2 o superior, para garantizar la confidencialidad durante la transferencia. Es fundamental definir e implementar políticas de retención y eliminación de datos que cumplan estrictamente con las regulaciones y leyes de protección de datos del sector salud en Chile, incluyendo la Ley N? 19.628 y otras normativas aplicables. Considere también la implementación de servicios de Prevención de Pérdida de Datos (DLP), ya sean nativos de la nube o de terceros, para monitoreary prevenir la fuga de información sensible fuera de su entorno controlado en la nube, fortaleciendo la protección de la información crítica.
e
Monitorización y Registro en la Nube: Active y configure de manera exhaustiva los servicios de registro (logging)ymonitorización que ofrece su proveedor de nube, como AWS CloudWatch, Azure Monitor o Google Cloud Logging, para obtener visibilidad sobre la actividad en su entorno. Establezca mecanismos para el análisis continuo de estos registros con el fin de detectar actividades inusuales o potencialmente maliciosas, identificar posibles incidentes de seguridad en etapas tempranasy facilitar el análisis forense detallado en caso de incidentes confirmados. Para una gestión de seguridad centralizada, integre los registros de seguridad de la nube con su Sistema de Gestión de Eventos e Información de Seguridad (SIEM) centralizado, si su institución dispone de uno, permitiendo una correlación y análisis más eficientes de los eventos de seguridad.
e
Seguridad de Cargas de Trabajo en la Nube (Instancias, Contenedores, Funciones):
implemente medidas de seguridad específicas y adaptadas al tipo de carga de trabajo que se ejecute en la nube para proteger cada componente de su infraestructura cloud.
Para instancias virtuales, aplique el endurecimiento de los sistemas operativos mediante la eliminación de servicios innecesarios y la configuración de parámetros de seguridad robustos, y utilice software de seguridad de endpoints(EDR/XDR) optimizado para entornos de nube para la detección y respuesta a amenazas. En el caso de contenedores, asegure el ciclo de vida de las imágenes mediante el escaneo de vulnerabilidades, configure políticas de seguridad a nivel de orquestación (como Kubernetes) y gestione los clústeres de forma segura. Para arquitecturas basadas en Funciones como Servicio (FaaS), siga las mejores prácticas de desarrollo seguro (SDLC seguro) y aplique una gestión de permisos granular para las funciones, adhiriéndose estrictamente al principio de mínimo privilegio para limitar el impacto potencial de cualquier vulnerabilidad.
Cumplimiento y Gobernanza en la Nube: Implemente políticas y controles específicos diseñados para asegurar el cumplimiento de las normativas del sector salud en Chile, como la Ley N? 21.663 y la Ley N? 19.628, así como otras regulaciones internacionales relevantes que puedan aplicar a su institución (por ejemplo, HIPAA si maneja datos de pacientes internacionales). Realice auditorías periódicas de la configuración de su entorno de nube, tanto internas como externas, para verificar el cumplimiento continuo
ART.
de estas políticas y regulaciones, generando informes de cumplimiento detallados para
O,
la documentación y la toma de decisiones. Utilice las herramientas de cumplimiento y
JE.
gobernanza que ofrece su proveedor de nube para automatizar la monitorización del
AOS
cumplimiento y facilitar la generación de informes, optimizando así el proceso de aseguramiento del cumplimiento normativo.
A

<!-- pág. 29 -->

Ye”
MÚA mmisterioDESALUD
[ rs-NC-007 | Versión:20 | Página28de7s
PET
Consideraciones Adicionales:
Modelo de Responsabilidad Compartida: Es fundamental que comprenda cuáles son las responsabilidades de seguridad de su institución y cuáles son las del proveedor de la nube.
Selección del Proveedor: Asegúrese de elegir proveedores de nube que cumplan con los estándares de seguridad y las regulaciones específicas del sector salud.
e
Evaluación Continua: Realice evaluaciones de seguridad de manera regular en su entorno de nube para poder identificar y mitigar nuevas amenazas y vulnerabilidades.
6.1.9. Tabla de cumplimiento por capas (ejemplo)
Rós
Objeto
Controles Claves
AS de
Principal
Restringir acceso
Control
biométrico
y
tarjetas
ISO 27001 A.11; NIST SP físico a inteligentes; CCIv y analítica de
800-53
DE
HIPAA
Física
instalaciones
y
video;
Zonificación
y
barreras
5164.310; Ley 21.663 Art.
áreas críticas.
físicas;
Sensores
amblentales,
Ley
19.628
SA
### 2. SAUPS
(disponibilidad)
pun
Prevenir accesos |NGFW, filtrado de paquetes;
ISO 27001 A.13; NIST SP
Sezudad ide
no autorizados y
IDSAPS;
VLANs
y
800-53
SC;
HIPAA
Red
segmentar
la red.
' microsegmentación;
VPN
8164.312(e);
Ley 21.663
seguras
Art.
Ley
19.628
Proteger
los
WAF;
Protección
DDoS;
Proxy
ISO 27001 A.13; NIST SP
Seguridad del
puntos de entrada
inversos; Gateway remoto seguro
800-53
SC-5;
HIPAA
Perímetro
a
la
red
8164.312(b);
Ley
21.663
institucional.
Art. 7; OWASP Top 10
Desarrollar
y
SSDLC,
OWASP/NIST;
ISO 27001 A.14; NIST SP
Seguridad en
mantener
SAST/DAST, pentesting; Gestión
800-218
(SSDF);
HIPAA
E
aplicaciones
segura de APls (OAuth2, TLS
5164.312(c); Ley 21.663 seguras.
1.2+);
Controles
en
frontend | Art. 8; Ley 19.628 Art.4 o... (XSS,CSRE, validación,
HTTPS)
Proteger
la
Cifrado
AES-256,
TLS
1.2*+;
150 27001 A.8, A.10, A.18;
Seguiliad ¡de
en
Firmas digitates; Clasificación de
NIST SP 800-57/111/88;
los Datos
reposo
y
en
datos; MFA, OAuth2, SAML; DLP, | HIPAA 8164.312(a-c); Ley tránsito.
backups seguros
21.663 Art. 3-4; Ley 19.628
Proteger
Antivirus/Antimalware; EDR/XDR;
ISO
27001
A.12,
A.13;
Seguridad de
que
Gestión de parches; Control de NIST SP 800-171; HIPAA ¿337
Endpoints
accedena la red y USB; MDM/UEM
8164.310(d); Ley 21.663 E
Ñ
datos.
PR
o
|Art.9
5 US?
Ss a
A

<!-- pág. 30 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD PARA ELSECTOR SALUD ae.
mMNisTERODESALUD
[| is=Nc-007 | Versión:2o |  Páginaz8de7a
PWDANT
Capa de
O
Controles Claves
MS yo
Principal
| segúrtad
Detectar
y | Monitoreo continuo, SIEM; SOC ISO 27001 A.16, A.12.4,
1 OVACIONa Ty
: responder
a
24175
CTI
(Cyber
Threat -A.17; NIST SP 800-137;
Monitoreo
amenazas
en | Intelligence);
Pentesting,
| HIPAA 8164.308(a)(6); Ley
' tiempo real.
auditorías, DRP
21.663 Art. 10-11
Asegurar
la
Gestión de identidades y accesos
| 1SO 27001 A.5.19, A.5.23,
protección de los
(IAM); Configuración segura de
| A.5.30; NIST SP 800-144;
| Seguridad en
recursos
y
(CSPM);
Cifrado
en
| NIST SP 800-53 AC, SC,
' Nube
tránsito
y
reposo;
SLA
con
AU; CIS Controls v8; Ley desplegados en proveedores; Monitoreo de uso y . 21.663
Art.
Ley
entornos cloud.
amenazas en la nube
19.628 Art. 8
6.1.10. Amenazas Cibernéticas en el Sector Salud:
La transformación
digital en el sector salud ha aumentado la exposición de las instituciones a amenazas cibernéticas que ponen en riesgo la confidencialidad, integridad, disponibilidad y privacidad de la información. Estas amenazas impactan tanto en los sistemas clínicos como en los dispositivos médicos, afectando directamente la calidad de la atención y la seguridad de los pacientes, quienes deben tener en cuenta las instituciones del sector.
A continuación, se describen los principales tipos de amenazas cibernéticas que enfrenta el sector salud junto con sus impactos potenciales y los controles claves para su mitigación:
Tipode
| Impactos Potenciales
: Controles Clave para su
Ataque
Mitigación
Malware que cifra los | -
Interrupción
de
Copias
de
datos
y
exige
un
servicios clínicos críticos
| cifradas y segregadas (ISO
rescate
económico | (HIS, PACS, LIS).
¡ 27001 A.12.3).
para su liberación.
| - Pérdida de acceso a | - EDR/XDR con capacidad de
datos esenciales para la contención automática.
RASOmarE
atención médica.
- Segmentación de
red y
- Costos financieros por
control
de
tráfico
lateral
| rescate,
recuperación y
(NIST SP 800-207).
multas regulatorias.
Plan de
ante
Daño
reputacional
incidentes (ISO 27035).
significativo.
-- Parches y actualizaciones o
E
le
a
_ periódicas.
¡ Explotación
de
Introducción
de
Evaluación
y
e
en | malware en sistemas de continuo de proveedores o edo ' proveedores de | misión crítica.
. (ISO 27001 A.15).
A
A
Suminist
software, hardware o
| - Compromiso de datos
- Requisitos de seguridad en
E
00 >
UmINnIstro
para
| sensibles.
Contratos (Ley 21.663, CIS v8
Y)
y
. comprometer
los | - Impacto indirecto en la
1G1 Control 15.1).
E
IR

<!-- pág. 31 -->

sE”
BA mnisTERIODESALUD
[| ts-N0-007 | Versión:20 | Páginasode7?a PAN
Tipo de
Impactos Potenciales
Controles Clave para su
Ataque
Mitigación
sistemas internos de | confiabilidad de la
Gestión
de
riesgos
de
las
instituciones
de
atención médica.
terceros (NIST SP 800-161).
salud.
- Control de acceso mínimo
necesario.
Aislamiento
de
entornos
loo
— PE
lo
críticos.
E
rl
Acceso no autorizado | -
Multas
severas
por
- Cifrado en reposo y en
y
filtración
de
| incumplimiento
de | tránsito (ISO 27001 A.10).
médica
| normativas
de
Gestión
de
identidad
y
| sensible,
incluyendo
| privacidad.
acceso (IAM) robusta.
Robo de
A
5d
a
a
clínicos, | - Litigios legales.
- DLP (prevención de fuga de
Datos de
datos
personales
y | - Pérdida de confianza de datos).
Pacientes
resultados
de
¡los
pacientes
y
del
Auditoría
y
laboratorio.
público.
continuo (SIEM).
Concientización
y
a
. Capacitación en privacidad.
Manipulación
o
- Riesgo directo para la
- Gestión de inventario de
interrupción
del
seguridad y la vida de los activos médicos (ISO 27001 funcionamiento de pacientes.
A.8).
médicos
Interrupciones
en
- Segmentación de red para
A
conectados,
como
procedimientos médicos | dispositivos loMT.
taques a
h
m1
Dispositivos
bombas de infusión,
criticos."
Control de
firmware
y
p
z
marcapasos
o
-Potencialdetitigaciones actualizaciones seguras.
Médicos
monitores
de | legales graves.
- Evaluaciones de seguridad
pacientes.
periódicas.
Supervisión
continua
del
comportamiento
de
los
Y ZA
y PS
dispositivos.
Técnicas
de
engaño | - Acceso no autorizado a
Programas
de
dirigidas
a
personal
sistemas clínicos.
concientización
y simulacros
administrativo
y
Instalación
de
dephishing.
Ingeniería
clínico
para
obtener
ramsomwareospyware.
| - Autenticación
multifactor
Social
credenciales
o instalar
- Compromiso de redes
| (MFA).
(Phishingy
malware.
| internas
y bases de datos
Filtros
de
correo
y
Spear
| sensibles.
sandboxing.
Phishing)
Política
de
mínimo
privilegio.
Monitoreo
de
accesos
Saturación
de
los
-Caídade plataformasde ' -
Servicios
de
mitigación
sistemas
de
telemedicina,
DDoS
(WAF
y
CDN
con
a través | de urgencias o sistemas capacidad de absorción).
Ataquesde
de tráfico
malicioso, | administrativos.
Alta
y
Denegación
impidiendo
su | - Afectación directa a la redundancia (ISO
27001
de Servicio
disponibilidad.
de
la
A.17).
(DDoS)
| atención médica.
Plan
de
continuidad SN
- Pérdida de ingresos y
operativa
y DRP.
pS
deterioro de la imagen  - Monitorización de tráfico en o _| institucional.
tiempo real...
*"__W
A

<!-- pág. 32 -->

INSTRUCTIVO DE SEGURIDAD DE LAINFORMACIÓN Y CIBERSEGURIDAD PARA EL SECTOR SALUD
Página31de79
| TLP:BLANCO
PROTECCION DE LOS ACTIVOS CRITICOS Los activos críticos en las instituciones del sector salud son esos elementos clave que aseguran que la organización funcione de manera segura y eficiente. Si estos activos se ven comprometidos o destruidos, las repercusiones pueden ser graves: la calidad de los servicios de salud puede verse afectada, la seguridad de los pacientes puede estar en riesgo y la continuidad de las operaciones puede verse amenazada. Entre estos activos se incluyen, pero no se limitan a, la información sensible de los pacientes, los sistemas de gestión hospitalaria, los dispositivos médicos conectados, la infraestructura de redes y los sistemas de comunicación.
Protegery salvaguardar los activos críticos debe ser una prioridad en el ámbito de la seguridad de la información y la ciberseguridad en las instituciones del sector salud. Para lograrlo, es esencial se implementen controles preventivos, detectivos y correctivos adecuados, asegurando que estos activos sean identificados, monitoreados y protegidos en todo momento.
7.1. Identificación de Activos Críticos El primer paso para proteger los activos críticos es identificarlos de manera precisa. Esta identificación debe hacerse en colaboración con los responsables de las diferentes áreas de la institución, para así entender el valor y la importancia de cada activo en relación con los servicios que se ofrecen.
Los activos críticos incluyen, pero no se limitan a:
e
Datos
sensibles:
personal de
pacientes,
médicos,
diagnósticos, tratamientos, etc.
Sistemas y plataformas: Sistemas de gestión hospitalaria, sistemas de registros médicos electrónicos (EMR), plataformas de administración de citas, etc.
e
Infraestructura tecnológica: Servidores, bases de datos, redes, dispositivos de almacenamiento, sistemas de respaldo, etc.
Dispositivos médicos conectados: Equipos médicos que dependen de sistemas tecnológicos para su funcionamiento (p. ej., respiradores, monitores cardíacos, dispositivos de imágenes, etc.).
7.2. Clasificación de Activos y Niveles de Criticidad Todos los activos del sector salud deben clasificarse según su nivel de criticidad para la operación institucional, considerando su confidencialidad, integridad, disponibilidad y
A
cumplimiento regulatorio. Se recomienda el siguiente esquema:
5 YEADO <)
ñ
E

<!-- pág. 33 -->

BA
miisteriomesaLuo
| trs-Nc-007 [ versión:2o |  Páginas2de79
MANN
Ead
Ejemplos
o
operación
Historia
Clínica
Electrónica,
Core
HIS,
eos
Sistema de Imagenología (RIS/PACS), ERP
Crítico (C1)
MsStracianal, aleala, grano Ma institucional, plataformas de telemedicina, operacional o expone ne
Ñ
datos personales sensibles.
LO - o ci A
información sensible.
Sistemas
de
agenda,
laboratorio
(LIS),
Alto (C2) E PS MS e
gestión documental,
correo
institucional,
procesos operativos o de soporte.
Portales ciudadanos.
Su indisponibilidad es tolerable por tiempos definidos sin afectar la Portales informativos, intranet, sistemas de
Medio (C3)
seguridad o integridad del paciente o apoyo no críticos.
la lnstitución.
Bajo (C4)
No afecta procesos misionales y su
Sistemas
de
capacitación,
encuestas
co"  usoescomplementario.
internas, aplicativos no sensibles.
7.3. Controles para la Protección de los Activos Críticos La protección y defensa de los activos críticos es fundamental en la estrategia de seguridad de la información en el sector salud. Identificar correctamente, evaluar riesgos, implementar controles de seguridad y establecer una buena gobernanza son pasos clave para mantener estos activos a salvo de amenazas cibernéticas y otros peligros, garantizando así la continuidad operativa y la protección de la información sensible de los pacientes.
Para proteger los activos críticos, es esencial implementar un conjunto de controles de seguridad que aborden tanto las amenazas como las vulnerabilidades que se hayan identificado. Estos controles deben incorporar las medidas, que se describen a continuación:
7.3.1. Control de Acceso Autenticación Multifactor (MFA): Implemente la Autenticación Multifactor (MFA) de forma obligatoria para acceder a todos los sistemas y activos críticos, requiriendo al menos dos métodos de verificación distintos, como su contraseña más un código de su teléfono (TOTP o notificación push) o su huella digital. Asegúrese de integrar esta funcionalidad con el sistema centralizado de gestión de identidades (IAM) para facilitar su administración y seguimiento.
Autorización Basada en Roles y Atributos (RBAC): Defina e implemente un sistema de autorización que asigne permisos de acceso alos activos críticos basándose en los roles laborales o atributos específicos de los usuarios. Otorgue únicamente el nivel de acceso mínimo necesario para que cada usuario realice sus tareas, utilizando un sistema centralizado de gestión de roles y permisos y aplicando listas de control de acceso ¿AM2w (ACLs) detalladas a nivel de sistemas, aplicaciones y bases de datos.
¿RÓS
Gestión de Cuentas y Credenciales: Establezca políticas robustas para la administración
Í
de cuentas de usuario, incluyendo la creación, modificación, suspensióny eliminación. SA
AQ

<!-- pág. 34 -->

BN—ministerioDesaLuD
[ trs.wc-007 | versión:zo [  Páginassde7o
PMA
Obligue al uso de contraseñas complejas que cumplan con criterios de seguridad y cámbielas periódicamente.
Utilice
de
gestión
de
empresariales para un almacenamiento seguro y configure el bloqueo automático de cuentas tras varios intentos fallidos de inicio de sesión, además de monitorear la creación de cuentas con privilegios elevados.
e
Control de Acceso a la Red: Aísle los activos críticos del resto de la red mediante la segmentación, utilizando VLANs y microsegmentación.
Controle estrictamente el tráfico de red hacia y desde estos activos configurando firewalls internos con reglas específicas que permitan solo las comunicaciones necesarias, basándose en listas blancas de direcciones [P y puertos autorizados.
e
Seguridad en Dispositivos Médicos: Implemente medidas de seguridad específicas para proteger los dispositivos médicos conectados a la red. Asegure la autenticación y el control de acceso propios de estos dispositivos y segméntelos lógicamente en la red mediante VLANs dedicadas o reglas de firewall restrictivas que limiten su comunicación a los sistemas esenciales para su operación y gestión.
e
Gestión de Vulnerabilidades: implemente un proceso continuo para identificar, clasificar y corregir las vulnerabilidades en todos los sistemas y aplicaciones. Utilice herramientas automatizadas de escaneo, evalúe y priorice las vulnerabilidades según su riesgo, y aplique parches y actualizaciones de seguridad de manera proactiva para mantener los sistemas protegidos.
7.3.2. Protección de Datos e Cifrado de Datos: Implemente el cifrado robusto de toda la información sensible, tanto cuando se transmita (en tránsito) como cuando esté almacenada (en reposo), utilizando algoritmos como AES-258 o superior. Asegure una gestión segura de las claves de cifrado, preferentemente mediante Módulos de Seguridad de Hardware (HSM). Utilice protocolos de comunicación seguros como TLS 1.2 o superior para todo el tráfico web y la transferencia de datos, acompañados de conjuntos de cifrados seguros, y configure y administre correctamente los certificados digitales para garantizar la integridad y confiabilidad de las comunicaciones.
Prevención de Pérdida de Datos (DLP): Implemente herramientas de software DLP y defina políticas claras para prevenir la fuga de información sensible desde los activos críticos. Configure el software DLP para monitorear y controlar la transferencia de archivos, el correo electrónico y otros canales de comunicación, estableciendo reglas basadas en la clasificación de la información para evitar su divulgación no autorizada.
e
Integridad de los Datos: Implemente mecanismos para asegurar que los datos críticos no sean modificados por personal o procesos no autorizados. Utilice sumas de verificación (checksums), hashes criptográficos y firmas digitales para detectar alteraciones, e implemente un sistema de control de versiones para rastreary gestionar los cambios. Mantenga registros de auditoría detallados de todas las modificaciones
So
realizadas a los datos para su revisión y análisis.
z
Monitoreo Continuo: Establezca sistemas de monitoreo en tiempo real que supervisen
QA
la actividad de los sistemas y la red en busca de comportamientos sospechosos,
A

<!-- pág. 35 -->

MA wmisTERIODESALUD
[| is-NC-007 | Versión:20 |  Págima34de7s
PAM
intentos de acceso no autorizadoo fallas en los sistemas críticos. Configure alertas para identificar y responder rápidamente a posibles incidentes de seguridad.
.e
Análisis de Logs: Implemente un sistema centralizado de gestión de logs (SIEM) para recopilar y analizar todos los registros de actividad relevantes para los activos críticos.
Configure el SIEM para correlacionar eventos, detectar patrones anómalos y generar alertas tempranas de posibles incidentes de seguridad, facilitando la investigación y respuesta.
Pruebas de Penetración: Realice pruebas de penetración de forma periódica en los sistemas de información y la infraestructura que soportan los activos críticos. Estas pruebas deben simular ataques reales para identificar posibles vulnerabilidades que podrían ser explotadas, permitiendo tomar medidas correctivas antes de que ocurran
7.3.3. Seguridad de la Infraestructura:
e
Fortalecimiento de Sistemas Operativos y Aplicaciones: Configure de forma segura los sistemas operativos y las aplicaciones que dan soporte a los Activos Críticos, aplicando las mejores prácticas de "hardening”. Desactive todos los servicios y funcionalidades que no sean esenciales. Asegure la configuración correcta de los permisos de archivos y directorios, e implemente políticas de seguridad locales para restringir acciones no autorizadas.
Gestión de Parches y Vulnerabilidades: Establezca un proceso robusto para la gestión de parches y vulnerabilidades en los Activos Críticos. Identifique, evalúe y aplique las actualizaciones de seguridad necesarias para los sistemas operativos, aplicaciones y firmware de manera oportuna. Utilice herramientas automatizadas para la gestión de parches y realice escaneos de vulnerabilidades de forma periódica para detectar y corregir posibles debilidades.
e
Protección Antimalware Avanzada: Implemente soluciones antimalware de última generación en todos los equipos (endpoints y servidores) que interactúan con los Activos Críticos. Elija software que ofrezca detección basada en el comportamiento, análisis en entornos aislados (sandboxing) y análisis de amenazas en tiempo real para una protección más efectiva contra software malicioso avanzado.
e
Registros y Monitoreo de Seguridad (Logging y SIEM): Active el registro detallado de la actividad en los sistemas y aplicaciones que soportan los Activos Críticos. Centralice estos registros en un sistema SIEM (Security Information and Event Management) para su análisis y correlación. Configure el SIEM para detectar comportamientos anómalos, generar alertas automáticas ante posibles incidentes de seguridad y facilitar la investigación forense en caso de ser necesario.
7.3.4. Resiliencia y Recuperación:
LAMA
e.
Respaldos Regulares (Backups): Implemente un sistema de respaldos automáticos y 7
SS
periódicos para todos los datos críticos, almacenándolos de forma segura en A. :
ubicaciones separadas geográficamente, idealmente utilizando servicios seguros en la
TON IE

<!-- pág. 36 -->

BON
miusterioDesaLuD
| ts-wc-007 | vVersión:zo [  Páginassde7o
PROA
nube o sitios de recuperación ante desastres. Asegúrese de cumplir con la regla 3-2-1 de respaldos, manteniendo al menos tres copias en dos medios diferentes, con una copia fuera del sitio principal, aislada y protegida contra accesos no autorizados. Automatice pruebas de restauración periódicas para verificar la integridad y funcionalidad de los respaldos como parte de los planes de continuidad operativa y recuperación ante e Planes de Recuperación ante Desastres (DRP): Desarrolle, implemente y mantenga un Plan de Recuperación ante Desastres (DRP) para asegurar la continuidad operativa de los activos críticos frente a interrupciones.
Identifique y clasifique los activos esenciales, defina los objetivos de recuperación (RTO y RPO), implemente sitios de respaldo (frio, tibio o caliente) según la criticidad, y realice simulacros periódicos para validar la efectividad del plan. Mantenga el DRP actualizado ante cambios tecnológicos o de riesgo.
e
Plan de Respuesta ante Incidentes: Establezca y documente un Plan de Respuesta ante Incidentes de Ciberseguridad que incluya procedimientos claros y técnicos para la identificación, contención, erradicación y recuperación de los activos críticos en caso de verse comprometidos. Defina roles y responsabilidades técnicas dentro del plan y asegúrese de que el equipo esté capacitado para ejecutar los procedimientos necesarios.
7.3.5. Seguridad en la Nube:
Configuración Segura de Servicios Cloud: Configure los servicios en la nube que alojan los Activos Críticos siguiendo las directrices de seguridad recomendadas por el proveedor. Implemente políticas de Gestión de Identidades y Accesos (IAM) específicas para el entorno cloud, defina y configure reglas de firewall y grupos de seguridad para controlar el tráfico de red, y asegúrese de utilizar las opciones de cifrado que ofrece el proveedor de la nube para proteger los datos en reposo y en tránsito.
Monitorización de la Seguridad en la Nube: Utilice las herramientas de monitorización y seguridad nativas del proveedor de la nube para supervisar la actividad y detectar posibles amenazas dirigidas a los Activos Críticos. Configure alertas para eventos de seguridad relevantes, como intentos de acceso no autorizados o configuraciones sospechosas, e integre los registros de actividad de la nube con su sistema SIEM (Security Information and Event Management) para una visión centralizada de la seguridad.
7.4. Matriz de controles por Nivel de Criticidad de Activos
EN
Se detalla a continuación, una propuesta de controles que deben ser implementados de
ES)
acuerdo con la criticidad de los activos:
z
o
A

<!-- pág. 37 -->

ae.
MÍA — WMINISTERIODESALUD
Página36de79
Control/Requisito
Tipo
C1 (Crítico)
C2 (Alto)
C3 (Medio)
C4 (Bajo)
A
S
E
Muttifactor (MFA)
Acceso
Opcional
Autorización
Basada
en Roles y Atributos
Acceso
Opcional
AA E IA, A A
A A PI
PA| EN
Gestión de Cuentas y
A
obli
Ob
a
and
Opcional
Credenciales
cceso
igatorio
igatorio
ecomendado
pciona
Control
de Accesoa la
Ñ
Red (Segmentación)
Red
Obligatorio | Recomendado
Opcional
en
Dispositivos ' Médicos — Dispositivo
Opcional
Opcional
(Autenticación
y
S
do
Semen AA
AAA]
Gestión de Parches y
Escaneo periódico de
General
Opcional
Cifrado
en tránsito y
reposo (TLS 1.2+/AESDatos
Opcional
256)
Prevención
de
Reda
Pérdida
de
Datos
Datos
Opcional
Opcional
do
AA AS YE
### 2. ERI
AA
Integridad
de
los
Datos
(Checksums,
R
d
hashes
Datos
Obligatorio E É
Opcional
Opcional
criptográficos
Firmas, Auditoría)
Monitoreo Continuo | esauridad | Obligatorio e
Opcional
Opcional
Análisis de Logs.| AAAA
A
AA
(SIEM)
Obligatorio SS
Opcional
Opcional
Pruebas
de
o
Recommend
Opcional
Opcional
Periódicas
do
p
P
'Fortalecimiento
de
a E
E
A AS
e ÉSaaron
Sistemas
Resmenta
Opcional
Opcional
Aplicaciones
do
(Hardening)
EA AE. IOA
Gestión de Parches y
Vulnerabilidades
Sistemas
Opcional
Antimalware
iS
Obligatorio | Obligatorio Recomendado | Opcional ¿VISADAP"
Avanzada
ervidores
IA

<!-- pág. 38 -->

INSTRUCTIVO DESEGURIDAD DE LA INFORMACIÓNYCIBERSEGURIDAD PARAEL SECTORSALUD a
MN
ITS-NC=007
Control/Requisito
Tipo
C1 (Crítico)
C2 (Alto)
C3(Medio)
. C4(Bajo)
. Registros y Monitoreo
L
me
i
de Seguridad (Logging
| Seguridad
ecomenca
Opcional
Opcional
do
y SIEM)
Copias de respaldo
con
prueba
de| Respaldo
- Recomendado
Opcional
restauración
ul
H
Y
Planes
de
A
d
Recuperación
ante
Respaldo
Obligatorio a .
Opcional
| Opcional
Desastres (DRP)
Plan de Respuesta
ns:
E
ántelnerdentes
: Recomendado
Opciona
| Configuración Segura
Pz
¡de
Servicios
Cloud
| (Features
de
Nube
de
Opcional
pciona
Seguridad)
a
A
pa.
Es RN
PA
: Monitorización
de
la
| Seguridad en la Nube
Nube
Opcional
| Opcional
Revisión anual
de |
e
mA
TS
: contratos y cláusulas
Contratos
Opcional
*! de seguridad
na
_
ña
h
Evaluación de código
RecómiBada
seguro
(OWASP, — Seguridad
do
Opcional:
SAST/DAST)
E
pu,
o
a:
AA
8. PROTECCION DE INFORMACION La protección de la información es fundamental en la gestión de la seguridad y ciberseguridad en el sector salud. Dado la sensibilidad de los datos clínicos, personales y administrativos que se manejan en las instituciones de salud, es vital implementar controles y medidas que garanticen su resguardo frente a accesos no autorizados, pérdida, alteración o divulgación indebida. Esta protección debe estar presente a lo largo de todo el ciclo de vida de la información, desde su creación hasta su destrucción segura.
Para cumplir con esta responsabilidad, las instituciones deben seguir las siguientes directrices:
8.1. Clasificación de la Información Toda información institucional debe ser clasificada conforme a su nivel de sensibilidad,
A
confidencialidad e impacto en caso de compromiso.
SADO =
e
La clasificación mínima debe incluir las siguientes categorías: Pública, Uso Interno, Confidencial y Información Sensible de Salud.
e

<!-- pág. 39 -->

ae”
MÍ
Página38de79
e.
Esta clasificación debe estar documentada, difundida y aplicada de manera transversal en todos los procesos tecnológicos y operativos.
8.2. Control de Accesoa la Información e Se debe aplicar el principio de privilegio mínimo, asegurando que cada usuario acceda únicamentea la información necesaria para el desempeño de sus funciones.
Es obligatorio implementar mecanismos de autenticación fuerte (por ejemplo, autenticación multifactor) en sistemas que gestionen información crítica o sensible.
e
Todos los accesos deben ser registrados, monitoreados y auditados de forma continua.
8.3. Protección en Tránsito y en Reposo La información debe ser cifrada cuando se almacene [en reposo) y durante su transmisión (en tránsito) mediante el uso de algoritmos criptográficos robustos aprobados por estándares internacionales como NIST o ISO/IEC.
Sedeberán implementar mecanismos criptográficos robustos para proteger el acceso y almacenamiento de credenciales de usuario, bases de datos del sistema y la transmisión de información sensible.
e
Está prohibido el uso de canales inseguros para el envío de información sensible, incluyendo correos electrónicos sin cifrado o dispositivos de almacenamiento portátiles sin protección.
e
Seguridad en la Transmisión de Datos: Todos los sitios y sistemas web deben cifrar las comunicaciones entre cliente y servidor utilizando HTTPS con certificados emitidos por entidades acreditadas en el país.
Se debe emplear TLS 1.2 o superior como estándar mínimo para garantizar la seguridad en la transmisión de datos, acompañados de conjuntos de cifrados seguros.
e
Cifrado en Reposo: Toda información almacenada debe estar protegida mediante AES256 o RSA-4086, u otros algoritmos aprobados en la política de uso de criptografía.
e
Se deben
utilizar sistemas de gestión segura de claves criptográficas para su generación, almacenamiento y rotación periódica.
e
Protección de Contraseñas:
El almacenamiento de contraseñas debe realizarse con algoritmos diseñados para resistir ataques de fuerza bruta, como bcrypt, PBKDF2 y
Argon2.
e
Monitoreo y Prevención de Vulneraciones: Se deben aplicar controles técnicos y administrativos para la detección temprana de intentos de vulneración del sistema de LAME, cifrado.
án
a)
e Los sistemas deben estar configurados para seleccionar siempre la opción de cifrado> E e más segura disponible.
E.
E

<!-- pág. 40 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN YCIBERSEGURIDAD a =
MÍ
——MINISTERIODESALUD
Página32de79
8.4. Almacenamiento y Resguardo e Lainformación debe ser almacenada únicamente en infraestructuras autorizadas por el Ministerio de Salud o por el organismo correspondiente, que cumplan con estándares de seguridad y con ubicación geográfica bajo jurisdicción nacional, salvo autorización expresa.
e
Los sistemas de respaldo deben garantizar la recuperación segura e íntegra de la información en caso de incidenteso fallas.
8.5. Eliminación y Destrucción Segura La eliminación y destrucción de información en las instituciones del sector salud debe realizarse bajo estrictos estándares de seguridad, con el fin de evitar la recuperación no autorizada de datos sensibles o críticos.
Este proceso debe ser trazable, auditable y alineado con la normativa vigente, incluyendo la Ley N* 21.719 sobre Protección de Datos Personales y la Ley N? 21.663 sobre Ciberseguridad.
Adicionalmente, en este proceso debe tenerse en cuenta lo previsto en la ley N* 20.584 sobre derechos y deberes del paciente, en el decreto N* 41, Reglamento de ficha clínica y su normativa complementaria.
Las siguientes directrices deberán ser cumplidas por todas las instituciones y proveedores que gestionen datos en el marco del Ministerio de Salud:
e
Lainformación clínica que conste en la ficha clínica y los documentos correspondientes a resultados de exámenes, recetas médicas, licencias médicas y demás documentos que la normativa señala que integran la ficha clínica no podrán ser objeto de borrado sin la autorización expresa y por escrito de la dirección médica del establecimiento.
Laeliminación de información deberá efectuarse mediante métodos seguros de borrado lógico (como sobre escritura múltiple con herramientas certificadas)y,cuando aplique, destrucción física de los soportes (por ejemplo, trituración, desmagnetización o incineración), de acuerdo con los estándares internacionalmente aceptados (NIST SP
800-88 Rev. 1, ISO/IEC 27040, entre otros).
e
Todaeliminación de información crítica o sensible debe ser registrada mediante actas o bitácoras, especificando el tipo de datos, el método utilizado, los responsables del proceso y la fecha de ejecución. Estos registros deben conservarse conforme a la política de retención documental del organismo.
e
Toda modificación, cancelación o destrucción de datos deberá realizarse Unicamente bajo instrucción explícita del mandante o autoridad responsable de la información.
Dichas instrucciones deberán ser documentadas y vinculadas al acta del proceso.
e
Enloscasos en que la información sea gestionada por un tercero (procesador de datos),
100%
este será responsable de ejecutar el proceso de eliminación conforme a los lineamientos ño)
o
contractuales y regulatorios, dejando constancia formal de cada una de las etapas y a —á resultados del procedimiento.
A

<!-- pág. 41 -->

MÍA — MINISTERIODESALUD
Página40de79
Todo dispositivo digital o soporte magnético que vaya a ser descartado debe someterse previamente a procesos de formateo o sanitización segura, evitando cualquier posibilidad de recuperación de datos. Está prohibido reutilizar equipos con datos sensibles sin aplicar procedimientos de limpieza certificados.
e
En proyectos de digitalización, queda estrictamente prohibido que los proveedores eliminen, destruyan o desechen los documentos originales sin contar con una autorización formal del mandante, la cual debe estar debidamente documentada.
8.6. Protección en Entornos de Nube Cuando se utilicen servicios en la nube o se externalicen procesos que involucren el tratamiento de información, las Instituciones del Sector Salud deben exigir al proveedor garantizar niveles de seguridad equivalentes o superiores a los establecidos por la normativa nacional vigentey las directrices ministeriales.
Para ello, los contratos deben incluir obligatoriamente cláusulas explícitas que aseguren la confidencialidad, integridad y disponibilidad de la información, así como el cumplimiento riguroso de la Ley N? 21.719 sobre Protección de Datos Personales, la Ley N? 21.663 Marco de Ciberseguridad, y otros cuerpos regulatorios aplicables.
Estas cláusulas deberán estar alineadas con las directrices definidas por el MINSAL en el Instructivo sobre Cláusulas de Protección de Datos y Seguridad, en su versión actualizada y vigente.
Además, es necesario implementar controles técnicos sólidos para proteger tanto la capa de software como los servicios que se despliegan en la nube, asegurando que estén a salvo de vulnerabilidades y accesos no autorizados:
Encriptación de Datos: Para proteger datos confidenciales y sensibles, se deben aplicar técnicas de cifrado robustas que impidan accesos no autorizados.
Toda la información almacenada en entornos de nube debe cifrarse utilizando estándares avanzados como AES-256.
e
Losdatosen tránsito deben protegerse mediante protocolos seguros, tales como TLS 1.3.
e
Lasclaves criptográficas deben ser generadas, administradas y almacenadas en sistemas seguros, preferentemente en Módulos de Seguridad de Hardware (HSM).
Se debe implementar autenticación multifactor (MFA) para el acceso a claves y sistemas donde se almacenen datos cifrados.
Seudonimización:
Cuando se trate de datos personales sensibles, se recomienda aplicar técnicas de seudonimización, conservando en servidores locales los códigos que permitan su
LETS
reidentificación. Esto busca evitar riesgos asociados a normativas de desencriptación forzosa EA en otrasjurisdicciones, garantizando el cumplimiento de la Ley 19.628 y los artículos 19 N*1 y Eo N24 de la Constitución Política.
SUI

<!-- pág. 42 -->

MN
e
Se recomienda
el uso de técnicas como tokenización y enmascaramiento, que sustituyen los datos reales por valores irreversibles fuera del sistema autorizado.
e
Las claves de seudonimización deben gestionarse de forma segura y almacenarse en sistemas separados.
Elasticidad: Se debe planificar anticipadamente la capacidad requerida en servicios cloud, permitiendo la asignación dinámica de recursos según las necesidades.
e
Losservicios contratados deben ser elásticos, capaces de escalar automáticamente.
e
Los contratos deben contemplar márgenes de crecimiento sin necesidad de nuevas licitaciones.
Garantía de Disponibilidad: Los sistemas deben estar diseñados para operar en esquemas de alta disponibilidad(HA]), con recursos distribuidos en múltiples regiones o zonas.
e
Deben establecerse mecanismos de restauración rápida ante incidentes críticos, como ciberataques o desastres, mediante planes BCP/DRP alineados con estándares internacionales.
Geolocalización y Protección de Datos Sensibles: El tratamiento de datos de geolocalización debe limitarse a lo estrictamente necesario.
Siestos datos se procesan fuera de Chile, el proveedor debe garantizar estándares de protección equivalentes a los nacionales.
e
Se deben aplicar medidas como cifrado en tránsito y en reposo, y controles de acceso restringido.
e
Los titulares deben poder ejercer sus derechos de acceso, y cuando corresponda, rectificación o cancelación, sin afectar la función del organismo.
e
ElMINSAL deberá mantener trazabilidad mediante registros de tratamiento y accesos, y realizar auditorías periódicas que aseguren la aplicación efectiva de estas medidas.
Automatización de Respaldos y Pruebas de Restauración: Los sistemas críticos deben contar con respaldos automatizados en la nube, con pruebas regulares de restauración que aseguren su disponibilidad y funcionalidad en caso de contingencias.
Distribución de Copias: Las copias deben almacenarse en múltiples regiones, incluyendo al menos una en infraestructura ubicada en Chile.
e
Se deberá evitar
la replicación automática fuera del país, o bien, controlarla
E
estrictamente.
SA
+ Se recomienda un enfoque híbrido: copia primaria en infraestructura propia (local o ¡58D aj privada)ysecundaria en nube pública, garantizando redundancia y control.
A

<!-- pág. 43 -->

ae”
MÍ
rnusterio nesacoo | trs-nc-007 [ versiónizo [ Páginauadezo
PIBES
Monitoreo y Registro de Eventos: El proveedor debe habilitar registros detallados (logs) en todas las capas del sistema.
e
Se
deben
usar
de
gestión
de
parches,
configurar
alertas
de
vulnerabilidades críticas y permitir respuestas automáticas.
e
Sedebe auditar:
o
Autenticaciones y accesos (exitosos/fallidos).
o
Eventos de red sospechosos.
o
Modificaciones en configuraciones y permisos.
o
Accesos
y
manipulaciones
de
datos
sensibles,
cumpliendo
el
principio
de
minimización.
Protección contra Amenazas Se debe implementar una arquitectura de seguridad en capas con mecanismos de detección, prevención y respuesta ante amenazas avanzadas, incluyendo:
Web Application Firewall (WAF):
e
Configure un WAF delante de las aplicaciones web expuestas en la nube para inspeccionar el tráfico HTTP/HTTPS y bloquear ataques a nivel de aplicación.
e
Implemente reglas de protección contra vulnerabilidades comunes como Cross-Site Scripting (XSS), Inyección SQL (SQLi) y File Inclusion Remota (RFI), basándose en firmas de ataque conocidas y comportamiento anómalo. Personalice las reglas según las necesidades específicas de las aplicaciones. Integrar el WAF con sistemas de registro y alerta para monitorizar y responder a posibles incidentes.
Protección contra ataques de Denegación de Servicio Distribuido (DDoS)
e
Lainfraestructura debe estar protegida contra intentos de saturar servicios mediante múltiples peticiones simultáneas.
e
Un ataque DDoS puede dejar fuera de línea portales de atención, sistemas de agendamiento y otras aplicaciones críticas.
Sedeben emplear servicios de mitigación que identifiquen patrones anómalos de tráfico y redirijan ataques antes de que lleguen a los sistemas internos.
e
Estaprotección debe estar habilitada tanto a nivel de red como de aplicación.
Inteligencia de Amenazas e Indicadores de Compromiso (loCs)
e
Lasolución debe integrar fuentes de inteligencia de amenazas (Threat Intelligence) para anticiparse a ataques conocidos y emergentes.
LosloCs(Indicadores de Compromiso)son evidencias técnicas (IPs, hashes de archivos, dominios maliciosos, etc.) que permiten detectar intrusiones en curso o pasadas.
e
Estas capacidades deben:
o
Estarintegradas con los sistemas de monitoreo y análisis de seguridad(como SIEM LME o XDR).
A |
p
O
as
PASA
E
o
Permitir respuestas automatizadas ante detecciones críticas.
o y
o
Aportar a una mejora continua del sistema defensivo y a una postura de seguridad “2 proactiva.
A

<!-- pág. 44 -->

BE
Página43 de 79
Políticas de lAM Basadas en Mínimos Privilegios y Roles:
e
Defina e implemente políticas de Gestión de Identidades y Accesos (IAM) que otorguen a usuarios, grupos y servicios cloud únicamente los permisos mínimos necesarios para realizar sus funciones.
Utilizar
roles
para
agrupar
permisos
basados
en
responsabilidades laborales.
e
Cree roles con permisos específicos para cada función. Asignar usuarios y servicios a estos roles en lugar de otorgar permisos directos. Revisar y auditar periódicamente las políticas de lAM para asegurar el cumplimiento del principio de mínimo privilegio. Utilizar herramientas de gestión de lAM proporcionadas por el proveedor de la nube.
Zero Trust Network Access (ZTNA):
Implemente un modelo de acceso Zero Trust para los servicios cloud, donde cada solicitud de acceso se verifica rigurosamente basándose en la identidad del usuario, el contexto de la solicitud (ubicación, hora, dispositivo) y el cumplimiento de las políticas de seguridad del dispositivo.
e
Configure una solución ZTNA que valide la identidad del usuario mediante mecanismos fuertes (MFA), evalúe el estado de seguridad del dispositivo antes de otorgar acceso y aplique políticas de acceso granular basadas en el contexto. Utilizar microsegmentación para limitar el radio de explosión en caso de compromiso.
Autenticación Multifactor (MFA):
e
Habilite y exija Autenticación Multifactor (MFA) para todos los accesos a la consola de administración de la nube, a los servicios cloud y alos recursos sensibles.
e
Configure MFA utilizando al menos dos factores de autenticación diferentes, como una contraseña y un código generado por una aplicación móvil(TOTP), un token de hardware, o datos biométricos. Asegurar la correcta implementación y el cumplimiento de las políticas de MFA.
Secure Access Service Edge (SASE):
Evalué e implemente una solución SASE para integrar funciones de seguridad en la nube con capacidades de red definidas por software (SD-WAN), centralizando la gestióny el control del acceso a los servicios cloud desde el borde de la red.
e
Configure la SD-WAN para optimizar la conectividad y el rendimiento. implementar los componentes de seguridad SASE como Firewall como Servicio (FWaaS), Puerta de Enlace Web Segura (SWG), Agente de Seguridad de Acceso a la Nube(CASB) y Zero Trust Network Access (ZTNA), según los requisitos de acceso y seguridad.
### 9. RESPUESTA ANTE INCIDENTES DE SEGURIDAD DE LA INFORMACION Y
CIBERSEGURIDAD, CONTINUIDAD OPERACIONAL
É paA
Es crucial responder de manera efectiva a los incidentes que afectan la seguridad de la
ENEDO
informacióny la ciberseguridad en el sector salud. Esto no solo protege los datos sensibles, sino que también asegura la seguridad de los pacientes y garantiza que los servicios de salud o

<!-- pág. 45 -->

ae”
MÍA—vWinisTERIODESALUD|
Página 44de79
MRASNN
funcionen sin contratiempos. La respuesta a estos incidentes debe ser planificada, eficiente yseguir las mejores prácticas de seguridad.
Además, los planes de continuidad operativa deben garantizar que las funciones esenciales sigan funcionando, incluso si se presenta un incidente. Este apartado tiene como objetivo establecer los procedimientos necesarios para gestionar los incidentes de seguridad de la información y asegurar la continuidad operativa en las instituciones del sector salud.
9.1. Incidentes de seguridad de la Información y Ciberseguridad De acuerdo con la Ley N* 21.663, su Reglamento de Reporte de Incidentes (Decreto N*
295/2024) y los estándares internacionales de ciberseguridad, todas las instituciones, tanto públicas como privadas, incluyendo las del Sector Salud, están obligadas a desarrollar, implementar y mantener un Plan de Respuesta ante Incidentes (IRP). Este plan es crucial para gestionar de manera efectiva y oportuna cualquier evento que ponga en riesgo la seguridad de la informacióny la ciberseguridad, y debe facilitar la coordinación con la Agencia Nacional de
Ciberseguridad.
El IRP debe estar en línea con la normativa vigente, revisarse de forma regular y contar con procedimientos claros para la notificación y el reporte de incidentes, especialmente aquellos que involucren datos sensibles o que puedan afectar la continuidad operativa. Es fundamental que el plan se mantenga actualizado y sea accesible para el personal pertinente.
La respuesta ante incidentes debe ser un proceso bien planificado, documentado y ejecutado rápidamente para reducir al mínimo los riesgos sobre la disponibilidad, integridad y confidencialidad de la información.
9.1.1.Plan de Respuesta ante Incidentes (IRP)* El Plan de Respuesta ante Incidentes (IRP) es un documento esencial que define los pasos l organizativos y técnicos a seguir para detectar, analizar, contener, eliminar y recuperarse de incidentes relacionados con la ciberseguridad o la seguridad de la información que puedan afectar a los sistemas, datos o servicios de una institución. Su objetivo principal es reducir al mínimo el impacto de estos incidentes, restablecer la normalidad en las operaciones de manera efectiva y aprender de la experiencia para reforzar las defensas en el futuro.
Para garantizar una gestión efectiva de los incidentes de seguridad de la información y ciberseguridad, las Instituciones del Sector Salud deben crear, implementar y mantener un Plan de Respuesta ante Incidentes (IRP) que contemple y desarrolle de manera detallada las siguientes etapas fundamentales:
Preparación:
o
Debe definir los roles y responsabilidades dentro del equipo encargado de WA responder a incidentes, asegurando que cada miembro sepa exactamente qué ¿ VIS
S
hacer si ocurre un
problema.
a
S
p
UE,
5 CISA - cybersecurity incident 8 vulnerability response playbooks.
AAA

<!-- pág. 46 -->

a—
MÍN
Página45de79
o
Desarrolle y lleve a cabo simulacros de incidentes cibernéticos es clave para que el personal esté bien preparado.
o
Asegúrese de que todos los sistemas y datos críticos estén respaldados correctamente y que los procedimientos de restauración estén listos para usarse.
Detección y Notificación:
o
Establezca mecanismos de monitoreo continuo, como un SIEM (Sistema de Gestión de Información y Eventos de Seguridad) es esencial para detectar incidentes en tiempo real.
o
Implemente procedimientos claros para que los colaboradores puedan reportar incidentes de seguridad de inmediato, incluyendo contactos de emergencia.
Evaluación y Contención:
o
Evalué la naturaleza y el alcance del incidente, lo que incluye identificar los activos afectados y la magnitud de la brecha de seguridad.
o
Implemente medidas para contener el incidente y evitar que se propague, como desconectar sistemas comprometidos o revocar accesos.
e
Erradicación:
o
Elimine
las
amenazas
y
relacionadas
con
el
incidente,
asegurándose de que los sistemas afectados sean limpiados y que se apliquen parches o soluciones de seguridad para prevenir futuros problemas.
e
Recuperación:
o
Restaure los sistemas y servicios afectados es crucial, asegurando que se sigan los procedimientos de recuperación previamente establecidos.
o
Verifique los sistemas restaurados estén libres de amenazas y funcionando de manera segura.
Revisión Post-Incidente:
o
Realizar un análisis post-incidente para identificar las lecciones aprendidas, actualizar los procedimientos y mejorar los controles de seguridad.
o
Redactar un informe detallado que incluya las causas identificades, las acciones tomadas, el impacto del incidente y las recomendaciones para evitar incidentes futuros.
9.1.2. Comunicación en Caso de Incidente Es crucial que exista una estrategia de comunicación clara durante un incidente de seguridad. Esta debe cubrir tanto las comunicaciones internas como externas, y debe incluir:
e
Notificación inmediata a los responsables y a los equipos clave dentro de la institución (IT, seguridad, gerencia).
e
Comunicación con autoridades competentes, si el incidente involucra una violación de mE datos sensibles o si hay obligación de reportarlo bajo la ley.
Maso
e Manejo de la comunicación con el público y los pacientes, especialmente si el incidente afecta los servicios que reciben.
AU DE

<!-- pág. 47 -->

ae”
BA
vinisterioDEsaLuD  [ is-Nc-007 | Versión:zo [  Página“sde79
MANN
9.1.3. Reporte de Incidentes de Ciberseguridad: Procedimiento y Plazos Obligatoriedad del Reporte: De acuerdo con el Artículo 3” del Decreto N* 295/2024, que aprueba el reglamento de reporte de incidentes de ciberseguridad, todos los organismos del Sector Salud que presten servicios esenciales están obligados a reportar aquellos incidentes que se consideren de impacto significativo, según los criterios definidos en dicho decreto El reporte es crucial para la documentación exhaustiva del incidente y para la comunicación oficial con las autoridades competentes, en particular con la
Agencia
Nacional
de
Ciberseguridad (ANCI).
Plataforma Oficial de Reporte (ANCI): A estos efectos, la Agencia ha dispuesto en siguiente portal de notificación de incidentes: https://portal anci gob .el/, Las instituciones del Sector Salud deberán utilizar este sitio web para notificar sus incidentes significativos.
Canales de Comunicación Alternativos (Contingencia): En caso de contingencia o problemas con la plataforma principal, la ANCI mantiene operativos los siguientes canales alternativos para el reporte y la comunicación:
e.
Teléfono: 1510
e
Correo Electrónico: ayudaWanci.gob.cl Es fundamental que las instituciones del Sector Salud conozcan y utilicen los canales designadosy sigan los procedimientos establecidos para el reporte oportuno y adecuado de los incidentes de ciberseguridad, cumpliendo así con las obligaciones legales y contribuyendo a la seguridad del sector a nivel nacional.
Requisitos para el Reporte: Para realizar el reporte a través de la plataforma, el responsable delegado por la dirección de la notificación dentro de la institución del Sector Salud (CISO)
deberá
registrarse
utilizando
su
Clave
Unica.
Posteriormente,
deberá
completar
la
información solicitada en cada uno de los tres pasos del proceso de reporte.
Contenido del Reporte y Taxonomía: El contenido específico que debe incluirse en cada etapa del reporte está regulado por el Decreto N” 295/2024. Adicionalmente, para proporcionar una guía técnicay facilitar la clasificación de los incidentes, la ANCI ha aprobado y publicado una Taxonomía de Incidentes de Ciberseguridad a través del DS 7/2025.
Etapas y procedimiento de Reporte en la Plataforma ANCI: El proceso de reporte se realiza en tres etapas secuenciales dentro de la plataforma:
Alerta Temprana:
e
Oportunidad: dentro de las 3 horas posteriores a la detección del incidente.
AR
PES
e Contenido: Información preliminar disponible sobre la naturaleza, el alcance y el posible A
Dn o!
impacto del incidente.
Dos e
e
DO

<!-- pág. 48 -->

INSTRUCTIVODE SEGURIDAD DELA INFORMACIÓN Y CIBERSEGURIDAD PARAELSECTOR SALUD
CN
BN
Página47de79
e
Contenido:
o
Descripción del incidente, incluyendo el tipo de amenaza detectada (ej., malware, acceso no autorizado, denegación de servicio).
o
Identificación de los sistemas, aplicaciones o datos afectados.
o
Gravedad estimada del incidente.
o
Acciones iniciales que se han tomado para contener el incidente.
o
Impacto potencial en la institución y en los servicios prestados.
Segunda Notificación:
e
Oportunidad: dentro de los 72 hrs siguientes a la confirmación del incidente.
Destinatario: ANC! y autoridades competentes.
e
Contenido: Reporte detallado del incidente, que incluya:
o
Información adicional sobre la evolución del incidente.
o
Detalles sobre las medidas adoptadas para la contención y erradicación del incidente.
o
Descripción de la restauración de los sistemas afectados y la reanudación de la operación normal.
o
Evaluación del impacto real en la confidencialidad, integridad y disponibilidad de los datos.
o
Informe de cualquier brecha de seguridad o violación de datos personales.
Informe Final:
Oportunidad: Dentro del plazo máximo de 15 días corridos contados desde el envío de la alerta temprana.
e
Condición: Al concluir la gestión del incidente. Una vez que el incidente ha sido completamente contenido, erradicado y los sistemas restaurados.
e
Destinatario: Este informe debe entregarse a las autoridades competentes, así como al Comité de Seguridad de la Información de la institución.
Contenido: El informe debe incluir el registro detallado de la información levantada respecto del incidente.
o
Unresumen completo del incidente desde su detección hasta su resolución.
o
El detalle las causas del incidente, las acciones de respuesta impiementadas.
o
Evaluación del impacto total del incidente y las lecciones aprendidas o Medidas preventivas adoptadas para evitar futuras para mitigar riesgos futuros.
o
Cualquier recomendación para mejorar los controles de seguridad o Protocolos de respuesta ante incidentes.
Coordinación Central: Las instituciones del sector salud pueden, además, establecer coordinaciones estratégicas con el Ministerio de Salud, a través de su CISO o de la Unidad de Seguridad de la Información y Ciberseguridad, del Departamento de Tecnologías de Información y Comunicaciones. Estas coordinaciones permiten articular acciones conjuntas en ámbitos como la gestión de proveedores de red, la aplicación de recomendaciones iniciales
| pue A
para el fortalecimiento de la postura de ciberseguridad institucional. Asimismo, estas
SADO
instancias pueden facilitar el apoyo técnico y operativo necesario para el restablecimiento a e

<!-- pág. 49 -->

ae
eN,
oportuno de los servicios afectados, en coordinación con el CSIRT Nacional, asegurando una respuesta eficaz ante incidentes de ciberseguridad de alto impacto.
Adicionalmente, se mantendrán operativos los siguientes canales Ministeriales disponibles para comunicarse en caso de contingencia:
e
Alteléfono 800 123573 e
Alcorreo electrónico masominsal.el e
Alcorreo electrónico seguridadticominsal.cl Informe de Lecciones Aprendidas:
o
Este informe debe ser realizado por el equipo de respuesta tras la resolución del incidente, y debe incluir un análisis detallado de las lecciones aprendidas, con el objetivo de mejorar la estrategia de ciberseguridad de la institución.
o
Este informe debe ser distribuido internamente a todas las partes interesadas y, sies necesario, se debe presentar a las autoridades competentes.
9.1.4. Confidencialidad y Protección de la Información Según lo establecido en la Ley N* 21.663, las instituciones tienen la responsabilidad de asegurarse de que la información relacionada con incidentes de ciberseguridad se comparta únicamente con las autoridades competentes y otras partes que estén debidamente autorizadas.
Por lo tanto, toda la información que se encuentra en las alertas, reportes e informes sobre incidentes, debe ser tratada con la máxima confidencialidad. Esto es crucial para prevenir la divulgación no autorizada de datos sensibles y para proteger la seguridad de los sistemasy la información involucrada.
9.2. Continuidad operacional El objetivo de la continuidad operativa es garantizar que las funciones críticas de la institución continúen sin interrupciones, incluso durante un incidente de seguridad. Esto es fundamental para asegurar que los servicios de salud no se vean comprometidos y que los pacientes no sufran consecuencias negativas debido a la caída de los sistemaso la pérdida de información.
9.2.1. Plan de Continuidad Operacional (BCP) y Plan de Recuperación ante
Desastres (DRP)
Cada institución debe desarrollar un Plan de Continuidad de Negocio (BCP, por sus siglas en inglés) específico para el sector salud, integrado con un Plan de Recuperación ante DesastreskAM3,, (DRP), que contemple los siguientes elementos:
3 VS
+. Análisis de Impacto en el Negocio (BIA):
A

<!-- pág. 50 -->

E
MN
Página49de79
o
Identificar
las funciones
críticas que deben mantenerse operativas en todo momento, como el acceso a los médicos de los pacientes, la administración de tratamientos y la operación de dispositivos médicos.
o
Determinar el tiempo máximo tolerable de inactividad (RTO - Recovery Time Objective)y el punto de recuperación de los datos (RPO - Recovery Point Objective)
l
para cada servicio crítico.
Estrategias de Respaldo y Recuperación:
o
Asegurar que se implementen respaldos regulares y se mantengan en ubicaciones seguras (preferiblemente en la nube o en centros de datos redundantes).
o
Tener un plan de recuperación ante desastres que incluyan la restauración de sistemas críticos.
o
Desarrollar un plan detallado de recuperación ante desastres(DRP) que abarque la restauración de sistemas críticos, la recuperación de datos al punto definido por el RPOy la reanudación de servicios dentro del RTO establecido.
Planes de Emergencia:
o
Desarrollar planes específicos para situaciones de emergencia, como desastres naturales, fallos en la infraestructura, o ciberataques que puedan afectar la operación de la institución.
o
Establecer procedimientos claros para la evacuación de datos y la reubicación temporal de servicios en centros alternativos sies necesario.
9.2.2. Monitoreo de la Continuidad Operacional El monitoreo continuo es clave para asegurar la efectividad del plan de continuidad operacional. Las instituciones deben implementar sistemas que permitan:
e
Monitorear la salud de los sistemas críticos en tiempo real, con alertas automáticas si algún sistema falla o se ve comprometido.
e
Verificar periódicamente que los respaldos se estén realizando de acuerdo con el cronogramay que los procedimientos de recuperación sean efectivos.
e
Realizar simulacros regulares para poner a prueba la respuesta ante incidentes y la efectividad de los planes de recuperación de manera constante.
10. CIBERSEGURIDAD EN DISPOSITIVOS MEDICOS loT Los dispositivos médicos que cuentan con conectividad a redes (loT) son una parte esencial de la infraestructura tecnológica en el Sector Salud. Se integran directamente en procesos clínicos clave y en el cuidado de los pacientes. Debido a su naturaleza interconectada y a la sensibilidad de los datos de salud que manejan, es crucial que estos dispositivos cumplan con
EA
estrictos estándares de seguridad de la información y ciberseguridad.
E
y
En el ámbito del Sector Salud, los dispositivos loT abarcan una amplia variedad de equipos y sistemas, que incluyen, pero no se limitan a:
Do

<!-- pág. 51 -->

e
Equipos
médicos
conectados
para
el
continuo
de
signos
vitales,
administración precisa de fluidos y medicamentos (bombas de infusión) soporte ventilatorio (ventiladores)y regulación cardíaca (marcapasos).
e
Dispositivos portátiles diseñados para la realización de diagnósticos en diversos entornos.
Dispositivos implantables y conectados como marcapasos y desfibriladores, que requieren una gestión segura de sus comunicaciones.
Equipos de imagenología con capacidades de telemetría para la transmisión y análisis remoto de imágenes diagnósticas.
Sensores corporales portátiles o vestibles (wearables) utilizados para el seguimiento de parámetros fisiológicos.
e
Sistemas integrales para el monitoreo remoto de pacientes en sus hogares o en centros de atención extendida.
e
Dispositivos
inteligentes
implementados
en
entornos
críticos como
quirófanos,
unidades de cuidados intensivos y ambulancias, que pueden controlar funciones vitales o asistir en procedimientos complejos.
e
Equipos de diagnóstico avanzados con funcionalidades de conectividad y generación automática de reportes.
e
Sensores y dispositivos vestibles para el seguimiento remoto de la condición de pacientes crónicos o en rehabilitación.
e
Infraestructura inteligente dentro de los establecimientos de salud, como cámaras de seguridad conectadas, refrigeradores biomédicos con monitoreo de temperatura, y estaciones clínicas inteligentes para el acceso a información del paciente.
e
Estos dispositivos loT tienen la capacidad de recolectar y transmitir información de salud altamente sensible, lo que los sitúa bajo la rigurosa supervisión de normativas de seguridad y privacidad tanto a nivel internacional como nacional.
Es fundamental considerar:
La gestión de los dispositivos loT en el sector de la salud necesita un enfoque integral que considere tanto la ciberseguridad como el cumplimiento de normativas vigentes. Esto significa que se deben implementar medidas técnicas y organizativas, como llevar un inventario detallado de los dispositivos, segmentar la red para mantenerlos aislados de otros sistemas, asegurar la autenticación de dispositivos y usuarios, aplicar actualizaciones de seguridad de manera regular, monitorear continuamente su actividad, cifrar los datos que transmiten y almacenan, mantener un registro de eventos relevantes para la seguridad, y desarrollar planes de específicos para relacionados con estos dispositivos.
La conexión de estos dispositivos a través de redes locales o Internet con otros sistemas clínicos, como HIS, RIS y PACS, trae consigo mejoras notables en la eficiencia y la calidad de la atención médica. Sin embargo, esta conectividad también plantea nuevos y complejos riesgos HTA en cuanto a la seguridad de la información y la ciberseguridad, los cuales deben ser WE dl
E
gestionados de manera proactiva.
p
ÁS

<!-- pág. 52 -->

ST
BA
ministerio DEsatuo | is-wc-007 | vVersión:2o [|  Páginastde7o
PENN
La gestión efectiva de los riesgos relacionados con el loT en el ámbito de la salud implica implementar medidas de protección específicas, tal como se indica en las guías y regulaciones actuales emitidas por el Ministerio de Salud, de acuerdo con:
10.1.
Instrucciones de Seguridad para Dispositivos Médicos loT:
Al momento de adquirir, implementar y operar dispositivos médicos loT, las instituciones del sector deben tener en cuenta las siguientes instrucciones de seguridad:
Inventario y Gestión de Activos: Implemente y mantenga un inventario de todos los dispositivos loT médicos conectados a las redes institucionales. Este inventario debe registrar la ubicación física del dispositivo, el fabricante, modelo específico, versión de firmware instalada y el personal responsable de su gestión y mantenimiento.
Segmentación de Red y Accesos Controlados: Implemente una arquitectura de red segmentada, tanto a nivel lógico (VLANs) como físico (aislamiento de puertos), para confinar los dispositivos loT en redes separadas de otros sistemas críticos. Controle el acceso a estas redes mediante la configuración de listas de control de acceso (ACLs) y firewalls con reglas específicas que limiten la comunicación solo a los servicios y sistemas necesarios para su funcionamiento.
Control de Acceso y Autenticación Segura: Establezca mecanismos de autenticación robustos para acceder a la configuración y la información de los dispositivos loT.
Deshabilite las credenciales predeterminadas de fábrica de manera inmediata y prohíba el uso de contraseñas débiles. Cuando las capacidades del dispositivo lo permitan, habilite la autenticación multifactor (MFA) para una mayor seguridad.
Gestión de Vulnerabilidades y Actualizaciones: Requiera a los proveedores la entrega regular de parches de seguridad y actualizaciones de firmware para sus dispositivos, junto con la documentación de las pruebas de seguridad que hayan realizado. Las áreas de Tl y clínica designadas deberán planificar, probar(en entornos no productivos cuando sea factible) e implementar estas actualizaciones, manteniendo un registro detallado del proceso.
Monitoreo y Registro de Actividades: Implemente soluciones de monitoreo continuo del comportamiento de los dispositivos médicos loT. Estas soluciones deben ser capaces de detectar accesos no autorizados, modificaciones en la configuración, patrones de tráfico anómalos y otros indicadores de compromiso. Asegure la generación y el almacenamiento seguro de registros de actividad (logs) detallados para facilitar auditorías y análisis forenses.
Cifrado de Datos y Comunicaciones: Asegure que toda la información generada o transmitida por los dispositivos loT médicos esté protegida mediante cifrado de
E
extremo a extremo. Utilice estándares criptográficos reconocidos internacionalmente o
A
EN
y robustos (por ejemplo, TLS 1.2 o superior para comunicaciones de red y AES-256 para datos en reposo cuandosea aplicable, acompañados de conjuntos de cifrados seguros).
E

<!-- pág. 53 -->

ae
MA
misterio cesaLuo | isenc-007 | versiórizo | Páginaszde7o
PRÚCREAN
Pruebas de Seguridad y Evaluaciones de Riesgo: Antes de la puesta en operación de cualquier dispositivo médico loT, realice pruebas de penetración y evaluaciones de riesgo específicas para identificar vulnerabilidades y evaluar su impacto potencial.
Estas pruebas deben incluir la verificación de la interoperabilidad segura con otros sistemas clínicos o administrativos con los que el dispositivo interactúe.
Cumplimiento Normativo y Contratual: Al establecer contratos con proveedores de dispositivos médicos loT, incluya cláusulas explícitas que aborden los requisitos de ciberseguridad, en concordancia con la Ley N* 21.663, la Ley N* 21.541 (relativa a la calidad y seguridad de los dispositivos médicos)y las políticas y normativas vigentes del
Ministerio de Salud.
Plan de Contingencia y Respuesta a Incidentes: Integre los dispositivos médicos loT dentro de los planes de operativa y a del establecimiento de salud. Asegure que existan procedimientos específicos para la identificación, contención, erradicación y recuperación de incidentes de seguridad que puedan afectar la disponibilidad o la integridad de estos dispositivos, manteniendo la trazabilidad y la comunicación oportuna de estos eventos.
11. SEGURIDAD EN TELEMEDICINA La telemedicina, como prestación de servicios de salud a distancia a través de tecnologías de la información y la comunicación (TIC), se ha convertido en una parte fundamental del sector salud. Su uso no solo mejora el acceso a la atención médica, sino que también hace que los servicios sean más eficientes, permitiendo una atención más rápida, personalizada y ajustada a las necesidades de cada paciente.
Sin embargo,
la telemedicina trae consigo nuevos retos en cuanto a la seguridad de la información y la ciberseguridad. Esto se debea la criticidad de los datos de salud que se manejan, la variedad de tecnologías que se utilizan y los riesgos que conlleva la transmisión y el almacenamiento de esta información a distancia. Estos retos requieren una atención especial para garantizar la confidencialidad, integridad y disponibilidad de los datos.
Este capítulo detalla las pautas y controles de seguridad que las instituciones del sector salud deben poner en práctica para asegurar la protección de la información en el ámbito de la telemedicina. Esto abarca el cumplimiento de la Ley N* 21.541 y la NORMA TÉCNICA N? 237 del Minsal, que establecen los estándares relacionados con las acciones y servicios de salud a distancia y telemedicina.
11.1. Controles de Seguridad para la Telemedicina Para asegurar la protección de la información en el ámbito de la telemedicina, las instituciones del sector salud deben considerar las siguientes directrices y controles de seguridad específicos:
Autenticación Robusta: Implementar autenticación multifactor(MFA) para todos los usuarios: US ¿>
(pacientes, profesionales, administrativos) que accedan a las plataformas de telemedicina.
*Y
IE

<!-- pág. 54 -->

INSTRUCTIVO DESEGURIDAD DE LA INFORMACIÓN YCIBERSEGURIDAD PARA EL SECTOR SALUD a =
MR
Página53 de 79
e
Utilizar mecanismos de autenticación que cumplan con los estándares de seguridad establecidos por la normativa ministerial.
e
Considerar la autenticación biométrica cuando sea apropiadoy factible.
Autorización y Control de Acceso: Definir y aplicar políticas de control de acceso basadas en roles y privilegios mínimos, asegurando que cada usuario acceda solo a la información necesaria para su función.
e
Gestionar los accesos de usuarios de manera centralizada y eficiente, incluyendo la creación, modificación y revocación de cuentas.
e
Implementar mecanismos de bloqueo automático de sesión por inactividad.
Confidencialidad de la Información: Cifrar las comunicaciones de telemedicina de extremo a extremo, utilizando protocolos seguros y actualizados (ej., TLS 1.2 o superior).
e
Proteger la información de salud transmitida y almacenada, tanto en reposo como en tránsito, mediante técnicas de cifrado adecuadas.
e
Asegurar que
las plataformas de telemedicina cumplan con los requisitos de confidencialidad establecidos en la Ley N* 19.628 (Protección de la Vida Privada) y otras normativas aplicables.
Integridad de la Información: Implementar mecanismos de verificación de la integridad de los datos para detectar cualquier alteración o manipulación no autorizada durante la transmisión y almacenamiento.
Utilizar firmas digitales u otros mecanismos de autenticación de origen para validar la identidad del emisor de la información.
e
la
integridad
de
los
metadatos
asociados
a
las
transacciones
de
telemedicina.
Disponibilidad de los Servicios: Implementar medidas de redundancia y contingencia para asegurar la disponibilidad continua de los servicios de telemedicina.
e
Establecer planes de recuperación ante desastres para minimizar el tiempo de inactividad en caso de fallos o incidentes.
e
Monitorear el rendimientoy la disponibilidad de las plataformas de telemedicina y tomar medidas proactivas para prevenir interrupciones.
Videoconferencia Segura: Los sistemas de videoconferencia deben contar con protocolos seguros de acceso de usuario para minimizar riesgos de intrusiones y suplantaciones.
Implementar cifrado robusto para la comunicación de video y voz, asegurando la inaccesibilidad de las conversaciones para terceros.
(E
+ Establecer mecanismos de verificación de la integridad de los datos en la comunicación
E
de video y voz.
Z
es
xl
E
Implementar protocolos de identificación de origen y destino en el enrutamiento de mensajes para validar la identidad del paciente y el profesional.
A

<!-- pág. 55 -->

a+.
BA
vinisTERIODESALUD
| tIS-NC-007
[| Versión:20 |  Páginas4de7a
MMM
Contar con servicios de registro y custodia segura de las videoconferencias para auditorías posteriores.
Almacenamiento Seguro de Datos: Almacenar los datos de telemedicina (incluyendo grabaciones, registros, etc.) en repositorios seguros, con controles de acceso estrictos y cifrado.
e
Definir políticas de retención y eliminación de datos de acuerdo con la normativa vigente.
Realizar copias de seguridad periódicas de los datos y almacenarlas en ubicaciones seguras.
Gestión de Incidentes: Establecer un plan de respuesta a incidentes de seguridad específico para la telemedicina, que incluya procedimientos para la detección, contención, erradicación, recuperación y notificación de incidentes.
e
Definir los roles y responsabilidades del personal en la gestión de incidentes.
e
Implementar mecanismos de monitoreo y alerta temprana para detectar posibles incidentes de seguridad.
Auditoría y Trazabilidad:
Implementar registros de auditoría detallados de todas las actividades relevantes en las plataformas de telemedicina.
e
Realizar auditorías periódicas para verificar el cumplimiento de las políticas y controles de seguridad.
Conservar los registros de auditoría durante el tiempo requerido por la normativa.
Cumplimiento Normativo: Asegurar que las prácticas de telemedicina cumplan con la Ley N?
21.541, la Norma Técnica N* 237, la Ley N” 19.628, la Ley N* 21.663 y otras regulaciones aplicables.
e
Mantenerse actualizado sobre los cambios en la normativa y adaptar las prácticas de seguridad en consecuencia.
12. INNOVACION Y TENDENCIAS EN CIBERSEGURIDAD Es fundamental impulsar la adopción de nuevas tecnologías, enfoques y buenas prácticas de ciberseguridad en el sector salud, basándonos en normativas nacionales (Ley N* 21.663, Ley N? 21.719), estándares internacionales (ISO 27001, NIST, CIS v8)
y marcos regulatorios como
HIPAA.
Esto contribuirá a establecer una postura de seguridad que sea resiliente, anticipativa y sostenible. Para fortalecer la ciberseguridad institucional, anticipar amenazas emergentes y UN!
adoptar un enfoque proactivo ante los desafíos tecnológicos del entorno digital actual, es Y Visa >
necesario considerar y aplicar las siguientes líneas de acción e innovación:
A

<!-- pág. 56 -->

E
MA
Página55de79
Detección y Respuesta Avanzada con Inteligencia Artificial y Automatización:
e
Implementar Herramientas EDR/XDR con lA: Adopte soluciones de Detección y Respuesta en Endpoints (EDR) y Detección y Respuesta Extendida (XDR) que integren análisis de comportamiento basado en Inteligencia Artificial para identificaryresponder a amenazas avanzadas de manera proactiva.
e
Evaluar Plataformas SOAR: Analice e implemente plataformas de Orquestación, Automatización y Respuesta de Seguridad (SOAR) para automatizar los flujos de trabajo de respuesta a incidentes, mejorando la eficiencia y reduciendo los tiempos de reacción.
Aplicar Aprendizaje Automático: Utilice técnicas de Machine Learning dentro de las herramientas de seguridad para optimizar la detección de amenazas y disminuir la cantidad de falsos positivos, permitiendo a los equipos de seguridad enfocarse en alertas genuinas.
Ciberinteligencia Predictiva y Táctica (TI/CTI):
e
Anticipar Amenazas con Análisis de Tendencias: Establezca procesos para analizar tendencias de amenazas, datos de inteligencia y reportes del sector para anticipar posibles ataques dirigidos a las instituciones de salud.
e
Integrar Plataformas CTI para Threat Hunting: Implemente y utilice plataformas de Ciberinteligencia (Tl/CTI) que se integren con herramientas de "caza de amenazas"
(Threat Hunting) para buscar proactivamente indicios de actividad maliciosa en la infraestructura.
e
Monitorear
y
Correlacionar
loCs:
Establezca
mecanismos
para
monitorear
y
correlacionar Indicadores de Compromiso (loCs) provenientes de diversas fuentes para detectar actividad sospechosa en tiempo real.
Compartir Inteligencia de Amenazas: Participe activamente en el intercambio de información sobre amenazas con otros Servicios de Salud y entidades relevantes para fortalecer la defensa colectiva.
Exploración de Tecnologías Emergentes (Blockchain):
Evaluar Uso de Tecnología Blockchain para Integridad y Trazabilidad: Investigue la viabilidad de utilizar la tecnología blockchain para asegurar la integridad, trazabilidad y transparencia en el manejo de datos clínicos y consentimientos informados.
e
Probar Pilotos de Blockchain: Realice pruebas piloto para evaluar el uso de blockchain en escenarios como el intercambio seguro de historiales clínicos y la validación de la trazabilidad de consentimientos informados.
Interoperabilidad
Segura: Asegure que
cualquier implementación de blockchain sea interoperable y segura con los sistemas existentes.
A
Prevención de Suplantación Digital (Deepfakes y Phishing Avanzado):
ER)
A
o
A

<!-- pág. 57 -->

a
BA
muisterioDEsacUD
| rs-NC-007 | Versión:20 |  Páginasede7s MEN
e
Mitigar Riesgos de Fraude Multimedia: Implemente medidas para mitigar los riesgos de fraude digital derivados de la manipulación multimedia (deepfakes).
e
Aplicar Validación Biométrica y Antifraude: Utilice tecnologías de validación biométrica y soluciones antifraude avanzadas para verificar la identidad y prevenir la suplantación.
Sensibilizar sobre Nuevas Tácticas de Phishing: Eduque al personal sobre las tácticas emergentes de phishing visual y de voz para aumentar su capacidad de detección.
e
Monitorear Deepfakes e Imagen Institucional: Establezca procesos para monitorear la posible creación y uso indebido de deepfakesy la imagen institucional en línea.
Incorporación de Ciberinteligencia en la Gestión de Amenazas:
e
Integrar Fuentes de Threat Intelligence: Incorpore fuentes de inteligencia de amenazas (Threat Intelligence) en los procesos de monitoreo y análisis de riesgos para obtener información contextual y oportuna sobre las amenazas.
Participar en Comunidades de Intercambio: Únase y participe activamente en comunidades de intercambio de información sectorial (como los grupos WSSP del sector salud y foros nacionales de ciberseguridad) para compartir y recibir información relevante sobre amenazas y buenas prácticas Identidad Digital y Autenticación Avanzada:
e
Fortalecer Gestión de Identidad y Accesos (IAM): Optimice los sistemas de Gestión de Identidad y Accesos para asegurar un control granular sobre quién tiene acceso a qué recursos.
e
Implementar Autenticación sin Contraseñas y Adaptativa:
Explore e implemente
métodos de autenticación sin contraseñas y autenticación adaptativa que consideren el riesgo del acceso en tiempo real.
e
Establecer Roles y Privilegios Temporales:
Implemente
la asignación de roles y privilegios con duración limitada y mecanismos de trazabilidad para auditoría.
e
Usar Identidad Federada(SSO): Explore la implementación de la federación de identidad (Single Sign-On - SSO) entre instituciones de salud para facilitar el acceso seguro y simplificado a recursos compartidos.
Implementación de la Arquitectura de Confianza Cero (Zero Trust Architecture - ZTA):
e.
Desarrollar Estrategia de Implementación ZTA: Elabore e implemente una estrategia gradual para adoptar el modelo de seguridad Zero Trust, implementando controles de acceso estrictos basados en la identidad del usuario, el contexto de la solicitud y la autenticación continua.
e.
Asegurar Microsegmentación y Monitoreo Continuo: Implemente la microsegmentación en redes clínicas y administrativas para limitar el radio de impacto de posibles brechas.
Asegure la verificación continua de dispositivos y el monitoreo constante de los flujos de red internos.
SNA
A

<!-- pág. 58 -->

a
MÍ mmusremonesacoo | ts-nc-007 | Versiónizo | Páginas7ae7o
MOMENTO
e
Aplicar Control de Acceso Basado en Identidad y Contexto: Implemente políticas de control de acceso dinámicas que consideren la identidad del usuario, su rol, la ubicación, el dispositivo utilizado y la sensibilidad de los datos a los que se intenta acceder.
Refuerzo de la Seguridad en Entornos Multicloud y Servicios SaaS:
e
Incorporar Herramientas de Seguridad Cloud: Implemente herramientas de Gestión de Postura de Seguridad en la Nube (CSPM), Protección de Cargas de Trabajo en la Nube (CWPP)y Agentes de Seguridad de Acceso a la Nube (CASB) para asegurar la visibilidad y el control en entornos multicloud y servicios SaaS.
Establecer Requisitos de Seguridad para Proveedores Cloud:
Defina e imponga
requisitos mínimos de seguridad para los proveedores de servicios en la nube, en cumplimiento con la Ley N? 21.663, HIPAA y otras normativas aplicables.
Fortalecimiento de la Protección de Tecnologías Operacionales (OT) y Dispositivos loMT:
e
Inventariar y Segmentar Activos loMT/OT: Identifique, clasifique y mantenga un inventario actualizado de todoslos activos de Tecnología Operacional(OT)y dispositivos de Internet de las Cosas Médicas (loMT). Implemente redes segmentadasy aisladas para su operación.
e
Incorporar Detección de Amenazas Específica: Implemente sistemas de detección de amenazas diseñados especificamente para entornos industriales y médicos conectados, que consideren los protocolos y las vulnerabilidades propias de estos sistemas.
e
Implementar NAC eIDS paraloMT: Utilice soluciones de Control de Acceso ala Red(NAC)
y Sistemas de Detección de Intrusiones (IDS) adaptadas a las características y necesidades de los dispositivos loMT.
e
Restringir Conexiones de Red Innecesarias: Minimice y controle estrictamente las conexiones de red salientes e innecesarias desde y hacia los dispositivos loMT y OT.
Mejora de la Resiliencia Cibernética Institucional:
e
Diseñar y Probar Planes de Continuidad y Recuperación:
Desarrolle y pruebe
exhaustivamente planes de continuidad operacional (BCP) y recuperación ante desastres (DRP) que consideren escenarios de ciberataques complejos, como ransomware y denegación de servicio distribuido(DDoS).
e
Implementar Respaldo Inmutable y Recuperación Orquestada: Adopte soluciones de respaldo de datos inmutables para proteger la información crítica contra el cifrado o la eliminación maliciosa. Implemente y pruebe mecanismos de recuperación orquestada para restaurar los sistemas de manera eficiente tras un incidente.
EA
### 13. CAPACITACION Y CONCIENTIZACION EN CIBERSEGURIDAD
OS
EN Todas las instituciones del sector salud deben desarrollar e implementar un programa continuo de capacitación y concientización en ciberseguridad. Este programa debe enfocarse e

<!-- pág. 59 -->

ae
MÍ
rnusreno cesaron | tisnc007 | versiónizo | Páginasadero
IRONMAN
en fortalecer la cultura de seguridad dentro de la organización, reducir el riesgo humano y garantizar el cumplimiento de las normativas vigentes.
13.1.Plan de Capacitación Anual en Ciberseguridad:
Desarrollo e Implementación: El Área de Seguridad de la Información de la Institución, en colaboración con la Dirección y área de Recursos Humanos, deberá elaborar e implementar un Plan Anual de Capacitación en Ciberseguridad. Este plan cubrirá a la totalidad del personal, incluyendo funcionarios de planta, a contrata, honorarios y proveedores externos que tengan acceso alos sistemas de información institucionales.
Niveles de Profundidad Diferenciados: El plan de capacitación deberá estructurarse en distintos niveles de profundidad, adaptados al perfil de riesgo y responsabilidades de cada grupo de usuarios:
o
Nivel
Básico (Usuarios
Generales):
Módulos
introductorios enfocados en la identificación de amenazas comunesy la adopción de prácticas seguras en el uso diario de las tecnologías institucionales.
o
Nivel Intermedio (Personal Técnico No Especializado): Formación que profundice en los conceptos de seguridad y proporcione herramientas prácticas para la protección de los sistemas y datos bajo su responsabilidad.
o
Nivel
Avanzado
(Personal
Técnico
Especializado):
Capacitación
técnica
especializada en áreas como gestión de vulnerabilidades, seguridad en entornos cloud, hardening de sistemas, criptografía, implementación y gestión de sistemas de monitoreo de seguridad (SIEM), y procedimientos avanzados de gestión de o Nivel Directivo: Sesiones informativas y talleres enfocados en el gobierno de la ciberseguridad, la gestión de riesgos cibernéticos, el cumplimiento normativo (Ley N* 21.663, Ley N* 21.719, HIPAA, etc.), y la toma de decisiones estratégicas ante incidentes de alto impacto.
13.2.
Módulos Temáticos:
El Plan Anual de Capacitación deberá incluir, como mínimo, los siguientes módulos temáticos, adaptados al nivel de profundidad correspondiente:
e
Fundamentos de Seguridad de la Información y Protección de Datos Personales:
Introducción a los conceptos clave de confidencialidad, integridad y disponibilidad de la información, así como los principios y normativas fundamentales para la protección de datos personales (Ley N? 19.628 y Ley N? 21.719).
e
Uso Seguro de Tecnologías y Redes Institucionales: Directrices para el uso seguro de equipos de escritorio, portátiles, dispositivos móviles, correo electrónico, navegación web, redes inalámbricas institucionales y el acceso remoto seguro.
Gestión de Contraseñas y Autenticación Segura: Políticas de creación y gestión de
Me
contraseñas robustas, la importancia de la rotación periódica y la implementación y uso£*24*3 obligatorio de la Autenticación Multifactor(MFA) para el acceso a sistemas críticos.
3 Y
as
IA

<!-- pág. 60 -->

BA
ministerioDESaLUD
[| ims-wc-007 [ Vversión:20 |  Páginasede7a
PAVO
e
Prevención de Phishing, Ingeniería Social y Malware: Reconocimiento de las diferentes técnicas de phishing y otros ataques de ingeniería social, así como las medidas preventivas contra la infección por software malicioso (virus, ransomware, spyware, etc.).
e
Normativa Vigente en Ciberseguridad y Privacidad: Revisión de las leyes, decretos, políticas y normativas internas y externas aplicables en materia de ciberseguridad y protección de la privacidad de los datos.
e
Procedimientos de Respuesta ante Incidentes: Protocolos y pasos a seguir para la identificación, reporte y respuesta inicial ante incidentes de seguridad de la información y ciberseguridad, incluyendo los canales de comunicación internos y con la ANCI.
13.3.
Capacitación Especializada para Equipos Técnicos y Directivos:
Equipos Técnicos: Deberán recibir formación avanzaday práctica en:
o
Gestión integral de vulnerabilidades (identificación, evaluación, priorización y remediación).
o
Seguridad en la nube (configuración segura de servicios, gestión de identidades y accesos en la nube, cumplimiento).
o
Endurecimiento (hardening) de sistemas operativos, servidores, aplicaciones y dispositivos de red.
o
Implementación y gestión de soluciones de cifrado para datos en tránsito y en reposo.
o
Implementación, configuración y análisis de sistemas de monitoreo de seguridad (SIEM) para la detección y correlación de eventos.
o
Procedimientos avanzados de gestión y respuesta a incidentes complejos.
Directivos: Deberán participar en sesiones de capacitación sobre:
o
Gobernanza de la ciberseguridad y su rol en la estrategia institucional.
o
Gestión de riesgos cibernéticos, incluyendo la evaluación del impacto financiero y reputacional.
o
normativo
y
las
implicaciones
legales de
los
incidentes de
seguridad.
o
Proceso de toma de decisiones estratégicas y comunicación en situaciones de incidentes de alto impacto.
13.5.1. Simulacros y Ejercicios de Ciberseguridad:
Realización Anual Obligatoria: Se deberá planificar y ejecutar al menos un ejercicio o simulacro de respuesta a incidentes de seguridad por año. Estos simulacros deben involucrar a usuarios clave de diferentes áreas, personal técnico relevante y los responsables de la continuidad operativa.
Ey
+. Escenarios Realistas: Los simulacros deben basarse en escenarios de amenazas fe
A
realistas y relevantes para el Sector Salud (ej. ataques de ransomware, filtración de datos, denegación de servicio).
o

<!-- pág. 61 -->

2 ES
Er
Documentación y Mejora Continua: Los resultados de cada simulacro deberán ser exhaustivamente documentados, identificando las fortalezas y debilidades en los procesos de respuesta. Se deberán definir y ejecutar acciones de mejora continua basadas en las lecciones aprendidas.
13.3.2. Evaluación y Seguimiento del Aprendizaje:
e
Evaluaciones Pre y Post Capacitación: Se implementarán evaluaciones diagnósticas al inicio y pruebas de conocimiento al finalizar cada módulo de capacitación para medir la efectividad del aprendizajey la retención de la información.
e
Registro de Participación: Se deberá mantener un registro centralizado y actualizado de la participación y el cumplimiento del Plan Anual de Capacitación por parte de todos los funcionarios. El cumplimiento de la capacitación será un requisito obligatorio.
e
Indicadores de Desempeño y Madurez: Se incorporarán indicadores de desempeño relacionados con la participación en la capacitación y la adopción de prácticas seguras para evaluar la madurez de la cultura de ciberseguridad institucional a lo largo del tiempo.
13.3.3. Materiales y Canales de Difusión:
e
Diversificación de Formatos: Se utilizarán diversos formatos de entrega de contenido para maximizar el alcance y la efectividad del aprendizaje, incluyendo sesiones presenciales, módulos de e-learning interactivos, cápsulas informativas concisas, newsletters periódicas con consejos de seguridad y videos explicativos.
e
Uso de Medios Digitales Internos: Se aprovecharán los canales de comunicación digital internos (intranet, plataformas de colaboración, correo electrónico institucional) para la difusión continua de materiales educativos y recordatorios sobre las mejores prácticas de ciberseguridad.
13.3.4.
Obligatoriedad y Registro Formal:
e
Carácter
Obligatorio:
La
participación
en
las
actividades
de
capacitación
en
ciberseguridad será de carácter obligatorio para todo el personal y se considerará parte integral de sus obligaciones laborales. El incumplimiento podrá tener las implicaciones que defina la normativa interna.
e.
Sistema de Registro Centralizado: Se implementará un sistema formal y centralizado para el registro de todas las actividades de formación y concientización realizadas, incluyendo la fecha, el módulo cursado, la duracióny el resultado de las evaluaciones (si aplica). Este registro deberá estar disponible para auditorías internas y externas.
### 14. ARQUITECTURA REFERENCIAL a a

<!-- pág. 62 -->

ae
MÍ
muusterovesacuo | tsnc:007 | versiómzo [  Págmaciae7o
MINI
Todo sistema desarrollado o implementado para el Sector Salud debe estar alineado con la
Arquitectura
Referencial
Ministerial,
la
cual
establece
las
directrices,
estándares
y
lineamientos arquitectónicos de referencia. Esta arquitectura es clave para garantizar que las soluciones tecnológicas sean interoperables, escalables, seguras y fácilmente integrables en el ecosistema tecnológico institucional. Las instituciones del sector salud deberán considerar las siguientes directrices:
e
Alineación con la Estrategia Tecnológica: Los sistemas deben diseñarse conformea los objetivos estratégicos y tecnológicos definidos por el
MINSAL,
asegurando
su
contribucióna la transformación digital del sector salud.
e
Uso de Estándares y Tecnologías Aprobadas: Todos los desarrollos deben seguir las tecnologías, plataformas, metodologías y patrones de diseño establecidos en la arquitectura referencial ministerial, asegurando uniformidad, robustez y sostenibilidad.
e
Revisión y Aprobación Arquitectónica: Cualquier cambio o excepción relevante a la arquitectura debe ser evaluado y aprobado por el equipo de gobernanza tecnológica institucional, asegurando suviabilidad, compatibilidad y control de riesgos.
e
Reutilización y Modularidad: Se debe promover el diseño modular y la reutilización de componentes tecnológicos, con el fin de reducir redundancias, acortar los plazos de desarrollo, mejorar la mantenibilidad y optimizar el uso de recursos.
e
Documentación Técnica Obligatoria: Toda solución tecnológica deberá contar con documentación arquitectónica actualizada que incluya la estructura del sistema, modelo de datos, diagramas de componentes, integraciones y configuraciones clave.
15. INTEROPERABILIDAD Los sistemas y aplicaciones desarrollados para el sector salud deben cumplir con los requisitos de interoperabilidad definidos por el Ministerio, con el fin de garantizar la integración fluida entre sistemas internos y externos, mejorar la continuidad asistencial y optimizar la gestión clínica y administrativa. Para ello, se deben aplicarlas siguientes directrices:
Cumplimiento de Estándares HL7: Los sistemas deberán ser compatibles con los estándares HL7 vigentes, incluyendo HL7 v2.x y HL7 FHIR (R4 o superiores), promoviendo la interoperabilidad semántica y técnica entre sistemas de información de salud.
e
Protocolos y Formatos de Intercambio Seguros: Se deberá emplear protocolos estandarizados como HTTPS, SFTP, REST, GraphQL y formatos como JSON o XML, asegurando una comunicación estructurada, confiable y protegida.
+ Desarrollo de APIs Documentadas: Toda solución debe exponer APIs bien documentadas
AD,
y estandarizadas que faciliten la integración funcional entre sistemas de salud, asegurando consistencia, trazabilidad y escalabilidad.
IN

<!-- pág. 63 -->

a
BA mmusteronesacuo
| irs-n0-007 | Versiórzo | Páginae2de7s
INEA
Compatibilidad con la Arquitectura Empresarial: Los desarrollos deben ajustarse a la arquitectura empresarial institucional vigente, respetando las capas tecnológicas, dominios funcionales y plataformas habilitadoras establecidas.
Gestión de Datos Normalizados:
La interoperabilidad exige que los datos estén estructurados y normalizados conforme a catálogos, códigos y estándares reconocidos por el sector salud, preservando la integridad y consistencia clínica.
e
Pruebas de Interoperabilidad: Es obligatorio realizar pruebas de interoperabilidad durante el ciclo de desarrollo, incluyendo pruebas funcionales, de seguridad y de rendimiento, asegurando una integración efectiva entre los distintos sistemas.
16. USO DE INTELIGENCIA ARTIFICIAL (1A)
El uso de la Inteligencia Artificial (IA) en el sector salud ofrece enormes ventajas, pero también plantea retos importantes en términos de seguridad, privacidad y ética. Es crucial que las instituciones sigan pautas claras y rigurosas para garantizar que la implementación de la lA sea segura, auditable y cumpla con la legislación vigente.
La colaboración
entre
los
proveedores de tecnología y las instituciones de salud es clave para alcanzar el éxito y fomentar la confianza en estos sistemas.
Cuando se trata de contratos o desarrollos tecnológicos en el ámbito de la salud que impliquen el uso de Inteligencia Artificial (IA), las instituciones del sector salud deben cumplir con los más altos estándares éticos, legales, técnicos y de seguridad.
Las siguientes directrices serán de cumplimiento obligatorio para los proveedores y responsables institucionales del proyecto:
e
Auditabilidad
y
Explicabilidad:
Los algoritmos
utilizados deben
ser auditables y
explicables.
El proveedor deberá
garantizar que, ante requerimiento, se puedan comprender las decisiones automatizadas que afectan procesos clínicos oO administrativos.
e
Cumplimiento Normativo: La implementación de lA deberá cumplir con las leyes vigentes, incluyendo la Ley N* 21.663 sobre Ciberseguridad, la Ley N* 21.719 sobre Protección de Datos Personales, la Ley N? 21.541 sobre Telemedicina y la Circular N?
711/2023 de SEGPRES sobre uso de lA en el sector público.
e
Evaluación y Gestión de Riesgos: Los proveedores deberán identificar y mitigar los riesgos relacionados con la seguridad, privacidad, equidad y sesgo algorítmico, a través de evaluaciones periódicas de impacto.
e
Supervisión y Revisión de Resultados: Se deberán implementar mecanismos para la supervisión continua de los sistemas de !A, garantizando que sus resultados no sean discriminatorios ni generen impactos adversos en pacientes, usuarios o profesionale de la salud.
e
IE

<!-- pág. 64 -->

BA
miisTERIODESALUO
| Is-N0-007 | Versión:20 [  Páginao3de7s
PENN
e
Derechos de los Usuarios: Se debe permitir a los usuarios cuestionar, corregir o apelar decisiones tomadas por sistemas de lA, además de facilitar el ejercicio de los derechos ARCO (Acceso, Rectificación, Cancelación y Oposición) cuando corresponda.
e.
Responsabilidad y Remediación:
El proveedor será responsable de los resultados generados por los sistemas de lA, debiendo corregir fallas, vulnerabilidades o impactos negativos derivados de su uso, asegurando la continuidad y confianza en los servicios digitales del sector salud.
16.1.Casos de Uso de la lA en el Sector Salud y los Riesgos Asociados e lA para el Diagnóstico: Los sistemas de IA pueden ser utilizados para apoyar en el diagnóstico de enfermedades mediante el análisis de imágenes médicas o el procesamiento de datos de pacientes. Sin embargo, uno de los principales riesgos asociados es el sesgo en los algoritmos, lo que puede llevar a diagnósticos erróneos o a la falta de detección de ciertas condiciones. También existe el riesgo de falta de transparencia en cómo los algoritmos toman decisiones, lo que podría generar desconfianza en los profesionales de la salud.
e
lA para el Tratamiento: Los sistemas de lA también pueden sugerir opciones de tratamiento basadas en los datos del paciente y en algoritmos predictivos. Sin embargo, los errores en las recomendaciones debido a la calidad deficiente de los datos o la falta de validación clínica pueden poner en peligro la seguridad del paciente. Es fundamental que las recomendaciones generadas por lA sean validadas por expertos médicos antes de ser implementadas.
e
lA parala Gestión de la Salud Pública: En el ámbito de la gestión de la salud pública, la lA puede ayudar a predecir brotes de enfermedades y optimizar recursos. No obstante, existe el riesgo de uso indebido de los datos personales de los pacientes y preocupaciones sobre la privacidad. Los sistemas de lA deben estar diseñados para garantizar que la información de los pacientes se utilice de manera ética y legal.
16.2.
Consideraciones de Seguridad y Privacidad en el Uso de lA en Salud Requisitos de Seguridad para los Datos Utilizados para Entrenar los Algoritmos de IA: Los datos utilizados para entrenar los algoritmos de lA deben ser almacenados y procesados de acuerdo con los más altos estándares de seguridad, garantizando su cifrado y protección contra accesos no autorizados. Esto incluye el uso de entornos seguros para el procesamiento de los datos y la implementación de controles de acceso estrictos.
Mecanismos para Garantizar la Transparencia y Explicabilidad de los Algoritmos:
Los proveedores de soluciones de lA deben implementar mecanismos que permitan la trazabilidad y auditabilidad de los algoritmos, lo que facilita que los resultados puedan ser explicados a los profesionales de la salud y pacientes cuando sea necesario.
PE
¡USADO
o

<!-- pág. 65 -->

BE
MÍ
misterio oesacoo | tsnc=007 | versiónzo |
Páginaeade7o
RINA
Medidas para Proteger la Privacidad de los Pacientes al Utilizar Sistemas de lA: Se deben adoptar medidas de anonimización y pseudonimización de los datos de los pacientes antes de ser utilizados para entrenar los algoritmos de lA. También deben implementarse políticas que regulen el consentimiento explícito de los pacientes para el uso de sus datos en estos sistemas.
Consideraciones Éticas y Legales en el Uso de la lA en Salud: El uso de la lA debe estar alineado con principios éticos que respeten la dignidad y los derechos humanos de los pacientes. Además, se deben considerar las implicaciones legales de la implementación de lA, asegurando que el uso de los datos personales y de salud cumpla con las leyes de protección de datos y privacidad vigentes.
17. AUDITORÍA Y CUMPLIMIENTO DEL SGSI La auditoría y el cumplimiento son fundamentales para asegurar que un Sistema de Gestión de Seguridad de la Información (SGSI) funcione de manera efectiva en las Instituciones del sector salud. Realizar auditorías de forma regular ayuda a detectar fallas en los controles de seguridad, a evaluar cómo se está cumpliendo con las políticas internas y las normativas externas, y a garantizar que siempre se esté mejorando en la protección de la información sensible de los pacientes.
A continuación, se presentan los tipos de auditorías que se recomiendan y las pautas para llevarlas a cabo, con el fin de asegurar que se cumplan las normativas, así como los estándares éticos y técnicos en la gestión de la seguridad de la información en el sector salud.
17.1. Tipos de Auditorías Recomendadas e Auditorías Internas: Realizadas por el personal de la institución, con el fin de evaluar la efectividad de los controles de seguridad y detectar áreas de mejora.
Auditorías Externas:
Llevadas a cabo por auditores independientes para obtener una evaluación imparcial del SGSI.
Auditorías de Cumplimiento: Dirigidas a verificar el cumplimiento con regulaciones específicas, como la Ley N* 21.663 y otras normativas locales e internacionales.
17.2.
Frecuencia de las Auditorías y Criterios para la Selección de Auditores e Frecuencia: Las auditorías internas deben hacerse al menos una vez al año, LN mientras que las externas y de cumplimiento se realizan cada dos años o según ;yy
A
las regulaciones pertinentes.
y
A

<!-- pág. 66 -->

a
BA
mwusreroesacuo | trs-nc-007 | versiónizo |  Páginaosao7a
POIMBETNT
e
Criterios para Selección de Auditores: Los auditores internos deben tener conocimientos en seguridad de la información, ser imparciales y contar con formación en auditoría. Los auditores externos deben ser profesionales independientes con experiencia en el sector salud y certificaciones adecuadas, mientras que los auditores de cumplimiento deben estar especializados en las normativas aplicables.
18. INDICADORES DE SEGURIDAD DE LA INFORMACION Y CIBERSEGURIDAD La evaluación sistemática, el control efectivo y la mejora continua del Sistema de Gestión de Seguridad de la Información (SGSI) así como de las medidas de ciberseguridad en las instituciones del sector salud, requieren un diseño, seguimiento y reporte bien estructurado de Indicadores Clave de Desempeño (KPI) e Indicadores Clave de Riesgo (KRI).
Estos indicadores ofrecen una visión objetiva, cuantificable y periódica sobre el estado de la seguridad de la informacióny la ciberseguridad a nivel institucional, lo que facilita la toma de decisiones estratégicas y operativas por parte de los responsables de seguridad y la Alta
Dirección.
En este contexto, las instituciones del sector salud deben establecer e implementar un conjunto de indicadores que les ayuden a evaluar el nivel de madurez del Sistema de Gestión de Seguridad de la Información (SGSI), la eficiencia en la ejecución de controles, el grado de cumplimiento normativo (Ley N* 21.663, Ley N” 19.628, |SO/IEC 27001:2022, NIST, entre otros), y su capacidad de respuesta ante riesgos relacionados con la seguridad de la informacióny la ciberseguridad.
Cada indicador debe tener una definición clara, una unidad de medida, una frecuencia de evaluación y una persona responsable para su seguimiento. Los resultados de estas evaluaciones deben presentarse periódicamente al Comité de Seguridad de la Información y a la Alta Dirección, y, cuando sea necesario, informarse a la Agencia Nacional de Cibersequridad.
Para una propuesta de indicadores aplicables, revisar la tabla contenida en el Anexo, punto
21.6.
19. MECANISMO DE DIFUSIÓN.
La comunicación del presente instructivo se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, alo menos se deberá hacer difusión mediante los siguientes canales:
e
Publicación en el sitio web Minsal http://www.Minsal.cl/seguridad_de_la_informacion/ e Publicación en la intranet de Minsal http://isalud.Minsal.cl/ (EZ e
Correo informativo.
a
a
E

<!-- pág. 67 -->

a
MA
20.CONTROL DE VERSIONES
| Versión
Fecha53]
- Pág.oSección modificada
Motivo dele]
AULA
AR
A
Todas
Creacióndeldocumento
i
l
E
Adaptación
normativa
nacional
y
estándares:
internacionales en materia
Abril 2025
Todas
de
de
la.
- Información
y
po
-Ciberseguridad
### 21. ANEXOS
21.1.
Definiciones y términos claves.
Para los efectos de la aplicación de este documento, los términos que a continuación se señalan tendrán el significado que se indica:
e
Activos de información: toda información o recurso relacionado para la creación, almacenamiento, gestión o transmisión de dicha
Podrán
ser activos
materiales (RRHH especializados, aparatos, equipos, redes, instalaciones, soportes y sistemas de almacenamiento) o intangibles (datos, aplicaciones, sistemas operativos, bases de datos, imagen, reputación, marcas de la organización).
e
Activo informático: toda información almacenada en una red y sistema informático que tenga valor para una persona u organización.
e.
Autenticación: propiedad de la información que da cuenta de su origen legítimo.
e
Anonimización: procedimiento irreversible en virtud del cual un dato personal no puede vincularse o asociarse a una persona determinada, ni permitir su identificación, por haberse destruido o eliminado el nexo con la información que vincula, asocia o identifica a esa persona. Un dato anonimizado deja de ser un dato personal.
e
Agencia: la Agencia Nacional de Ciberseguridad, que se conocerá en forma abreviada como ANC!.
e
Auditorías de seguridad: procesos de control destinados a revisar el cumplimiento de las políticas y procedimientos que se derivan del Sistema de Gestión de la Seguridad de la
Información.
e
Seudonimización: tratamiento de datos personales que se efectúa de manera tal que ya no puedan atribuirse a un titular sin utilizar información adicional que permita la reidentificación, la cual debe constar en medios seguros, gestionados por separado, y estar sujeta a medidas técnicas y organizativas destinadas a garantizar que accedan a ella TI personas sólo personal autorizado por el responsable del tratamiento.
eE
a

<!-- pág. 68 -->

Ciberespacio: El ciberespacio es un ambiente complejo, soportado por hardware y las redes de comunicaciones, en el cual constan interacciones entre personas, software y servicios de Internet, destinados a la distribución mundial de información y comunicación"
(1S0 27032).
e
Ciberataque: Acción realizada con la finalidad de destruir, exponer, alterar, deshabilitar, o exfiltrar u obtener acceso o hacer uso no autorizado de un activo informático.
e.
Ciberseguridad: Preservación de la confidencialidad e integridad de la informacióny de la disponibilidad y resiliencia de las redes y sistemas informáticos, con el objetivo de proteger a las personas, la sociedad, las organizaciones o las naciones de incidentes de ciberseguridad.
e
Incidente
de
ciberseguridad:
Todo
evento
que
perjudique
o
comprometa
la
confidencialidad o integridad de la información, la disponibilidad o resiliencia de las redes y sistemas informáticos, o la autenticación de los procesos ejecutados o implementados en las redes y sistemas informáticos.
e.
Confidencialidad: Propiedad que consiste en que la información no es accedida o entregada a individuos, entidades o procesos no autorizados.
e
Continuidad de servicios: Capacidad de un organización para mantener la disponibilidad de sus servicios, reduciendo el riesgo de eventos que puedan dar lugar a una interrupción O inestabilidad en las operaciones de la entidad, manteniendo niveles aceptables de servicios, entendiendo por tales, las prestaciones básicas del sistema que sustentan las operaciones esenciales del servicios y propiciando la recuperación del nivel normal de servicios de tecnologías de la información(Tl) enel menor tiempo posible.
e
Disponibilidad: Propiedad que consiste en que la información es accesible y utilizable cuando es requerida por un individuo, entidad o proceso autorizado.
e
Datos Personales o datos de carácter personal:
los datos relativos a cualquier información concerniente a personas naturales, identificadas o identificables, con independencia de su soporte.
e
Datos Sensibles: Datos personales que se refieren a características físicas o morales de las personas o a hechos o circunstancias de su vida privada o intimidad, entre otros, los hábitos personales, origen racial, las ideologías y opiniones políticas, las creencias o convicciones religiosas, los estados de salud físicos o psíquicos y la vida sexual.* Equipo de Respuesta a Incidentes de Seguridad Informática o CSIRT:
Centros
multidisciplinarios que tienen por objeto prevenir, detectar, gestionar y responder a
* La ley 21.719, que entrará en vigor el 01 de diciembre de 2026, sustituye la definición de datos sensibles por la siguiente: “Datos personales sensibles: tendrán esta condición aquellos datos personales que se refieren a las características físicas o morales de las personas o a hechos o circunstancias de su vida (EA privada o intimidad, que revelen el origen étnicoo racial, la afiliación política, sindical o gremial, la Situación socioeconómica, las convicciones ideológicas o filosóficas, las creencias religiosas, los datos relativos a la salud, al perfil biológico humano, los datos biométricos, y la información relativa a la vida sexual, a la orientación sexual y a la identidad de género de una persona natural”.

<!-- pág. 69 -->

MÍ
riusrenionesacoo | tisnc-007 | versiónizo | Páginacadero
PINBEIMNNO
incidentes de ciberseguridad o ciberataques, en forma rápida y efectiva, y que actúan conforme a procedimientosy políticas predefinidas, ayudando a mitigar sus efectos.
Gestión de incidentes: Procedimientos para la detección, análisis, manejo, contención y resolución de un incidente de ciberseguridad y responder ante ésta.
e
Incidente: Evento inesperado o no deseado con consecuencias en detrimento de la seguridad de las redes, equipos y sistemas de información (véase también ciberincidente).
e
Infraestructura crítica: las instalaciones, sistemas físicos o servicios esenciales y de utilidad pública, redes, servicios y equipos físicos y de tecnología de la información cuya afectación, degradación, denegación, interrupción o destrucción cause un grave dañoa la salud o al abastecimiento de la población, a la actividad económica esencial, al medioambiente o a la seguridad del país. Se entiende por este concepto la infraestructura indispensable para la generación, transmisión, transporte, producción, almacenamiento y distribución de los servicios e insumos básicos para la población, tales como energía, gas, agua o telecomunicaciones;
la relativa a la conexión vial, aérea, terrestre, marítima, portuaria o ferroviaria, y la correspondiente a servicios de utilidad pública, como los sistemas de asistencia sanitaria o de salud.
e
Integridad: Propiedad que consiste en que la información no ha sido modificada o destruida sin autorización.
e
Nubeprivada: La infraestructura de la nube se aprovisiona para uso exclusivo de una única organización aun cuando comprenda múltiples unidades de dicha organización. Puede ser propiedad, administrado y operado por la organización, un tercero o una combinación de ellos, y puede existir dentro o fuera de las instalaciones de la organización.
e
Nube pública: La infraestructura y los recursos lógicos que forman parte del entorno se encuentran disponibles para el público en general a través de Internet. Suele ser propiedad de un Prestador de Servicios que gestiona la infraestructura y el servicio o servicios que se ofrecen.
e.
Protección de los activos de información: Adopción de las medidas que resguarden la seguridad física de los dispositivos, así como los accesos a éstos.
e
Redy sistema informático: conjunto de dispositivos, cables, enlaces, enrutadores u otros equipos de comunicaciones o sistemas que almacenen, procesen o transmitan datos digitales.
Resiliencia: Capacidad de las redes y sistemas informáticos para seguir operando luego de un incidente de ciberseguridad, aunque sea en un estado degradado, debilitado o segmentado, y la capacidad de las redes y sistemas informáticos para recuperar sus funciones después de un incidente de ciberseguridad.
e
Riesgo: posibilidad de ocurrencia de un incidente de ciberseguridad; la magnitud de un riesgo es cuantificada en términos de la probabilidad de ocurrencia del incidente y del impacto de las consecuencias de este.
e
Riesgo de Ciberseguridad: Toda circunstancia o hecho razonablemente identificable y previsible, que tenga un posible efecto adverso en la seguridad de las redes, equipos y EN sistemas de información. Se puede cuantificar como la probabilidad de materialización de 3 USA
El
ION

<!-- pág. 70 -->

E
una de las amenazas antes mencionadas que produzca un impacto en términos de operatividad, o de integridad, confidencialidad o disponibilidad de datos.
e
Seguridad de la información: Conjunto de medidas preventivas y reactivas de los organismos administradores y sus respectivos sistemas tecnológicos, que tienen por objeto resguardar y proteger la información, asegurando la confidencialidad, integridad, autenticidad y disponibilidad de los datos, continuidad de servicios y protección de activos de información.
e
Tratamiento de datos: cualquier operación o conjunto de operaciones o procedimientos técnicos, de carácter automatizado o no, que permitan de cualquier forma recolectar, procesar, almacenar, comunicar, transmitir o utilizar datos personales o conjuntos de datos personales.
Vulnerabilidad: Debilidad de un activo o control que puede ser explotado por una o más amenazas informáticas.
21.2.
Normativa sobre seguridad de la información.
21.2.1. Normativa del sector salud:
e
DFLN?1, de 24 de abril de 2006, Ministerio de Salud, que fija el texto refundido, coordinado y sistematizado del Decreto Ley N* 2.763, de 1979 y de las leyes N* 18.933 y 18.469;
e
DFLN2725, Ministerio de Salud, Código Sanitario;
LeyN”19.966, de 2004, que establece un régimen de garantías de salud;
LeyN?19.650, que perfecciona normas del área de la salud;
e
Ley N” 20.120 de 22 de septiembre de 2006, sobre la investigación científica en el ser humano, su genoma, y prohíbe la clonación humana y demás normativa del área de la salud.
e
Ley N*20.584, referida a Deberes y Derechos que tienen las Personas en relación con acciones vinculadas a su Atención de Salud;
e
Ley N” 20.724, de 2014, que modifica el Código Sanitario en materia de regulación de medicamentos;
e
LeyN”20.,850, de 2016, que crea un sistema de protección financiera para diagnósticos y tratamientos de alto costo y rinde homenaje póstumo a don Luis Ricarte Soto Gallegos;
e
LeyN”21.258, de 2020, que crea la ley nacional del cáncer, que rinde homenaje póstumo al doctor Claudio Mora.
e
Ley 21.541, de 17 de marzo de 2023, que modifica la normativa que indica para autorizar a los prestadores de salud a efectuar atenciones mediante telemedicina.
e
Decreto N? 41, de 24 dejulio de 2012, del Ministerio de Salud, Reglamento de Ficha Clínica;
e
Decreto N? 31 de 15 de junio de 2012, del Ministerio de Salud, Reglamento sobre entrega de información y expresión de consentimiento informado en las atenciones de salud;
E
e
Decreto N” 38, de 2005, del Ministerio de Salud, Reglamento Orgánico de los
SE:
establecimientos de salud de menor complejidad yde los establecimientos de autogestión
Ca
en red.
Ministerio de Salud — Departamento deRS

<!-- pág. 71 -->

MA
ministerioDEsaLUD | tis-Nc-007 | Versiów:20 | Página7ode7a
PASAN
Decreto N” 38, de 26 de diciembre de 2012, del Ministerio de Salud, que aprueba Reglamento sobre derechos y deberes de las personas en relación con las actividades vinculadas con su atención de salud.
Decreto N” 38, de 2013, del Ministerio de Salud, que modifica decreto N” 466 de 1984, Reglamento de Farmacias, Droguerías, almacenes farmacéuticos, botiquines y depósitos autorizados.
Decreto N?6, de 16 de abril de 2021, del Ministerio de Salud, Reglamento sobre acciones de vinculadas a la atención de salud realizadas a distancia.
Decreto N* 820, 2011, Ministerio de Salud.
21.2.2. En materia de documentos electrónicos:
Ley N*19.880/2003: Ley que establece bases de los procedimientos administrativos que rigen los actos de los órganos de la administración del Estado. Esta ley es importante porque establece condiciones sobre los plazos y la forma en que los servicios públicos deben responder frente a requerimientos de ciudadanosy de otros servicios públicos.
LeyN”21.180, de transformación digital del Estado.
LeyN?” 19.799 de 12 de abril de 2002, de firmas y documentos electrónicos.
Decreto N”*181, que aprueba Reglamento de la ley N” 19799 sobre documentos electrónicos.
Firma electrónicay la certificación de dicha firma.
e
Decreto N*83, de 2005, del Ministerio secretaría General de la Presidencia, e Decreto N? 14, de 2014, del Ministerio secretaría General de la Presidencia, el decreto N?1 de 2015, del Ministerio secretaría General de la Presidencia.
e
Decreto N*4, 2021, Ministerio Secretaría General de la Presidencia, Reglamento que regula la forma en que los procedimientos administrativos deberán expresarse a través de medios electrónicos, en las materias que indica, según lo dispuesto en la ley N* 21.180 sobre transformación digital del estado.
e
Decreto N* 24, 2019, Ministerio de Economía, que aprueba norma técnica para la prestación del servicio de certificación de firma electrónica avanzada.
DecretoN”1, 2015, Ministerio Secretaría General de la Presidencia, aprueba norma técnica sobre sistemasy sitios web de los órganos de la administración del estado.
21.2.3.En materia de seguridad de la información:
LeyN?21.663 sobre Marco de Ciberseguridad, esta ley proporciona un marco para asegurar la ciberseguridad de infraestructuras críticas.
e
Decreto N” 295, de 2024, del Ministerio del Interior y Seguridad Pública: Aprueba reglamento de reporte de incidentes de ciberseguridad de la ley N? 21.633.
e
Decreto N%483, de 2024, del Ministerio del Interior y Seguridad Pública: Aprueba Reglamento que determina la estructura interna de la Agencia Nacional de Ciberseguridad.
Decreto N*164, de 2023, del Ministerio del Interior y Seguridad Pública: Aprueba Política ES
YA
Nacional de Ciberseguridad 2023-2028.
ES Sa
Ministerio de Salud — Departamento deolbdsdsiMentad

<!-- pág. 72 -->

e
Decreto Supremo N*7, 2023, Ministerio secretaría General de la Presidencia, que establece una Norma Técnica de Seguridad de la Información y Ciberseguridad, en concordancia con la Ley N2 21.180 e
Decreto Supremo
N*
2005, Aprueba norma
técnica
para
los órganos
de
la
administración
del estado, sobre seguridad y confidencialidad de los documentos electrónicos.
e
Decreto N*273, 2022, Ministerio del Interior y Seguridad Pública, Establece obligación de reportar incidentes de ciberseguridad.
e
Circular N* 711/2023 establece lineamientos sobre el uso de herramientas de inteligencia artificial (IA) en el sector público de
Chile,
proporcionando directrices para una implementación ética, segura y transparente de estas tecnologías en gubernamentales. Con el objetivo de asegurar que las aplicaciones de |A en el sector público se alineen con los valores de protección de derechos, transparencia y seguridad de la información, además de fomentar la eficiencia y mejorar la calidad de los servicios público.
e
Resolución Exenta N*372/2025 que aprueba texto de las recomendaciones del Consejo para la Transparencia sobre Transparencia Algorítmica y Oficio N”“7286/2025 Guía del
Consejo
para
la Transparencia para la adopción de las Recomendaciones sobre
Transparencia Algorítmica.
21.2.4.En materia de protección de datos personales:
e
Art. 19 Nos. 1 y 4 de la Constitución Política de la República.
e
Ley N”19.628/1999: Sobre protección de la vida privada, que define dato personal, dato personal sensible, y establece las condiciones debe cumplir toda entidad que maneje estos datos.
e
Ley N” 21.719/2024: Que modifica la ley N? 19.628, sustituyendo su nombre por “Ley de Protección de Datos Personales” y actualiza las normas de este cuerpo normativo de acuerdo con los estándares actualmente vigentes. Esta ley entra en vigor el 1 de diciembre de 2026.
e
LeyN”20.575 sobre el principio de finalidad en el tratamiento de datos personales.
e
Decreto N* 779, de 2000, que Aprueba Reglamento del Registro de Bancos de Datos Personales a cargo de organismos públicos.
Resolución Exenta N” 489, 2022, Consejo para la Transparencia, Aprueba procedimiento para la tramitación de solicitudes de ejercicio de derechos de la ley N* 19.628, sobre proteccióna la vida privada.
E
21.2.5.En materia de delitos informáticos:
Es
Ministerio de Salud — Departamento deAaa

<!-- pág. 73 -->

a E
MÍ
Página72de79
LeyN”21.459/2022: Establece normas sobre delitos informáticos, deroga la Ley N? 19.223 y modifica otros cuerpos legales con el objeto de adecuarlos al Convenio de Budapest. Esta ley establece los delitos informáticos reconocidos en Chile.
LeyN*20.009, sobre clonación de tarjetas de crédito.
Decreto N* 83, de 2017, que promulgó el Convenio de Budapest en Chile. Tratado internacional de combate contra la ciberdelincuencia.
21.2.6.En materia de propiedad Intelectual:
e
LeyN?19.039, de Propiedad Industrial e Ley N* 17.336, de Propiedad Intelectual.
Fija condiciones para la protección de los programas computacionales como propiedad intelectual de sus autores.
21.2.7. Normas de aplicación general:
e
Ley 21.542, Que modifica la carta fundamental con el objeto de permitir la protección de infraestructura crítica por parte de las fuerzas armadas, en caso de peligro grave o inminente e LeyN” 21.180, de transformación digital del Estado;
LeyN”19.880 de bases de los procedimientos administrativos;
e
LeyN*20.285 de transparencia y acceso ala información pública:
LeyN”19.886 de compras públicas.
Decreto N” 661 que aprueba reglamento de la Ley N” 19.886, de bases sobre contratos administrativos de suministro y prestación de servicios, y deja sin efecto el decreto supremo n? 250, de 2004, del Ministerio de Hacienda Resolución Exenta N* 619 - B de 26 de noviembre de 2018, de la Dirección de Compras y
Contratación Pública.
21.3.
Estándares Internacionales y Normativa Nacional en Seguridad de la
Información y Ciberseguridad
TEMA
NOMBRE
ISO 27001:2022
alba
A
sistema
de
gestión
de
la
de
la
lA
_
información (SGSI).
E,
ISO 27002:2022
P
q
ad
mantener y mejorar un sistema de gestión de la
A
oseguridad
dela información
Seguridad de la
La
publicación
especial 800-53 del
Instituto
NIST SP 800-53
Nacional de Estándares y Tecnología (NIST, por
ES
WEE
a
SU siglas eninglés) es un estándar de seguridad ¿USABO
A

<!-- pág. 74 -->

INSTRUCTIVO DESEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD
ST
MÍ
muusteriooesacuo | imsmno:007 | versión:zo |  Página7sae7o
MANRIINANO
TEMA
NOMBRE
de la información que proporciona un catálogo de controles de privacidad y seguridad para sistemas .de
Originalmente
destinado
a
agencias federales de EE.
ISO/IEC 27799:2016
Aplicalos principios de la I|SO/IEC 27002 al ámbito l
Seguridad de la
(alineada con prácticas de la salud, proporcionando guías específicas en europeas)
. para proteger la información de salud personal.
o
l
. Estándar que proporciona principios y directrices
| Gestión de riesgos
ISO 31000
' para la gestión de riesgos aplicables a cualquier o _ tipodeorganización.
O
: Define requisitos para establecer y mantener un
| con tieSO ql
ISO 22301
| sistema de gestión de continuidad del negocio
negocio
¿e PU
ante eventos disruptivos.
. E
. Health Insurance Portability and Accountability
HIPAA (EE.UU.)
Act. Ley estadounidense que regula la protección datos y privacidad de la información de salud en formato sas
Es
electrónico.
Y
s
| Reglamento General de
Reglamento obligatorio para todos los países de la
E
UE que establece normas estrictas sobre cómo datos
Proteccin
Bios
deben manejarse
y protegerse
los datos
(GDPR) - UE 2016/679
qUe ce
fo
HE
PESO
EN
Eno (johsan
Marco promovido por la Comisión Europea para el
Electronic Health
Ñ
E
f
Y
intercambio de registros electrónicos de salud datos
Record Exchange
con Interaperabilidad y seguridad
Ú——_—_
A
e
AA]
Ley N? 19.628
Ley chilena sobre Protección de la Vida Privada, datos regula el tratamiento de datos personales.
| Modifica
la
Ley
N*
19.628,
incorporando
dátos
Ley N* 21.719
. estándares modernos de protección de datos : personales.
Establece un marco para el intercambio seguro de
European Data
| datos dentro de la UE, fomentando la reutilización
datos
Governance Act(DGA)
| de datos sensibles de forma segura, incluidos los
: de salud.
Marco
basado
en
cinco
funciones
clave
NIST Cybersecurit
| (Identificar,
Proteger,
Detectar,
Responder
Seta
Framework
Recuperar)
ar
gestionar e
E
l
- Ciberseguridad.
Conjunto
de
controles
priorizados
para
Cibersegtiridad
CIS Controls v8
defenderse contra las amenazas cibernéticas más comunes. Util para establecer una base mínima de ciberseguridad
Proporciona
para
la
gestión
de
ISONÑEC 27035
incidentes de seguridad de la información, incluyendo la planificación, detección, respuesta . y lecciones aprendidas.
ATA
Cib
idad
Directiva NIS 2 - UE
Reemplaza la Directiva NIS original, reforzando los po5
| dsd >
2022/2555
requisitos
de
ciberseguridad
para
sectores
LY
O
e
o

<!-- pág. 75 -->

MA rumusreriovesacuo
[ is"nc-007 [ Versión:zo [ Páginarade7o
Piti
TEMA
NOMBRE
críticos, incluyendo salud, con obligaciones más o estrictas.
- ¿3
Ea dENS
Desarrolla
buenas
prácticas,
marcos
y
E
ma
herramientas para mejorar la ciberseguridad a Unión Europea para la a
Ciberseguridad)
nivel europeo; promueve la cooperación entre a
IS
estados miembros.
El
Ley Marco de Ciberseguridad de Chile, establece
Ley N* 21.663
lineamientos, gobernanza y obligaciones para
EN
organizaciones públicas y privadas
| Proporciona
detalladas
para
Seguridad de redes
ISO/IEC 27033 a sesungad,. en redes: IneNOndo , gestión y protección de la infraestructura _| dered.
e
Regula la atención médica por medios digitales
Salud digital
Ley N*21.541
| (telemedicina),
incluyendo
requisitos
de
py
e
- ciberseguridad
y protección de datos.
A
o
Circular N2711/2023
Lineamientos para el uso ético y seguro de lA y Etica de inteligencia artificial en
Sci
organismos públicos de Chile.
ho
Marco legal propuesto por la Comisión Europea
Za
para regular el desarrollo y uso de sistemas de pÉtica
Alcosa
inteligencia
artificial,
con
foco
en
ética,
A)
| transparencia
y riesgo.
E
o
Recomendaciones
del Consejo
para
la
Transparencia
Transparencia sobre Transparencia Algorítmica
Algorítmica sobre
aprobadas en Resolución Exenta N*372/2025 y
Pa
Sistemas de decisiones Oficio N*7286/2025 Guía del Consejo para la lA y Etica pa automatizadas y
| Transparencia
para
la
adopción
de
las
semiautomatizadas
Recomendaciones
sobre
Transparencia
(SDA)
Algorítmica.
21.4.
Matriz de Riesgos de Seguridad de la Información en el Sector Salud (ejemplo)
Amenaza
Vulnerabilidad
Impacto
Control Preventivo
Control
Potencial
Correctivo
Ataques
de
| Sistemas
Inaccesibilidad
Actualización
Plan
de
ransomware
desactualizados,
a datos clínicos
periódica
de
recuperación
falta
de
parches
críticos,
software
ante
| de seguridad
interrupción
de
Implementación
(IRP)
de
deEDRyantivirusde
Restauración
salud
nueva generación
desde
respaldos
- Segmentación de
verificados
co
|redescríticas
ES
A
A

<!-- pág. 76 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD PARAEL SECTOR SALUD a
BA
ministerio DEsaLuD  [ is-wc-007 [ Versión:20 |  Págima7sde7a
PAN
Pérdida o robo | Falta de cifrado de | Fuga de
| - Cifrado completo
| - Borrado remoto
de dispositivos | dispositivos, de
| de datos
móviles
ausencia de MDM
sensible
de
móviles
' - Investigación de
(Mobile
Device
pacientes
de
Gestión
de — incidente
y
Management)
' dispositivos móviles notificación a la (MDM)
' autoridad
(en
caso
de
ser
' multifactor
requerido
por la
| normativa)
Acceso
no | Políticas
de
Modificación
o  -Políticas de control | -
Bloqueo
autorizado
a|acceso
débiles,
exfiltración
de
de acceso basadas
. inmediato
de
sistemas
datos
de
enroles (RBAC)
' cuentas
clínicos
compartidas o no
pacientes, daño
comprometidas
robustas
reputacional
multifactor (MFA)
' - Análisis forense
j-
Revisiones
de
acceso
y:
periódicas
de
remediación
de
ls
: La laIll
po
_ cuentasypermisos
| brechas
Phishing
Falta
de
Compromiso de
Programas
de  -
dirigido
a | capacitación
en
credenciales,
concienciación
en  Restablecimiento
personal
ciberseguridad,
infección
de
ciberseguridad
: inmediato
de
administrativo
filtros
de
correo
malware
- Filtros avanzados
o clínico
inadecuados
de
correo
Análisis
de
(antiphishing,
: dispositivos
y
antispam)
; contención
— de
Fallas
en
|Ausencia
de
alta
Interrupción
en
Implementación
Activación
de
' disponibilidad
y
diagnósticos,
de arquitecturas de
procedimientos
de
sistemas | respaldo
de
tratamientos,
alta
de
críticos
(HIS, | sistemas
- procedimientos
(HA)
' operativa
PACS, LIS)
clínicos
Sistemas
de
Recuperación
| respaldo en caliente
| de
y
pruebas
de
desde
entornos
Ñ
- recuperación
' alternativos
E
[IEEE

<!-- pág. 77 -->

ae
MÍ
Página76de79
21.5.
Estructura de Políticas y Procedimientos (ejemplo)
Categoría ISO/IEC
Política /
| a
Procedimientos
27001:2022
P
Asociados
Establece
el
marco
Procedimiento de revisión
Política General de
general de gestión de la y aprobación de políticas.
Políticas de
de
la
| Procedimiento de difusión
s
de
la|.
See
Ms
oe
y
el
| institucional.
a
compromiso
institucional.
Regula el acceso físico y
Procedimiento de gestión
Organización dela
Política
de
Control
lógico alos sistemas
yla
de
cuentas de
usuario.
de Accesos
Procedimiento de revisión ¡pr periódica de accesos.
pan
Establece normas para
| Procedimiento
de
Política
de
Uso
Políticas de
el uso correcto de los | monitoreo del uso de
L
Aceptable
de
e
o
recursos
tecnológicos | recursos.
Recursos
AR
Le
bai
- | institucionales.
J
_. de sanción por mal uso.
Define cómo identificar,
| Procedimiento
de
SE
Política
de
Gestión
clasificar y proteger los
| inventario. Procedimiento
Gestión de Activos
n
z
JE
AA
pl
de Activos
activos de información.
| de
clasificación
y
MN
Una
TI |
| etiquetado.
Política
de
Establece criterios para de
Gestión de Activos
Clasificación
y
el uso y protección de la clasificación.
| Manejo
de
la
según
su
de
sensibilidad. | destrucción segura.
Establece
| Procedimiento
de
Política de Respaldo
para
respaldar
y
| respaldos. Procedimiento
Operación
m-
E
e
y Recuperación
-| restaurar
| de prueba de restauración.
AS
crítica.
e
Asegura
| Procedimiento
de
Política
de
o
Jal
¿ETT
o
frente ainterrupciones.
| activación
del
plan.
e
Operacional vDRP
Procedimiento de pruebas
IA ir
EAEEA
Controla acceso físico y | Procedimiento de control
Seguridad Física
y
Política de Seguridad protección delentorno.
físico.
de
del Entorno
Física y Ambiental
contingencias
LA fl
ambientales.
Adquisición,
Política de Seguridad
Integra seguridad desde de desarrollo y en el Ciclo de Vidade
| el diseño hasta el retiro
desarrollo seguro. Pruebas mantenimiento losSistemasdesistemas.
| deaceptación.
L
Relación con
Política de Relación
Establece requisitos de | Evaluación de seguridad para terceros | proveedores. Acuerdos de
Proveedores
con Proveedores
h
a
E
y contratistas. confidencialidad.
A
Política de Gestión
Define cómo responder | Procedimiento de
Gestión de
P
AA
A
Iholentes
de
de
y
aprender
de | notificación. Análisis postincidente.
ll
NA
, VISADO
A
E

<!-- pág. 78 -->

INSTRUCTIVO DE SEGURIDAD DE LA INFORMACIÓN Y CIBERSEGURIDAD ae
MÍ
Categoría ISO/IEC
Política/.
ER ón A
Procedimientos
27001:2022
P
Asociados
pa
¡Política
de | Garantiza cumplimiento
| Procedimiento de gestión
-x
a
ti
Protección de Datos
de
Ley
19.628
en
| de
consentimientos.
palio
. Personales
'tratamiento de datos.
|Anonimización.
m7
ormas de uso seguro y
| Prevención
de
phishing.
e
¡ Política de Correos
A
Al
Sa
Ñ
Comunicaciones
profesional
del correo
| Cifrado de correos.
Electrónicos
od.
2, E!
in
_ Institucional,
A
Determina mecanismos | Procedimiento de cifrado.
el
¡ Política de Uso de
de
cifrado
aceptados | Gestión dellaves.
Criptografía
A
' Criptografía
para
proteger
la
E
ES
WA
rt
AE
Instrumentos
que | Revisión de cumplimiento '. Procedimientos e detallan cómo| técnico.
Auditorías
Transversal
' Instructivos
implementar
los | internas.
Técnicos
controles definidos por tr "cra
JAR
¿MS políticas.
Mo
21.6.
Indicadores Clave de Desempeño e Indicadores Clave de Riesgo (ejemplo)
Proporciona una lista de ejemplos de métricas de seguridad, tanto a nivel técnico como de gestión:
O
ig
Unida oi Meta
: Umbr
Categoría /
- Nombre del
Objetivo
Fórmula /
dde
Frecuenc
alde
Responsable
Área
J
Métrica
Medi
ía
Umbr
| Alert
P
da
lalo
io
a:
gag
ze
: Porcentaje
Evaluar
el
' de
cumplimient
eN
% de áreas
. cumplimient | o de normas ete
Entaidadolde
CapaFísica
' o
de
| de
acceso
e
Mensual
100%
alo
nr
cumplimien
Infraestructura
| políticas de
| físico
a
to total
j
' Acceso
zonas
j
físico
| críticas
P
de
Detectar
Número
de
L
E
accesos
no
N2 de
d
autorizados,
eventos
N2
Mensual
| Seguridad Física
e seguridad
físi
robos
o
registrados
ísica
y
| vandalismo
o
AO
AE: A
Medir
la
(%intentos
E
E
Nasa
Ml
eficacia de
bloqueados
Capa
ESipQues
«de
las barreras
eta
Semanal ME
Red/Firewall
Perimetral
intentos
de
- 99.9%
99.5%
Admin
AL
perimetrale
intentos) x
i
intrusión
j
NA
S
de
y
Número
de | Supervisar
N2 de
alertas
anomalías y
alertas
o
es
Encargado de
críticas
del | amenazas
críticas
me
El
A
Soc
IDS/IPS
| externas
generadas
H
mo
Porcentaje
% de
de
¡SS
segmentos
- Trimestra
Arquitecto de
Lis
Cc
MES
i
Y
Y
AA o
cumplimient
| OPENS
: implementa
de
SHE
sae
Red
E
E
| ción de una
le
Es
(o)
de
dos
A

<!-- pág. 79 -->

a.”
el
A
Categoría/
Nombre del
ia
Fórmula /
dde
Frecuenc
alde
Área
Pavo
Métrica
Medi
ia
Umbr
Alert
ESO
da
al
a
segmentaci
| arquitectura
Número
de
|E
N2 de
indebidos
N2
Mensual
Encargado de
deseguridad e
entre
interna
segmentos
¡IA SORIA
1 y 7; |:E
E
717 EA EG
A PA A EP
Endpoints
Verificar
(o
CapaEnd
A
da
software de | de
to idos
Semanal
298% | <95% | Soporte Técnico antivirus/ED | P / total)x 100 oo actualizado
|R
Detecciones
| Monitorear
= At
de
malware
| infecciones
SOC
o EDR
Ss
N2
Semanal
en
en equipos |onfirmada
Admin
endpoints
| de usuario
m.
T
NO, US
Y
Zo
O
ET!
A
TN MS |
pe
| Identificar
A EN
Vulnerabilid
vulnerabilid
Capa de
-S
| riesgos
SS
Desarrollo/
Al
ades críticas
ades
N2
Mensual
E
Aplicación
A
¡graves
en
Seguridad App
sin corregir
eoftware
abiertas >
Lo
—_
AE
A
AI
E
A
APESSoIE
verificación
conde
AEGPES
Trimestra
pruebas
de
sequridad
críticas con
290%
QA/DevSecOps
qu
SAST/DAST
en sistemas
ecos
| críticos
ol
Asegurar
(% AS A
A
Capa de
paa
confidencial
bases/archi
Trimestra
P
idad
de
vOS
295%
DBA / Seguridad
Datos
cifrados
en
RAR
cifrados /
PES
| sensibles
total) x 100
o
| a e
N2 de
Responsable de
de
fuga
de
A
N2
Anual
s o pérdidas
datos
validados
Datos
A
A
| dedatos
A
A
A
A
Asegurar
Capa
Personal
conocimient - (% personal ral
Administrati | capacitado o básico de capacitado
Anual
295%
<930% O
va
enseguridad | cibersegurid
| /total)x100
p
O
AS
— ad
q.
a
e
E
——SI ——coo
A
A
Incumplimie E
N2 de
ntos
de
violaciones
a
Comité de
0e:
contrarias a
N2
Mensual
políticas
de
documenta
normativas
Internas
das
DIEZ
RA
Cuentas
| Prevenir
(e
E
A
Gestión de
inactivas
OE
ata
Administrador
entidades | desnebiitod indebidos : das in
Mensual
¡AM
as
| por cuentas
detectadas)
ER
SS
obsoletas
x 100
Y
EN
IA
O
A
A
Y
E
E
A
II

<!-- pág. 80 -->

a
MÍ
IE
Unida
Meta
| Umbr
Categoría/
| Nombre del
. Fórmula/ | dde  Frecuenc alde
Área
Objetivo
Métrica
Medi
ia
—Umbr
| Alert
| sión
a
da
calla:
| Tasa
de | Reducir
(sin
Gestiónde
vulnerabilida
| exposición
mitigar/
i
d
| Vulnerabilid
. des críticas
| prolongada
total
Mensual
: cagao
lor.
ne
Ñ
A
Infraestructura
ades
¿sin
mitigar
| a
riesgos
críticas) x
E
| (>30O días)
| graves
o
| Mempo
Mejorar
: E tiempo de
|: Respuesta O
eficienciaen
respuesta/
' Trimestra
i
i
' respuesta
o
Horas
<8h
i
>12h
CSIRT local
Ate
contener
N2
ln.
amenazas
ei
__ incidentes
A
O 2
O: IO:
| Tiempo
| Reducir
mi
de
| latencia
Y tiempo de
o
| desde
detección /
SOC/SIEM
: detección
z
Horas
Mensual
<Ih
>4h
ocurrencia
N2
Admin
lA
hasta
i
sE
L
| detección
"CAE
ME
Asegurar
(o
e
alineación
a
i
Cumplimient
controles
: Cumplimient
o
con
EN
bey
implementa
Oficial de
Ñ
21.663,
Anual
100%
Lo
: ONormativo
normativasy
19.628,
1SO
dos!
¡leyes
27001:2022,
requeridos)
x 100
po
a
ete:
ME] O
E A
¡ll A
E
Consideraciones para la Implementación:
e
Estatablaes un ejemplo. Deberás adaptarlos indicadores a las necesidades específicas, los activos críticos y los riesgos particulares de cada institución del sector salud.
e
Asegúrate de que los indicadores sean relevantes para los objetivos de seguridady las prioridades de la organización.
e
Losindicadores deben ser cuantificablesy fáciles de medir.
e
Losresultados de los indicadores deben permitir la toma de decisiones informadasy la implementación de acciones correctivas.
e
Losindicadores deben revisarse y ajustarse periódicamente para asegurar su continua relevancia y efectividad.
e
Considera la implementación de herramientas de gestión de seguridad de la información (SIEM, paneles de control de seguridad) para facilitar la recopilación, el análisis y la visualización de estos indicadores.
SNISADO
O
o