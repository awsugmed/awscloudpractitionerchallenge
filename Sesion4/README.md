# Servicios de Almacenamiento en AWS

---

## 1. Introducción a los servicios de almacenamiento de AWS

AWS ofrece múltiples opciones de almacenamiento que se adaptan a diferentes necesidades:

* **Almacenamiento por bloques**: Volúmenes que se conectan a instancias EC2 (EBS)
* **Almacenamiento de objetos**: Almacenamiento escalable para datos no estructurados (S3)
* **Almacenamiento de archivos**: Sistema de archivos compartido para múltiples instancias (EFS)
* **Transferencia de datos física**: Dispositivos para mover grandes cantidades de datos (Snowball)

La elección del servicio adecuado depende de factores como el tipo de datos, la frecuencia de acceso, los requisitos de rendimiento y el costo.

---

## 2. Amazon EBS (Elastic Block Store)

### Características principales
* Almacenamiento por bloques persistente diseñado para EC2
* Volúmenes independientes del ciclo de vida de la instancia
* Replicado automáticamente dentro de su zona de disponibilidad
* Escalable hasta 64 TiB por volumen
* Posibilidad de cifrado mediante AWS KMS

### Tipos de volúmenes
* **SSD de uso general (gp2/gp3)**: Balance entre precio y rendimiento
* **SSD de IOPS aprovisionadas (io1/io2)**: Para cargas de trabajo intensivas en I/O
* **HDD optimizado para rendimiento (st1)**: Para cargas de trabajo de alto rendimiento con acceso secuencial
* **HDD en frío (sc1)**: Para datos de acceso infrecuente

### Casos de uso
* Bases de datos relacionales
* Aplicaciones empresariales
* Sistemas de archivos para instancias
* Cargas de trabajo que requieren baja latencia

### Características importantes
* **Snapshots**: Respaldos incrementales almacenados en S3
* **Elastic Volumes**: Modificación de tipo, tamaño y rendimiento sin tiempo de inactividad
* **Multi-Attach**: Conexión de un volumen io1/io2 a múltiples instancias (con limitaciones)

---

## 3. Amazon S3 (Simple Storage Service)

### Características principales
* Almacenamiento de objetos escalable, duradero y rentable
* Durabilidad del 99,999999999% (11 nueves)
* Disponibilidad del 99,99%
* Capacidad virtualmente ilimitada
* Acceso mediante HTTP/HTTPS y API
* Tolerancia a fallos mediante replicación en múltiples AZs

### Clases de almacenamiento
* **S3 Standard**: Acceso frecuente, alta disponibilidad
* **S3 Intelligent-Tiering**: Optimización automática de costos
* **S3 Standard-IA**: Acceso infrecuente con disponibilidad inmediata
* **S3 One Zone-IA**: Acceso infrecuente con menor redundancia
* **S3 Glacier Instant Retrieval**: Archivado con acceso inmediato
* **S3 Glacier Flexible Retrieval**: Archivado con recuperación en minutos a horas
* **S3 Glacier Deep Archive**: Archivado a largo plazo con recuperación en horas

### Casos de uso
* Almacenamiento de copias de seguridad y recuperación ante desastres
* Alojamiento de contenido estático y sitios web
* Data lakes y análisis de big data
* Almacenamiento de aplicaciones nativas de la nube
* Distribución de contenido multimedia

### Características importantes
* **Versionado**: Preserva múltiples versiones de objetos
* **Ciclo de vida**: Transición automática entre clases de almacenamiento
* **Replicación**: Copia automática entre buckets (incluso entre regiones)
* **Control de acceso**: Políticas de bucket, IAM, ACLs, puntos de acceso
* **Eventos**: Desencadenamiento de funciones Lambda por cambios en objetos
* **Select**: Consultas SQL para recuperar subconjuntos de datos

---

## 4. Amazon EFS (Elastic File System)

### Características principales
* Sistema de archivos totalmente administrado compatible con NFS
* Compartido entre múltiples instancias EC2
* Escalado automático (petabytes) sin aprovisionamiento previo
* Rendimiento escalable
* Alta disponibilidad y durabilidad (replicación en múltiples AZs)

### Modos de rendimiento
* **General Purpose**: Para la mayoría de cargas de trabajo
* **Max I/O**: Para aplicaciones con miles de instancias conectadas

### Modos de rendimiento
* **Bursting**: Rendimiento que escala con el tamaño del sistema de archivos
* **Provisioned**: Rendimiento independiente del tamaño del sistema de archivos

### Clases de almacenamiento
* **Standard**: Para archivos de acceso frecuente
* **Infrequent Access (IA)**: Para archivos de acceso menos frecuente
* **Archive**: Para datos raramente accedidos

### Casos de uso
* Compartir archivos entre instancias EC2
* Sistemas de gestión de contenidos
* Desarrollo y pruebas
* Aplicaciones web
* Cargas de trabajo de análisis de big data

### Características importantes
* **Lifecycle Management**: Migración automática entre clases de almacenamiento
* **Encryption**: Cifrado en reposo y en tránsito
* **Access Points**: Simplificación del acceso para aplicaciones
* **Montaje en múltiples VPCs**: A través de AWS Transit Gateway

---

## 5. AWS Snow Family - Storage Gateway

### Características principales
* Servicio de transferencia de datos física
* Petabytes de datos transferidos de manera segura
* Evita los cuellos de botella de ancho de banda de red
* Dispositivos robustos y seguros

### Familia de dispositivos
* **Snowcone**: 8TB, más pequeño y portátil
* **Snowball Edge**: 
   * Storage Optimized: 80TB
   * Compute Optimized: 42TB con capacidades de cómputo
* **Snowmobile**: Contenedor de envío con capacidad de exabytes

### Proceso de uso
1. Solicitar dispositivo en la consola de AWS
2. Recibir el dispositivo
3. Conectar a la red local y transferir datos
4. Devolver el dispositivo a AWS
5. AWS carga los datos en el servicio de destino

### Casos de uso
* Migración de datos a la nube
* Centros de datos en proceso de cierre
* Recuperación ante desastres
* Análisis de datos en ubicaciones remotas
* Transferencia de contenido multimedia

### Características importantes
* **Snowball Edge**: Capacidades de cómputo local
* **AWS OpsHub**: Interfaz gráfica para gestionar dispositivos Snow
* **AWS DataSync**: Complemento para transferencias periódicas
* **Cifrado**: Protección de datos en reposo y en tránsito

---

### AWS Storage Gateway

### Características principales
* Servicio híbrido que conecta entornos on-premises con almacenamiento en la nube
* Proporciona integración transparente con servicios de AWS
* Disponible como dispositivo físico o máquina virtual
* Gestión centralizada a través de la consola de AWS
* Compatibilidad con protocolos estándar de la industria

### Tipos de gateways
* **File Gateway**: 
  * Interfaz NFS/SMB para almacenar archivos como objetos en S3
  * Caché local para acceso de baja latencia a archivos frecuentes
  * Integración con AD para autenticación

* **Volume Gateway**:
  * **Stored Volumes**: Almacena datos localmente y los respalda en AWS
  * **Cached Volumes**: Almacena datos en S3 con caché local para acceso frecuente
  * Interfaz iSCSI para aplicaciones locales

* **Tape Gateway**:
  * Emulación de biblioteca de cintas virtuales (VTL)
  * Migración sin problemas de backups basados en cinta a la nube
  * Compatible con software de backup existente

### Casos de uso
* Extensión de almacenamiento on-premises a la nube
* Backups y recuperación ante desastres
* Migración progresiva a la nube
* Reducción de costos de almacenamiento físico
* Acceso a datos locales con respaldos en la nube

### Características importantes
* **Bandwidth Management**: Control de ancho de banda utilizado
* **Encryption**: Cifrado en tránsito y en reposo
* **Snapshot Schedule**: Programación de snapshots para backups
* **Monitoring**: Integración con CloudWatch para monitoreo
* **Optimización de transferencia**: Compresión y deduplicación de datos

---

## 6. Comparación y casos de uso

| Servicio | Tipo | Latencia | Durabilidad | Casos de uso |
|----------|------|----------|-------------|--------------|
| **EBS** | Bloques | Muy baja | Alta (en una AZ) | Bases de datos, aplicaciones con estado |
| **S3** | Objetos | Baja | Muy alta (11 nueves) | Contenido estático, archivos, backups |
| **EFS** | Archivos | Baja-Media | Alta (múltiples AZs) | Compartir archivos, CMS, desarrollo |
| **Snowball** | Transferencia física | N/A | Alta durante transporte | Migración masiva de datos |
| **Storage Gateway** | Híbrido | Baja (caché) | Alta (depende del tipo) | Extensión on-premises, backups |

### Consideraciones para la elección
* **Tipo de acceso**: Aleatorio vs. secuencial
* **Patrón de acceso**: Frecuente vs. infrecuente
* **Requisitos de latencia**: Milisegundos vs. segundos
* **Compartición**: Instancia única vs. múltiples instancias
* **Volumen de datos**: Gigabytes vs. petabytes
* **Costo**: Optimización según el caso de uso

### Estrategias de arquitectura comunes
* **Arquitectura híbrida**: EBS para bases de datos, S3 para archivos estáticos
* **Procesamiento de datos**: S3 como repositorio central, EFS para procesamiento compartido
* **Migración a la nube**: Snowball para datos iniciales, Direct Connect para sincronización
* **Aplicaciones sin servidor**: S3 para almacenamiento persistente, Lambda para procesamiento
* **Entornos híbridos**: Storage Gateway para integrar infraestructura on-premises con la nube
* **DR Híbrido**: Storage Gateway para backups en la nube de servidores locales

---

##  Recursos

* **Guia Certificación:** https://main.d1kpe7q4abdg6y.amplifyapp.com/es/

* **Mapas Conceptuales:** https://main.d1kpe7q4abdg6y.amplifyapp.com/es/mapas-mentales/

* **Cloud Quest:** https://explore.skillbuilder.aws/learn/courses/11458/aws-cloud-quest-cloud-practitioner