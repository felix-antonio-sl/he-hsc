<!-- pág. 2 -->

**1**
**PROPOSITO**
El propósito de este documento es garantizar que los sistemas del Ministerio de Salud (MINSAL) utilicen versiones aceptables y actualizadas de las tecnologías base, con el objetivo de minimizar vulnerabilidades de seguridad, reducir riesgos asociados a posibles brechas en los activos de la organización y establecer una infraestructura tecnológica robusta que salvaguarde la información, los sistemas y los recursos digitales del Ministerio.
**2**
**OBJETIVO**
Establecer un stack tecnológico de referencia que incluya lenguajes de programación, bases de datos, bibliotecas, frameworks y herramientas de desarrollo (frontend y backend)
aprobados por el Ministerio de Salud (MINSAL).  Este stack busca garantizar que todos los sistemas del Ministerio se desarrollen e implementen utilizando las versiones más seguras, estables y actualizadas de estas tecnologías, contribuyendo a la reducción de riesgos de ciberseguridad, la protección de la integridad y confidencialidad de los datos, y la continuidad operativa de los sistemas institucionales.
**3**
**STACK TECNOLOGICO**
Las versiones mínimas aceptables del stack tecnológico de seguridad para Minsal dependen de los componentes y herramientas específicas. A continuación, se proporciona una guía general sobre las versiones aceptables y consideraciones que deben aplicarse:

| STACK TECNOLOGICO DE SEGURIDAD |  |  |  |  |
| --- | --- | --- | --- | --- |
|  | Sistema de Gestión de Seguridad de la Información – Nivel Central |  |  |  |
|  | MINISTERIO DE SALUD | ID: ITS-NC-004 | Versión: 2.0 | Página 2 de 6 |

| Stack Tecnológico | Tipo |  | Versión | Ultima Versión | Observación |
| --- | --- | --- | --- | --- | --- |
|  |  |  | Mínima |  |  |
|  |  |  | Recomendada |  |  |
| JBOSS | APP Server | 8.0 |  | 8.0.4 | Versión 8.0, esta versión tiene vulnerabilidades identificadas. En caso de utilizarla, es imprescindible aplicar todos los parches de seguridad disponibles para mitigar dichos riesgos. |
| Wordpress | CMS | 6.6 |  | 6.7 | se recomienda utilizar la versión 6.6 como mínimo, ya que ofrece mejoras y mayor robustez en seguridad. |
| ASP.NET (core) | Framework | 8.0.2 |  | 9.0 | Última versión LTS o superior. Es importante considerar que la versión 8 cuenta con soporte de parches hasta la versión 8.0.11. |
| Laravel | Framework | 10.0 |  | 11.35.0 | Cada versión contará con un soporte de dos años, por lo que es fundamental tener en cuenta las fechas de "End of Life" (EOL). En particular, la versión 10 tendrá soporte para actualizaciones de seguridad hasta el 04 de febrero de 2025. |
| NodeJS | Framework | 22.12.0 |  | 23.4.0 | Es importante considerar que la versión mínima recomendada, 22.12.0, está afectada por una vulnerabilidad alta documentada en |

<!-- pág. 3 -->

| STACK TECNOLOGICO DE SEGURIDAD |  |  |  |  |
| --- | --- | --- | --- | --- |
|  | Sistema de Gestión de Seguridad de la Información – Nivel Central |  |  |  |
|  | MINISTERIO DE SALUD | ID: ITS-NC-004 | Versión: 2.0 | Página 3 de 6 |

| Stack Tecnológico | Tipo |  | Versión | Ultima Versión | Observación |
| --- | --- | --- | --- | --- | --- |
|  |  |  | Mínima |  |  |
|  |  |  | Recomendada |  |  |
|  |  |  |  |  | CVE-2024-36138. Sin embargo, se mantiene como versión recomendada con su referencia de parche como solución, ya que debería ser suficiente para garantizar la compatibilidad con otras tecnologías y, además, aún cuenta con soporte. |
| React | Framework | 18.1 |  | 19 | Versión 18.1 o superior |
| JAVA | Lenguaje | 21 |  | 23 | Versión 21 o superior. Considerar que ambas versiones que se indican 21 y 23 de JAVA se presentan vulnerabilidades conocidas, en caso de usarse deben aplicar el parche respectivo. |
| PHP | Lenguaje | 8.3.14 |  | 8.4.1 | Versión 8.3.14 o superior |
| Python | Lenguaje | 3.11.4 |  | 3.13.1 | Versión 3.11.4 o superior |
| Javascript | Lenguaje | es11 |  | es14 | Versión es11 o superior |
| Typescript | Lenguaje | 5.3 |  | 5.8.0 | Versión 5.3 o superior |
| Bootstrap | Librería | 5.0.0 |  | 5.3.3 | Versión 5.0 o superior |
| JQuery | Librería | 3.6.0 |  | 4.0.0 Beta | Versión 3.6 o superior |
| ReactJS | Biblioteca | 17.0 |  | 19.0 | Versión 17.0 o superior |
| RedCAP | Software | 13.4.12 |  | 14.0.12 | Versión 13.4.12 o superior |
| Apache HTTP | Web Server | 2.4.62 |  | 2.4.62 | Versión 2.4.62 o superior |
| Apache Tomcat | Web Server | 10.1.34 |  | 11.0.2 | Versión 10.1.34 o superior |
| IIS | Web Server | 10 |  | 10 | Versión 10.0 o superior |
| NGINX | Web Server | 1.26.2 |  | 1.27.3 | Versión 1.26.2 o superior |
| Uvicorn | Web Server | 0.30.1 |  | 0.34.0 | Versión 0.30.1 o superior |
| Windows | OS | 10 |  | 11 versión 23h2 | Versión 10 o superior |
| Windows Server | OS | 2022 |  | 2025 | Versión 2022 o superior. Se debe considerar que esta versión presenta vulnerabilidades conocidas. En caso de utilizarla, se debe aplicar los parches y actualizaciones correspondientes para garantizar la seguridad del sistema. |
| RHEL | OS | 9.3 |  | 9.5 | Versión 9.3 o superior |
| Oracle Linux | OS | 9.1 |  | 9.5 | Versión 9.1 (versión 2023.01.31) o superior |
| CentOS | OS | 9 |  | 10 | Versión 9 o superior |
| MySQL | DB | 8.4.3 |  | 9.1.0 | Versión 8.4.3 o superior. Es importante tener en cuenta que la versión 9.0 no cuenta con soporte de seguridad, por lo que no se recomienda su uso. En su lugar, se debe optar por versiones más recientes que cuenten con actualizaciones y soporte adecuado para garantizar la seguridad de los sistemas. |
| PostgreSQL | DB | 15.10 |  | 17.2 | Versión 15.10 o superior |

<!-- pág. 4 -->

| STACK TECNOLOGICO DE SEGURIDAD |  |  |  |  |
| --- | --- | --- | --- | --- |
|  | Sistema de Gestión de Seguridad de la Información – Nivel Central |  |  |  |
|  | MINISTERIO DE SALUD | ID: ITS-NC-004 | Versión: 2.0 | Página 4 de 6 |

| Stack Tecnológico | Tipo |  | Versión | Ultima Versión | Observación |
| --- | --- | --- | --- | --- | --- |
|  |  |  | Mínima |  |  |
|  |  |  | Recomendada |  |  |
| SQL Server | DB | 2017.0 |  | 2022 | Versión 16.0 o superior. Es importante considerar que varias de las versiones del GDR mencionadas presentan vulnerabilidades conocidas. Por lo tanto, si se opta por usar alguna de estas versiones, se deberá aplicar los parches de seguridad correspondientes para mitigar los riesgos asociados. Se recomienda siempre usar la versión más actualizada disponible que esté debidamente parchada para garantizar la seguridad del sistema. |
| MongoDB | DB | 7.0.16 |  | 8.0.4 | Versión 70.0.16 o superior. Se recomienda como versión mínima la última versión de la serie 7.0. Las versiones de MongoDB 7.1.1, 7.2.2 y 7.3.4 no son recomendadas, ya que no cuentan con soporte de seguridad. Es crucial utilizar versiones que cuenten con actualizaciones de seguridad activas para garantizar la protección de los datos y la integridad del sistema. |
| Elasticsearch | DB | 8.11.1 |  | 8.17 | Versión 8.11.1 o superior |
| Redis | DB | 7.2.6 |  | 7.8.2 (7.4) comunity edition | Versión 7.2.6 o superior |
| Windows Server | OS | 2022 (20348.2966) |  | 2025 | Versión 2022 o superior |
| docker.io/librar y/alpine | Imagen Base | 3.18 |  | 3.21 | Versión 3.18 o superior. Se recomienda utilizar esta versión o una superior para asegurar la compatibilidad con otras tecnologías y mantener las actualizaciones de seguridad pertinentes. |
| registry.access .redhat.com/re dhat/ubi9- minimal | Imagen Base | 9.2-latest |  | 9.3-latest | Versión 9.2 o superior Se recomienda utilizar esta versión o una superior para garantizar la compatibilidad con otras tecnologías, así como para asegurar la implementación de las últimas actualizaciones de seguridad. |
| docker.io/librar y/ubuntu | Imagen Base | 22.04 |  | 25.04 | Versión 22.04 o superior Generalmente usada como base para construcción de imágenes de contenedores. |
| Fastapi | Framework | 0.110.1 |  | 0.115.6 | Versión 0.110 o superior Usado para el desarrollo de microservicios en python |
| Spring | Framework | 6.1.15 |  | 6.2.1 | Versión 6.1.15 o superior Usado para aplicaciones JEE y microservicios |
| Gitlab | Control de versiones | 17.5.4 |  | 17.6.2 | Versión 17.5.4 o superior. Es importante tener en cuenta que esta versión dejará de recibir soporte el 16 de enero de 2025. Las versiones desde la 17.6 hasta la anterior a la 17.6.2 presentan vulnerabilidades conocidas, por lo que, en caso de utilizar estas versiones, es |

<!-- pág. 5 -->

**4**
**ACTUALIZACIONES**
Es crucial monitorear regularmente las actualizaciones de seguridad y los avisos de vulnerabilidades proporcionados por los proveedores de las soluciones de seguridad. Además, considerar las características específicas de tu entorno y la compatibilidad entre las diferentes herramientas en el stack tecnológico de seguridad, por ejemplo:
**Sistemas Operativos:**
Utilizar las versiones más recientes y compatibles de sistemas operativos populares, como Windows Server, Linux o macOS.
Mantener actualizaciones y parches de seguridad.

| STACK TECNOLOGICO DE SEGURIDAD |  |  |  |  |
| --- | --- | --- | --- | --- |
|  | Sistema de Gestión de Seguridad de la Información – Nivel Central |  |  |  |
|  | MINISTERIO DE SALUD | ID: ITS-NC-004 | Versión: 2.0 | Página 5 de 6 |

| Stack Tecnológico | Tipo |  | Versión | Ultima Versión | Observación |
| --- | --- | --- | --- | --- | --- |
|  |  |  | Mínima |  |  |
|  |  |  | Recomendada |  |  |
|  |  |  |  |  | fundamental aplicar los parches de seguridad correspondientes. Se recomienda actualizar a una versión más reciente para mantener la seguridad y el soporte adecuado. |
| Nexus | Registro de artefactos | 3.73 |  | 3.75 | Versión 3.73 o superior |
| Maven | Build Tools y gestionador de dependencias | 3.8.8 |  | 4.0.0-rc-2 | Versión 3.8.8 o superior Herramienta para la construcción de artefactos de software que se ocupa de todo ciclo (generación de código, compilación, pruebas, empaquetados, publicación, etc.) |
| Gradle | Build Tools y gestionador de dependencias | 8.4 |  | 8.11.1 | Versión 8.4 o superior Herramienta para la construcción de artefactos de software que se ocupa del todo ciclo (generación de código, compilación, pruebas, empaquetados, publicación, etc.) |
| Poetry | Gestionador de dependencias | 1.6 |  | 1.8.0 | Versión 1.6 o superior Herramienta para el control de las dependencias en aplicaciones en python |
| Composer | Gestionador de dependencias | 2.8.0 |  | 2.8.4 | Versión 2.8.0 o superior Herramienta para el control de las dependencias en aplicaciones en php |
| yarn | Gestionador de dependencias | 4.4.0 |  | 4.5.3 | Versión 4.4.0 o superior Herramienta para el control de las dependencias en aplicaciones en javascript o typescript |
| RabbitMQ | Cola de Mensajería | 3.13.1 |  | 4.0.5 | Versión 3.13.1 o superior Utilizar última versión estable |
| Moodle | sistemas de gestión del aprendizaje (LMS) | 4.4.5 |  | 4.5.1 | Utilizar última versión estable |

<!-- pág. 6 -->

**5**
**DIFUSION**
La comunicación del presente documento se efectuará de manera que el contenido de la documentación sea accesible y comprensible para todos los usuarios, a lo menos se deberá hacer difusión mediante los siguientes canales:
Publicación en sitio web de Minsal http://www.minsal.cl/seguridad_de_la_informacion/ Publicación en la intranet de Minsal http://isalud.minsal.cl/ Correo informativo Equipo TI.
**6**
**REVISION**
La revisión del contenido de este documento se efectuará a lo menos cada un año por el el Jefe de TIC, el CISO o el Comité de Seguridad de la Información, o atendiendo necesidades de cambios para garantizar versionamientos respectivos recomendables.
**7**
**CONTROL DE VERSIONES**

| STACK TECNOLOGICO DE SEGURIDAD |  |  |  |  |
| --- | --- | --- | --- | --- |
|  | Sistema de Gestión de Seguridad de la Información – Nivel Central |  |  |  |
|  | MINISTERIO DE SALUD | ID: ITS-NC-004 | Versión: 2.0 | Página 6 de 6 |

| Versión | Fecha |  | Creado |  | Pág. o Sección |  | Descripción de la |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  |  |  | por |  | modificada |  | modificación |
| 1 | Enero 2024 | José Villa |  | Todo el documento |  | Creación del documento |  |
| 2 | Diciembre 2024 | Equipo TIC |  | Pag 2 a la 6 Punto Propósito, objetivo y Tabla Stack |  | Actualización de versiones |  |