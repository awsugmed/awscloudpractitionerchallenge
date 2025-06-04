# Herramientas de Automatización y DevOps en AWS

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=pNTqTaeEUPw&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=10 "Link de la charla en Yotube")
> - [LinkedIn de Aldrin Leal](https://www.linkedin.com/in/aldrinleal/ "LinkedIn de Aldrin Leal")

---

## Contenido de la charla:

- ** AWS CloudFormation: infraestructura como código**
- **AWS Elastic Beanstalk: despliegue automático de aplicaciones**
- **AWS CodeDeploy, CodePipeline, CodeBuild**
- **Integración con herramientas de terceros**

---

## Introducción

Esta sesión forma parte del challenge de preparación para el AWS Cloud Practitioner y cubre servicios clave de AWS que permiten automatizar la entrega, el despliegue y la gestión de infraestructura y aplicaciones en la nube.

---

## 1. AWS CloudFormation: Infraestructura como Código (IaC)

### ¿Qué es?
AWS CloudFormation permite definir y aprovisionar toda la infraestructura de tu aplicación como código (Infrastructure as Code).

**Ventajas:**

- Gestión declarativa mediante archivos YAML o JSON.

- Versionamiento y reutilización de plantillas.

- Asegura que la infraestructura sea consistente y reproducible.

**Ejemplo:**

Crear una plantilla que defina una VPC, subred, instancia EC2 y una política de seguridad, todo con un solo archivo.

 ---

## 2. AWS Elastic Beanstalk: Despliegue Automático de Aplicaciones

**¿Qué es?**
Elastic Beanstalk permite desplegar y escalar aplicaciones web automáticamente sin necesidad de gestionar manualmente la infraestructura.

**Características:**

- Soporta múltiples lenguajes: Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker.

- Configura automáticamente EC2, Load Balancer, Auto Scaling, RDS, etc.

- Permite personalización avanzada si se desea.

**Caso de uso:**

Subes tu archivo .zip con el código, Beanstalk se encarga del resto (infraestructura, balanceo, escalabilidad).

---

## 3. AWS Code (CodeDeploy, CodePipeline, CodeBuild)

**AWS CodePipeline:**

- Servicio de CI/CD para automatizar el ciclo de vida de desarrollo.
- Integra pasos como compilación, pruebas, despliegue y producción.

**AWS CodeBuild:**

- Servicio para compilar el código fuente y ejecutar pruebas.
- Escala automáticamente según la necesidad.

**AWS CodeDeploy:**

- Automatiza el despliegue de código en instancias EC2, Lambda o servidores on-premise.
- Admite actualizaciones con mínima o cero interrupción (rolling, blue/green).

**Flujo típico:**

- El código se sube a GitHub.

- CodePipeline detecta el cambio.

- CodeBuild compila y prueba.

- CodeDeploy hace el despliegue a producción.
---

## 4. Integración con Herramientas de Terceros
AWS se puede integrar con otras herramientas populares en el mundo DevOps como:

|Herramienta|Integración Típica|
|-------------|------------------|
|GitHub / GitLab|Repositorio de código fuente|
|Jenkins|Orquestador CI/CD externo|
|Terraform|Infraestructura como código alternativa|
|Docker / Kubernetes|Contenedores y orquestación avanzada|
|Slack / Teams|Notificaciones y alertas|

---

## 5. Recomendaciones Finales
- Empieza usando Elastic Beanstalk si quieres simplicidad.

- Usa CloudFormation o Terraform para gestionar infra como código.

- Si tu app requiere despliegues frecuentes, considera CodePipeline + CodeBuild + CodeDeploy.

- Automatiza lo más posible para lograr entornos reproducibles y seguros.

---