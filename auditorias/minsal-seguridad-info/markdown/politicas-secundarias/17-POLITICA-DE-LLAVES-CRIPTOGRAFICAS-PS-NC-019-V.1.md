<!-- pág. 1 -->

Ministorio de
POLÍTICA DE LLAVES CRIPTOGRAFICAS
Código
PS-NC-19
o
Versión oficial:
v1.0
¿0 A
Fecha de la versión:
Marzo 2023
Y
Elaborado por:
José Villa Catalan / Luciano Rojas
V/S ENCARGADO
Cc
Revisado por
Jose Villa—Encargado de (0%)
E
s DE SEGURIDA U
Seguridad de la Información.
INFORMACIÓN Yo
Carlos Maldonado -— Encargado
CIBERSEGURID
Operaciones
k
Rodrigo Zamorano — Encargado
Proyectos
dao Dadhiel p2
Aprobado por:
Jorge Herrera - Jefe
DES
Departamento de Tecnologías de la Información y Comunicaciones <= rele DE S
TECNOLOGIAS DELA
INFORMACIÓNY — <
Fa COMUNICACIONES ZE
e)
Toda versión impresa de este documento se considera como Copia No Controlada.
Eg DE SY

<!-- pág. 2 -->

se
Contenido
PROPÓSITO cerro
arc
reci
AS AAAEREA
S — AANCLOJÓMMBO 05 ARLICACIÓNrr oda MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS ..cccoocccccncncnnccononononananannnnananannonarananananinon2
TERMINOLOGÍAscience rra
RAS
S
ROLES Y RESPONSABILIDADESsenora aa
MATERIAS. QUE ABORDA.secretarias DIRECTRICES DE LA POLÍTICA.....cncadaconniooiAAEERAA nm
E
Gestión de CÍaves.......ocoooccccoocccnonnccnnnnanannccnnnnocononononnn coronar oonnncnnnrana nar nnnnncrac nncnnnarnnnnaranaca rnnnn O
MECANISMO DE DIFUSIÓN......ononcccoccncnoncononcncnncnconononnoncnnononnnn cnoncnn onanana nnnonnnanar ranarrarar orrnrannana
PERÍODO DE REVISONossa ii
NAAA
CUMPUMIENTO commercials
AAA AAA
HISTORIAL Y CONTROL DEVERSIONES .ccccccccnnc
RAnme
AAA
A

<!-- pág. 3 -->

FÉ | MINISTERIO DE SALUD
PROPÓSITO
Definir reglas para el uso de claves criptográficas para proteger la confidencialidad, integridad, autenticidad e integridad de la información cifrada en el Ministerio de Salud (MINSAL).
ALCANCE O ÁMBITO DE APLICACIÓN El alcance o ámbito de aplicación del presente documento se extiende a la Subsecretaría de Salud Pública y Subsecretaría de Redes Asistenciales.
Esta política es aplicable a todos los funcionarios (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para las Subsecretarías de Salud Pública y de Redes Asistenciales, que traten información sensible.
Asimismo, se aplica a aquellos que tengan autorización de acceso a la información que pueda afectar los activos de información. Esto incluirá tanto al personal autorizado como a aquellos encargados de implementar los controles de cifrado en los servicios de red y en los sistemas de información del Ministerio de Salud.
Esta política abarca el siguiente control definido en la norma NCh-ISO IEC 27002:2022, sobre controles de seguridad de la información:
8.24 Uso de criptografía.
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS NCh-1S027001:2013: Tecnología de la información - Técnicas de seguridad - Sistemas de gestión de la seguridad de la información — Requisitos.
LeyN” 19.628, de Protección de vida privada y datos personales.
LeyN” 19.799, de firmas y documentos electrónicos.
Ley N” 19.927, de Delitos de Pornografía Infantil.
Ley N” 20.285 regula el principio de transparencia de la función pública y el derecho de accesoa la información de los órganos de la Administración del Estado.
LeyN” 21.180, de Transformación Digital del Estado.
Ley N” 21.459, que Establece normas sobre Delitos Informáticos, deroga la Ley N*19.223 y modifica otros cuerpos legales con el Objeto de Adecuarlos al Convenio de Budapest.
Decreto N” 83, de 2004, Ministerio Secretaría General de la Presidencia, que aprueba norma técnica para los órganos de la administración del estado sobre seguridad y confidencialidad de los documentos electrónicos.
Decreto Supremo N”%1, de 2015, Ministerio Secretaría General de la Presidencia, que Aprueba norma técnica sobre sistemasy sitios web de los Órganos de la Administración del
Estado.
Decreto N*273, de 2022, Ministerio del Interior y Seguridad Pública, que Establece obligación de reportar incidentes de ciberseguridad.

<!-- pág. 4 -->

Documentos Relacionados o Política de Seguridad para la clasificación y manejo de información [1].
TERMINOLOGÍA
i.
Cifrado: que está escrito con letras, símbolos o números que solo pueden comprenderse si se dispone de la clave (llave criptográfica) necesaria para descifrarlos.
li.
Cifrar: es un procedimiento que utiliza un algoritmo de cifrado con cierta clave (clave de cifrado)
que transforma la información, sin atender a su estructura lingúística o significado, de tal forma que sea incomprensible o, al menos, difícil de comprender para cualquier persona que no tenga la clave secreta.
ii.
Controles criptográficos: son los procedimientos y mecanismos utilizados para proteger la información mediante el cifrado y descifrado de los datos.
iv.
Datos personales o datos de carácter personal: los datos relativos a cualquier información concerniente a personas naturales, identificadas o identificables, con independencia de su soporte.
v.
Datos sensibles: datos personales que se refieren a características físicas o morales de las personas o a hechos o circunstancias de su vida privada o intimidad, tales como los hábitos personales, origen racial, las ideologías y opiniones políticas, las creencias o convicciones religiosas, los estados de salud físicos o psíquicos y la vida sexual.
vi.
Datos en reposo: se refiere a los datos que se encuentran almacenados y no se están utilizando activamente en un momento dado. Estos datos pueden ser almacenados en dispositivos físicos como discos duros, cintas magnéticas, servidores u otros métodos de almacenamiento.
vii.
Datos en tránsito: se refieren a los datos que se están moviendo de un dispositivo o lugar a otro, a través de una red o canal de comunicación. Estos datos pueden ser transmitidos a través de diferentes medios, como internet, redes privadas, líneas telefónicas, entre otros.
viii.
Tratamiento de datos: cualquier operación o complejo de operaciones o procedimientos técnicos de carácter automatizado o no, que permitan recolectar, almacenar, grabar, organizar, elaborar, seleccionar, extraer, confrontar, interconectar, disociar, comunicar, ceder, transferir, transmitir o cancelar datos de carácter personal, o utilizarlos en cualquier otra forma.
ix.
Llaves criptográficas: son códigos (algoritmos) que se generan de forma automática y se guarda en un directorio especial durante la instalación. Generalmente, esta información es una secuencia de númeroso letras que se utilizan en criptografía para especificar la transformación del texto plano en texto cifrado, o viceversa.
x.
Texto plano: es un archivo informático que contiene únicamente texto compuesto por caracteres que son legibles por humanos, sin ningún tipo de formato tipográfico. También son llamados archivos de texto llano, simple o sin formato.
Xi.
Nivel de clasificación: se refiere a la categorización de la información en función de su nivel de confidencialidad.
o
Secreto: aquellos documentos e informaciones que requieren un nivel elevado de protección y confidencialidad, de acuerdo con lo establecido en esta Política y por el ordenamiento jurídico. Estos datos no pueden ser divulgados, salvo en situaciones específicamente autorizadas y debidamente registradas mediante actos o resoluciones que indiquen su clasificación como secretos.
o
Reservado: información altamente sensible y de uso exclusivamente interno. Su divulgación podría implicar un impacto no deseado para el Ministerio de Salud (MINSAL)
o podría vulnerar la normativa vigente. Para su protección, debe ser declarada como

<!-- pág. 5 -->

A
de Gestión de Seguridad de la Información — Nivel Central reservada considerando lo dispuesto en la Ley 20.285, sobre acceso a la información pública.
o
Pública: Es toda información que el Ministerio de Salud (MINSAL) genere, obtenga, adquiera, o controle; corresponde a datos que son de acceso público y que por lo tanto no tienen requerimientos frente a la Confidencialidad.
o
Uso interno:
Es toda información que no contiene datos sensibles, que puede encontrarse en proceso de construcción, y que está disponible para todos los empleados y terceros seleccionados. Esta información puede ser entregada al público sujeto a normativa vigente, previa consulta al propietario del activo.
ROLES Y RESPONSABILIDADES Para asegurar el uso adecuadoy efectivo de la criptografía para proteger la confidencialidad, autenticidad e integridad de la información en la organización, se definen los siguientes roles y responsabilidades:
A
Departamento TIC
Ponera
disposición los recursos necesarios para garantizar la adecuada administración de llaves criptográficas, de acuerdo con lo establecido en la presente política.
ii.
Encargado de Seguridad de la Información Velar por el cumplimiento de la presente política para garantizar que se realice una gestión adecuada de las llaves criptográficas.
iii.
Dueño del activo (Propietario de la información)
Custodiar las llaves criptográficas asignadas.
iv.
Administrador del Sistema Responsable de la activación, recepción y la distribución de las llaves criptográficas a los usuarios autorizados.
MATERIAS QUE ABORDA.
Directrices de cifrado para propietarios de la información y personal en general.
Tipos de cifrado para proteger los datos en reposo, en tránsito y en uso.
DIRECTRICES DE LA POLÍTICA Se debe garantizar que la información que se custodie o de la cual se sea propietario, y que esté clasificada según su nivel de confidencialidad, sea cifrada al momento de almacenarse y transmitirse por cualquier medio.
El administrador del sistema será responsable y encargado de activar, recibir y distribuir las llaves criptográficas a los usuarios autorizados, asegurándose de que esté activa durante el periodo de tiempo establecido.
Los responsables de las llaves criptográficas deberán almacenarlas de forma segura, comprometiéndose a restringir el acceso sólo a los usuarios autorizados. De igual forma, en caso de existir, se debe almacenar una copia de las llaves en un lugar seguro para poder recuperarla en caso de extravío.

<!-- pág. 6 -->

2 | MINISTERIO DE SALUD
1D: PS-NC- 19
Versión: 1
Elcambio o actualización de las llaves deberá ser solicitado por el personal responsable o por aquellos que hagan uso de ellas. Es importante proteger las claves secretas y privadas para evitar su copia o modificación sin autorización.
Lasllaves serán revocadas por el oficial de seguridad de la información o persona delegada, cuando exista sospecha de que pudieron ser accedidas por una persona no autorizada o cuando el colaborador finalice su relación con la Institución.
Se deberá mantener registro de las actividades realizadas para todas y cada una de las actividades pertenecientes a la administración, gestión y eliminación de las llaves criptográficas.
Los sistemas que actualmente cuenten con algún mecanismo de cifrado deben cumplir con la presente política.
Gestión de claves
Se debe implementar una gestión adecuada de claves que incluya procesos seguros para generar, almacenar, archivar, recuperar, distribuir, retirar y destruir claves criptográficas. Esta gestión de claves debe estar basada en un conjunto de normas, procedimientos y métodos preestablecidos.
Todas las claves criptográficas deben estar protegidas contra modificaciones y pérdidas.
Además, las claves secretas y privadas deben contar con protección contra el uso no autorizadoy la divulgación. El equipo utilizado para generar, almacenary archivar las claves debe ser protegido físicamente.
Además de garantizar la integridad, también es necesario considerar la autenticidad de las claves públicas y la revocación de claves. Esto implica establecer mecanismos para retirar o desactivar claves en situaciones en las que hayan sido comprometidas o cuando un usuario deja de pertenecer a una organización.
MECANISMO DE DIFUSIÓN.
La comunicación de la presente política se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos, se deberá hacer difusión mediante los siguientes canales:
Publicación en el sitio web de Minsal http://www.minsal.cl/seguridad_de la informacion/ Publicación en la intranet de Minsal http://isalud.minsal.cl/
Correo informativo.
PERÍODO DE REVISIÓN.
Lapresente política deberá ser revisada a lo menos cada dos años o cuando ocurran cambios significativos para garantizar que:
o
Sigue siendo adecuada para su propósito.
o
Refleje los cambios en las tecnologías, algoritmosy cifradores.
o
Está alineada con las mejores prácticas de la industria.
o
Respalde el cumplimiento normativo, contractual y legal continuo.
A su vez, se realizarán actualizaciones cada vez que se produzcan “colisiones criptográficas” exitosas a los algoritmos válidos.
y

<!-- pág. 7 -->

B|
CUMPLIMIENTO
El incumplimiento de esta política puede resultar en acciones disciplinarias, que incluyen la terminación del empleo o la cancelación del acceso a los sistemas de información de la organización.
HISTORIAL Y CONTROL DE VERSIONES
Versión
Fecha
Creado por
Pág. o Sección
Descripción de la modificación modificada
20.03.2023
José Villa C.
Todas
Creación del documento
REFERENCIAS
[1]. SITIO WEB MINSAL — Política de Seguridad para la clasificación y manejo de información — http://www.minsal.cl/seguridad_de la informacion/