# Monitoreo y Gestión de Recursos

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=2cGwdSTdUqQ&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=8 "Link de la charla en Yotube")
> - [LinkedIn de Lorena Jimenez](https://www.linkedin.com/in/lorejimenezarq/ "LinkedIn de Lorena Jimenez")

---

## Contenido de la charla:

- **Amazon CloudWatch**
- **AWS CloudTrail**
- **AWS Trusted Advisor**
- **AWS Config**
- **AWS Direct Connect:**
- **Mis tips para el examen**

---

## Introducción

Esta sesión forma parte del challenge de preparación para el AWS Cloud Practitioner y tiene como objetivo introducir los fundamentos de redes en la nube, servicios clave de AWS como Amazon VPC, Route 53, CloudFront y opciones de conectividad.

## Introducción

Observar sistemas, recopilar métricas, evaluar esas métricas y a lo largo del tiempo, luego usarlas para tomar decisiones o tomar acciones, es lo que llamamos supervisión.

En esta sesión veremos una variedad de servicios y herramientas que lo ayudarán a supervisar su entorno de AWS.  Esta supervisión ayudará a medir cómo funcionan los sistemas, alertará cuando las cosas no van bien e incluso le ayudará a depurar y solucionar problemas a medida que aparecen.

---

## 1. Amazon CloudWatch

Amazon CloudWatch es un servicio que supervisa las aplicaciones, responde a los cambios de rendimiento, optimiza el uso de los recursos y proporciona información sobre el estado operativo. Al recopilar datos en todos los recursos de AWS, CloudWatch brinda visibilidad del rendimiento de todo el sistema y permite a los usuarios configurar alarmas, reaccionar automáticamente a los cambios y obtener una visión unificada del estado operativo.

**Métricas de CloudWatch:**

CloudWatch funciona mediante el seguimiento y la supervisión de **métricas**, que son variables vinculadas a los recursos.
En Amazon CloudWatch, las **métricas** son datos numéricos que representan el comportamiento o rendimiento de los recursos de AWS, como uso de CPU, tráfico de red o latencia. Se recopilan en intervalos regulares y pueden ser predeterminadas (de servicios como EC2, RDS, etc.) o personalizadas.

**Alarmas de CloudWatch:**

Las alarmas se utilizan para monitorear métricas y ejecutar acciones automáticamente cuando una métrica supera (o cae por debajo de) un umbral definido. Por ejemplo, puedes activar una notificación SNS, que es el servicio de notificación simple de AWS, si el uso de CPU supera el 80%.

**Alarmas de CloudWatch:**

- Alarma de facturación para supervisar los cargos estimados de AWS.
- Alarma de uso de CPU.
- Alarmas para detener, terminar, reiniciar o recuperar una instancia EC2.
- Alarma de latencia del balanceador de carga que envíe un correo electrónico.

**ESTADOS DE LAS ALARMAS DE MÉTRICAS:**

Una alarma de métrica tiene los siguientes estados posibles:
- **OK:**  La métrica o expresión está dentro del umbral definido.
- **ALARM:**  La métrica o expresión está fuera del umbral definido.
- **INSUFFICIENT_DATA:**  La alarma acaba de iniciarse, la métrica no está disponible o no hay suficientes datos disponibles en la métrica para determinar el estado de la alarma.

**VENTAJAS DE AMAZON CLOUDWATCH:**

- Tener acceso a todas las métricas desde una ubicación central.
- Obtener visibilidad de sus aplicaciones, infraestructura y servicios.
- Reducir el tiempo promedio de resolución, o MTTR, y mejorar el costo total de propiedad, o TCO.
- Generar información para optimizar aplicaciones y recursos operativos.

---
## 2. AWS CloudTrail

AWS CloudTrail es un servicio de AWS que le ayuda a habilitar la auditoría operativa y de
riesgos, la gobernanza y el cumplimiento de sus normas en su cuenta de AWS.
Con CloudTrail, puede ver un historial completo de la actividad de los usuarios y las llamadas a la API de las aplicaciones y recursos.

** Beneficios de CloudTrail: **

- **Trazabilidad:** CloudTrail permite conocer las actividades de los usuarios mediante el registro de la actividad realizada en su cuenta. CloudTrail registra información importante sobre cada acción, incluido quién ha efectuado la solicitud, qué servicios se han utilizado, qué acción se ha realizado, los parámetros de las acciones y los elementos de la respuesta enviada por el servicio de AWS. Esta información le ayuda a realizar un seguimiento de los cambios que se producen en los recursos de AWS y a solucionar problemas operativos.
- **Conformidad:** CloudTrail lo ayuda a demostrar la conformidad, mejorar la posición de seguridad y consolidar los registros de actividad en todas las regiones y cuentas.  CloudTrail facilita la tarea de garantizar la conformidad con las políticas internas y los estándares regulatorios.
- **Almacene de forma inmutable eventos dignos de auditoría:**  En AWS CloudTraiL, puede almacenar de forma inmutable eventos dignos de auditoría. Genere de forma sencilla los informes de auditoría que exigen las políticas internas y las normativas externas.
- **Obtenga información y analice actividades inusuales:**  Detecte el acceso no autorizado y analice los registros de actividad con Amazon Athena o con consultas basadas en SQL. Ahora es aún más fácil gracias a la generación de consultas en lenguaje natural (versión preliminar), la cual utiliza tecnología de IA generativa, para los usuarios con menos experiencia en la redacción de consultas SQL o CloudTrail. Responda con alertas de EventBridge basadas en reglas y flujos de trabajo automatizados.

** Casos de uso: **
- **Cumplimiento y auditoría:**  Proteja su organización de cualquier penalidad mediante el uso de registros de CloudTrail de modo que se demuestre la conformidad con las distintas normativas, como SOC, PCI e HIPAA.
- **Seguridad: ** Mejore la posición de seguridad mediante el registro de las actividades y los eventos de los usuarios, y configure reglas de flujos de trabajo automatizadas con Amazon EventBridge.
- **Operaciones:**  Responda a las preguntas operativas, facilite la depuración e investigue problemas como la limitación de velocidad con las consultas basadas en SQL, la generación de consultas en lenguaje natural, Amazon Athena o la visualización de las tendencias con paneles en CloudTrail Lake.
---

## 3. AWS Trusted Advisor: Buenas prácticas:

AWS Trusted Advisor lo ayuda a optimizar los costos, aumentar el rendimiento, mejorar la seguridad y la resiliencia, y operar a escala en la nube. Trusted Advisor evalúa continuamente su entorno de AWS mediante comprobaciones de prácticas recomendadas en las categorías de optimización de costos, rendimiento, resiliencia, seguridad, excelencia operativa y límites o cuotas de servicio de la nube, y recomienda medidas para corregir cualquier desviación de las prácticas recomendadas.

**FUNCIONAMIENTO DE AWS TRUSTED ADVISOR:**

Trusted Advisor realiza en tiempo real una serie de comprobaciones para cada pilar en su cuenta, según las prácticas recomendadas de AWS y para las verificaciones de cada categoría, ofrece una lista de acciones recomendadas y recursos adicionales para obtener más información sobre las prácticas recomendadas de AWS.

---
## 4. AWS Config: Cumplimiento y configuraciones:
AWS Config es un servicio completamente administrado que le proporciona inventario de recursos, historial de configuración y notificaciones de cambios de configuración para la seguridad y la gobernanza. Con AWS Config, puede descubrir recursos de AWS existentes, registrar configuraciones para recursos de terceros, exportar un inventario completo de sus recursos con todos los detalles de configuración y determinar cómo se configuró un recurso en cualquier momento. Estas capacidades utilizan la auditoría de cumplimiento, el análisis de seguridad, el seguimiento de cambios de recursos y la resolución de problemas.

**FUNCIONAMIENTO DE AWS CONFIG :**

AWS Config es un servicio que supervisa y registra continuamente las configuraciones de los recursos de AWS. Detecta cambios, evalúa el cumplimiento de reglas predefinidas y conserva un historial detallado de cada recurso para auditorías, solución de problemas o gobernanza. Funciona recolectando instantáneas y cambios de configuración, guardándolos en un bucket S3, y opcionalmente notificando eventos a través de Amazon SNS. Esto permite saber qué cambió, cuándo y quién lo hizo.

**Aspectos clave:**
- Detección de recursos.
- Seguimiento de cambios.
- Evaluación de cumplimiento.
- Registro y almacenamiento.
- Integración con otros servicios.

**REGLAS DE AWS CONFIG:**
Las reglas de AWS Config permiten evaluar si los recursos de AWS cumplen con las políticas de configuración establecidas dentro de una organización. Por ejemplo, puedes definir una regla que detecte si se lanza una instancia EC2 con una IP pública o si un bucket de S3 está configurado como público. En estos casos, AWS Config evaluará esos recursos y los clasificará como compliant (cumple) o non-compliant (no cumple).

Existen reglas administradas por AWS que cubren escenarios comunes, pero también puedes crear reglas personalizadas usando AWS Lambda para casos específicos. Es importante aclarar que AWS Config no impide por sí mismo que se realicen acciones (como crear un bucket público), ni remedia automáticamente los incumplimientos. Para aplicar restricciones preventivas, se deben usar herramientas como Service Control Policies (SCPs) dentro de AWS Organizations. **AWS Config se enfoca en monitorear, detectar y notificar, pero no en bloquear.**

**CASOS DE USO DE AWS CONFIG:**

**Agilice la resolución de problemas operativos y la administración de cambios:** Podemos descubrir los recursos que existen en nuestra cuenta o publique los datos de configuración de los recursos de terceros en AWS Config, registrar sus configuraciones y capturar cualquier cambio para solucionar rápidamente los problemas operativos.
**Despliegue un marco de conformidad como código:** Podemos codificar nuestros requisitos de conformidad como reglas de AWS Config y autorizar acciones de corrección y automatizar la evaluación de las configuraciones de los recursos en toda nuestra organización.
**Audite de manera continua el control de seguridad y el análisis:** También podemos evaluar las configuraciones de recursos para las potenciales vulnerabilidades y revisar el historial de configuraciones tras incidentes potenciales para examinar nuestro posicionamiento de seguridad.

---

## En resumen

Comprender lo que sucede en su entorno es clave para mantener aplicaciones eficientes,
seguras y en cumplimiento.

- En esta sesión vimos cómo CloudWatch puede proporcionar comprensión casi en tiempo real de cómo se comporta su sistema, incluyendo recibir alertas de condiciones que requieren su atención.
- CloudWatch también le da la capacidad de analizar esas métricas a lo largo del tiempo a medida que ajusta su sistema para obtener el máximo rendimiento.
- Hablamos de cómo CloudTrail puede ayudarle a saber exactamente quién hizo qué, cuándo y desde dónde. Responde a todas sus preguntas de auditoría de AWS, excepto por qué lo hicieron.
- Analizamos Trusted Advisor que compila un panel rápido de más de 40  comprobaciones comunes relacionadas a costos, rendimiento, seguridad y resiliencia en un panel de control comprensible.
- Finalmente, aprendimos que podemos usar AWS Config para rastrear el historial de configuración de tus recursos y garantizar el cumplimiento normativo. Es como un registro de auditoría que registra la configuración de tus recursos.

---