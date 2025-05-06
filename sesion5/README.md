# Servicios de Almacenamiento en AWS

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=hIiPO70uWg4 "Link de la charla en Yotube")
> - [LinkedIn de Idelfonso Pineda](https://www.linkedin.com/in/ildefonso-pineda-hern%C3%A1ndez-74773927/ "LinkedIn de Idelfonso Pineda")

---

## Contenido de la charla:
- Amazon RDS (bases de datos relacionales)
- Amazon DynamoDB (bases de datos NoSQL)
- Amazon Redshift (data warehouse)
- AWS Aurora (bases de datos administradas)
- AWS Database Migration Service (DMS)

---
## 1. AWS RDS

### **¿Qué es AWS RDS?**

- **Amazon Relational Database Service (RDS)** es un servicio gestionado que facilita la configuración, operación y escalado de bases de datos relacionales en la nube.
- **Características principales:**
	- **Automatización:** Automatiza tareas como aprovisionamiento, parches y backups.
	- **Escalabilidad:** Escala fácilmente la capacidad de almacenamiento y procesamiento.
	- **Seguridad:** Ofrece cifrado en reposo y en tránsito, y opciones de recuperación ante desastres.

### **Casos de Uso de AWS RDS:**

- **Aplicaciones Web:** Manejo de bases de datos para aplicaciones web y móviles.
- **E-commerce:** Gestión de datos de productos, clientes y transacciones.
- **Análisis de Datos:** Almacenamiento y procesamiento de grandes volúmenes de datos para análisis.
- **Aplicaciones Empresariales:** Soporte para aplicaciones críticas de negocio.

**Ejemplo:**
- **Airbnb:** Utiliza AWS RDS para manejar millones de reservas y datos de usuarios de manera eficiente.

### **Capacidades:**

**Compatibilidad:** Soporta motores de bases de datos como MySQL, PostgreSQL, MariaDB, Oracle y SQL Server.
**Alta Disponibilidad:** Opciones de Multi-AZ para alta disponibilidad y recuperación ante desastres.
**Monitoreo:** Integración con Amazon CloudWatch para monitoreo y alertas.

### **Ventajas:**

**Costo-Eficiencia:** Pago por uso, sin costos iniciales elevados.
**Flexibilidad:** Escalabilidad automática y sin tiempos de inactividad.
**Seguridad:** Integración con AWS Identity and Access Management (IAM) para control de acceso.

[![](rds)](imagenes/rds.png)
---
## 2. AWS DynamoDB

### ¿Qué es AWS DynamoDB?

- **AWS DynamoDB** es una base de datos NoSQL totalmente gestionada y sin servidor que ofrece un rendimiento de milisegundos de un solo dígito a cualquier escala.
- **Características principales:**
	- **Sin servidor:** No requiere aprovisionamiento de servidores ni mantenimiento.
	- **Escalabilidad:** Se ajusta automáticamente para manejar cualquier cantidad de tráfico y datos.
	- **Rendimiento:** Consistente y rápido, ideal para aplicaciones modernas y de alta demanda.

### Casos de Uso Comunes:

- **Aplicaciones Web y Móviles:** Manejo de datos de usuarios, sesiones y perfiles.
- **IoT:** Almacenamiento y procesamiento de datos de dispositivos conectados.
- **Gaming:** Gestión de datos de jugadores, puntuaciones y estadísticas.
- **E-commerce:** Manejo de carritos de compra, inventarios y transacciones.

**Ejemplo:**

- **Amazon Prime Day:** DynamoDB maneja trillones de llamadas API durante eventos de alto tráfico como Prime Day.

### Capacidades:
- **Modelo de Datos:** Soporta modelos de datos clave-valor y documentos.
- **Transacciones ACID:** Garantiza la integridad de los datos en aplicaciones empresariales.
- **Alta Disponibilidad:** Diseñado para ser altamente disponible y resistente.

### Ventajas:
- **Costo-Eficiencia:** Pago por uso, sin costos de aprovisionamiento.
- **Flexibilidad:** Escalabilidad automática y sin tiempos de inactividad.
- **Seguridad:** Integración con AWS Identity and Access Management (IAM) para control de acceso.

---
## 3. AWS Aurora

### ¿Qué es AWS Aurora?

- **AWS Aurora** es un servicio de base de datos relacional compatible con MySQL y PostgreSQL, diseñado para ofrecer rendimiento y disponibilidad superiores.
- **Características principales:**
	- **Alto rendimiento:** Hasta cinco veces más rápido que las bases de datos estándar de MySQL y hasta tres veces más rápido que PostgreSQL.
	- **Alta disponibilidad:** Replica automáticamente seis copias de tus datos en tres zonas de disponibilidad.
	- **Escalabilidad:** Escala automáticamente el almacenamiento hasta 128 TB por instancia de base de datos.

### Casos de Uso Comunes:

- **Aplicaciones Web y Móviles:** Manejo de bases de datos para aplicaciones de alto rendimiento.
- **E-commerce:** Gestión de datos de productos, clientes y transacciones.
- **Análisis de Datos:** Almacenamiento y procesamiento de grandes volúmenes de datos para análisis.
- **Aplicaciones Empresariales:** Soporte para aplicaciones críticas de negocio.

**Ejemplo:**

- **Expedia:** Utiliza AWS Aurora para manejar grandes volúmenes de datos de reservas y mejorar la experiencia del usuario.

### Capacidades:
- **Compatibilidad:** Compatible con MySQL y PostgreSQL, facilitando la migración de aplicaciones existentes.
- **Seguridad:** Cifrado de datos en reposo y en tránsito, y opciones de recuperación ante desastres.
- **Monitoreo:** Integración con Amazon CloudWatch para monitoreo y alertas.

### Ventajas:
- **Costo-Eficiencia:** Pago por uso, sin costos iniciales elevados.
- **Flexibilidad:** Escalabilidad automática y sin tiempos de inactividad.
- **Alta disponibilidad:** Diseñado para ser altamente disponible y resistente.
---

## 4. AWS Redshift

### ¿Qué es AWS Redshift?
- **Amazon Redshift** es un servicio de almacenamiento de datos en la nube que permite realizar análisis de datos a gran escala.
- **Características principales:**
	- **Alto rendimiento:** Optimizado para consultas rápidas y complejas.
	- **Escalabilidad:** Capacidad de escalar desde unos pocos gigabytes hasta petabytes de datos.
	- **Integración:** Se integra fácilmente con otros servicios de AWS y herramientas de análisis de datos.

### Casos de Uso Comunes:
- **Análisis de Datos:** Procesamiento y análisis de grandes volúmenes de datos.
- **Business Intelligence:** Generación de informes y visualización de datos para la toma de decisiones.
- **Machine Learning:** Preparación y análisis de datos para modelos de aprendizaje automático.
- **E-commerce:** Análisis de datos de ventas, clientes y productos.
**Ejemplo:**
- **Lyft:** Utiliza AWS Redshift para analizar datos de viajes y mejorar la experiencia del usuario.

### Capacidades:
- **Columnar Storage:** Almacenamiento columnar para consultas rápidas y eficientes.
- **Compresión de Datos:** Compresión automática para reducir el espacio de almacenamiento.
- **Redshift Spectrum:** Consulta datos directamente en S3 sin necesidad de cargarlo en Redshift.

### Ventajas:
- **Costo-Eficiencia:** Pago por uso, con opciones de ahorro mediante instancias reservadas.
- **Flexibilidad:** Escalabilidad automática y sin tiempos de inactividad.
- **Seguridad:** Cifrado de datos en reposo y en tránsito, y opciones de recuperación ante desastres.

---
## AWS DMS

### ¿Qué es AWS DMS?

- **AWS Database Migration Service (DMS)** es un servicio que facilita la migración de bases de datos a AWS de manera rápida y segura.
- **Características principales:**
	- **Compatibilidad:** Soporta migraciones de bases de datos homogéneas y heterogéneas.
	- **Automatización:** Automatiza tareas de replicación y migración de datos.
	- **Seguridad:** Cifrado de datos en tránsito y opciones de recuperación ante desastres.

### Casos de Uso Comunes:
- **Migración de Bases de Datos:** Migración de bases de datos locales a la nube de AWS.
- **Replicación de Datos:** Replicación continua de datos para alta disponibilidad y recuperación ante desastres.
- **Modernización de Aplicaciones:** Migración de bases de datos a motores más modernos y eficientes en AWS.
- **Análisis de Datos:** Migración de datos a servicios de análisis como Amazon Redshift.

**Ejemplo:**
- **Samsung:** Utiliza AWS DMS para migrar sus bases de datos a AWS, mejorando la eficiencia y reduciendo costos.

### Capacidades:
- **Soporte Multiplataforma:** Compatible con bases de datos como Oracle, SQL Server, MySQL, PostgreSQL, y más.
- **Monitoreo:** Integración con Amazon CloudWatch para monitoreo y alertas.
- **Transformación de Datos:** Capacidad de transformar datos durante la migración.

### Ventajas:
- **Costo-Eficiencia:** Pago por uso, sin costos iniciales elevados.
- **Flexibilidad:** Migración sin tiempos de inactividad significativos.
- **Seguridad:** Cifrado de datos en tránsito y opciones de recuperación ante desastres.

---

##  Recursos

* **Guia Certificación:** https://main.d1kpe7q4abdg6y.amplifyapp.com/es/

* **Mapas Conceptuales:** https://main.d1kpe7q4abdg6y.amplifyapp.com/es/mapas-mentales/

* **Cloud Quest:** https://explore.skillbuilder.aws/learn/courses/11458/aws-cloud-quest-cloud-practitioner