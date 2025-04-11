# Introducción a la Nube y AWS

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=HhPGckLLDWY "Link de la charla en Yotube")
> - [LinkedIn de Santiago Bedoya](https://www.linkedin.com/in/santiago-bedoya-diaz/ "LinkedIn de Santiago Bedoya")
> - [Enlace a las diapositivas para descargar](https://www.canva.com/design/DAGjKBw1ub4/QgyUPHykg_TzFbxDarUdYw/edit?utm_content=DAGjKBw1ub4&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton "Enlace a las diapositivas para descargar")

## Contenido de la charla:
- Conceptos de computación en la nube
- Beneficios de la nube: escalabilidad, elasticidad, agilidad
- Modelos de implementación: nube pública, privada e híbrida
- Modelos de servicio: IaaS, PaaS, SaaS
- Introducción a AWS y su infraestructura global
- Well architected Framework
- Servicios principales de AWS


### Contexto: ¿Cómo se trabajaba antes?
Antes de la computación en la nube, las empresas que querían desarrollar y lanzar aplicaciones tenían que construir y mantener su propia infraestructura de TI. Esto implicaba:

1️⃣ **Adquirir servidores físicos:** Las empresas debían comprar hardware costoso y calcular con antelación la capacidad que necesitarían, sin posibilidad de ajustarla dinámicamente.

2️⃣ **Gestionar un data center:** Esto incluía alquilar o comprar un espacio físico, pagar electricidad, refrigeración, y contratar personal para mantener los servidores.

3️⃣ **Largos tiempos de implementación:** Desde la compra del hardware hasta su configuración podían pasar meses antes de que una aplicación estuviera lista para producción.

4️⃣ **Escalabilidad complicada:** Si una empresa crecía y necesitaba más capacidad, debía comprar nuevos servidores, lo que tomaba tiempo y requería una gran inversión.

5️⃣ **Monitoreo y mantenimiento 24/7:** Equipos de TI debían vigilar constantemente la infraestructura para evitar caídas y resolver problemas.

6️⃣ **Planificación del desastre:** Si un servidor fallaba o ocurría un desastre natural, las empresas debían tener planes de recuperación costosos y poco eficientes.

**Ejemplo: Un problema real**

🔹 Historia de una startup en los 2000:
Imagina que una startup en el año 2000 quiere lanzar una aplicación web. Primero, debe estimar cuántos usuarios tendrá en el primer año, comprar servidores acorde a esa estimación (con el riesgo de quedarse corto o gastar de más), contratar personal de TI para instalar y configurar los servidores, pagar por electricidad y refrigeración, y crear un sistema de respaldo en caso de fallas.

💡 **Problema:**
- Si la startup tiene más éxito del esperado, los servidores colapsan porque no pueden escalar rápidamente.
- Si el negocio no crece tanto como pensaban, terminan con servidores sin usar, perdiendo dinero.
- Los desarrolladores pasan más tiempo lidiando con infraestructura que innovando en el producto.

### La necesidad de una nueva solución:

🔹 Para muchas empresas, la infraestructura tradicional era costosa, inflexible y difícil de manejar.

🔹 No todas las compañías podían permitirse comprar y mantener un data center.

🔹 La tecnología avanzaba rápido, pero los negocios se quedaban atrás debido a las limitaciones de su infraestructura.

💡 **Transición hacia la nube:**
Aquí es donde nace la idea de la computación en la nube: una solución que permite a las empresas acceder a infraestructura de TI sin comprar servidores, sin preocuparse por mantenimiento, y con la capacidad de escalar en minutos.

### ¿Qué es la nube?
- Es poder acceder bajo demanda de recursos de TI a través de Internet con un modelo de precios de pago por uso.
- Es el uso de una red de servidores remotos conectados a internet para almacenar, administrar y procesar datos, servidores, bases de datos, redes y software. En lugar de depender de un servicio físico instalado, se tiene acceso a una estructura donde el software y el hardware están virtualmente integrados.

### Características de la nube:
Estas son las cinco propiedades esenciales que definen la nube:

1️⃣ **On-demand self-service:** Los usuarios pueden aprovisionar recursos sin intervención humana.

2️⃣ **Broad network access:** Acceso a los recursos desde cualquier lugar a través de la red.

3️⃣ **Multi-tenancy & Resource pooling:** La infraestructura es compartida entre múltiples clientes de manera segura.

4️⃣ **Rapid elasticity & Scalability:** Capacidad de escalar los recursos automáticamente según la demanda.

5️⃣ **Measured service:** El uso de los recursos se mide y se cobra de manera precisa.

### Principales ventajas de la nube:
Estos beneficios explican por qué la nube ha transformado la industria:

1️⃣  **Trade capital expense for variable expense( Cambie los gastos de capital por gastos variables):** Se eliminan los gastos de capital en hardware y centros de datos.

2️⃣  **Stop spending money running and maintaining data centers (Detenga el gasto en centros de datos):**  Costos de mantenimiento y administración

3️⃣ **Benefit from massive economies of scale (Benefíciese de las economías de escala):** Más clientes, más AWS, más infrastructura, más rebajas, precios reducidos

4️⃣ **Stop guessing capacity( Deje de adivinar la capacidad):** Capacidad insuficiente, sobre aprovisonamiento

5️⃣  **Increase speed and agility( Aumente la velocidad y la agilidad ):** Se pueden desarrollar y desplegar aplicaciones más rápido

6️⃣**Go global in minutes(Globalícese en minutos):** Se pueden lanzar aplicaciones en múltiples regiones en minutos

### Problemas resueltos con la nube:
La nube soluciona muchas de las limitaciones de los modelos tradicionales:

🔹 **Flexibilidad:** Permite cambiar tipos y tamaños de recursos según la necesidad.

🔹 **Eficiencia de costos:** Se paga solo por lo que se usa.

🔹 **Escalabilidad:** Se pueden manejar cargas de trabajo variables con facilidad.

🔹 **Elasticidad:** Se pueden agregar o reducir recursos automáticamente según la demanda.

🔹 **Alta disponibilidad y tolerancia a fallos:** Las aplicaciones pueden ejecutarse en múltiples centros de datos.

🔹 **Mayor agilidad:** Se acelera el desarrollo, prueba y despliegue de aplicaciones.

### Modelos de implementación en la nube
Existen tres formas principales de implementar infraestructura y aplicaciones en la nube:

1️⃣**Nube Privada (On-Premises o en instalaciones locales)**

📌 **Definición:** La infraestructura es utilizada exclusivamente por una sola organización y se gestiona en su propio centro de datos. Puede usar tecnologías de virtualización y automatización, pero sigue siendo propiedad de la empresa.

📍 **Ejemplo:**
Un banco que necesita controlar todos sus datos por regulación decide construir su propio centro de datos con servidores privados y firewalls internos.

📌 **Ventajas:**

✔️ Mayor control sobre seguridad y datos.

✔️ Cumple con regulaciones estrictas (bancos, gobiernos, salud).

✔️ Mejor rendimiento en entornos sensibles a la latencia.

📌 **Desventajas:**

❌ Costos elevados de infraestructura y mantenimiento.

❌ Escalabilidad limitada (agregar servidores físicos es lento y costoso).

❌ Menos flexibilidad frente a cambios de demanda.

2️⃣ **Nube Pública**

📌 **Definición:** Infraestructura y servicios ofrecidos por proveedores de nube como AWS, Google Cloud y Azure. Los recursos son compartidos entre múltiples clientes, aunque cada uno tiene su propio entorno seguro.

📍 **Ejemplo:**
Una startup lanza una aplicación en AWS, utilizando instancias EC2, bases de datos en RDS y almacenamiento en S3 sin comprar hardware propio.

📌 **Ventajas:**

✔️ Bajo costo inicial y modelo de pago por uso.

✔️ Alta escalabilidad y flexibilidad.

✔️ Rápida implementación y acceso a tecnologías avanzadas.

📌 **Desventajas:**

❌ Menos control sobre la infraestructura.

❌ Requiere estrategias de seguridad bien configuradas.

3️⃣ **Nube Híbrida**

📌 **Definición:** Combina infraestructura local con servicios en la nube, permitiendo que los datos y aplicaciones se muevan entre ambas según la necesidad.

📍 **Ejemplo:**
Una empresa de retail mantiene sus datos financieros en su propio data center (por seguridad) pero usa la nube para su página web y análisis de datos en tiempo real.

📌 **Ventajas:**

✔️ Balance entre control, seguridad y escalabilidad.

✔️ Permite aprovechar la nube sin perder inversiones previas en data centers.

✔️ Se adapta a regulaciones donde ciertos datos no pueden estar en la nube pública.

📌 **Desventajas:**

❌ Puede ser compleja de administrar.

❌ Puede generar costos adicionales si no se gestiona bien la conexión entre ambos entornos.

### Modelos de Servicio en la Nube
Los servicios en la nube se dividen en tres modelos principales:

1️⃣ **Infraestructura como Servicio (IaaS)** 🖥️

📌 **Definición:**
Proporciona acceso a recursos básicos de infraestructura como servidores, almacenamiento y redes. El usuario tiene control sobre el sistema operativo y las aplicaciones, pero no sobre el hardware subyacente.

📍 **Ejemplo:**
- AWS EC2 (máquinas virtuales en la nube).
- Amazon S3 (almacenamiento en la nube).
- Google Compute Engine.

✔️ **Ventajas:**
- Mayor control sobre la infraestructura.
- Se paga solo por lo que se usa.
- Escalabilidad sin necesidad de comprar hardware físico.

❌ **Desventajas:**
- Se requiere administrar sistemas operativos, seguridad y configuraciones.
- Mayor complejidad técnica.

🛠️ **Caso de uso:**
Una startup que necesita servidores para alojar su sitio web y su base de datos, pero no quiere comprar ni mantener hardware físico.

2️⃣ **Plataforma como Servicio (PaaS)** 🏗️

📌**Definición:**
Proporciona un entorno de desarrollo y ejecución en la nube donde los desarrolladores pueden crear, probar y desplegar aplicaciones sin preocuparse por la gestión de la infraestructura subyacente.

📍 **Ejemplo:**
- AWS Elastic Beanstalk.
- Google App Engine.
- Heroku.

✔️ **Ventajas:**
- Los desarrolladores pueden centrarse en escribir código sin preocuparse por servidores o redes.
- Facilidad para escalar aplicaciones.
- Se incluyen herramientas como bases de datos y entornos de ejecución.

❌ **Desventajas:**
- Menos control sobre la infraestructura.
- Puede haber limitaciones en la personalización.

🛠️ **Caso de uso:**
Un equipo de desarrollo que quiere desplegar rápidamente una aplicación web sin preocuparse por configurar servidores o bases de datos.

3️⃣**Software como Servicio (SaaS)** ☁️

📌 **Definición:**
Ofrece aplicaciones completas listas para usar a través de Internet, sin necesidad de instalación ni mantenimiento por parte del usuario.

📍 **Ejemplo:**
- Gmail, Google Drive, Dropbox.
- Microsoft 365.
- Salesforce.

✔️ **Ventajas:**
- No requiere instalación ni mantenimiento.
- Acceso desde cualquier lugar con Internet.
- Actualizaciones automáticas.

❌ **Desventajas:**
- Menos control sobre la configuración y seguridad.
- Dependencia del proveedor del servicio.

🛠️ **Caso de uso:**
Una empresa que necesita una plataforma de correo electrónico sin preocuparse por configurar servidores o mantener software.

### ¿Qué es un centro de datos?
Una ubicación física que almacena servidores físicos y equipos de hardware relacionados. Contiene la infraestructura informática que requieren los sistemas de TI, como servidores, unidades de almacenamiento y equipos de red. Es la instalación física que almacena los datos digitales de cualquier empresa.

### AWS es un conjunto de centros de datos:

**36 regiones:** Cada región de AWS consta de al menos 3 zonas de disponibilidad aisladas y físicamente separadas.

**114 zonas de disponibilidad:** Grupo de uno o más centros de datos con alimentación, redes y conectividad redundantes en una región de AWS.

**Más de 600 edge locations:** Puntos de presencia que se utilizan para alojar datos en caché. Más de 600 edge locations.
Estos puntos de presencia permiten a Amazon CloudFront entregar datos, contenido, aplicaciones y API de forma segura a clientes de todo el mundo con baja latencia y altas velocidades de transferencia, todo ello dentro de un entorno amigable para los desarrolladores.

### AWS Well-Architected Framework: Diseñando Arquitecturas en la Nube Correctamente
🔍 **¿Qué es el AWS Well-Architected Framework?**
Es un conjunto de principios y buenas prácticas que AWS recomienda seguir para diseñar sistemas en la nube de manera segura, eficiente y confiable.

💡 **Ejemplo de contexto:**
"Imagina que construyes una casa sin planos. Puede que al principio todo parezca bien, pero con el tiempo aparecen problemas: falta de espacio, mala ventilación, sobrecarga eléctrica… AWS creó este framework para que las empresas eviten estos errores al construir en la nube."

🏛️ **Los 6 Pilares del Well-Architected Framework**
AWS divide su marco de buenas prácticas en 6 pilares fundamentales:

1️⃣ **Excelencia Operacional** 🛠️
📌 **¿Qué significa?**
- Mejorar continuamente procesos y operaciones.
- Automatizar tareas para reducir errores humanos.

📍 **Ejemplo:**
- Uso de AWS CloudFormation para automatizar infraestructura.
- Implementación de CI/CD con AWS CodePipeline para despliegues más rápidos.

💡 **Pregunta:**
¿Cuántos procesos de su día a día podrían automatizar para evitar errores y ahorrar tiempo?

2️⃣ **Seguridad** 🔐
📌 **¿Qué significa?**
- Proteger datos, sistemas e infraestructura en la nube.
- Aplicar principios de mínimos privilegios y control de acceso.

📍 **Ejemplo:**
- Uso de AWS IAM para gestionar permisos y accesos.
- Cifrado de datos en tránsito y en reposo con AWS KMS.

💡 **Pregunta:**
¿Cómo manejan la seguridad en sus cuentas personales? ¿Usan contraseñas fuertes y autenticación de dos factores? 🔑

3️⃣**Fiabilidad**⚡
📌 **¿Qué significa?**
- Diseñar sistemas que puedan recuperarse de fallos automáticamente.
- Implementar arquitecturas altamente disponibles.

📍 **Ejemplo:**
- Uso de Auto Scaling para aumentar o reducir servidores según demanda.
- Implementación de AWS Route 53 para cambiar tráfico en caso de falla.

💡 **Pregunta:**
¿Alguna vez han usado un servicio que se cayó y no pudieron acceder? Imaginen si eso pasa con un banco o una tienda en línea.

4️⃣**Eficiencia de Rendimiento** 🚀
📌 **¿Qué significa?**
- Optimizar el uso de recursos para un mejor rendimiento.
- Elegir el tipo de instancia y base de datos adecuados.

📍 **Ejemplo:**
- Migrar una base de datos tradicional a Amazon Aurora para mayor rendimiento y menor costo.
- Uso de AWS Lambda para ejecutar código sin gestionar servidores.

💡 **Pregunta:**
¿Han notado cómo algunas apps cargan más rápido que otras? Muchas veces esto se debe a una arquitectura bien optimizada.

5️⃣ **Optimización de Costos** 💰
📌 **¿Qué significa?**
- Pagar solo por lo que realmente se usa.
- Identificar recursos infrautilizados o ineficientes.

📍 **Ejemplo:**
- Uso de AWS Cost Explorer para monitorear y optimizar gastos.
- Implementación de instancias reservadas o Spot Instances para reducir costos.

💡 **Pregunta:**
¿Cuántas veces han pagado por servicios que no usan? Lo mismo pasa en la nube si no optimizamos costos.

6️⃣ **Sostenibilidad** 🌱
📌 **¿Qué significa?**
- Diseñar arquitecturas que reduzcan el impacto ambiental.
- Minimizar el uso de servidores físicos y optimizar consumo energético.

📍 **Ejemplo:**
- Uso de AWS Graviton (procesadores eficientes en energía).
- Desplegar aplicaciones en regiones de AWS con energías renovables.

💡 **Pregunta**:
¿Sabían que los centros de datos consumen grandes cantidades de energía? AWS trabaja para reducir ese impacto.

### Referencias y documentación usada:
- [Blog de medium para imagenes e información](https://sathittham.medium.com/aws-cloud-practitioner-certification-cheat-sheet-1191b36137a8 "Blog de medium para imagenes e información")
- [Imagen arquitectura cloud](https://www.spiceworks.com/tech/cloud/articles/what-is-cloud-computing/ "Imagen arquitectura cloud")
- [AWS Training & Certification](https://www.linkedin.com/showcase/aws-training-&-certification/ "AWS Training & Certification")
- [Stephane Maarek](https://www.linkedin.com/in/stephanemaarek/ "Stephane Maarek")
- [Imagen aws region](https://disaster-recovery.workshop.aws/en/intro/infra-aws/regions-az.html "Imagen aws region")
- [AWS Well Architected Framework](https://docs.aws.amazon.com/es_es/wellarchitected/latest/framework/welcome.html "AWS Well Architected Framework")
