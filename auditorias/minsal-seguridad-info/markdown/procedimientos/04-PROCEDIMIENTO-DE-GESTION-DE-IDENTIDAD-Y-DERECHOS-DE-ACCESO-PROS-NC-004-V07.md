<!-- pág. 1 -->

Ministorio de
bierno
de Chile
PROS-NC-004
PROCEDIMIENTO PARA LA GESTION DE IDENTIDAD Y DERECHOS DE ACCESO Sistema de Gestión de Seguridad de la Información - Nivel Central Versión Oficial Actual vO07 - Noviembre del 2024 a a
Elaborado
| NG UNA
Ze).Zaz,
lb 7
Revisado
H=> ANA
TH) l%)y LL
E
qm
2 : ISEURIDAD $
Aprobado
NS Lelela
ul :ANEds, 4 SEGURIDAD s
S not
Documento Controlado, prohibida su reproducción parcial o total sin autorización
SÁ
Clasificación de seguridad: Uso Interno

<!-- pág. 2 -->

Ñ
SALUD
Contenido
IS
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS ...oocnnccccccanccoconinnnccnannnnccccococnananns 4
AMBITODE APLICAClÓN coooocononococococococonoonononanacononononoronoconocacanocononanonanancnocanonocononccccanano ADMINISTRACIÓN DE CUENTAS ESPECIALES c0ococcococococcocnocononcncnncnonocnononnncncncononconono9 CREACIÓN, ELIMINACIÓN O AJUSTES DE DERECHOS DE ACCESO .0ooococcococococncocon.. 10 ELIMINACIÓN O AJUSTE DE LOS DERECHOS DE ACCESO cooococccococcoonnncncconnninoncncns 13 RESPONSABILIDADES EN LA DESVINCULACIÓN O CAMBIO DE EMPLEO .................. 18 GESTIÓN DE DERECHOS DE ACCESO PRIVILEGIADOS.....oooococococococoncnonococinnonononanoso 19 REVISIÓN DE LOS DERECHOS DE ACCESO DE USUARIO coooocoococcccononononononononononncnno 19 PERFILES DE ACCESO DE LOS USUARIOS...occncccccononccononcnccnooncconononcconnnc cocoanoncnnonoo Z 0D
PERCDODEREVIS[ÓN.........x.05:-.
17,205
oem ui
000000. 2
e
OS
EXCEPCIONES AL CUMPLIMIENTO DEL PROCEDIMIENTO ...oooocccnccccononcnonnnconononaninonncc
ZO
¡si VA

<!-- pág. 3 -->

"MN
MINISTERIO
DE
ly
¿pue
pS
O
| Página 3 de 25
SALUD
PROPÓSITO.
Establecer las actividades necesarias para la gestión de identidades y derechos de accesos a la información, asegurando una adecuada administración de las autorizaciones y claves de acceso de los usuarios a los activos tecnológicos de la organización.
Administrar el ciclo de vida de los usuarios, desde la creación de las cuentas, roles y permisos necesarios hasta su inhabilitación; a partir de los requerimientos reportados por el Departamento de Gestión de Personas y/o de su Jefatura directa; lo anterior para que el funcionario tenga acceso adecuado a los sistemas de información y recursos tecnológicos, validando su autenticación, autorización y auditoría.
ALCANCE.
Subsecretarías de Salud Pública y de Redes Asistenciales.
Este procedimiento es aplicable a todos los funcionarios' (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para las Subsecretarías de Salud Pública y de Redes Asistenciales y que tengan derechos de accesoa la información que puedan afectar los activos de información del Ministerio de Salud.
En cuanto a las temáticas de protección abordadas, el ámbito de aplicación de este procedimiento corresponde al(a los) Dominio(s) de Seguridad de la Información y Controles de Seguridad respectivos, detallados a continuación:
Alcance de Dominios y Controles de Seguridad de la Información
Estándar
ID Control
Nombre del Control
5.11
Devolución de Activos
5.15
Control de Acceso
5.16
Gestión de Identidad
150 27001:2022
Información de Autenticación
5.18
Derechos de Acceso
Responsabilidades en la desvinculación o cambio de empleo Gestión de Privilegios de Acceso
TERMINOLOGÍA.
Para los fines de este procedimiento, se definen los siguientes términos:
Privilegios de Acceso: Conjunto de permisos otorgados a un usuario para interactuar con los recursos o información de la organización, los cuales incluyen: lectura, escritura, ejecución, modificación o eliminación de datos según el nivel de autorización.
Derechos de Acceso: Permisos específicos que determinan qué recursos o información puede ser accedida por un usuario y en qué condiciones, de acuerdo con su rol y la clasificación de la información. Los derechos de acceso incluyen:
o
Acceso Total: Permiso para acceder, modificar y eliminar toda la información o recursos asignados.
oA
Alo largo del procedimiento cada vez que se mencione funcionario se refiere a: funcionarios (planta, contrata, reemplazos:PY y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.).
o
F

<!-- pág. 4 -->

A
| Versión: 7
| Página 4 de 25 MIA
W Neo)
SALUD
o
Acceso Restringido: Permiso limitado a ciertas áreas de información o recursos.
o
Acceso de Solo Lectura: Permiso para ver la información sin poder modificarla.
o
Acceso Condicional: Permiso de acceso bajo condiciones específicas, como autorización previa o necesidad operativa.
Principio de Necesidad de Saber: Solo se otorgarán derechos de accesoa la información en función de la necesidad de cada usuario para desempeñar su función dentro de la organización.
Principio de Menor Privilegio: Los usuarios recibirán únicamente los privilegios mínimos necesarios para realizar sus tareas específicas, minimizando el riesgo de acceso indebido a información sensible.
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS.
Marco Normativo.
o NCh I5027001:2022: Seguridad de la información, ciberseguridad y protección de la privacidad - Controles de seguridad de la información o El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior.
Decretos Supremos y Normas Internacionales de Seguridad de la Información y
Ciberseguridad:
Otras normas relacionadas:
o
Ley20.285 regula el principio de transparencia de la función pública y el derecho de accesoa la información de los órganos de la Administración del Estado.
o
Ley19.628 de Protección de protección de datos personales.
o
Ley 19.927 de Delitos de Pornografía Infantil.
o
Ley 19.880, de bases de los procedimientos administrativos que rigen los organismos del Estado o Ley N* 20.584, de derechos y deberes de los pacientes frente a las acciones y prestaciones de salud.
o
Ley N* 21.180 Ley de Transformación Digital del Estado, establece directrices para la modernización de los procesos y servicios digitales en instituciones públicas.
o
LeyN” 21.459, que Establece normas sobre Delitos Informáticos, deroga la Ley N*19.223 y modifica otros cuerpos legales con el Objeto de Adecuarlos al
Convenio de Budapest.
o
Ley N* 21.663 sobre Marco de Ciberseguridad, esta ley proporciona un marco para asegurar la ciberseguridad de infraestructuras críticas, que indirectamente impacta en la protección de datos.
o
La Ley 21.668 establece la interoperabilidad de las fichas clínicas, sobre protección de datos establece un marco legal para salvaguardar la privacidad y 4 ES los derechos de los ciudadanos en relación con sus datos personales.
E

<!-- pág. 5 -->

— A
| Página 5 de 25
SALUD
o
Decreto 273, de 2022, que establece la obligación de reportar incidentes de ciberseguridad a los organismos del Estado al CSIRT de gobierno.
o
Decreto N? 41, de 2012, del Ministerio de Salud, Reglamento de Ficha Clínica.
o
Decreto Exento N' 51 que “aprueba norma general Técnica N* 237 estándares asociados a las acciones y prestaciones de salud a distancia y telemedicina” o El Decreto N* 533 establece el marco regulatorio en ciberseguridad para las instituciones públicas en Chile.
o
El Decreto Supremo N* 7 establece una Norma Técnica de Seguridad de la Información y Ciberseguridad, en concordancia con la Ley N* 21.180 sobre Transformación Digital del Estado.
o
Decreto N*73, 2022 del Ministerio del Interior.
Documentos Relacionados.
o
Política de seguridad en la identificación y autenticación de usuarios.
o
Política de Seguridad para el control de acceso.
o
Política de Seguridad para las relaciones con los proveedores.
AMBITO DE APLICACIÓN.
Todos los usuarios y sistemas de control de accesos de la organización y sus unidades dependientes donde sea implementado este procedimiento, para el uso de:
o
Datos,
o
Sistemas Operativos,
o
Sistemas de Aplicación, o
Bases de Datos,
o
Otros Recursos Informáticos.
ROLES Y RESPONSABILIDADES.
Jefatura de Unidad, Departamento o División (Dueños de Activos).
e
Responsable de autorizar y garantizar que los accesos de los usuarios a los diferentes aplicativos tecnológicos bajo su gestión estén alineados con las necesidades del cargo y las políticas de seguridad Ministeriales.
e
Aprobarynotificar formalmente el ingreso de nuevos funcionarios, asegurando que se les asignen los derechos de acceso adecuadosa sus funciones.
e
Solicitar oportunamente la creación, modificación o eliminación de accesos a los sistemas de información, conforme a los cambios en roles o funciones.
AAN
e
pa
y

<!-- pág. 6 -->

ml
e
SALUD
e
Comunicar oportunamente cualquier desvinculación, traslado o modificación en las responsabilidades de los funcionarios para actualizar o revocar sus derechos de acceso, previniendo riesgos de accesos indebidos.
e
Asegurar que los usuarios de cada unidad cumpla con las normativas establecidas en el procedimiento de gestión de identidad y derechos de acceso.
Coordinador Administrativo o funcionario designado.
e
Responsable de gestionar las solicitudes de acceso a los sistemas de información, asegurando que estén directamente relacionadas con las funciones autorizadas por la Jefatura y cumplan con las políticas de seguridad institucional.
e
Comunicar de manera inmediata al Departamento de Gestión de Personas, cualquier desvinculación de funcionarios para proceder con la revocación o ajuste de sus derechos de accesoa los sistemas de información.
e
Recopilar, validarymantener los antecedentes mínimos necesarios para la tramitación del ingreso de nuevos usuarios, incluyendo la asignación de derechos de acceso provisionales cuando corresponda.
Departamento TIC (Unidad de Operaciones).
Responsable de configurar los accesos iniciales a los sistemas de información bajo su administración para los nuevos funcionarios, según las autorizaciones aprobadas por la Jefatura correspondiente.
e
Revocar
de manera
oportuna
los accesos
de
los
funcionarios
desvinculados,
asegurando que no queden cuentas activas asociadas a usuarios no autorizados.
e
Coordinar la recuperación de los activos de información y cuentas asociadas a los funcionarios desvinculados, conforme al apartado 7.5.3 del presente procedimiento, para evitar la pérdida o exposición de datos institucionales.
e
Mantener un registro actualizado de todas las acciones realizadas sobre accesos y permisos, facilitando auditorías internas o externas cuando sea necesario.
Departamento Administración y Servicios Recuperar los activos asignados a los funcionarios que se desvinculan.
Administradores de Sistemas e.
Gestionar y ser responsable de los accesos de usuarios a las aplicaciones en las que tienen derechos de administración, resguardar las contraseñas de administración.
e
Administrar y supervisar los accesos de los usuarios a las aplicaciones y sistemas bajo su responsabilidad, asegurando que se cumplan los principios de autorización y privilegios mínimos.
e
Realizar revisiones regulares de los permisos asignados para detectar y corregir accesos indebidos o desactualizados.
Y,

<!-- pág. 7 -->

| PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS DE ACCESO.
"Ml
MINISTERIO
DE
| Versión: 7
| Página 7 de 25
SALUD
e
Asegurar que las configuraciones de acceso y seguridad de las aplicaciones cumplan con las normativas establecidas en la política de gestión de identidad y derechos de acceso.
e
Informar oportunamente al Departamento TIC o a las áreas correspondientes sobre cualquier irregularidad, incidente de seguridad o necesidad de ajuste en los accesos.
Departamento de Gestión de Personas.
e
Proveer al Departamento TIC un listado actualizado de ingresos y desvinculaciones de funcionarios, con una periodicidad mínima trimestral, para facilitar la gestión oportuna de los derechos de accesoa los sistemas.
e
Asegurar la comunicación efectiva con las jefaturas responsables para verificar y validar la información relacionada con los movimientos de personal.
Encargado de Seguridad de la Información.
e
Coordinar y supervisar periódicamente la revisión de la gestión de identidad y los derechos de acceso de los usuarios, asegurando que estos sean acordes a las funciones asignadasy a los principios de mínimo privilegio.
Supervisar que
las cuentas de
usuario, especialmente aquellas con privilegios administrativos, sean deshabilitadas o eliminadas de manera oportuna, en colaboración con el Departamento de Tecnologías de Información y Departamento de
Gestión de Personas.
e
Asegurar que las acciones realizadas en la gestión de identidad y acceso cumplan con las normativas legales, las políticas institucionales y los estándares de seguridad vigentes.
Departamento de Auditoría Interna.
e
Evaluar el cumplimiento de este procedimiento, proponiendo mejoras para asegurar la conformidad con normativas legales y estándares internos.
Funcionarios.
e.
Mantener la confidencialidad de las contraseñas y claves secretas asociadas a su accesoa las plataformas tecnológicas del MINSAL.
e
Cumplir con lo dispuesto en las Políticas y Procedimientos del Sistema de Seguridad de la Información en todas las acciones relacionadas con su rol y responsabilidades.
e
Evitarla divulgación de información sensible o confidencial relacionada con el Minsal, tanto dentro como fuera del ámbito laboral.
e
Asumir la responsabilidad sobre el uso y protección de la información institucional, incluso fuera de las dependencias del trabajo y del horario laboral habitual.
e
Garantizar la transferencia ordenada y completa de la información perteneciente al SN a
AO
Minsal en caso de cese de funciones, cambio de puesto o responsabilidades.
iv

<!-- pág. 8 -->

-M
IN]
DE
eE:
ANS
| Página 8 de 25
SALUD
e
Familiarizarse y cumplir con las Políticas de Seguridad de la Información del Ministerio, independientemente de su condición de funcionario o tercero autorizado para acceder a las plataformas tecnológicas
PROCEDIMIENTO.
REGISTRO DE USUARIOS.
7.1.1
Consideraciones generales.
La asignación y control de privilegios y derechos de acceso serán gestionados de acuerdo con el rol del usuario, la clasificación de la información y las necesidades operativas, asegurando que solo las personas autorizadas puedan acceder a los recursos según los niveles de seguridad establecidos. Los accesos serán revisados periódicamente para garantizar que se ajustena las políticas de seguridad vigentes.
En cualquier registro de usuarios se debe utilizar registros únicos para permitir a los usuarios vincularse y ser responsables de sus acciones (ver Política de seguridad en la identificación y autenticación de usuarios).
Es responsabilidad de los Administradores de Sistemas debe mantener un registro formal de todas las personas autorizadas, asignándoles un ID único. Este registro debe incluir los derechos de accesoa la información y activos asociados y actualizarse cada vez que ocurran cambios en los derechos de acceso lógico y físico, para que asegure la trazabilidad de estos.
7.1.2 Creación de accesos para funcionarios nuevos.
La solicitud de los accesos debe ser entregada por la unidad solicitante con a los menos 2 días hábiles de anticipación, esta solicitud de acceso no incluye el proceso de compra de equipos o licenciamiento requerido y para su implementación debe contar con la aprobación del departamento de personal.
Previa creación de acceso, se realizará una validación de la identidad de la persona para asegurar que no tiene otro usuario asignado y que la nueva identidad en los sistemas sólo sea asignada a una única persona.
La Jefatura que está contratando, deberá coordinar, los recursos específicos a los cuales el usuario requiere acceder, tales como:
alaredde la unidad contratante alequipo de procesamiento (PC)
aunaaplicación específica alaolas bases de datos que requiere alosservicios (Impresoras, telefonía, etc.)
asistemas y menús y/o funcionalidades específicas de los sistemas alas carpetas compartidas
TN
=  alosobjetos, grupos y dominios a e
GS

<!-- pág. 9 -->

je
| Versión: 7
SALUD
aotrosrecursos que deben identificarse puntualmente Se debe tener en cuenta que debe existir una adecuada segregación de funciones, desde un punto de vista de control interno, de acuerdo con la función administrativa del usuario, la criticidad de los datosy la oposición de intereses.
Se podrán conceder derechos de acceso temporales por un periodo de tiempo limitado y revocarlos en la fecha de expiración, en particular en el caso de personal temporal o personal que requiere acceso temporal a activos de información de la institucional a los que no tiene acceso de manera regular.
7.1.3
Solicitud de acceso para funcionarios activos.
En el caso de los traspasos de cargos, se debe evaluar si los permisos otorgados con anterioridad deben o no continuar vigentes. Si se deben habilitar más permisos de los que actualmente tienen, se deberá contar con el requerimiento por parte del
Jefe de
Departamento respectivo.
7.1.4
Solicitud de acceso para funcionarios con conectividad remota.
En el caso de usuarios que se desempeñarán bajo modalidad de trabajo remoto (teletrabajo), se debe evaluar de acuerdo con los accesos solicitados, los permisos y herramientas requeridas, las cuales deberán ser configuradas en el equipo asignado para esta función. Estos permisos una vez definidos deberán ser autorizados por parte del Jefe de Departamento respectivo.
7.1.5 Acceso a los recursos de cada uno de los equipos.
Elacceso alos recursos de los equipos debe ser autorizado por el Jefes de Unidad o supervisor directo con autorización del Jefe de Departamento o Jefe de Divisiones de la organización para los cuales se está solicitando acceso.
La asignación de permisos a los recursos solicitados debe ser revisadas por el Administrador de Sistemas y deberá contar con las aprobaciones de accesos necesarios antes de su implementación. Aprobar los derechos de accesos requiere que estos se encuentren en línea con la clasificación de información definida en la Política de Clasificación y Manejo de la Información, con los protocolos definidos en la Política de Identificación y Autenticación de Usuarios, y con los requisitos de seguridad del perímetro físico.
Como
principio
general,
el
usuario
sólo debe tener acceso a los recursos mínimos indispensables para realizar su tarea y se le prohibirá el acceso a todos los recursos de información salvo a aquellos que se les permita expresamente.
ADMINISTRACIÓN DE CUENTAS ESPECIALES.
aA
E-
AL
Y

<!-- pág. 10 -->

MIRE epE
| Versión: 7
| Página 10 de 25
MA INTAO
SALUD
Cuando un usuario requiera una cuenta especial con altos privilegios, es decir, acceso a sistemas de información, sistema operativo o sistema de administración de bases de datos, el control de dichos accesos estará a cargo del Departamento TIC. La creación de estas cuentas deberá ser autorizada por la Unidad de Operaciones y/o el Encargado de Seguridad.
Los permisos de acceso serán asignados de acuerdo con la necesidad de uso del usuario y conformea la Política de Control de Acceso, es decir, bajo el principio de mínimo privilegio y en función de los roles o funciones que desempeñe.
Se deberán identificar las cuentas de usuarios con mayor riesgo en cada uno de los sistemas para garantizar un control adecuado sobre los accesos críticos.
Las contraseñas de acceso con altos privilegios deben ser gestionadas de manera estricta, en particular, en el caso de servidores internos (no externalizados).
La responsabilidad de la administración de las contraseñas con mayores privilegios recae directamente en el Departamento TIC, quien velará por su seguridad y conformidad con los procedimientos establecidos.
CREACIÓN, ELIMINACIÓN O AJUSTES DE DERECHOS DE ACCESO.
Para solicitar accesos o eliminación al sistema y a los datos, la Jefatura respectiva deberá enviar un correo electrónico con dicha solicitud al área de
Tl
a
Mesa
de
Servicio
mdseminsal.cl, este correo electrónico una vez validado, será utilizado como parte de la solicitud que se enviará al administrador del Sistema?.
El sistema debe poseer mecanismos de protección de accesos, de identificación del usuario que genera el pedido y posibilitar la conservación del documento de respaldo.
CREACION DE USUARIOS
La Jefatura respectiva deberá informar las incorporaciones nuevas de la unidad a la cuenta mail mdseminsal.cl, lo antes posible una vez conocida la fecha de incorporación de la nueva contratación.
Adicional
a
lo
anterior,
de
Gestión
de
Personas
debe
comunicar
trimestralmente, a través de un correo electrónico, al Encargado de Seguridad y/o jefe Depto.
TIC, el nombre de los usuarios que se han incorporado a la organización, para que realicen un control efectivo de los usuarios habilitados.
Aspectos mínimos para considerar por parte de las áreas de soporte en la incorporación de un nuevo funcionario:
Completar correctamente ficha de personal Firma conforme de acuerdo de confidencialidad por parte del usuario Revisar disponibilidad o validar adquisición de recursos técnicos requeridos PC, Notebook, Celular, Licencias y otros específicos requeridos Crearusuario en Active Directory des y
MA
? Encargado de la administración de usuarios (creación y eliminación de accesos) para los Sistema ¿59 o Informático bajo su responsabilidad.
y

<!-- pág. 11 -->

de
al
no.
Versión: 7 | Página 11 de 25
SALUD
Crear cuentas VPN de ser requerida
Daraccesosa
carpetas compartidas
Daraccesos atodos los sistemas Incorporar nuevo usuario a grupos de trabajo comúnmente usados (teléfono)
Asignar cuenta de Correo Asignar usuario de grupos de correo
Crearusuario enimpresoras Sistema operativo cliente debidamente licenciado y aprobado por la entidad.
= — Driversinternos y de periféricos utilizados en la organización.
La creación de los accesos de nuevos funcionarios (correo electrónico, Active Directory, estación de trabajo), se debe realizar de acuerdo con el siguiente flujo:
E
A
Solicita
PON
doo
E E Racexdaz ce +?
ls
E 3
Hcdibado
a :
|q
Artecedentes Sel
L
E pl -
AN
E Registra de
| z
derechos de
H
ICO
E
É
Revisa y
a
Pp]
A
z
requerimiento
E
a
g
E
di
erntreza ce cayes
i
¡gooo
qe acceso ¿firma
E
Ue acceso
EN 0%
fegisiro de entrega
E |
E
ross
usuarios
E Al
O
GUN
MBADO -,
c

<!-- pág. 12 -->

y
a
| Versión: 7
| Página 12 de 25
SALUD
información de su dependencia, es responsable de solicitar mediante correo electrónico mdseminsal.cl los accesos básicos para los nuevos funcionarios mediante el Formulario de solicitud para creación/eliminación de accesos.
Elárea de Soporte del Departamento TIC es responsable de la creación de los accesos básicos de ingreso, que incluye:
Creación de correo electrónico.
Creación de usuario en Active Directory.
Habilitación de estación de trabajo.
La entrega de las contraseñas temporales de ingreso se realiza mediante el Registro de Entrega de Claves de Acceso, que es firmado por el funcionario que recibe, quedando una copia en poder de Soporte y otra en poder del funcionario.
En
el registro de entrega de claves de acceso se proporciona un enunciado con las responsabilidades implicadas en el uso de los sistemas de información del Ministerio?.
Las condiciones de uso incluyen:
Cambiar clave inicialmente programada por TIC Mantener confidenciales las claves secretas.
Cumplir con lo establecido en las Políticas y Procedimientos del Sistema de Seguridad de la Información, en todo lo que sea de su competencia.
Entender la responsabilidad funcionaria, aún fuera de las dependencias de trabajo y fuera del horario normal de trabajo.
7.4.1
Registro de usuarios en los sistemas de información.
La creación o eliminación de accesos a los sistemas de información se debe realizar de acuerdo con el siguiente flujo:
E ——_ A
EN
3 Los requerimientos de seguridad para el uso de correo electrónico y la gestión de contraseñas, están definidos en la política E Y de protección de mensajes electrónicos y la Política de Seguridad en la identificación y autenticación de usuarios.
SS

<!-- pág. 13 -->

gg
— e
_—————_———_—_
——— — o _——
AAA
Y
y
a.
Versión: 7 | Página 13 de 25
SALUD
EA E
E TE DA
E
E
ArY
E
hotifcar
l
hatificar
a
No
si
o
FET
PA
Solasar
g
E
a
Pee
Encregar aves
¿Pequermieto de
HEsO E
Je acceso
ad
del Siztema?
información de su dependencia, es responsable de solicitar mediante correo electrónico la creación o eliminación de los accesos a los sistemas de información” mediante el Formulario de solicitud de creación/eliminación de accesos firmado.
En el formulario se deberá indicar:
Usuario a asignar accesos (nombre.apellido).
"Rut.
Detallar el o los sistemas a los cuales el funcionario deberá tener acceso.
Detalle del perfil de usuario con el que debe contar el funcionario para cada uno de los sistemas a los cuales se solicita acceso.
En caso de ser necesario se debe solicitarla autorización de acceso del usuario a los sistemas, al propietario para su uso y/o acceso.
ELIMINACIÓN O AJUSTE DE LOS DERECHOS DE ACCESO.
Para estos casos la Jefatura de Unidad, Departamento, División o Coordinador Administrativo deberá solicitar al Departamento de Gestión de Personas la eliminación de accesos respectivos, la Jefatura respectiva debe informar la baja de los usuarios que ya no presten servicios en sus respectivas funciones. Lo anterior mediante correo electrónico dirigido a la a, e
ARPA
AN
E
e
* Para el caso de los Sistemas y/o software que no cuente con licenciamiento, la solicitud debe ser acompañada sa Ya
E
con los recursos necesarios para la compra y/o licenciamiento.
k
ES

<!-- pág. 14 -->

PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS DEACCESO
A
no
Versión: 7 | Página 14 de 25
SALUD
Jefatura de Personal, quien informará oportunamente a la Jefatura del Departamento TIC y/o Encargado de Seguridad, apenas se determine la fecha de desvinculación o cambio de cargo.
Aspectos mínimos para considerar por parte de la Unidad de Operacionesy el área de soporte para bajas de usuarios:
- — Eliminar usuario en Active Directory.
Eliminar cuentas VPN.
— Eliminar accesos a todos los sistemas.
— Eliminaraccesos a carpetas compartidas.
- — Eliminar cuenta de Correo.
Eliminar usuario de grupos de correo.
- — Eliminar usuario de las impresoras.
Respaldar información de carpetas compartidas.
— Respaldar cuenta de correo, si el usuario lo solicita.
— Respaldar PC del usuario de acuerdo con lo solicitado por Jefe Unidad responsable.
Formatear PC del usuario (cuando sea requerido).
7.5.1
Consideraciones generales.
Todo funcionario
es responsable de
devolver todos
los activos pertenecientes a la organización que estén en su poder como consecuencia de la finalización de su relación laboral, contrato o acuerdo.
Equipos personales: en los casos en que un funcionario utilice equipos propios, tiene la obligación de transferir toda la información pertinente a Minsal y eliminarlo de cualquier soporte que posea, de ser necesario la Departamento TIC podrá tener acceso a los equipos para asegurar la transferencia de información.
Si un funcionario posee conocimiento perteneciente a Minsal, por haber sido desarrollado dentro del marco de las labores para las que fue contratado, que es importante para las operaciones en curso, es su responsabilidad documentar dicha información y transferirla al
Servicio.
Todo funcionario que mantenga información personal en los equipos proporcionados por Minsal deberá consignarla en una carpeta denominada “información personal”. Toda la información no incluida en esta carpeta se considerará laboral y por tanto podrá ser revisada y respaldada por MINSAL.
7.5.2 Eliminación de Accesos a funcionarios con accesos críticos o privilegiados.
Para el caso de funcionarios con accesos críticos o privilegiados*, se debe tener especial cuidado en la gestión de la suspensión de accesos, para estos casos, posteriora la notificación de desvinculación y o renuncia del funcionario, se deberá proceder con el bloqueo de todas las cuentas del usuario y activos de acuerdo con lo siguiente:
> Esto es, que cuentan con uno o más permisos por encima de los atribuidos a las cuentas normales a sistemas de información, at Ms sistema operativo, sistema de administración de base de datos o que dichos permisos se suelan traducir en tener acceso a E Y información sensible o privilegiada para el que hacer del Ministerio de Salud.
a
A
G
Y

<!-- pág. 15 -->

Ñ
### 10. DE
MO MEZ
| Versión: 7 | Página 15 de 25
SALUD
Bloquearlos accesos a los sistemas de información.
Bloqueo de casilla (s) de correo y configuración de mensaje automático de aviso para los correos entrantes.
Bloqueo de cuentas (por ejemplo, VPN, Videoconferencia, almacenamiento en la nube, etc.).
Avisaralos proveedores relacionados de la desvinculación del funcionario.
Recuperación de los activos que han sido asignados al funcionario.
Identificación y respaldo de la información laboral contenida en los dispositivos (la información personal o privada no podrá ser revisada, sino que debe ser simplemente eliminada)a solicitud del Jefe directo del área o Unidad.
Eliminar de los grupos de mensajería instantánea relacionados a sus funciones en la institución.
Unavez recuperada la información, podrá revocarse las cuentas respectivas.
Para estos casos la Jefatura de Unidad, Departamento, División o Coordinador Administrativo deberá solicitar al Departamento de
Gestión
de Personas
la
eliminación de accesos respectivos. Lo anterior mediante correo electrónico dirigido a la Jefatura de Personal, quien informará oportunamente a la Jefatura del Departamento TIC y/o Encargado de Seguridad, quien procederá de inmediato con las acciones indicadas anteriormente. Además de avisar a proveedores relacionados con el fin de evitar gestiones posteriores a la desvinculación que puedan poner en riesgo el normal funcionamiento del Minsal.
Cualquier acción que se realice sobre los accesos y activos asignados, debe ser comunicado al funcionario.
Al funcionario se le debe otorgar la oportunidad de respaldar su información personal.
7.5.3 Recuperación de activos y eliminación de derechos de accesos.

<!-- pág. 16 -->

PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS
DE ACCESO
DS.
us
y
os
Versión: 7 | Página 16 de 25
SALUD
TEN
PEA E
eeacioretiminacion
de acsesos
i ad
E
po
A
Á SE
E
S
Pe
tomes
ES
E
Registro de
E
2335
caportiros,
G
| E
| 109e : Egreso Orá
equpestiato mod,
E z
bento. Gestión ES
Egreso
Eo
E
Penas
B|
E
E
i E
tana
E
Wo
js;
antecedertes
En
informar
a
E
a31i9nadoz
E
ed
E
activos información
Í
Temclógicos
Registro de
y
derechosde
E
accezo
información de su dependencia, es responsable de informar, mediante correo electrónico mdsOminsal.cl, cualquier desvinculación de funcionarios mediante el Formulario de solicitud para creación/eliminación_ de accesos?
Esta
notificación
debe
ser
enviada
en
simultáneamente a:
Departamento de Gestión y Desarrollo de Personas.
Departamento de Administración y Servicios.
Departamento TIC.
6 Para
el caso de los cambios de en la funciones o dependencias, la Jefatura debe informar dichos cambios al Departamento de Gestión y Desarrollo de Personas quién a su vez informará al Departamento TIC la revisión de los derechos de acceso de los usuarios.
SN =
q:
a
ES
ADO

<!-- pág. 17 -->

l
PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS DEACCESO mn.
¡D: PROS-04
| Página 17 de 25
SALUD
Ante el informe de desvinculación de algún funcionario, el Departamento de Administración y Servicios? es responsable de gestionar la recuperación de los activos asignados al funcionario.
Entre otros, se encuentran:
e
Documentos corporativos, e
Equipamiento,
e
Teléfonos móviles,
e
Tarjetas de acceso,
e
Manuales,
Los activos recuperados deben ser registrados en el Sistema de Inventario, el cual debe documentar toda la información y activos, incluidos, pero no limitados a: dispositivos finales de usuario, dispositivos de almacenamiento portátiles, equipos especializados, claves físicas (como tarjetas RFID o MFA físicos), y copias físicas de información (archivadores, informes, etc. En virtud del nivel de clasificación de la información)
Ante el informe de desvinculación de un funcionario, el jefe directo será responsable de coordinar la recuperación de la información corporativa contenida en los activos digitales asignados, como computadores o discos duros externos. Este proceso debe garantizar la protección de la información institucional, el respaldo de datos críticos, y la correcta transferencia o eliminación de la información, utilizando herramientas y procedimientos que cumplan con las políticas de la organización. Todo este proceso debe realizarse conforme a las políticas y estándares establecidos por Minsal, en colaboración con el Departamento TIC cuando sea necesario.
El departamento TIC es responsable de bloquear los derechos de acceso a los sistemas de información (cambio de contraseñas, eliminación de usuario según sea requerido), junto con recuperar los activos tecnológicos de información asignados al funcionario. Entre otros, se encuentran:
e
Discos Duros.
e
CD-DVDderespaldos.
e.
Software.
e
Manuales.
e
Cualquier información almacenada en medios electrónicos.
La recuperación de activos de información se realiza de acuerdo con el siguiente modelo:
7 En los casos de equipos asignados directamente por la División o Departamento, el Coordinador Administrativo o la
S
Jefatura correspondiente debe gestionar la recuperación de los activos.
E
NOS

<!-- pág. 18 -->

Ñ
| A
| Versión: 7
| Página 18 de 25
SALUD
Cain
¿Activo puede
|abs?
sea>da?
intarmación
y
NO
A Eamacón
dl
¿si aplica?
sl
NO
E Y E .—”
Sl
Una vez transcurridos 30 días desde el bloqueo de los derechos de acceso, estos deben ser eliminados.
En caso de que no se devuelvan todos los equipos asignados o sean devueltos con desperfectos, se debe informar al Departamento de Administración y Servicios, para que se tomen las medidas correspondientes.
RESPONSABILIDADES EN LA DESVINCULACIÓN O CAMBIO DE EMPLEO
Personal externo:
Según lo definido en la política de seguridad para las relaciones con los proveedores, todo personal externo que desarrolle labores para MINSAL deberá conocer y aplicar, dentro de su ámbito de acción, los lineamientos contenidos en la Política General de Seguridad de la Información, disponible en el sitio web de MINSAL, observando sus directrices y colaborando en su aplicación, resguardando la confidencialidad de toda la información a la que tenga acceso. Todas estas obligaciones y las definidas en el Sistema de Gestión de Seguridad de la Información continuarán vigentes tras la finalización de las actividades que el personal externo desarrolle para MINSAL.
Personal a honorarios:
Según lo definido en las cláusulas de confidencialidad en contratos de honorarios deberán dar cumplimientoa las políticas de Seguridad de la Información del Minsal, la política de privacidad y protección de datos personales, debiendo resguardar la confidencialidad de toda la información a la que tenga acceso todas estas obligaciones y las definidas en el Sistema de Gestión de Seguridad de la Información continuarán vigentes tras la finalización de las actividades que el personal externo desarrolle para MINSAL.
Funcionarios (Planta, contrata, reemplazos y suplencia):
Todas las obligaciones de protección de datos y confidencialidad de la información, definidas en el Sistema de Gestión de Seguridad de la Información de Minsal, continuarán vigentes tras la 7% finalización de las actividades que el personal externo desarrolle para MINSAL.
y
DGA

<!-- pág. 19 -->

_______ PROCEDIMIENTO DEGESTIÓN DE IDENTIDAD Y DERECHOS DEACCESO
Ñ
e
a
| Versión: 7 | Página 19 de 25
SALUD
GESTIÓN DE DERECHOS DE ACCESO PRIVILEGIADOS La asignación, modificación y eliminación de derechos de acceso privilegiados a sistemas de información, sistemas operativos y sistemas de administración de bases de datos, que están bajo la responsabilidad del Departamento TIC. Mantendrán un registro actualizado y auditable de los accesos privilegiados.
Los derechos de acceso privilegiados serán asignados únicamente a usuarios cuya función o rol lo requiera estrictamente, siguiendo el principio de mínimos privilegios. La asignación se realizará conforme a lo establecido en la Política de Control de Acceso, garantizando que los permisos concedidos se limiten al requisito mínimo necesario para desempeñar sus tareas.
Se llevará a cabo una revisión regular de los derechos de acceso privilegiados para asegurar su vigencia y adecuación a las responsabilidades actuales de los usuarios. Cualquier acceso innecesario o desactualizado deberá ser revocado inmediatamente
7.7.1
Parala Gestión de Derechos sobre Acceso Privilegiados en Sistemas No Administrados por el Departamento TiC Los derechos de acceso privilegiados en sistemas que no son administrados directamente por el
TIC, como
los sistemas en
la
nube
o en
infraestructuras externas, deberán ser gestionados de acuerdo con las políticas de acceso específicas de esos entornos.
Elacceso privilegiado a estos sistemas debe cumplir con los mismos principios de mínimos privilegios y será responsabilidad del dueño del activo asegurar que los proveedores ofrezcan mecanismos para la auditoría y el control adecuado de estos accesos.
Losaccesos privilegiados a sistemas externos deberán establecerse procedimientos claros para la asignación, modificación y revocación de accesos privilegiados en dichos sistemas, manteniendo consistencia con la Política de Control de Acceso.
Encaso de que un acceso privilegiado ya no sea necesario, ya sea por un cambio en el rol del usuario o por la finalización de su relación con la organización, dicho acceso será revocado inmediatamente, sin excepción.
REVISIÓN DE LOS DERECHOS DE ACCESO DE USUARIO?
Los Dueños de los Activos de Información tendrán la responsabilidad de revisar e informar al Jefe del Departamento TIC o al Departamento de Gestión Personas sobre cualquier cambio en las funcioneso roles del personal que implique una modificación de los derechos de acceso.
Los derechos de acceso de los usuarios deberán revisarse al menos cada seis meses, asegurando que sean consistentes con las funciones actuales del personal.
Se debe chequear la asignación de privilegios para asegurar que no se hayan obtenido privilegios no autorizados.
AVES
Los requerimientos de seguridad para la gestión de derechos de acceso, están definidos en la política de contro! de Acceso. cY a l

<!-- pág. 20 -->

mM
TE
| Versión: 7 | Página 20 de 25
SALUD
Los ID de usuario y cuentas que ya no sean necesarias deberán ser identificados y eliminados para prevenir accesos indebidos.
PERFILES DE ACCESO DE LOS USUARIOS.
Los perfiles de accesos son el conjunto de atribucionesy privilegios a los cuales tiene acceso una cuenta de usuario o grupo de usuarios.
Los Jefatura de Unidad, Departamento o División, responsables de la custodia de los datos de sus procesos deben revisar en forma periódica los perfiles de usuario del personal vigente y realizar una actualización de éstos cada vez que ocurra un cambio en la definición de funciones Jefe Departamento TIC y/o Gestor de Identidad.
La administración de perfiles radica en el Gestor de Identidades y las Jefaturas de Unidad, Departamento o División, responsables de la custodia de los datos de sus procesos. La responsabilidad de asignar un determinado perfil a un usuario corresponderá al Jefe de Departamento solicitante, velando porque sus atribuciones correspondan a la descripción de cargo y responsabilidades funcionales que se le confieren al usuario.
Se debe considerar lo siguiente:
Realizar un constante análisis de las funciones del personal de las unidades.
El perfil de usuario debe ser solicitado formalmente poreljefe directo.
Los perfiles de usuario deberán estar acorde a las funciones de cada rol dentro de la organización.
Noasignar mayores privilegios a un usuario que las descritas por función.
Cualquier cambio en los perfiles de usuario debe ser aprobado por el Jefe del área.
7.10
NIVELES DE AUTORIZACIÓN Los requerimientos de creación, eliminación o modificación de accesos a recursos deben ser autorizados por los siguientes responsables:
Requerimiento
Responsable de autorizar
Accesos
de
usuarios
a
los
equipos
de
Jefe de Departamento, Gestor de Identidad y procesamiento y a los recursos: servicios, Gestión de Personas (RRHH)
e
aplicaciones y/o datos o Accesos de cuentas de usuario especiales
Jefe
de
Informática
y
Encargado
de.
Seguridad
Bajas
de
usuarios
en
los
equipos
de
Jefe de Departamento, y Gestión de Personas procesamiento (RRHH)
7.11.
ADMINISTRACIÓN DE CLAVES DE ACCESO.
El Ministerio de Salud considera que todos los sistemas computacionales que permitan accedera la información que éste administra, deben contar con un sistema de identificación y autenticación de usuarios que permita garantizar que sólo personal debidamente autorizado
EN
¡Ms

<!-- pág. 21 -->

PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS
DE ACCESO
A
| Versión: 7
| Página 21 de 25
SALUD
tiene acceso a la información, considerando además sólo el acceso a través de claves seguras
*. Para una adecuada administración de las claves de acceso a los recursos informáticos, debe tenerse en cuenta las siguientes consideraciones:
7.12
CUENTAS DE USUARIO.
Las cuentas de usuario deben cumplir con los requerimientos que se detallan a continuación:
Cada persona debe tener una única identificación de su cuenta personal de usuario en todos los sistemas / equipos de la unidad.
Laidentificación de la cuenta personal debe correspondera una nomenclatura estándar predefinida compuesta por (12) caracteres como mínimo. Contener Letras mayúsculas, minúsculas y números.
Laidentificación de cuentas especiales también debe correspondera una nomenclatura estándar predefinida compuesta por (12) caracteres como mínimo, asignando los primeros dos caracteres al código correspondiente al sistema / aplicación, y los restantes deberán ser una serie de caracteres que identifiquen el tipo de permiso otorgadoa la cuenta.
Se deja establecido que para aquellas aplicaciones donde el control de acceso a la aplicación es realizado fuera del Active Directory de la unidad esta clave de acceso será de acuerdo con lo estipulado por el proveedor sin especificación de largo.
7.13
UTILIZACIÓN DE LAS CUENTAS DE USUARIO.
Se prohíbe a los usuarios la utilización de cuentas genéricas y compartir su cuenta con otros usuarios.
7.14
DATOS A INCLUIR EN LAS CUENTAS DE USUARIO.
En la descripción de cada cuenta personal se debe incluir:
RUN o Número único de Identificación, elnombrey apellido completo del responsable, elnombrea visualizar, elárea, ounidada la que pertenece, email, anexo,
Cargo.
Jefe Unidad o Supervisor Directo.
En la descripción de las cuentas especiales, adicionalmente debe figurar la función para la que fue creada.
7.15
ADMINISTRACIÓN DE CONTRASEÑAS DE CADA USUARIO.
? Política de Identificación y Autenticación de Usuarios.
A
QU:

<!-- pág. 22 -->

E
y
EE
O
| Versión: 7 | Página 22 de 25
SALUD
Toda cuenta de usuario debe tener asociada obligatoriamente una contraseña.
Cada vez que un usuario sea creado en un recurso de la organización, se deberá definir una contraseña única y robustas. Esta contraseña de carácter personal deberá ser cambiada obligatoriamente en el primer acceso realizado por el usuario.
Todas las contraseñas deben cumplir con los siguientes requisitos:
Deben permanecer encriptadasy residir en archivos ocultos y protegidos.
No deben ser visibles por pantalla al momento de ser ingresadas.
Deben ser definidas con una longitud mínima de doce (12) posiciones.
Deben contener letras y números (ser alfanumérica)
Nodeben ser en blanco y Nodeben ser genéricas o de fácil detección.
Para la generación de contraseñas se debe seguir la siguiente metodología de combinación de datos:
La contraseña no debe ser igual a la identificación personal (User_ID) ni tampoco ser demasiado obvias.
El Gestor de Identidades debe comunicar al usuario la contraseña (cuando se le otorgue por primera vez).
En
caso
de
que
el
Gestor
de
Identidades
lo
crea
conveniente
debe
utilizar
adicionalmente procedimientos de llamado y re-llamado para asegurarse la identidad del usuario al que le transfiere la contraseña.
Para el cambio de las contraseñas deben considerarse los siguientes requisitos:
Exigir el cambio automático, la primera vez que el usuario ingresa al sistema.
Exigir el cambio automático, al menos cada noventa (90) días, puede ser menor.
Ser distinta por lo menos de las últimas seis (3) anteriores.
Permitir ser cambiadas toda vez que el usuario lo requiera.
7.16
BLOQUEO DE CUENTAS.
De cumplirse el número de intentos fallidos establecido, la cuenta debe quedar bloqueada, siendo los únicos autorizados para su desbloqueo el Departamento TIC y podrá ser habilitada por Soporte Tl. Para las cuentas especiales de mayor riesgo, la reconexión debe ser documentada y comunicada al Encargado de Seguridad.
De ser solicitado se podrá bloquear la cuenta de usuario durante los permisos o ausencias prolongadas. Para ello el usuario o su respectivo Jefe directo deberá informar, a través de un correo electrónico, las fechas durante las cuales se producirá la ausencia.
El bloqueo se deberá mantener hasta la efectiva comunicación con el usuario responsable de la misma.
7.17
OTRAS CLAVES DE SISTEMAS Existen servicios propios de las unidades, que, dado su criticidad e importancia estratégica dentro del departamento, e! conocimiento, administración y uso de estas claves radican sólo a uu

<!-- pág. 23 -->

PROCEDIMIENTO DE GESTIÓN DE IDENTIDAD Y DERECHOS DE ACCESO a e
| Versión: 7
| Página 23 de 25
SALUD
en dicha unidad, excluyendo al área de Informática de la subsecretaría o unidad de esta responsabilidad.
Estas claves de acceso son, por ejemplo:
Usuario y contraseña a las cuentas bancarias de la organización.
Usuario y contraseña para Facturación Electrónica.
Otros.
REGISTROS:
Solicitud para creación de accesos.
Entrega de credenciales y claves de acceso.
Planilla de registro de eliminación de accesos.
Registros de entrega y devolución de equipamiento.
El período de mantención de los registros será de dos años.
MECANISMO DE DIFUSIÓN.
La comunicación del presente procedimiento se efectuará de manera que el contenido dela documentación sea accesible y comprensible paratodos los usuarios, alo menosse deberá hacer difusión mediante los siguientes canales:
e
Publicación en la intranet de Minsal http://isalud.minsal.cl/ e.
Correoinformativo.
e
Publicación en el sitio web Minsal http://www.minsal.cl/seguridad_de_la_informacion/
PERÍODO DE REVISIÓN.
El presente procedimiento deberá ser revisado cada dos años o cuando ocurran cambios significativos para garantizar que:
o
Sigue siendo adecuado para su propósito y preciso.
o
Reflejalos cambios en las tecnologías.
o
Está alineado con la legislación vigente, los estándares internacionales y las mejores prácticas.
EXCEPCIONES AL CUMPLIMIENTO DEL PROCEDIMIENTO En situaciones excepcionales, el Jefe de Departamento TIC, el CISO o el Comité de Seguridad de la Información tendrán la facultad de evaluar y establecer condiciones específicas para la excepción al cumplimiento de este procedimiento, siempre que tales excepciones no infrinjan la legislación vigente ni comprometan la seguridad de la información.
Cada excepción deberá ser debidamente documentada, y se deberá iniciar un proceso de revisión
Del procedimiento en
el que se determinará si es necesario realizar
E
modificaciones específicas.
A
ES

<!-- pág. 24 -->

| dal JLS
| Versión: 7
| Página 24 de 25
SALUD
CONTROL DE VERSIONES.
0s
Fecha de
Secciones modificadas
Motivo del cambio
Versión
Aprobación
Diciembre 2013
Todo el documento
Creación
del
Registro de usuarios
de
los
Julio 2014
Eliminación
de
derechos
de
flujos del proceso
acceso
Se
los
flujos
del
a
proceso, se eliminó la sección de normativa 2013 de la gestión de contraseñas (se
NCh-ISO 27001
incluyen
en
la
política
de
Noviembre 2016
identificación de usuarios.
Se incluye el control:
A.07.03.01
Responsabilidades
en
la
desvinculación
o
cambio
de
empleo
Se incluye el control A.09.04.03.
— Revisión
y
Se
los
documentos
del
aplicables.
Se
cambia
División
TIC
por
Departamento TIC.
Se
cambia
de
RRHH
por
de
Gestión
y Desarrollo de Personas.
Se actualiza el flujo del punto 6.1.2
Octubre 2019
Se actualiza el flujo del punto 6.1.3
Se actualiza
el
flujo
del punto
6.2.2 del procedimiento.
En el punto 6.5 la responsabilidad de revisar los accesos se cambia alos Encargados de Seguridad de la Información.
Se
los
registros
de
operación del procedimiento.
Se actualizan las vías de difusión o
Se
incluye
punto
6.2.2.
Revisión
y
Marzo 2021
Eliminación
de
Accesos
a
del
Funcionarios
con
accesos
críticos o privilegiados.
pay

<!-- pág. 25 -->

A
—————— A SIA AS RARA AAA
RA
Ñ
| Ia
| Página 25 de 25
SALUD
sz
Fecha de
Secciones modificadas
Motivo del cambio
Versión
ds
Aprobación
Incluye Gestión de
Identidad
e
Revisión
y
Agosto 2021
Identificación y Autenticación de del usuarios.
Pag. 3, 4,5, 6, 7, 9, 10, 16,21 a
Normativa
ISO
27002:2022;
normativa
ISO
Terminología;
Leyes
y
27001:2022
decretos;
Roles
y
Responsabilidades; 7.1 Registro
Sl
a
de
Usuarios;
Gestión
de
Derechos Privilegiado; Vigencia respaldos; 10 Periodo revisión; 11
Excepciones.