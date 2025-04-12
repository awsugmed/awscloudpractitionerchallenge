# Identidad y Seguridad en AWS.

Seguridad es el segundo dominio (tema) de mayor peso en el examen de certificación CLF-C02.

### 1. Modelo de responsabilidad compartida (Shared Responsibility Model)
- **¿Quién es responsable de mantener seguros los recursos en AWS:**
¿tú (el cliente de AWS) o AWS?
**La respuesta es:** Sí ¡ambos!

	Tu entorno de AWS no es un único objeto, sino un conjunto de componentes que se complementan entre sí. AWS es responsable de algunas partes de tu entorno y tú (el cliente) de otras. Este concepto se conoce como el modelo de responsabilidad compartida.

- **Analogía del constructor y el dueño de una casa:**
El modelo se asemeja a la división de responsabilidades entre el propietario y el constructor de una casa: El constructor (AWS) es responsable de construir su casa y garantizar su solidez. Como propietario (el cliente), es responsable de asegurar todo en la casa, por ejemplo, las puertas y ventanas cerradas con llave.

- **Las responsabilidades (y control) varían en función del servicio elegido por el cliente, al igual que el grado de personalización y control por parte del cliente:**

	AWS siempre es responsable como mínimo de la capa física, la red y la virtualización.
	El cliente siempre es responsable del acceso a los datos.
	**Por ejemplo:**
	- **En Ec2:** AWS es responsable desde la capa física hasta el hypervisor. El cliente desde el tráfico de red, pasando por el SO, cifrado de datos hasta el acceso a ellos.
	- **En el caso de servicios administrados de AWS, como S3 y DynamoDB:** AWS maneja la capa de infraestructura, y además las plataformas (Motores de BD, runtimes, software de servidor). Mientras que los clientes son responsables de administrar sus datos (incluidas las opciones de cifrado), clasificar sus recursos y utilizar las herramientas de IAM para establecer los permisos correspondientes.

### 2. AWS IAM (Identity and Access Management)
- **¿Qué es AWS IAM?**

	- IAM nos permite gestionar de forma segura el acceso a recursos de AWS mediante usuarios, grupos, roles y políticas.
	- IAM es autenticación y autorización como servicio y es gratis para todos los usuarios de AWS.
	- Un servicio de AWS es una funcionalidad administrada (como S3, EC2 o RDS), mientras que un recurso es una instancia específica dentro de ese servicio (como un bucket de S3, una instancia EC2 o una base de datos RDS).
	- **Identidades:** usuarios, grupos, roles. que se les pueden asociar políticas.
	- **Entidades:** users y roles, usados para autenticar, excluye grupos.
	- **Principals:** entidad que puede hacer solicitudes a AWS, como un usuario/usuario federado, rol asumido, una cuenta o servicio de AWS.

- **Características de users, politicas, grupos y roles:**
	- **User:**
		- Consiste en un nombre y credenciales (las credenciales pueden ser mediante password o access keys).
		- De forma predeterminada, un nuevo usuario de IAM en AWS no tiene permisos asociados. Para que el usuario de IAM pueda realizar acciones en AWS, como iniciar una instancia de EC2, debe otorgarle los permisos necesarios.
		- **Práctica recomendada:** crear usuarios de IAM individuales para cada persona que necesite acceder a AWS. Incluso si tiene varios empleados que requieren el mismo nivel de acceso, debería crear usuarios de IAM individuales para cada uno. Esto proporciona seguridad adicional al permitir que cada usuario de IAM tenga un conjunto único de credenciales de seguridad.
		- **Best practice:** Do not use the root user for everyday tasks. Instead, use the root user to create your first IAM user and assign it permissions to create other users.

	- **Políticas de IAM:**
		- Permiten personalizar el nivel de acceso de los usuarios a los recursos. 
		- **Por ejemplo**, puede permitir que los usuarios accedan a todos los buckets de Amazon S3 dentro de su cuenta de AWS o solo a uno específico.
		- **Práctica recomendada:** Siga el principio de mínimo privilegio (sólo dar los permisos requeridos para el trabajo y nada más) al otorgar permisos. Al seguir este principio, ayuda a evitar que los usuarios o roles tengan más permisos de los necesarios para realizar sus tareas. Por ejemplo, si un empleado sólo necesita acceder a un bucket específico, especifíquelo en la política de IAM. Haga esto en lugar de otorgarle acceso a todos los buckets de su cuenta de AWS.

	- **Grupos:**
		- En lugar de asignar permisos a cada Dev individualmente, puede crear un grupo IAM "Developers", luego agregar usuarios al grupo y asignar permisos a nivel de grupo. Asignar políticas de IAM a nivel de grupo también facilita el ajuste de permisos cuando un empleado cambia de puesto.
		- **Por ejemplo**, si un Dev se convierte en Ops, puede eliminarlo del grupo de IAM "Developers" y añadirlo al grupo de IAM "AWS Operators". Esto garantiza que los empleados solo tengan los permisos necesarios para su puesto actual.

	- **Roles:**
		- Antes de que un usuario, app, servicio o cuenta de AWS pueda asumir un rol de IAM, se le deben otorgar permisos mediante una política/relación de confianza que se define en el rol.
		- **Práctica recomendada:** Los roles de IAM son ideales para situaciones en las que el acceso a servicios o recursos debe otorgarse temporalmente, en lugar de a largo plazo, por ejemplo para evitar asociar los permisos a una credencial de usuario de largo plazo y evitar que quemarla en el código.
		- Los roles usan credenciales temporales que AWS se encarga de rotar (proporcionadas por STS), es más seguro que definir usuarios con credenciales estáticas! 
		Sirven para tener:
			- Permisos entre cuentas.
			- Permisos desde servicios o recursos de aws.
			- Autorización a cuentas federadas (DA, Google, FB).
			- No tener que quemar credenciales en el código, sino asumir el rol con SDK desde un servicio de AWS.

	- **Las políticas se dividen en 2 tipos:**
		- **Políticas basadas en identidad:** se aplican a un rol, usuario o grupo.
		- **Políticas basadas en recurso:** se aplican a un recurso como un bucket de S3 y requieren que se defina un principal (usuario, rol, cuenta o servicio)
		- **Relación/Política de confianza:** (es una política exclusiva de los roles basada en recurso) define qué principal puede asumir el rol.

	- **Curiosidad:**
		Un rol de IAM en AWS es tanto una identidad como un recurso, pues:

		 ✅ **Identidad**:  puede tener políticas basadas en identidad adjuntas (como un usuario), permitiéndole hacer cosas en AWS.
		 ✅ **Recurso:** tiene una política de confianza (basada en recursos), que define quién puede asumirlo (el "principal").

		 **Nota:** Si les preguntan, digan que identidad ;)


### 3. Seguridad en la red: Security Groups y Network ACLs:

- **Conceptos y términos importantes de seguridad en AWS:**
	- Las **VPC y subredes** son para aislar mis recursos de los de otros clientes de AWS y determinar exactamente cómo puede fluir el tráfico de red.
	- Una **VPC** es un segmento de la red de AWS.
	- Una **subred** es un segmento de una **VPC** en la que se pueden agrupar recursos en función de las necesidades operativas o de seguridad.
	- En una **VPC**, las subredes pueden comunicarse entre sí. Por ejemplo, podría tener una aplicación que incluyera instancias de Amazon EC2 de una subred pública que se comunicaran con bases de datos ubicadas en una subred privada.
	- Un **firewall** es un sistema que me permite controlar tráfico de red/conexiones entre redes y/o equipos.
	- La **ACL** de red predeterminada de tu cuenta permite todo el tráfico entrante y saliente, pero puedes modificarlo añadiendo tus propias reglas.
		- En el caso de las **ACL** de red personalizadas, todo el tráfico entrante y saliente se deniega hasta que se añaden reglas para especificar qué tráfico se va a permitir. Además, todas las **ACL** de red tienen una regla de denegación explícita. Esta regla garantiza que si un paquete no coincide con ninguna de las demás reglas de la lista, se deniega.
	- De forma predeterminada, un **grupo de seguridad** deniega todo el tráfico entrante y permite todo el tráfico saliente. Puedes añadir reglas personalizadas para configurar qué tráfico se debe permitir. Cualquier otro tipo de tráfico se denegará.
		- Si tienes varias instancias de Amazon EC2 dentro de una **subred**, puedes asociarlas al mismo **grupo de seguridad** o usar grupos de seguridad distintos para cada instancia.
		- Realmente los **SG** se aplican a nivel de ENI (no de instancia) y las ENI se asocian a distintos tipos de recursos como EC2, RDS, VPC endpoints, ELB, etc... Pero si les preguntan, digan que controlan el tráfico de una o más instancias.
	- Las **NACL** usan filtrado de paquetes sin estado. No recuerda conexiones previas y comprueba los paquetes que cruzan la subred en cada sentido: entrante y saliente.
	- Los **SG** usan filtrado de paquetes con estado. Recuerda la decisión tomada con las conexiones anteriores que pasaron por el SG y deja pasar las conexiones de respuesta.
		- Cuando una respuesta de paquete para esa solicitud vuelve a la instancia, el grupo de seguridad recuerda la solicitud anterior. El grupo de seguridad permite que la respuesta continúe, independientemente de las reglas entrantes del grupo de seguridad.

	**Nota:** Ni VPC, ni SGs ni NACLs tiene costo directo (se cobra el datatransfer dependiendo del origen y destino de los paquetes que entran y salen de las subredes).

### 4. Protección de datos en reposo y en tránsito:
- **Conceptos y términos importantes de cifrado en AWS:**
	- **Cifrar:** es transformar/representar datos mediante un algoritmo y una clave/llave secreta de manera que sólo sean legibles por quienes tienen la calve correcta. El objetivo es la confidencialidad.
	- Una clave/llave criptográfica es una cadena de dígitos larga y aleatoria usada para cifrar y descifrar datos.
	- Los datos en reposo se protegen  almacenándolos cifrados:
		- **Cifrado del lado del cliente:** el cliente de AWS cifra los datos ANTES de enviarlos a AWS.
		- **Cifrado del lado del servidor:** AWS cifra los datos después de recibirlos.
	- La opción que elija depende de quién quiere que administre o proporcione las llaves de cifrado.
	- Normalmente el cifrado en reposo es mediante criptografía simétrica o híbrida (simétrica para los datos, asimétrica para cifrar la llave simétrica).

- **Servicios AWS para cifrado en reposo:**
	- **KMS:**
		- Supongamos que necesita cifrar unos datos. Cifra esos datos con una clave para crear un texto de cifrado. Ahora debe almacenar la clave, pero también necesita una manera de cifrarla, para que cualquier persona no pueda leerla. Por lo que crea otra clave, que usará para cifrar la primera clave. Pero, ¿qué hacer con la clave que acaba de crear? Probablemente también debería cifrarla. ¿Y qué hacer con la clave usada para eso? Así podríamos seguir indefinidamente. Lo que realmente necesita es un lugar para almacenar su clave principal y saber que está segura.
		- KMS facilita considerablemente la administración de este proceso de almacenamiento y recuperación de las claves de cifrado.
		- KMS soluciona este problema usando una jerarquía de claves, donde tú solo manejas claves de datos temporales, y KMS se encarga de protegerlas con claves maestras seguras y gestionadas, eliminando la necesidad de cifrar claves infinitamente.  Puedes desactivar temporalmente las claves para que nadie las pueda utilizar. especificar qué usuarios y roles de IAM pueden administrar las claves, etc.
		- Costo adicional:
			- Si usas SSE-S3, no se genera ni usa una CMK de KMS, y por tanto no hay costos de KMS.
			- Si eliges SSE-KMS, sí se genera o usa una CMK de KMS, por lo que sí se aplica el costo de $1 USD por mes por la CMK activa y las operaciones de cifrado/descifrado.
			- Si usas SSE-C, tú gestionas la clave, y KMS ni la guarda, entonces no cobra por ella.
	- **Módulos de seguridad de hardware (HSM) en AWS:**
		CloudHSM te da control total sobre los módulos de seguridad hardware (HSM), ideal para quienes necesitan cumplir con regulaciones estrictas o quieren administrar sus propias claves físicamente.
		Costo adicional (alto).
	- **Macie:**
		Utiliza machine learning para descubrir, clasificar y proteger información confidencial (como la información de identificación personal (PII) o la propiedad intelectual o de pagos/TC.) en AWS de manera automática.
		Costo adicional.

- **Para cifrado en tránsito AWS recomienda las siguientes soluciones y prácticas** para ayudarlo a proporcionar protección para sus datos en tránsito, que proporcionan confidencialidad e  integridad:
	- Usar conexiones seguras: SSH, TLS, IPSEC
	- Usar certificados digitales (también llamados certificados SSL - Los certificados de ACM son 100% TLS, no SSL. Llamarlos "certificados SSL" es  cuestión de nombre, porque SSL es una versión anterior de TLS ya obsoleta.
		- Un certificado digital ("SSL") es un documento criptográfico que permite cifrar datos contra el servidor que lo usa y comprobar su autenticidad (confirmar que el servidor al que me conecto es el real y no una suplantación).
		- Normalmente el cifrado en tránsito es mediante criptografía híbrida (simétrica para los datos, asimétrica para cifrar la llave simétrica).
		- **Ejemplo:** Conexión HTTPS:
			 1. abres https://sitio.com en tu navegador.
			 2. El navegador y el servidor realizan un handshake TLS:
			 *El servidor envía su clave pública (por ejemplo, en un certificado TLS).
			 *El navegador usa esa clave para cifrar una clave simétrica secreta y enviarla al servidor (el servidor puede descifrar porque tiene la clave privada correspondiente).
			 3. Ambos confirman la clave de sesión simétrica.
			 4. Todo lo que viaja por esa conexión (datos, contraseñas, tokens) va cifrado con esa clave simétrica.
	- ACM se encarga de la compleja tarea de crear y administrar los certificados SSL/TLS públicos para sus aplicaciones y sitios web basados en AWS. ACM también se puede utilizar para emitir certificados SSL/TLS X.509 privados que identifican internamente a los usuarios, equipos, aplicaciones, servicios, servidores y otros dispositivos.

	 Los certificados públicos que se usan en otros servicios de AWS como balanceadores o distribuciones de cloudfront son gratis. Los certificados privados emitidos por la CA de AWS tienen costo (elevado por activar la CA privada).


### 5. Otros servicios de seguridad en AWS:
- **WAF:**
Un firewall (permite o deniega conexiones) con base en la información de la solicitud HTTP. Similar a la NACL, usa listas de control de acceso web (web ACL), pero que trabajan a nivel de aplicación (capa 7).
También se puede filtrar por IP de origen en las WACLs pues esta info también se puede envíar a WAF en los metadatos/cabeceras de la solicitud HTTP.
WAF Genera costo adicional.

- **Shield:**
**Un ataque de denegación de servicio (DoS):** intento malicioso para lograr que un sitio web o una aplicación no estén disponibles para los usuarios, mediante saturación de solicitudes desde una única fuente (dirección IP).

	 Ataque de denegación de servicio distribuido (DDoS), se usan varias fuentes para intentar afectar la disponibilidad. Esto puede proceder de un grupo de atacantes o de un solo atacante. Uno solo puede usar varios equipos infectados (conocidos "bots") para enviar tráfico excesivo a un sitio web o app desde múltiples orígenes.

	 **2 niveles de protección en shield:**
	- **Shield Standard: **protege automáticamente a todos los clientes de AWS gratis! de los ataques DDoS más comunes y frecuentes.  Usa diversas técnicas de análisis para detectar el tráfico DDoS en tiempo real y mitigarlo.
	- **Shield Advanced: **tiene costo adicional, detecta y mitigar ataques DDoS avanzados y proporciona diagnósticos detallados de estos.
También se integra con otros servicios como CloudFront, Route 53, ELB. y WAF para mitigar ataques DDoS complejos.
***Recomendado: Shield Advanced es para empresas que dependen de su disponibilidad en línea o en industrias sensibles (finanzas, salud, comercio, etc.). Para sitios informativos o tráfico moderado, Shield Standard suele ser suficiente.

- **Artifact:**
Portal de autoservicio para descargar informes, certificaciones de cumplimiento y auditoría y de los acuerdos que pacta con AWS. Hay informes de acuerdo con la legislación de cumplimiento de muchos países (ej. legislación: Habeas Data en Colombia).
	- **Cuando se usa?** para demostrar conformidad con estándares internacionales o nacionales, para confirmar controles, para entregar a auditores.
	- **Artifact reports:** para obtener los informes de cumplimiento de AWS hechos por auditores externos con base a normas y regulaciones internacionales (ej. PCI, ISO 27001,...)
	- **Artifact agreements:** revisar, aceptar y terminar acuerdos de servicio con AWS para cuentas individuales o para cuentas de organizations.

- **Inspector:**
Ejecución de evaluaciones de seguridad automatizadas. Comprueba vulnerabilidades de seguridad y desviaciones de prácticas recomendadas de seguridad en recursos de AWS, como el acceso abierto a instancias de EC2 y las instalaciones de software vulnerables.

	Para usar inspector se definen unos targets donde correrá el escaneo (en algunos casos se instalan agentes como en ec2), la plantilla de evaluación (qué voy a evaluar) y se corre el escaneo, él luego proporciona una lista de hallazgos de seguridad ordenada por nivel de severidad e incluye una descripción detallada del problema, así como una recomendación sobre cómo solucionarlo.

	Esto sólo abarca una parte de la seguridad en AWS, por lo que AWS no garantiza que siguiendo las recomendaciones proporcionadas se solucionen *todos* los posibles problemas de seguridad.

	Costo adicional por evaluación realizada por host/imagen.

- **CloudTrail:**
Registro de eventos y llamadas a las API de AWS en la cuenta (mediante cualquier medio: Consola, CLI, SDK, roles y usuarios de IAM).
*90 días gratis de retención por default en los logs, integración con S3 y CW logs para mayor almacenamiento y análisis (con costo adicional).
	- **3 tipos de eventos registrados:**
		- **Admon:** operaciones de lectura y escritura en los recursos de la cuenta. activos por default.
		- **Datos:** cambios en objetos de S3 y ejecuciones de lambda, costo adicional, posible alto volumen.
		- **Insights:** detección de actividad inusual en la cuenta con base en los eventos, ej. Aumentos repentinos de llamadas StartInstances, TerminateInstances. Esto ayuda a detectar incidentes como mal uso, errores de automatización o posibles compromisos de la cuenta.

- **GuardDuty:**
Identifica amenazas mediante la supervisión continua de la actividad de la red y el comportamiento de la cuenta en tu entorno de AWS:
	- No tienes que desplegar ni administrar ningún software de seguridad adicional.
	- Analiza continuamente los datos de varias fuentes de AWS, incluidos los registros de flujo de VPC y los registros DNS.
	- Los hallazgos incluyen los pasos recomendados para la corrección. También puedes configurar funciones Lambda para que adopten medidas correctivas en la cuenta automáticamente.
	- Costo adicional por eventos analizados (CloudTrail, DNS, VPC Flow Logs), depende del volumen.



### 6.  Recursos
- AWS Skillbuilder provee muchos recursos para prepararse para el examen desde cursos, juegos hasta simulacros del mismo. algunos de estos gratis:
	- [AWS Cloud Practitioner Essentials Course](https://explore.skillbuilder.aws/learn/courses/134/aws-cloud-practitioner-essentials/lessons/136404/aws-cloud-practitioner-essentials "AWS Cloud Practitioner Essentials Course")
	- [AWS Cloud Practitioner Essentials Course en Español](https://explore.skillbuilder.aws/learn/courses/10455/aws-cloud-practitioner-essentials-espanol-de-espana/lessons/142384/fundamentos-de-la-nube-de-aws-para-profesionales "AWS Cloud Practitioner Essentials Course en Español")
	- [Modelo de responsabilidad compartida](https://aws.amazon.com/es/compliance/shared-responsibility-model/?nc1=h_ls "Modelo de responsabilidad compartida")
	- [AWS Security Fundamentals](https://explore.skillbuilder.aws/learn/courses/572/aws-security-fundamentals-second-edition-espanol-latam/lessons/81192/aspectos-basicos-de-seguridad-de-aws-segunda-edicion-espanol-latinoamerica-aws-security-fundamentals-second-edition-spanish-from-latin-america "AWS Security Fundamentals")



> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=PWcl1vwGCrc&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=1 "Link de la charla en Yotube")
> - [LinkedIn de Cristian Pavony](https://www.linkedin.com/in/ingenierocristianpavonyv/ "LinkedIn de Cristian Pavony")