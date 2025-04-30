# Servicios de Cómputo de AWS

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=IhxrEubfIfI&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=2 "Link de la charla en Yotube")
> - [LinkedIn de Yuriangel Sena](https://www.linkedin.com/in/yuriangelsena-datos/ "LinkedIn de Yuriangel Sena")

---

## Contenido de la charla:
- **Cómputo en AWS:**
	- Introducción a los servicios de cómputo en la nube con AWS.
- **Servicios de Cómputo en AWS y Escalado:**
	- Conceptos de escalado y su importancia en la nube.
- **Amazon EC2:**
	- Descripción general.
	- Tipos de Instancias.
	- Modelos de Precio.
- **Escalado en EC2:**
	- Tipos de Escalado (horizontal, vertical, automático).
- **Balanceo de Carga:**
	- Elastic Load Balancing (ELB).
- **AWS Lambda:**
	- Computación sin servidor (serverless computing).
- **Contenedores en AWS:**
	- Amazon ECS (Elastic Container Service).
	- Amazon EKS (Elastic Kubernetes Service).

---

## Introducción

En esta charla abordaremos los principales servicios de cómputo en la nube de **Amazon Web Services (AWS)**, su papel fundamental en las aplicaciones modernas y cómo podemos escalar y balancear cargas de trabajo eficientemente.

## 1. Cómputo en AWS

### ¿Qué es cómputo en AWS?

Se refiere a todos los servicios que te permiten ejecutar aplicaciones, procesar datos, alojar sitios web o manejar cargas de trabajo **sin gestionar hardware físico propio**.

---

## 2. Servicios de Cómputo

| Categoría            | Servicio                          |
|----------------------|-----------------------------------|
| Máquinas Virtuales   | Amazon EC2                        |
| Contenedores         | Amazon ECS, Amazon EKS            |
| Serverless           | AWS Lambda                        |
| Balanceador de carga | Elastic Load Balancing (ELB)      |
| Escalado automático  | Auto Scaling Groups, Elastic Beanstalk |

### ¿Qué es escalado?

Ajuste dinámico de recursos para responder a la demanda, optimizando costos y rendimiento.

### Tipos de escalado

| Tipo       | Definición                                                   |
|------------|--------------------------------------------------------------|
| Vertical   | Aumentar/disminuir recursos de una instancia (CPU, RAM).     |
| Horizontal | Agregar/eliminar instancias para distribuir la carga.        |
| Automático | Escalado dinámico basado en métricas (con Auto Scaling).     |

---

## 3. Amazon Elastic Compute Cloud (EC2)

Amazon Elastic Compute Cloud (Amazon EC2) **proporciona capacidad de computación escalable bajo demanda en la nube de Amazon Web Services (AWS)**. El uso de Amazon EC2 reduce los costos de hardware para que pueda desarrollar e implementar aplicaciones con mayor rapidez.
- Control total sobre las instancias.
- Configuración de redes, seguridad y almacenamiento.
- Escalado según la demanda.

### Tipos de instancias

**Una instancia de EC2 es un servidor virtual en la nube de AWS.**  Sin embargo, técnicamente son máquinas virtuales, ya que utilizan tecnologías de virtualización (como Nitro System) para crear entornos de cómputo aislados sobre hardware físico compartido.

Cuando inicia una instancia de EC2, el tipo de instancia que especifica determina el hardware disponible para la instancia. Cada tipo de instancia ofrece una combinación diferente de recursos de computación, memoria, red y almacenamiento. Para obtener más información, consulte la Guía de tipos de instancia de Amazon EC2.

#### Estructura de nombres de instancias

```
c7gn.large → Familia + Generación + Capacidad adicional + Tamaño
```

| Componente           | Significado                                     |
|----------------------|-------------------------------------------------|
| Familia (c, m, r, g) | Tipo de recursos optimizados (CPU, memoria, GPU)|
| Generación (7)       | Versión del hardware                            |
| Capacidad adicional (gn) | Variantes específicas                      |
| Tamaño (large)       | Cantidad de recursos asignados                 |

#### Familias de instancias

| Familia | Optimización                | Casos de uso                                  |
|---------|-----------------------------|----------------------------------------------|
| General | Balanceada (m)              | Servidores web, entornos de desarrollo       |
| Compute | CPU intensiva (c)           | Juegos online, procesamiento batch           |
| Memory  | RAM intensiva (r)           | Bases de datos en memoria, analítica         |
| GPU     | Aceleración hardware (g, p) | Machine learning, renderizado, computación científica |
| Storage | E/S alta local (i, d)       | Bases de datos NoSQL, data warehouses        |

### Modelos de precio

| Modelo               | Uso recomendado                       | Descuento aproximado |
|----------------------|---------------------------------------|----------------------|
| Bajo demanda         | Pruebas, desarrollo, cargas impredecibles | —                |
| Instancias reservadas| Aplicaciones estables y predecibles   | Hasta 66–72%        |
| Savings Plans        | Cargas dinámicas entre regiones/instancias | Hasta 72%      |
| Instancias Spot      | Cargas tolerantes a interrupciones    | Hasta 90%           |
| Hosts dedicados      | Licencias específicas, cumplimiento regulatorio | Variable     |

## 4. Escalado en EC2

- **Auto Scaling Groups (ASG)**: Permiten escalar horizontalmente instancias EC2 con políticas automáticas.
- **Elastic Load Balancer (ELB)**: Distribuye tráfico entrante entre múltiples instancias EC2 activas.

## 5. Balanceo de carga

**Elastic Load Balancing (ELB)**

Servicio que distribuye automáticamente el tráfico de entrada entre varias instancias, contenedores o IPs.

- Mejora disponibilidad y tolerancia a fallos.
- Tipos:
  - Application Load Balancer (HTTP/HTTPS)
  - Network Load Balancer (TCP/UDP)
  - Gateway Load Balancer (appliances virtuales)

## 6. AWS Lambda (Serverless)

**Computación sin servidor (Serverless)**

Permite ejecutar código sin aprovisionar ni administrar servidores.

- Solo pagas por el tiempo de ejecución.
- Escalado automático.
- Integración con otros servicios (API Gateway, S3, etc.).

## 7. Contenedores en AWS

### Amazon ECS

- Servicio de **orquestación de contenedores** totalmente administrado.
- Compatible con Docker.
- Soporta modo EC2 (en instancias propias) o **Fargate** (serverless containers).

### Amazon EKS

- Servicio de Kubernetes administrado.
- Ideal para quienes ya usan Kubernetes.
- Compatible con herramientas y ecosistema estándar de K8s.

---