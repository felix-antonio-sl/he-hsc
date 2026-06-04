<!-- pág. 1 -->

PROS-NC-011
PROCEDIMIENTO PARA EL ASEGURAMIENTO DE
CALIDAD DE SOFTWARE
Sistema de Gestión de Seguridad de la Información — Nivel Central
AO
A
Versión Oficial Actual vO1 — Mayo del 2021 mn
Elaborado
Encargado Aseguramiento de Mayo 2021 A goesIApS
Calidad TIC MINSAL
A] Hé[N — DELA
ja)
José
Villa Catalan /Encargado
VA ( CIBER:ECUIDAD
osé
Vi
Revisado
de Ciberseguridad
Mayo 2021
|GN A
PS
Gino Paolo Peirano Alvarado
ARDEN pa *
Jefe Departamento Tecnologías
EN Po
Aprobado
Sta mormación y
Juio 2021
¿AX
RA
Comunicaciones
(E DEPARTAEN di
Ol
L—FECNONGÍAS DELA
NS COMUNICACIONESES]
ElE

<!-- pág. 2 -->

PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE
MATT
SOFTWARE
e
IP
vnNsSTERIODESALUD
Contenido
E
a
A
Oooo
B
TERMINOLOGÍA.eee
DOCUMENTOS APLICABLESecc
ROLES YRESPONSABILIDADES cocoa econo o REINOe e cocer SOLICITUD DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE .crccanoocannoocanonoccncorcicorea ALCANCES DEL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE.........4 PLANIFICACIÓN DEL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE..4 AMBIENTE PARA EL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE...5 e DATA PARA EL PROCESO DE ASEGURAMIENTO DE CALIDAD.....aceeciannrromennnecerrsse9 VERSIONAMIENTO DEL SOFTWARE A CERTIFICAR v.cccccnaccanonconnnonnocononneromeeniaancecencaaS SEGUIMIENTO AL PROCESODE ASEGURAMIENTO
DE CALIDADocio
PRUEBASDE CARGA Y ESTRESecc
6.10
ANÁLISIS DE CÓDIGO FUENTE car rc cc cc LO
A RAol
A
A
e
O
REVISION Y MEDICIONe
e
toca LL
CONTROL DE VERSIONEScinco caca cae do

<!-- pág. 3 -->

PEE
PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE
O aO
PROPÓSITO
Establecer un marco regulatorio mínimo para el Aseguramiento de Calidad de Software de Minsal, con el propósito de que los desarrollos y mantenciones de software estén alineados con los procedimientos de seguridad de la información definidos en Minsal para el desarrollo de sistemas.
ALCANCE
Las áreas de desarrollo de la organización y todas las áreas usuarias de las aplicaciones desarrolladas.
Subsecretarías de Salud Pública y de Redes Asistenciales.
Este procedimiento es aplicable a todos los funcionarios! (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para las Subsecretarías de Salud Pública y de Redes Asistenciales y que tengan derechos de accesoa la información que puedan afectar los activos de información del Ministerio de Salud.
Este procedimiento abarca los siguientes controles definidos en la norma NCh-ISO
27001.0f2013:
A.14.02.01 Política de desarrollo seguro A.14.02.02 Procedimientos de control de cambios del sistema A.14.02.03 Revisión técnica de las aplicaciones después de los cambios en la plataforma de operación A.14.02.09 Prueba de aprobación del sistema
TERMINOLOGÍA
MINSAL: Ministerio de Salud.
SGSI: Sistema de Gestión de Seguridad de Información.
DOCUMENTOS APLICABLES
- Marco Normativo
o
NCh-15027001:2013: Tecnología de la información — Técnicas de seguridad — Sistemas de gestión de la seguridad de la información — Requisitos.
o
El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior.
Decretos Supremos y Normas Internacionales de Seguridad de la
Información y Ciberseguridad:
Leyes relacionadas
e
Documentos Relacionados Alo largo del procedimiento cada vez que se mencione funcionario se refiere a: funcionarios (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.).
EPA
A
Todaversión impresa deeste documento seconsidera como Copia NoControlada.
qu

<!-- pág. 4 -->

E PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE
TT
SOFTWARE
. O
o Documento del Sistema de Gestión de Seguridad de la
Información,
disponibles en http://isalud.minsal.cl
E
ROLESYRESPONSABILIDADES Todas las áreas de desarrollo de Minsal, los Usuarios, Custodios Físicos, Custodios de los Datos, contratistas, Administradores de Seguridad, las Unidades de Informática, Gestión de Personas y el Comité de Seguridad de la Información, son responsables del cumplimiento de este procedimiento.
PROCEDIMIENTO
o
SOLICITUD DE ASEGURAMIENTO DE CALIDAD DESOFTWARE Los líderes de los proyectos de desarrollo o mantención de sistemas deben formalizar la necesidad de un proceso de aseguramiento de calidad de software para un aplicativo específico a través del formulario Solicitud de Aseguramiento de Calidad de Software, como parte de su planificación del proyecto, el que debe hacerse llegar al encargado del servicio en TIC MINSAL.
Juntoa la solicitudse debe adjuntar la metodología a utilizar en el desarrollo o mantención del software, la documentación de requerimientos de negocio asociados al nuevo sistema a desarrollar o a la modificación que se requiere aplicar a dicho sistema, manuales de usuario, y toda otra documentación o información que sea relevante para el proceso de aseguramiento de calidad requerido.
El encargado del servicio de Aseguramiento de Calidad de Software dejará registro de la solicitud recepcionada en el Catastro de Solicitudes de Aseguramiento de Calidad de Software, asignándole un código de identificación a dicha solicitud el que será entregado al requirente del proceso de aseguramiento de calidad.
ALCANCES DEL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE El encargado de Aseguramiento de Calidad de Software en TIC Minsal, deberá analizar y evaluar el alcance y estrategia propuestas para el proceso de Aseguramiento de Calidad de Software para el nuevo desarrollo o mantención del sistema, y lo formalizará al requirente del proceso de aseguramiento de calidad.
PLANIFICACIÓN DEL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE El encargado de Aseguramiento de Calidad de Software en TIC Minsal, deberá estimar los recursos y plazos asociados al proceso de certificación requerido, y los hará llegar al requirente del proceso de certificación, quien a su vez incorporará dichas actividades y plazos en el plan principal del proyecto de desarrollo o mantención de software.
pl.

<!-- pág. 5 -->

E
JE] PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE O VINISTERIO DE SALUD Este plan de proyecto ajustado deberá ser compartido con el encargado del servicio de Aseguramiento de Calidad de Software, para una mejor coordinación y seguimiento de las actividadese hitos del proyecto.
AMBIENTE PARA EL PROCESO DE ASEGURAMIENTO DE CALIDAD DE SOFTWARE El requirente del servicio deberá coordinar la preparación y habilitación de todos los ambientes o requisitos tecnológicos para llevar a cabo el proceso de aseguramiento de calidad de software e informará al encargado del servicio cuando este se encuentre disponible. Junto a esto, se deberán entregar las credenciales que sean necesarias para acceder al sistema y sus funcionalidades, según los roles definidos.
El requirente del servicio deberá garantizar que el ambientea utilizar durante el proceso de aseguramiento de calidad de software no sufrirá cambios de ningún tipo durante el tiempo que demande cada ciclo de aseguramiento de calidad. En caso de ser requeridas nuevas intervenciones sobre estos ambientes, estas actividades deberán ser coordinadas con el encargado de aseguramiento de calidad.
El no cumplimiento de este punto, podría generar la invalidación del proceso de aseguramiento de calidad aplicado o en curso, por lo que un nuevo proceso de aseguramiento de calidad deberá ser planificado cuando las condiciones sean las adecuadas.
DATA PARA EL PROCESO DE ASEGURAMIENTO DE CALIDAD La data requerida para llevar a cabo el proceso de aseguramiento de calidad deberá ser provista por el requirente del servicio, a no ser que el equipo de aseguramiento de calidad esté en condiciones y tenga todo lo disponible para preparar la data de prueba que permita realizar el proceso.
VERSIONAMIENTO DEL SOFTWARE A CERTIFICAR En requirente del servicio deberá garantizar que las fuentes y/o binarios del sistema desarrollo o modificado se encuentren versionados en la plataforma de versionamiento utilizado por Minsal.
El sistemaa certificar deberá contar con un número de versión que permita su identificación y trazabilidad, respecto a versiones anteriores del mismo.
El proceso de aseguramiento de calidad será válido solo para la versión especificada por el requirente.
SEGUIMIENTO AL PROCESO DE ASEGURAMIENTO DE CALIDAD
El
encargado
del
proceso de
Aseguramiento
de
Calidad
de
Software
entregará
periódicamente un avance en el proceso, incluyendo estadísticas, hallazgos detectados y evidencias de los hallazgos detectados.
sol a,
A
pSYe

<!-- pág. 6 -->

IT
SOFTWARE
OU
UONVINISTERIODE SALUD ASEGURAMIENTO DE CALIDAD DE SOFTWARE FUNCIONAL
6.8.1 Criterios deAceptación del aseguramiento de calidad funcional El serviciode aseguramiento de calidad de software funcional posee los siguientes criterios e de aceptación para cada proceso de certificación, los que adicionalmente serán informados al comienzo del proceso al requirente del servicio. Estos criterios de aceptación permitirán la aprobación o rechazo final al proceso de aseguramiento de calidad.
Condición a . . . a .
eii
Condición de Aceptación e a Cantidad de casos de prueba ejecutados
| 100% de los casos de prueba definidos
N? de hallazgosInvalidantes pendientes N? de hallazgos Graves pendientes e N? de hallazgos Medios pendientes Impacta hasta un 1% de los casos de prueba N? de hallazgos Leves pendientes
| Impacta hasta un 5% de los casos de prueba
_
6.8.2 Análisis y diseño de Casos de Prueba El equipo de Aseguramiento de Calidad de Software realizará el análisis de la documentación de requerimientos funcionales entregado y diseñará los casos de prueba propuestos para el proceso de aseguramiento de calidad.
El encargado del servicio de aseguramientode calidad enviará los casos de prueba diseñados al requirente del servicio, para efecto de que sean revisados, confirmados, o ajustados y complementados por el negocio, si así amerita.
La nueva versión de los casos de prueba validados por el negocio deberá ser entregada al encargado del servicio de Aseguramiento de calidad de software para que sean utilizados en el proceso.
El encargado del servicio dejará registro de los casos de prueba que serán utilizados en el proceso.
i
6.8.3 Ciclo de ejecución de casos de prueba El proceso de Aseguramiento de Calidad considera la ejecución de los casos de prueba definidos en hasta 3 ciclos de aseguramiento de calidad.
El encargado del servicio de aseguramiento de calidad informará al requirente el resultado de cada ciclo de ejecución de los casos de prueba.
d
Luego de cada ciclo de aseguramiento de calidad, y en basea los criterios de aceptación establecidos, el proceso será evaluado para su aprobación.
aa
Al término del tercer ciclo de aseguramiento de calidad, y si los criterios de aceptación no
AL
se han cumplido, el proceso de aseguramiento de calidad será rechazado.
. pa.

<!-- pág. 7 -->

PONE] PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD
DE
TU OVINISTERIO DESALUD El encargado del servicio dejará registro del resultado de cada ciclo de ejecución de casos de prueba.
6.8.4 Hallazgos detectados en proceso de Aseguramiento de Calidad de Software Durante el proceso y al término de cada ciclo de aseguramiento de calidad, se entregará al requirente del servicio los hallazgos que se hayan detectado, las evidencias asociadas a estos hallazgos cuando estas aporten información para la claridad del hallazgo detectado, y estadísticas del proceso ejecutado.
El requirente del servicio deberá coordinar la revisión de los hallazgos con el negocio, para efecto de definir el curso a seguir con cada uno de ellos y compartirá la decisión con el equipo de aseguramiento de calidad de software.
El encargado del servicio dejará registro de los hallazgos detectados en cada ciclo de ejecución de casos de prueba, de las evidencias generadas y de la decisión del negocio respecto a estos hallazgos.
6.8.5 Término del proceso de Aseguramiento de Calidad de Software Funcional Cuando en basea los criterios de aceptación definidos para el proceso de aseguramiento de calidad, se haya decidido el resultado del proceso, el encargado del servicio confirmará al requirente el resultado de este y preparará y compartirá el Informe de Término del Proceso de Aseguramiento de Calidad que incluirá el resultado final del proceso.
El proceso de aseguramiento de calidad podrá ser cancelado, esto es, no se continuará con el mismo, siempre que exista acuerdo entre el requirente del servicio y el encargado del servicio.
El encargado del servicio dejará registro tanto del resultado final del proceso en el Catastro de Solicitudes de Aseguramiento de Calidad como del Informe Final del proceso de aseguramiento de calidad de software.
PRUEBAS DE CARGA Y ESTRES
6.9.1 Equipo, Roles y Responsabilidades Para llevar a cabo un proceso de Pruebas de carga y estrés deberá ser conformado un equipo multidisciplinario. Este equipo deberá estar conformado por representantes de al menos las siguientes áreas o empresas: Negocio, Proveedores, Proyectos TIC MINSAL, Arquitectura TIC MINSAL, PMO TIC MINSAL, Operaciones TIC MINSAL, Seguridad de la Información TIC MINSAL y Aseguramiento de Calidad de Software TIC MINSAL Se deberán definir los roles y responsabilidad en el proceso para cada uno de los integrantes del equipo.
PERAL,
A A ES:

<!-- pág. 8 -->

ETE PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE
TU
OSONNISTERIODESALUD
6.9.2 Estadísticas y Métricas Actuales y Futuras El negocio deberá informar las estadísticas y métricas actuales del sistema, y de las proyecciones esperadas para un periodo dado de tiempo en el futuro.
6.9.3 Flujos de Negocio a considerar El negocio deberá definir los flujos más representativos de su servicio, para efecto de que sean utilizados en las pruebas de carga y stress.
6.9.4 Niveles de servicio esperados El negocio deberá definir los niveles de servicio actuales y esperados para su servicio en el futuro, para efecto que sean utilizados como de referencia para el proceso de pruebas de cargay stress.
6.9.5 Modeloa utilizar en las pruebas El encargado de aseguramiento de calidad deberá coordinar con el equipo asignado para el proceso, la definición del modelo que deberá utilizarse en las pruebas de carga y stress.
6.9.6 Monitoreo, Métricas y Evidencias
E
El encargado
de aseguramiento de calidad deberá coordinar con el equipo asignado, la definición del monitoreo de la infraestructura, comunicaciones y aplicaciones a realizar, y las métricas y evidencias que deberán ser obtenidas durante la ejecución de las pruebas.
Deberán definirse los responsables de la preparación y ejecución del monitoreo, y de la entrega de las métricas y evidencias, una vez se hayan ejecutado las pruebas de carga.
6.9.7 Automatización
El encargado de aseguramiento de calidad deberá coordinar la definición de las herramientas y equipamiento de automatización que serán utilizados para simular los flujos de negocio representativos a ser utilizados durante las pruebas de cargay stress.
El encargado de negocio coordinará el desarrollo de las automatizaciones requeridas y de la preparación de dichos procesos para la ejecución de las pruebas de carga y stress.
6.9.8 Estrategia de Pruebas de Carga y Stress El encargo del servicio de aseguramiento de calidad coordinará la elaboración de la estrategia a utilizar para aplicar pruebas de Carga y Stress sobre el sistema requerido, a través del documento Estrategia de Pruebas de Carga y Stress.
a ]aa

<!-- pág. 9 -->

IU
ONINISTERIODE SALUD
Página9de1t1
El encargado del servicio de aseguramiento de calidad dejará registro de este documento elaborado.
6.9.9 Ciclo de ejecución de pruebas de carga y stressos de prueba El proceso de Pruebas de Carga y Stress se realizará en basea ciclos de ejecución, hasta que los resultados sean aceptados por el equipo asignado.
plo
6.9.10
Recopilación de métricas y evidencias i El encargado de aseguramiento de calidad coordinará con el equipo asignado la recopilación de métricas y evidencias, las documentará y compartirá con el equipo para un análisis del ciclo de ejecución.
El encargado del servicio dejará registro de estas métricas y evidencias.
6.9.11
Análisis de resultados de ciclo de ejecución El encargado del servicio de aseguramiento de calidad coordinará con el equipo asignado, el análisis de los resultados obtenidos en cada ciclo de ejecución de pruebas de carga y stress.
Producto de este análisis, el equipo deberá definir las actividades siguientes, tales como:
aplicar cambios en infraestructura, aplicar cambios en comunicaciones, aplicar cambios a configuraciones de software básico, aplicar ajustes a los aplicativos o componentes del sistema o dar por finalizado el proceso de pruebas de cargay stress.
6.9.12
Aplicaciones de mejoras, ajustes o modificaciones A partir de lo acordado por el equipo asignado producto del análisis de resultados de cada ciclo de ejecución de pruebas de cargay stress, cada responsable definido deberá aplicar las acciones acordadase informará al equipo del resultado de dichas actividades.
Una vez finalizadas las actividades previamente acordadas, el encargado de aseguramiento de calidad coordinará con el equipo asignado, la ejecución de un nuevo ciclo de pruebas de cargay stress.
6.9.13
Término del proceso de Pruebas de Carga y Stress Cuando el proceso de Pruebas de Carga y Stress haya finalizado, el encargado del servicio de aseguramiento de calidad preparará y compartirá el Informe de Término del Proceso de Pruebas de Carga y Stress con todos los antecedentes definido u obtenidos durante el proceso.
El encargado del servicio dejará registro tanto del resultado final del proceso de Pruebas de Carga y Stress como del Informe Final del proceso.
) La
Toda
versión impresa deeste documento se consideracomo Copia NoControlada.
E
(Ele

<!-- pág. 10 -->

ole PROCEDIMIENTO DE ASEGURAMIENTO DE CALIDAD DE aO - MINISTERIO DE SALUD
Página 10de 11
6.10 ANÁLISIS DE CÓDIGO FUENTE
El software
que sea desarrollado o modificado será analizado en sucódigo fuente para.
detectar vulnerabilidades de seguridad o de calidad del mismo.
El encargado del servicio coordinará este análisis y hará entrega del informe con los resultados al solicitante del servicio, para que coordine la resolución de las vulnerabilidades.
El encargado del servicio dejará registrode este proceso de análisis y de sus resultados.
U a
a

<!-- pág. 11 -->

a
SOFTWARE
UU
NINISTERIODE SALUD
REGISTROS
Solicitud de Aseguramiento de Calidad de Software Aseguramiento de Calidad de Software Casos de prueba diseñados Casos de prueba ejecutados por ciclo Hallazgos detectados en el proceso Evidencias generadas en el proceso
Métricas del proceso
"Informe de Término del Proceso de Aseguramiento de Calidad Pruebas de Carga y Stress Estrategia de Pruebas de Carga y Stress Métricas y Evidencias generadas durante el proceso "Informe de Término del proceso de Pruebas de Carga y Stress
DIFUSION
La comunicación del presente procedimiento se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en la intranet de Minsal http://isalud.minsal.
cl/
Correo informativo.
REVISION Y MEDICION
El presente procedimiento deberá ser revisado a lo menos cada dos años o cuando ocurran cambios significativos para asegurar su continua idoneidad, eficiencia y efectividad.
CONTROL DE VERSIONES
Versión |Fecha
de | Motivo
del
Secciones modificadas sa
Aprobación cambio
ESAS
Julio 2021
| Creación del
Todas
documento
ES a