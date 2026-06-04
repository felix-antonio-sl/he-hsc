<!-- pág. 1 -->

Ministorio de
POLITICA DE SEGURIDAD PARA EL CONTROL DE
ACCESO LOGICO
Código
PS-NC-008
Versión oficial:
V3.0
Fecha de la versión:
Marzo 2023
Eo DE
Elaborado por:
Rodrigo Vidal - Unidad Seguridad
Vie
de la Información.
E > ENCARGADO A
Revisado por
Jose Villa — Encargado de s DE SEGURIDAD U Seguridad de la Información.
INFORMACIÓN Y
Carlos Maldonado — Encargado
CIBERSEGURIDAD
Operaciones
Rodrigo Zamorano — Encargado aw Ved
Proyectos
Jan Medd po.
Aprobado por:
Jorge Herrera - Jefe
Departamento de Tecnologías de la Información y Comunicaciones
RA
DES
S
Y
S
<= DEPARTAMENTO DE
ns)
TECNOLOGÍAS DE LA
INFORMACIÓNY
A COMUNICACIONES ¡E
We
ES

<!-- pág. 2 -->

ContenidoA
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS o.coooccccocccconccnincconnconanconancnnonnarananorananonnos D Cumplimiento de la legislación: omnes oercnnocerrarenms Y Accesos a las redes y a los servicios de la red cocaina Y comal de ae08s0 € la NOTACIÓN noneneenrmassctreerserer ene noronvcactaiics Y
Administración del SCCESO.....vocconmmomircar rear id Administración de accesos especiales asmaarre Segregación de fUNCIONES ...cccoocccooccnononcnanccnnnnccnnanonanncnnnnnnnnnnnnnnnnrnn nc nannaronanna aan anc aranannananas O Revisión de los derechos de A0CESO orar monarca Revocación de los accesos lÓBICOS......coooocccnoocccnnnanancnnnnncnonann conan nc nnnancnn naar acc ranancoronannnrnnona O
Revocación delos accesossupra r
6.10
Procedimientos de inicio de sesión Seguro ...ccocccccconnooonnccnonananancnnnnanaannnnnnnnnnna nonora nana nannnna O Uso de programas utilitarios privilegiadossix
6.12
Control de acceso al código fuente de los programaS........ccoooccnnnccncnonananinonanonanannnonanananos Z
E
PERÍBDO DERENCIÓN:xsara E EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA ..ooococicicicccocicccnccononononcononconcnnononoronananonanarananas 7

<!-- pág. 3 -->

PRÓPOSITO
Esta Política tiene por objetivo establecer las definiciones que regulan el acceso a los medios compartidos de información del Ministerio de Salud (MINSAL).
ALCANCE O AMBITO DE APLICACIÓN La presente política se aplica a toda información almacenada en las carpetas compartidas, bases de datos, sistemas computacionales, servidores, y demás medios del MINSAL.
Es aplicable a todos los funcionarios (planta, contrata, reemplazos y suplencia), así como al personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para la Subsecretaría de Salud Pública y la Subsecretaría de Redes Asistenciales.
Esta política abarca los siguientes controles definidos en la norma NCh-ISO 27002:2013, denominada “Tecnologías de la información-Técnicas de seguridad-Códigos de prácticas para los controles de seguridad de la información” y, en específico:
A.09.01.01 Política de control de acceso A.09.01.02 Accesosa las redesy a los servicios de la red A.09.02.02 Asignación de acceso de usuario A.09.04.01 Restricción del accesoa la información A.09.04.02 Procedimientos de inicio de sesión seguro A.09.04.04 Uso de programas utilitarios privilegiados A.09.04.05 Control de acceso al código fuente de los programas MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS e
Marco Normativo
o
NCh-IS027001:2013: Tecnología de la información
- Técnicas de seguridad
Sistemas de gestión de la seguridad de la información — Requisitos.
o
Ley N” 19.628, de Protección de vida privada y datos personales.
o
Ley N” 19.799, de firmas y documentos electrónicos.
o
Ley N” 19.927, de Delitos de Pornografía Infantil.
o
Ley N” 20.285 regula el principio de transparencia de la función pública y el derecho de accesoa la información de los órganos de la Administración del Estado.
o
Ley N” 21.180, de Transformación Digital del Estado.
o
Ley N* 21.459, que Establece normas sobre Delitos Informáticos, deroga la Ley N*19.223 y modifica otros cuerpos legales con el Objeto de Adecuarlos al Convenio de Budapest.
o
Decreto N” 83, 2004, Ministerio Secretaría General de la Presidencia, que aprueba norma técnica para los órganos de la administración del estado sobre seguridad y confidencialidad de los documentos electrónicos.
o
El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior.
Decretos
Supremos
y
Normas
Internacionales
de
de
la
Información y Ciberseguridad:
Leyes relacionadas

<!-- pág. 4 -->

pay
e
Documentos Relacionados o Procedimiento gestión derechos de acceso y devolución de activos [1].
o
Política Seguridad de la Red [2].
ROLES Y RESPONSABILIDADES
Administrador de Sistemas.
o
Deben definir los accesos a los datos por parte de los usuarios de la institución como terceros, asegurando de mantener una adecuada segregación de funciones, y gestionar los accesos definidos de manera efectiva.
Jefe Departamento TIC o Debe establecer los controles y reglas de control de acceso para garantizar la seguridad y privacidad de la información.
TIC Administración y Operaciones / Soporte TIC o
Debe gestionar
los derechos de acceso a los medios de procesamiento de información que tenga a su cargo, según lo descrito en esta política.
MATERIAS QUE ABORDA.
e
Política de control de acceso.
e
Accesos a las redes y a los servicios de la red.
DIRECTRICES DE LA POLÍTICA Cumplimiento de la legislación Las medidas de control de accesoa la información definidas deben cumplir y ser consistentes con lo dispuesto por las normas y requerimientos legales definidos en el su Normativa del Sistema de Gestión de Seguridad de la Información a través de la Política General de Seguridad de la Información [3].
Accesos a las redesy a los servicios de la red Los usuarios solo deben tener accesoa la red y a los servicios de red en los que cuentan con autorización específica. El detalle de este punto se encuentra en la Política de Seguridad de la
Red.
Control de accesoa la Información
Todos
los funcionarios del MINSAL, incluso terceros, deberán tener acceso sólo a la información que necesitan para el desarrollo legítimo de sus funciones y actividades dentro de la organización. La asignación de privilegios y acceso a los activos de información deben estar basados en las necesidades de las áreas y aprobados por el propietario de los activos.
Estas necesidades de acceso deben ser determinadas por las respectivas jefaturas, en función de las tareas asignadas al cargo del funcionario.
Para todo medio de procesamiento de información al que se necesite conceder accesos (por ejemplo: servidores, aplicaciones, carpetas compartidas, etc.), el dueño de la Información en conjunto con el Departamento TIC debe designar un responsable del medio, quién será encargado de autorizar los permisos de accesoy solicitar los espacios necesarios.
Sólo se deben conceder accesos a terceros previa solicitud del dueño del medio de procesamiento de información y el dueño de la información, y nunca antes de haberse firmado un acuerdo de confidencialidad. Las cuentas de acceso a terceros deben tener

<!-- pág. 5 -->

HR | MINISTERIO DE SALUD hy especificado un tiempo de expiración el que debe ser controlado por el Administrador del sistema.
El Comité de Seguridad de la Información del Nivel Central tiene las facultades de suspender o eliminar los accesos a cualquier persona que represente riesgo en la confidencialidad, integridad o disponibilidad de la información.
Cualquier intento de acceso no autorizado a los equipos, carpetas compartidas, sistemas e información será considerado un incidente grave, por lo que debe reportarse de inmediato según lo descrito en el procedimiento de Gestión de Incidentes de Seguridad de la
Información.
Ante cualquier daño a un activo de información se procederá de acuerdoa lo descrito en la Política General de Seguridad de la Información (Sanciones) y el Procedimiento Acuerdos de Confidencialidad en contratos con terceros.
Administración del acceso
La
administración
de
perfiles de
usuario en
las
aplicaciones
radica en
los
usuarios
administradores de cada aplicación y las jefaturas de división correspondiente. No obstante, la responsabilidad de asignar un determinado perfil a un usuario puede ser delegada por la Jefatura de la División solicitante o por aquellos a quienes se les haya autorizado No se podrá otorgar accesoa los sistemas a ningún usuario hasta que se haya completado el proceso de autorización y registro de acuerdo con el Procedimiento de gestión de derechos de accesos y devolución de activos.
Para facilitar la administración de los accesos, se deben definir perfiles de acceso asignables a grupos de usuarios que, por sus responsabilidades en la organización, presenten necesidades de acceso equivalentes.
El área de Operaciones TIC debe implementar las reglas de control de acceso solicitadas por los Administradores de Aplicación y las Jefaturas de División correspondiente.
Administración de accesos especiales Las cuentas de administración tienen el poder de realizar cualquier acción sobre los sistemas que se administran, por lo que deben ser gestionadas con la máxima precaución. Debiendo cumplir, a lo menos, con lo siguiente:
Utilizar este tipo de cuentas únicamente para realizar labores que requieran permisos de administración;
Implementar un control de acceso basado en un doble factor de autenticación, de ser posible;
Registrar todas sus acciones (registro de logs);
Elacceso como administrador debe ser notificado convenientemente;
Evitar que los privilegios de las cuentas de administrador puedan ser heredados;
Lasclaves de acceso deben ser lo más robustas posibles y ser cambiadas con frecuencia;
Pueden ser sometidas a auditorías periódicas;
El otorgamiento de accesos con mayores privilegios (por ejemplo, acceso a: bases de datos, código fuente, etc.) a funcionarios que no pertenezcan al área de Operaciones TIC, debe ser solicitado por la Jefatura de la División responsable o quien delegue, al Encargado de Seguridad de la Información, justificando la solicitud.

<!-- pág. 6 -->

i
Segregación de funciones Los derechos de acceso deben ser asignados a perfiles individuales, de forma tal que las acciones realizadas con los accesos otorgados sean de responsabilidad directa del funcionario.
El otorgamiento de accesos respecto a recursos de información del MINSAL debe considerar una adecuada segregación de funciones, de modo que un mismo funcionario no pueda disponer, por su voluntad, del control de un proceso de negocios completo.
Las excepciones a
la
regla anterior deben ser aprobadas por la Jefatura de División correspondiente y autorizadas por el Jefe de Departamento TIC.
Revisión de los derechos de acceso El área de Operaciones TIC, es responsable de los accesos de los administradores de aplicaciones, de tal forma que se establezca un control efectivo desde el registro inicial de la cuenta hasta el momento en que requiera ser modificada, revocada o eliminada (ver Procedimiento de gestión de derechos de acceso y devolución de activos).
Los derechos de accesos deben ser revisados:
A intervalos regulares no mayores a 6 meses.
Después de cualquier cambio mayor en la organización.
Losaccesos de cuentas con mayores privilegios deben ser revisados al menos 2 veces al año.
Revocación de los accesos lógicos Ante situación de un cambio de cargo de funcionario, se deben revisar sus permisos de acceso lógico asignados y verificar que éstos sigan siendo válidos de acuerdo con su nueva función.
Cuando un funcionario termina su relación laboral con el MINSAL, todos sus permisos de acceso a la información deben ser revocados.
Es responsabilidad de las Jefaturas Directas informar formalmente las desvinculaciones de acuerdo con lo descrito en el procedimiento de gestión de derechos de acceso y devolución de activos.
Revocación de los accesos Los Usuarios Líderes de aplicación deben revisar en forma periódica los perfiles de usuario del personal vigente y solicitar al área Operaciones TIC la actualización de éstos cada vez que ocurra un cambio en la definición de funciones. Cualquier cambio en las funciones de una persona que acceda a información del negocio deberá verse reflejado en sus privilegios de acceso.
6.10
Procedimientos de inicio de sesión seguro El acceso a los sistemas y aplicaciones debe estar controlado por procedimientos de inicio de sesión seguro. El detalle de este control se encuentra en la Política de Identificación y autenticación de usuarios y el Procedimiento para la gestión de identidad y derechos de acceso.
6.11
Uso de programas utilitarios privilegiados El uso de programas de utilidad que pueden ser capaces de anular el sistema y los controles de aplicación se deben restringir y controlar integramente.
El detalle de este control se encuentra en el Procedimiento de control de cambios en los medios y sistemas de procesamiento de la información.

<!-- pág. 7 -->

Y
epi
6.12
Control de acceso al código fuente de los programas Se debe restringir el acceso al código de fuente de programas. El detalle de este control se encuentra en la Política de desarrollo de sistemas.
MECANISMO DE DIFUSIÓN.
La comunicación de la presente política se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
e
Publicación en la intranet de Minsal http://isalud.minsal.cl/ e
Correo informativo.
PERÍODO DE REVISIÓN.
La revisión del contenido de esta Política se efectuará a lo menos cada dos años por el Comité de Seguridad de la Información, o atendiendo necesidades de cambios para garantizar su idoneidad, adecuación y efectividad.
EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA En casos especiales, el Comité de Seguridad de la Información evaluará y podrá establecer condiciones puntuales de excepción en el cumplimiento de las presentes directrices, siempre que no infrinja la legislación vigente. Toda excepción debe ser documentada y dar lugar a un proceso de revisión de la política, que determinará si se deben agregar directrices específicas.
HISTORIAL Y CONTROL DE VERSIONES (Versión | Fecha | PágioSeción| ——
Motivodelcambio
ao
MI
O o
Octubre
Todas
| Creación del Documento
¡ Cambio de formato de documento.
Octubre
i
2019
Todas
| Se actualizan las referencias normativas.
Se actualizan dominios de la norma ISO 27001. |
| 6.5
| Se incluyen requisitos a cumplir para cuentas de
| administración.
Marzo
| Se incluyen los controles:
20233
$1610,611
A.09.02.02, A.09.04.01, A.09.04.02,
REFERENCIAS
[1]. SITIO INTRANET MINSAL — Procedimiento gestión derechos de acceso y devolución de activos — http://isalud.minsal.cl/ministerio/dgstic/SGSI/Paginas/default.aspx [2]. SITIO INTRANET MINSAL —
Política
de
la
Red
http://isalud.minsal.cl/ministerio/dgstic/SGSI/Paginas/default.aspx [3]. SITIO WEB MINSAL—
Política
General
de
de
la
Información
https://www.minsal.cl/seguridad_de la informacion/ /