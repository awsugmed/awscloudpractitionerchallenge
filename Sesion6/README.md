# Redes y Entrega de Contenido

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=Fx1VXYbT53I&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=7 "Link de la charla en Yotube")
> - [LinkedIn de Javier Madriz](https://www.linkedin.com/in/javier-madriz/ "LinkedIn de Javier Madriz")

---

## Contenido de la charla:
- **Amazon VPC:**
	- Creación de redes privadas.
- **Subnets, Gateways, NAT, VPN**
- **Amazon Route 53:**
	- DNS en la nube.
- **AWS CloudFront:**
	- CDN y aceleración de contenido.
- **AWS Direct Connect:**
	- Conexión a redes privadas.

---

## Introducción

Esta sesión forma parte del challenge de preparación para el AWS Cloud Practitioner y tiene como objetivo introducir los fundamentos de redes en la nube, servicios clave de AWS como Amazon VPC, Route 53, CloudFront y opciones de conectividad.

## 1. ¿Qué es una red y cómo se compone?

Una red es un conjunto de dispositivos (como servidores, computadoras o recursos en la nube) conectados para comunicarse entre sí. En AWS, estas redes son virtuales y se crean mediante Amazon VPC.

**Componentes básicos:**

- **Subredes (Subnets)**: Divisiones lógicas dentro de una red.
- **Rutas (Routing Tables):** Determinan cómo viaja el tráfico.
- **Gateways:** Conectan redes privadas a internet u otras redes.
- **Firewalls (Security Groups / NACLs):** Controlan qué tráfico entra o sale.

---

## 2. Amazon VPC (Virtual Private Cloud)

Amazon VPC permite lanzar recursos AWS (como instancias EC2) dentro de una red virtual privada aislada.

**Elementos clave:**

- Subnets públicas y privadas.
- Internet Gateway (IGW): Permite tráfico desde/hacia internet.
- NAT Gateway / NAT Instance: Permite a subnets privadas acceder a internet sin ser accesibles desde fuera.
- VPN / AWS Direct Connect: Para conexión con redes físicas.

**Ejemplo práctico:**
Crear una VPC con 2 subnets públicas (para servidores web) y 2 subnets privadas (para base de datos).

---
## 3. Conectividad: Internet, VPN y entre redes

- Internet Gateway: Acceso a internet para subnets públicas.
- NAT Gateway: Subnets privadas pueden acceder a internet (descargar actualizaciones, etc.).
- VPN Site-to-Site: Conecta un data center físico con la VPC.
- AWS Direct Connect: Enlace privado y dedicado a AWS (más rápido y seguro que internet).

---

## 4. Amazon Route 53 (DNS en la Nube)
Route 53 es el servicio de DNS (Domain Name System) de AWS. Traduce nombres como midominio.com a direcciones IP.

**Funciones importantes:**

- Registro de dominios.
- Resolución de nombres dentro y fuera de AWS.
- Políticas de enrutamiento:
- Simple: una sola IP.
- Weighted: distribuir tráfico entre varios recursos.
- Latency-based: dirigir al recurso más rápido según ubicación.
- Geolocation y Geoproximity

---
## 5. Amazon CloudFront (Content Delivery Network)
CloudFront es una red de entrega de contenido (CDN) que acelera la distribución de archivos estáticos o dinámicos.

**Beneficios:**

- Menor latencia gracias a ubicaciones geográficas cercanas (edge locations).
- Integración con S3, EC2, ALB y Lambda.
- Protección con AWS Shield y WAF.

**Caso de uso:**
Una página web estática alojada en S3 sirve su contenido a usuarios globales más rápidamente usando CloudFront.

---

## 6. AWS Direct Connect
- Conexión dedicada entre tu infraestructura on-premise y AWS. Ideal para:
- Aplicaciones sensibles a latencia.
- Grandes volúmenes de datos.
- Requisitos de seguridad estrictos.

---

## 7. Recomendaciones Finales
- Usa subnets privadas para recursos sensibles (bases de datos, backend).
- Siempre restringe el tráfico con security groups y NACLs.
- Usa CloudFront + S3 para contenido estático accesible globalmente.
- Evalúa Direct Connect o VPN si necesitas integración con redes físicas.

---