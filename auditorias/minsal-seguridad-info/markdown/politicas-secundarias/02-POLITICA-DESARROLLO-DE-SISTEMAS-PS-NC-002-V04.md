<!-- pág. 1 -->

20N
Ministorio de
Y
Salud
PS-NC-002
POLITICA DESARROLLO DE SISTEMAS Versión Oficial Actual vO04 - Noviembre del 2024
QQ, Respensable
oo
Fecha
y Ema
y
Elaborado
NS
L
¡ALA
a
NA
EN
o
z
IA PAR EA
Revisado
y
YN
a NAT
ES HEAD AREADO A
Aprobado il hovzla UARCAA. OAERSEGURIDAD [TT Documento Controlado. Prohibida su reproducción parcial o total sin autorización. is A r E 0
Clasificación
de seguridad: Pública
NS NS

<!-- pág. 2 -->

A
CA DESARROLLO DESISTEMAS
Pi
Contenido
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS ..ccconicnnniccconocanocaccnnnnccanacacanincnanincacnnnno2 EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA ..cocconccncnnnnincnncnnnonionenonnenecnaciriasascos17 e — S

<!-- pág. 3 -->

la
sá3
PROPÓSITO
Esta Política de Desarrollo de Sistemas, establece los lineamientos para garantizar la seguridad en los productos de software desarrollados para el Ministerio de Salud(Minsal)
y las instituciones del Sector Salud.
Define las directrices y requisitos que deben estar presentes tanto en los desarrollos internos como externos de la Institución, considerándolas en cada una de las etapas de desarrollo, controlando los ambientes de trabajo en desarrollo, testing y producción.
ALCANCE O ÁMBITO DE APLICACIÓN Esta política se aplica atodos los sistemas de información desarrollados, actualizados o mantenidos para el Minsal y las instituciones del Sector Salud, independientemente de si el trabajo es realizado por equipos internos de la institución o por proveedores y profesionales externos contratados para dichos fines.
Es aplicable atodos los funcionarios (planta, contrata, reemplazos y suplencia), personal a honorarios y terceros (proveedores, compra de servicios, etc.), que presten servicios para la Subsecretaría de Salud Pública y la Subsecretaría de Redes Asistenciales que participen en cualquier etapa del desarrollo de un sistema de información.
En cuanto a las temáticas de protección abordadas, el ámbito de aplicación de esta política corresponde al (a los) Dominio(s) de Seguridad de la Información y Controles de Seguridad respectivos, detallados a continuación:
Alcance de Dominios y Controles de Seguridad de la Información
Estándar
1D
Nombre del Control
Control
Seguridad de la información en la gestión de proyectos Acceso al código fuente
8.19
Instalación del software en sistemas de producción
IS027001:2022
8.25
Seguridad en el ciclo de vida del desarrollo
E
8.29
Pruebas de seguridad en desarrollo y aceptación
8.31
Separación de los entornos de desarrollo, prueba y producción
8.32
Gestión de cambios
MARCO NORMATIVO Y DOCUMENTOS RELACIONADOS.
Marco Normativo:
|1S0 27001:2022 Seguridad de
la información, ciberseguridad y protección de la privacidad - Sistemas de gestión de la seguridad de la información - Requisitos.
150 127002:2022 sobre Seguridad de la información, ciberseguridad y protección de la privacidad
END
a
y

<!-- pág. 4 -->

num
El Marco Jurídico referido a los Sistemas de Seguridad de la Información (SSI), publicado en el portal del CSIRT del Ministerio del Interior.
o
Decretos Supremos y Normas Internacionales de Seguridad de la Información y
Ciberseguridad.
Normas relacionadas:
LeyN”19.628, de Protección de vida privada y datos personales.
LeyN”19.799, de firmas y documentos electrónicos.
Ley19.880, de bases de los procedimientos administrativos que rigen los organismos del Estad LeyN”19.927, de Delitos de Pornografía Infantil.
LeyN” 20.285 regula el principio de transparencia de la función pública y el derecho de accesoa la información de los órganos de la Administración del Estado.
LeyN”21.180, de Transformación Digital del Estado.
Ley N” 21.459, que Establece normas sobre Delitos Informáticos, deroga la Ley N*19.223 y modifica otros cuerpos legales con el Objeto de Adecuarlos al Convenio de
Budapest.
Ley N? 21.663 sobre Marco de Ciberseguridad, esta ley proporciona un marco para asegurar la ciberseguridad de infraestructuras críticas, que indirectamente impacta en la protección de datos.
Decreto N? 83, 2004, Ministerio Secretaría General de la Presidencia, que aprueba norma técnica para los órganos de la administración del estado sobre seguridad y confidencialidad de los documentos electrónicos.
DFLN?, 2005, Ministerio de Salud.
Decreto N”136, de 2005, Reglamento Orgánico del Ministerio de Salud.
El Decreto N* 533 establece el marco regulatorio en ciberseguridad para las instituciones públicas en Chile, que incluye normas para la protección de la información, la gestión de incidentes de ciberseguridad y la protección de infraestructuras críticas, en las que se procesan datos personales.
El Decreto Supremo N* 7 establece una Norma Técnica de Seguridad de la
Información
y
Ciberseguridad,
en
concordancia
con
la
Ley
N*
21.180
sobre
Transformación
Digital del Estado. Que tiene el objetivo de definir estándares mínimos de seguridad y ciberseguridad para todos los órganos de la administración pública en Chile, contribuyendo a la protección de los datos personales y a la seguridad de la información en los sistemas digitales gubernamentales.
Documentos Relacionados Procedimiento de desarrollo seguro [1].
NO
a Controlado.o reproducción parcial o total sin autorización.
3vi
S
asificación de seguridad o:
Pública
NS

<!-- pág. 5 -->

ROLES Y RESPONSABILIDADES.
Jefe Departamento TIC.
o
Establecery aplicar los controlesy políticas de acceso necesarios para garantizar la seguridad en los entornos de desarrollo, pruebas y producción.
o
Supervisar la implementación de medidas de control de acceso y evaluar su efectividad en colaboración con el Encargado de Seguridad de la Información.
o
Supervisar que los desarrollos se realicen en ambientes seguros y diferenciados.
Encargado de Seguridad de la Información / Encargado de Ciberseguridad.
o
Eoordinar y supervisar revisiones de seguridad periódicas en los sistemas de producción, identificando y mitigando vulnerabilidades.
o
Proponer y actualizar prácticas y controles de seguridad específicos para el desarrollo seguro de sistemas, alineados con los estándares de la institución y normativas aplicables.
o
Realizar evaluaciones de riesgos en conjunto con los equipos de desarrollo y Operaciones para asegurar el cumplimiento continuo de la política.
Operaciones TIC (Soporte).
o
Recibir, canalizar y gestionar de manera eficiente cualquier aviso de problema o incidente en la operación de los sistemas de información.
o
Documentar y escalar incidentes de seguridad conforme a los protocolos de respuesta establecidos.
Operaciones TIC (desarrollo de sistemas) / Áreas de Negocio que cuenten con equipos de desarrollo de sistemas.
o
Cumplir con todos los lineamientos y requisitos establecidos en esta política en cada fase del desarrollo y actualización de sistemas.
o
Documentar de manera exhaustiva el sistema, incluyendo sus modificaciones y actualizaciones, asegurando trazabilidad y coherencia con los estándares de seguridad.
Operaciones TIC (Infraestructura).
o
Implementar y mantener medidas de protección adecuadas para garantizar la integridad, disponibilidad y seguridad de los entornos de desarrollo, pruebas y o Asegurar que los entornos de infraestructura estén configurados y monitoreados para soportar el desarrollo seguro y continuo de los sistemas de información del
Minsal.
S
mé,
AE

<!-- pág. 6 -->

POLÍTICA DESARROLLO DESISTEMAS res
MATERIAS QUE ABORDA.
Separación de los ambientes de desarrollo, prueba y operacionales.
Política de desarrollo seguro.
Entorno de desarrollo seguro.
Prueba de seguridad del sistema.
Prueba de aprobación del sistema.
Control de acceso al código fuente de los programas.
DIRECTRICES DE LA POLÍTICA Cumplimiento de la legislación Las medidas de control de acceso y seguridad aplicadas en el desarrollo de sistemas deben cumplir con todas las normativas y requisitos legales vigentes, en concordancia con lo establecido en la “Normativa del Sistema de Gestión de Seguridad de la Información del MINSAL”, la Guía Técnica “Lineamientos de Desarrollo de Software”y sus actualizaciones emitidas por el Gobierno Digital de SEGPRES, así como las leyes aplicables en protección de datos, transformación digital, documentos y firmas electrónicos y ciberseguridad vigentes.
Definiciones asociadas a la Seguridad en el Desarrollo de Sistemas Entorno Pre-Productivo: Hace referencia a los entornos de trabajo en las fases de Desarrollo y Testing, donde se simulan las condiciones del entorno de producción para testear la seguridad y funcionalidad antes de la implementación final.
Seguridad en el Desarrollo de Sistemas: Conjunto de prácticas y estándares aplicados durante el ciclo de vida del desarrollo de software, que buscan proteger el sistema y la información manejada contra accesos no autorizados, fallos, y otros riesgos de seguridad.
Ciclo de Vida Seguro de Desarrollo de Software (SDLC Seguro): Metodología que integra la seguridad en cada fase del ciclo de vida de desarrollo, desde la planificación hasta el despliegue y mantenimiento, para reducir vulnerabilidades en el sistema.
Evaluación de Vulnerabilidades: Proceso para identificar, clasificar y priorizar posibles vulnerabilidades en el software o sistema, permitiendo tomar medidas preventivas antes de la implementación.
Principio de Privilegios Mínimos: Práctica de otorgar al usuario, sistema o proceso solo los derechos necesarios para cumplir su función, limitando así el alcance de accesos no autorizados.
Autenticación y Autorización: Procesos de verificación de identidad y control de acceso en el sistema, esenciales para evitar accesos no autorizados y proteger la integridad y confidencialidad de la información.
¡UY

<!-- pág. 7 -->

2 por
o MINISTERIO DESALUD
| A
| Página 6 de 18 | TipiBLaNco |
Control de Versiones: Sistema que gestiona y rastrea los cambios en el código fuente, permitiendo identificar responsabilidades, revertir modificaciones y asegurar la integridad del códigoa lo largo del tiempo.
Codificación
Segura:
Conjunto
de
prácticas
para
escribir
código
libre
de
vulnerabilidades, asegurando que el software sea robusto frente a posibles ataques.
Gestión
de
Parcheo:
Proceso
de
actualización
de
software
para
corregir
vulnerabilidades conocidas, mejorando la seguridad del sistema post-despliegue.
Lineamientos generales Se deben establecery aplicar criterios estandarizados de seguridad y calidad en cada fase del ciclo de vida de desarrollo de los sistemas, conforme a los estándares internos y normativos del sector.
Todoslos sistemas desarrollados deben cumplir con los lineamientos establecidos en esta política, independientemente de si son desarrollados internamente o por terceros.
Los sistemas críticos son aquellos componentes de software, internos o externos, que contienen información sensible o son esenciales para las operaciones institucionales y requieren medidas de seguridad estrictas y monitoreo constante.
Todo desarrollo realizado por terceros debe adherirse a los lineamientos de seguridad definidos en esta política, en todas las etapas del desarrollo, incluyendo controles de calidad y pruebas de seguridad.
Análisis previo del Sistema de Información.
Durante la fase inicial de evaluación, se debe identificar la problemática de seguridad de la información que debe ser atendida por el nuevo sistema, detallando las amenazas y vulnerabilidades potenciales.
Enelestudio de factibilidad, evaluar la criticidad del sistema y definir los controles de seguridad necesarios que se implementarán para mitigar riesgos.
Los requisitos de los usuarios deben ser recopilados y autorizados formalmente, y deben formar parte del documento inicial del proyecto. En esta etapa, es fundamental la participación del jefe de proyecto y del usuario solicitante para asegurar que se cumplan los objetivos de seguridad.
Diseño del Sistema de Información.
Consideraciones en el Diseño del Proyecto:
Durante la fase de diseño de un proyecto, se deben incluir los siguientes elementos:
¿ay
A

<!-- pág. 8 -->

nu
o
Diseño de Presentación: Define cómo el usuario final visualizará e interactuará con el sistema, asegurando una experiencia intuitiva y alineada con los requisitos del usuario.
o
Diseño de Arquitectura: Establece el tipo de proyecto (web, escritorio, servicios web, móvil), su interacción con otros sistemas y el lenguaje de desarrollo. Este diseño permite definir cómo se integrará el sistema con la infraestructura existente y con otros desarrollos.
o
Diseño de Base de Datos: Involucra la creación del diseño lógico y conceptual del modelo de negocio, optimizado para el rendimiento y seguridad del sistema, alineado con los objetivos del proyecto.
Coordinación de Roles:
o
Esfundamental coordinar la participación del Jefe de Proyecto, el Encargado de la Base de Datosy el Encargado de la Plataforma de Soporte de Aplicaciones, quienes deben aportar al diseño y desarrollo del proyecto. Esta etapa culmina con el levantamiento final de los requisitos, documentados en el documento de requerimientos.
Registros de Auditoría de Datos:
o
Todoregistro de auditoría debe incluir la identidad del usuario que crea o modifica el dato, así como la fecha y hora de cada evento de creación y modificación.
o
Losregistros de auditoría deben estar protegidos contra accesos no autorizados y manipulaciones indebidas, asegurando la integridad de la informacióna lo largo del ciclo de vida del sistema.
Desarrollo y Testing.
Prohibiciones en el Desarrollo:
Estáprohibido:
o
Escribir o modificar código auto-copiante, malicioso, o cualquier otro tipo de código perjudicial (virus, gusanos) en la infraestructura de la institución.
o
Incluir en
los programas funciones u operaciones no documentadas o no autorizadas.
o
Realizar modificaciones de programas sin que el cambio quede debidamente registrado y documentado.
Gestión y Protección del Código Fuente:
o
El código fuente debe almacenarse en el repositorio correspondiente para garantizar la trazabilidad de todas las modificaciones.
o
El acceso al código fuente de los distintos sistemas debe estar restringido, protegido mediante contraseñas asignadas, y disponible solo a usuarios autorizados.
E.
1E

<!-- pág. 9 -->

nes
o
Los consultores externos tendrán acceso al código únicamente durante el período de vigencia del proyecto.
o
Toda empresa externa que trabaje con código de sistemas críticos debe firmar un acuerdo de confidencialidad.
Entorno de Desarrollo:
o
El desarrollo debe realizarse en un entorno local separado, utilizando bases de datos de desarrollo distintas de las de producción para evitar riesgos de seguridad.
o
Elproceso de desarrollo se basa en el documento de levantamiento de requisitos.
Pruebas y Testing:
o
Se deben realizar al menos dos tipos de pruebas: pruebas internas del equipo de testing y pruebas de aceptación del usuario solicitante.
o
Las pruebas del sistema deben abarcar:
o
Pruebas
de
Integración:
Validación
de
instalación,
almacenamiento,
configuración, seguridad, calidad y recuperación ante errores.
o
Pruebas Funcionales y de Rendimiento: Evaluación de la funcionalidad y eficiencia del sistema bajo distintas condiciones de uso.
o
Losresultados de las pruebas deben documentarse en el plan de prueba.
Control de Acceso en el Entorno de Testing:
o
Los controles de acceso en el entorno de testing deben ser tan estrictos como en el entorno de producción.
o
Los usuarios solicitantes con acceso al entorno de testing solo tendrán permisos de lectura para proteger la integridad de los datos.
Validación de Sistemas Críticos:
o
Los sistemas críticos deben incluir validación de datos de entrada para asegurar un procesamiento adecuado.
o
Deben incorporarse controles de validación en los datos de salida, para confirmar la precisión del procesamiento ejecutado.
o
Los sistemas críticos que interactúan con otros sistemas deben incluir controles que aseguren la integridad de los mensajes intercambiados.
Adherencia a Lineamientos Técnicos:
o
Todoslos desarrollos deben cumplir con los lineamientos y recomendaciones de la guía técnica aplicable para el desarrollo de software en la Administración del
Estado.
2)Y
o:
Clasificación deseguridad o: Pública

<!-- pág. 10 -->

no
Pruebas de seguridad del sistema e Todos los productos de software desarrollados para el MINSAL deberán someterse a rigurosas pruebasy verificaciones de seguridad durante su fase de desarrollo y antes de suimplementación en producción, de acuerdo con los criterios establecidos por el
Departamento TIC.
e
Laspruebas de seguridad se llevarán a cabo siguiendo el procedimiento definido para el análisis de seguridad en aplicaciones, garantizando que se aborden todas las vulnerabilidades y se cumplan los estándares de seguridad pertinentes.
Marcha Blanca y Producción.
e
Elpasoa
producción del proyecto será autorizado por el usuario solicitante una vez finalizadas las pruebas de testing, mediante notificación por correo electrónico.
e
Se establecerán plazos específicos para la marcha blanca, los cuales variarán según las características y requisitos del proyecto.
e
Esobligatorio revisar y auditar los controles de seguridad definidos en la etapa de diseño antes de la implementación en producción.
e
Elequipo de desarrollo debe realizar una revisión y auditoría exhaustivas de sus propios sistemas antes de proceder a las pruebas formales.
e
Elequipo de pruebas (testing) llevará a cabo una revisión y auditoría de los controles de seguridad, conforme a las especificaciones establecidas durante la fase de diseño.
e
Cualquier
modificación
al
proyecto
requerirá
reiniciar
el
ciclo
de
desarrollo,
comenzando con
el levantamiento de requisitos para asegurar que se aborden adecuadamente los cambios.
e
Todos los traspasos a producción deberán llevarse a cabo durante períodos de baja carga de trabajo, coordinados de manera efectiva con el área responsable del sistema para minimizar el impacto en las operaciones.
Protección de los Datos de Producción Estáestrictamente prohibido el uso de bases de datos operativas (de producción) para la realización de pruebas, así como la exportación de modelos y datos a terceros externos.
6.10
Separación de Ambientes:
Esfundamental establecer entornos de trabajo separados para desarrollo, testing y producción, considerando las siguientes medidas:
o
Separación de Red:
Utilizar segmentos de red distintos con direcciones IP diferenciadas.
as
Y
IÓ

<!-- pág. 11 -->

=_—==————---------===
A
A
TN
A.
MINISTERIO DESALUD | 15
| Página 10 de 18
MAIN
TAS
o
Separación de Versiones del Sistema: Asegurar que cada ambiente opere con versiones específicas del sistema para evitar conflictos.
o
Separación de Bases de Datos: Implementar bases de datos distintas para cada entorno, garantizando que la información de producción no se vea comprometida.
o
Separación de Roles: Definir roles específicos y distintos para cada ambiente de trabajo, asegurando que se cumplan los principios de mínima privilegio.
Reglas de Implementación:
o
Se deben definir, documentar e implementar reglas y autorizaciones claras para la transición de software del estado de desarrollo al estado de producción.
o
Todos los cambios en los sistemas y aplicaciones de producción deberán ser probados en un entorno de prueba o ensayo antes de su implementación en
Restricciones en Pruebas:
o
A menos que se presenten circunstancias excepcionales, las pruebas no deben realizarse en los sistemas de
Cualquier excepción
deberá
ser
aprobada por el Encargado de Seguridad/Ciberseguridad.
Acceso a Herramientas de Desarrollo:
o
Los compiladores, editores y otras herramientas de desarrollo o utilidades del sistema no deben estar accesibles desde los sistemas operacionales a menos que sea absolutamente necesario.
Uso de Perfiles de Usuario:
o
Los usuarios deben utilizar distintos perfiles para los sistemas operacionales y de prueba. Se deben mostrar menús con mensajes de identificación adecuados para mitigar riesgos adicionales.
Modificaciones de Software Crítico:
o
Cualquier modificación de software crítico, ya sea a través de parches o módulos adicionales, debe ser analizada y validada en los ambientes de desarrollo y prueba antes de su implementación en producción.
Acceso Restringido a Ambientes de Producción:
o
Ningún
proveedor,
programador
o
analista
encargado
del
y
mantenimiento de aplicaciones tendrá acceso a los ambientes de producción, garantizando así la integridad y seguridad de la información crítica.
pá
A
S
DO -
Ñ
GS

<!-- pág. 12 -->

PES
Sistema de Gestión de Seguridad de la información - Nivel Central
6.11
Control de Cambios a Datos de Producción:
e
Esfundamental planificar de manera detallada todas las etapas del proceso de paso a producción. Esta planificación debe incluir los siguientes aspectos:
o
Garantizar que se realicen copias de seguridad completas antes de cualquier cambio.
o
Identificar y asignar los recursos necesarios para llevar a cabo el cambio.
o
Definir pruebas que se realizarán antes y después de la implementación para validar el cambio.
o
Planificar
y comunicar el cambio con la suficiente antelación a todas las personas comprometidas.
o
Establecer criterios claros que determinen cuándo un cambio es aceptado o rechazado.
o
Desarrollar un plan de contingencia que permita revertir los cambios en caso de que se identifiquen problemas durante o después de la implementación.
e
Todolo anterior debe estar en concordancia con lo establecido en el procedimiento para la gestión de cambios en ambientes productivos.
e
Los
tipos
de
cambios
realizados
deben
ser
documentados
y
registrados
adecuadamente. La conservación de esta documentación deberá mantenerse por el periodo que el Minsal determine, asegurando la trazabilidad y el cumplimiento normativo.
6.12
Controles Criptográficos e Seimplementarán sistemas y técnicas criptográficas robustas para asegurar el acceso y almacenamiento de claves de usuario, así como para la protección de las bases de datos del sistemay la transmisión de datos sensibles de la institución.
e
Todos los sitios y sistemas web deberán garantizar la encriptación de todas las comunicaciones entre el cliente y el servidor. Es obligatorio utilizar el protocolo HTTPS, empleando certificados válidamente emitidos por entidades acreditadas en el país.
e
Sedeberá cumplir con lo establecido en la política de uso de criptografía, asegurando el uso de algoritmos de encriptación aprobados y considerados seguros, para salvaguardar la integridad y confidencialidad de la información.
6.13
Adquisición de Sistemas a Terceros e Esimprescindible establecer un acuerdo formal y previo con instituciones o empresas externas que garantice la protección de la propiedad intelectual, el uso de datos, el de
Ú

<!-- pág. 13 -->

nu
tratamiento de datos sensibles y los niveles de confidencialidad de la información manejada en el proyecto.
e
Elacuerdo debe incluir, además, las responsabilidades de los terceros en la corrección de errores y gestión de incidentes de seguridad, asegurando así una respuesta adecuada ante cualquier eventualidad.
e
Esnecesario diferenciar claramente entre el encargado de establecer y autorizar los acuerdos con terceros y aquellos responsables de auditar su cumplimiento, para evitar conflictos de interés y asegurar una supervisión adecuada.
e
La
instancia
de
certificación
y aceptación
del
sistema
debe
ser totalmente
independiente del proveedory de la contraparte institucional del contrato.
e
El proceso de adquisición del sistema debe ser formal y cumplir con todas las disposiciones de seguridad establecidas en esta política, garantizando así la integridad del proceso.
e
Enloscasos en que se acuerde el desarrollo de aplicaciones por parte de un proveedor externo, este deberá aceptar y aplicar las políticas de seguridad definidas por el
MINSAL
para todos
los procesos de
desarrollo.
Esto
incluye compromisos de confidencialidad, derechos de propiedad intelectual, condiciones de soporte y mantenimiento, así como cláusulas relacionadas con la finalización de sus actividades o el traspaso de sus servicios a terceros, si se permite.
e
Para la realización de pruebas de software, los proveedores de desarrollo deberán proporcionar datos ficticios o anonimizados, evitando en todo momento la utilización de datos reales, para así proteger la privacidad y la integridad de la información sensible.
6.14
Adquisición de Sistemas en la Nube En el caso de adquirir sistemas que operen en la nube, se deberá asegurar que el proveedor cumpla con estándares de seguridad establecidos por Minsal y certificados relevantes que garanticen la protección de datos en entornos de nube. Además, se deberá exigir al proveedor un acuerdo de nivel de servicio (SLA) que defina claramente los requisitos de disponibilidad, seguridad y respuesta ante incidentes, así como las políticas de recuperación de datos y gestión de incidentes específicos para entornos en la nube.
6.15
Arquitectura Referencial Todo sistema desarrollado o implementado para el Minsal, debe alinearse con la
Arquitectura
Referencial
Ministerial
establecida,
que
describe
las
directrices
y
estándares arquitectónicos de referencia. Esta arquitectura es fundamental para asegurar que las soluciones sean interoperables, escalables y fácilmente integrables en el entorno tecnológico existente. Para cumplir con esta cláusula, se deben considerar los siguientes puntos:
TS
Ey
pe
E

<!-- pág. 14 -->

PE
Alineación con
la
Estrategia
Tecnológica:
Los
sistemas
deben
diseñarse
y
desarrollarse de acuerdo con la visión y los objetivos tecnológicos establecidos en la arquitectura de referencia, garantizando que soporten las metas estratégicas y operativas de la organización.
Estándares y Tecnologías Aprobadas: Los desarrollos deben seguir los estándares de tecnología, infraestructura y metodologías definidos en la arquitectura referencial, incluyendo el uso de plataformas, frameworks y patrones de diseño aprobados, con el fin de asegurar la uniformidady la calidad en todas las aplicaciones.
Revisión y Aprobación: Cualquier cambio significativo en la arquitectura del sistema propuesto debe ser revisado y aprobado por Jefe TIC o equipo encargado de la gobernanza de la arquitectura, para garantizar su compatibilidad y minimización de riesgos.
Reutilización y Modularidad: Se debe promover el diseño modular y la reutilización de componentes para facilitar la escalabilidad, reducir la duplicación de esfuerzos, y optimizar el uso de recursos y tiempo en desarrollos futuros.
Documentación
y
Actualización
Continua:
Es
obligatorio
documentar
las
arquitecturas de los sistemas desarrollados y los modelos de datos, debiéndose mantener esta documentación actualizada en cada fase de implementación, de manera que se facilite su integración y mantenimiento a largo plazo.
6.16
Interoperabilidad
Todos los sistemas y aplicaciones desarrollados para el Minsal, deben cumplir con los requisitos de interoperabilidad definidos, con el fin de garantizar que puedan interactuar eficazmente con otros sistemas internos y externos, facilitando la integración de datos y procesos de negocio. Esta interoperabilidad es fundamental para optimizar la eficiencia, mejorar la toma de decisiones y asegurar una experiencia de usuario consistente. Para lograr esto, se establecen las siguientes directrices:
Cumplimiento de Estándares HL7: Los sistemas deben ser compatibles con el estándar HL7 (Health Level Seven) en sus versiones vigentes, incluyendo HL7 v2.x y FHIR (Fast Healthcare Interoperability Resources), este último en sus versiones R4 y posteriores, para asegurar un intercambio de datos entre sistemas de información de salud que respete la consistencia y precisión clínica.
Esto
permitirá
la
interoperabilidad eficaz de información entre sistemas de historia clínica electrónica (HCE), sistemas de apoyo clínico (RIS, LIS, etc.)y otras aplicaciones de salud.
Estándares de Integración y Protocolos: Los sistemas deben utilizar estándares de integración ampliamente aceptados (como REST, GraphQL, JSON, XML) y protocolos de comunicación seguros (como HTTPS, SFTP y TCP/IP) que permitan la transmisión de datos de manera confiable y segura entre sistemas de información de salud.
APIs Documentadas y Consistentes: Es obligatorio desarrollar APIs (interfaces de programación de aplicaciones) documentadas y consistentes, que faciliten el acceso y la integración de funcionalidades y datos entre diferentes sistemas de información de salud, tanto internos como de terceros, asegurando una comunicación clara y eficaz.
AY

<!-- pág. 15 -->

a
Compatibilidad con
la Arquitectura Empresarial: Todos los desarrollos deben diseñarse para ser compatibles con la arquitectura empresarial existente y futura de la organización, considerando los lineamientos normativosy plataformas habilitadoras que permitan una integración coherente de los sistemas en el ecosistema tecnológico.
Gestión
de
Datos
Interoperables:
Los
datos
deben
manejarse
en
formatos
estructurados y normalizados según las directrices organizacionales y normativas vigentes, permitiendo su fácil intercambio y procesamiento entre aplicaciones sin pérdida de consistencia o integridad de la información.
Pruebas de Interoperabilidad: Durante el proceso de desarrollo, es indispensable realizar pruebas de interoperabilidad para verificar que el sistema funcione de manera óptima en entornos de interoperabilidad y cumpla con los requisitos de conectividad, rendimiento y seguridad al interactuar con otros sistemas.
6.17
Control de Acceso al Código Fuente de los Programas La gestión y protección del código fuente son fundamentales para asegurar la integridad, confidencialidad y disponibilidad de los sistemas de información. Se establecen las siguientes directrices:
Almacenamiento del Código Fuente: El código fuente debe almacenarse en un repositorio correspondiente a Minsal, asegurando así la trazabilidad de todas las modificaciones realizadas a lo largo del ciclo de vida del software. Se recomienda que las bibliotecas de código fuente sean almacenadas en un entorno central controlado y preferiblemente no residan en los sistemas operacionales.
Acceso Restringido: El acceso al código fuente de los distintos sistemas debe estar estrictamente restringido. Este acceso será protegido mediante contraseñas asignadas y estará disponible solo para usuarios autorizados.
El acceso de lectura y escritura al código fuente se otorgará según las necesidades Ministeriales, gestionándose adecuadamente para abordar riesgos de alteración o mal uso.
Acceso de Consultores ExternosyProveedores: Los consultores externos tendrán acceso al código únicamente durante el período de vigencia del proyecto. Este acceso se limitará a las funcionalidades necesarias para el cumplimiento de sus responsabilidades. Se prohíbe expresamente el acceso de consultores externos o proveedores a ambientes productivos, asegurando que sus actividades se realicen exclusivamente en entornos de desarrollo y prueba.
Acuerdos de Confidencialidad: Cualquier empresa externa que trabaje con código de sistemas críticos deberá firmar un acuerdo de confidencialidad, garantizando así la protección de la informacióny la propiedad intelectual involucrada en el proyecto.
Gestión de Acceso: El accesoa las bibliotecas de código fuente debe administrarse de acuerdo con procedimientos establecidos, asegurando que el personal de apoyo no tenga acceso sin restricciones. Las actualizaciones de las bibliotecas de código fuente y la emisión de los mismos a los programadores, se deben realizar únicamente tras recibir la autorización correspondiente.
LARES,
Ss

<!-- pág. 16 -->

mu
Los desarrolladores no deben tener acceso directo al repositorio de código fuente; en su lugar, deben utilizar herramientas de desarrollo que controlen las actividades y autorizaciones sobre el código.
Mantenimiento de Registros: Las listas de programas deben mantenerse en un entorno seguro. Se debe llevar un registro de auditoría de todos los accesosa las bibliotecas de código fuente para asegurar la trazabilidad de las acciones realizadas.
Acceso
Centralizado
¡para
Componentes
Compartidos:
Cuando
varios
desarrolladores utilizan componentes de código dentro de la organización, se debe implementar acceso de lectura a un repositorio de código centralizado para facilitar la colaboración sin comprometer la seguridad.
Controles Adicionales para Código Publicado: Si el código fuente está destinado a ser publicado, se deben considerar controles adicionales para garantizar su integridad, como la implementación de firmas digitales.
6.18
Cláusula de Propiedad Intelectual para desarrollos Titularidad y Derechos de Propiedad: Toda creación intelectual, incluyendo, pero no limitada a software, código fuente, documentación, algoritmos, diseños, metodologías y otros elementos relacionados con el desarrollo de sistemas, será propiedad exclusiva del Minsal. Esto aplica a cualquier desarrollo realizado en entornos locales o en la nube, independientemente de si ha sido creado por un tercero, personal interno, personal a honorarios, consultores externos, estudiantes en práctica o cualquier otro funcionario que participe en proyectos de desarrollo a nombre del Minsal.
Propiedad del Código Fuente: Todo código fuente generado en el marco de las actividades de desarrollo de sistemas, ya sea en proyectos internos o externosy sin importar el entorno en que se aloje (local o en la nube), será de propiedad exclusiva del Minsal. Este código deberá ser documentado, versionado y almacenado en repositorio centralizado y seguros de la organización, bajo control y acceso restringido. La propiedad del código fuente garantiza a Minsal el derecho de uso, modificación, distribución y explotación de los sistemas desarrollados sin limitaciones.
Creaciones de Funcionarios, Personal a Honorarios y Estudiantes en Práctica:
Todos los derechos de propiedad intelectual derivados de creaciones realizadas por funcionarios, personal a honorarios, estudiantes en práctica y cualquier otra persona que desarrolle sistemas en el marco de sus actividades en nombre del Minsal deben ser transferidosa la Institución mediante documento formal de cesión de derechos que contenga el nombre de la obra, el proceso al cual corresponde, su versión, la unidad en la cual el cedente se desempeñóy la fecha.
e
x

<!-- pág. 17 -->

POLÍTICA DESARROLLO DESISTEMAS MINISTERIO DESALUD | 1ON
| Página16 de 18 | TLPiBLANCO |
Contratación de Terceros: Cuando el desarrollo de sistemas sea realizado total o parcialmente por proveedores externos o consultores, el contrato deberá incluir una cláusula de cesión de derechos, mediante la cual se transfiera la totalidad de la propiedad intelectual de las creaciones resultantes a nombre del Minsal. Además, estos contratos deberán asegurar que el código fuente y la documentación técnica completa sean entregados al Minsal, garantizando así la disponibilidad y el control total sobre los activos desarrollados.
Licenciasy Uso de Herramientas de Terceros: En caso de que el desarrollo requiera el uso de software o componentes de terceros, ya sean de código abierto o bajo licencia comercial, se deberán revisar y aprobar las condiciones de uso para asegurar que no afecten los derechos de propiedad intelectual del Minsal sobre el producto final. Solo se podrán utilizar componentes cuya licencia permita su integración sin comprometer la titularidad o explotación de la creación intelectual de la organización.
Confidencialidad y Protección de Información: Toda información, especificación técnica, metodología o código generado durante el desarrollo de sistemas será considerado confidencial y propiedad de Minsal. La divulgación, copia o uso no autorizado de cualquier parte de la creación intelectual están estrictamente prohibidos, y se requerirá que todas las partes involucradas, incluidos empleados, personal a honorarios, estudiantes en práctica y proveedores externos, firmen acuerdos de confidencialidad (NDAs) para asegurar la protección de la información.
Derechos de Uso en Caso de Terminación de Contratos: En situaciones en las que se dé por terminado el contrato con un proveedor de desarrollo, Minsal mantendrá el derecho exclusivo de uso y acceso a todos los materiales, código fuente y documentación producidos en el marco del contrato. El proveedor deberá realizar la transferencia inmediata de todos los derechos y activos digitales a
Minsal,
asegurando la titularidad total y sin limitaciones de uso.
MECANISMO DE DIFUSIÓN.
La comunicación de la presente política se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en la intranet de Minsal http://isalud.minsal.cl/
Correo informativo.
Publicación en sitio web Minsal http://www.minsal.cl/seguridad_de_la_informacion/
PERÍODO DE REVISIÓN.
AS

<!-- pág. 18 -->

MA vinisTERIO DE SALUD
| A
| Página 17 de 18
MATT
La presente política deberá ser revisada cada dos años o cuando ocurran cambios significativos para garantizar que:
Sigue siendo adecuado para su propósito y preciso.
Reflejalos cambios en las tecnologías.
Está alineado con legislación vigente, los estándares internacionales y mejores prácticas.
EXCEPCIONES AL CUMPLIMIENTO DE LA POLÍTICA En situaciones excepcionales, el Jefe de TIC, el CISO o el Comité de Seguridad de la Información tendrán la facultad de evaluar y establecer condiciones específicas para la excepción al cumplimiento de las directrices establecidas en esta política, siempre que tales excepciones no infrinjan la legislación vigente ni comprometan la seguridad de la información.
Cada excepción deberá ser debidamente documentada, y se deberá iniciar un proceso de revisión de la política en el que se determinará si es necesario incorporar directrices adicionales o realizar modificaciones específicas.
HISTORIAL Y CONTROL DE VERSIONES
Versión
Fecha
Pág.oSección modificada
Motivo del cambio
| AO
| Todas
¡ Creación del Documento
E
le.
Pan
in
PP.
É
| Cambio de formato de documento.
Octubre
Ñ
i
Todas
Se actualizan las referencias normativas.
2019
AE
yal
LoS
A
__ Seactualizan
todos los puntos de la política._
| Se incluyen los controles 9.4.5 Control de
| acceso al código fuente del programa y
| A.14.01.01 Análisis y especificación de los
| requisitos de seguridad de la información.
E
[Se especifica en punto 6.7 pruebas de
| seguridad del sistema.
Marzo 2023
6.7, 6.8,6.12,6.12, 6.14 : Se especifica en punto 6.8 la Protección de ¡los Datos de Producción.
¡Se
agrega
punto
6.11
Controles.
: criptográficos.
| Se agrega en 6.12 adquisición de terceros, lo
| relativo a desarrollo de aplicaciones por
o
AA
sl
_parte de un proveedor externo.
Sn.)
“Pag. 2,3, 4, 6-8, 12, 13
Octubre
alcance;
Normativo;
4: Actualización
a norma ISO 27002
2024,
| Responsables; 6 Directrices de : Mejoras en todo el documento
la Política 6.2 Definiciones; 6.6
Desarrollo y Testing;
E
6.15 Arquitectura referencia;
| A
— ENE
E
a
E
S

<!-- pág. 19 -->

nu
Sistema de Gestión de Seguridad de la información - Nivel Central
| a ae pp
| Página 18 de 18
MAIN
p
o
| 6.18
Interoperabilidad;— 6.18.
VE
j
- Clausula Propiedad Intelectual; 9
M1
REFERENCIAS
[1]. SITIO INTRANET MINSALProcedimiento de seguro http://isalud.minsal.cl/ministerio/dastic/SGSI/Paginas/default.aspx [2]. SITIO WEB GOB DIGITALLineamientos para el de software en instituciones públicas https://digital.gob.cl/transformacion-digital/estandares-yquias/quia-desarrollo-software/
B7-0 z
A