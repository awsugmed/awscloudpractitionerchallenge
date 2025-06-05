# Facturación y Precios en AWS

> **Nota:** La información aquí es tomada de documentación oficial, y de información en internet.
> Este repositorio es una recopilación de las charlas que daremos en el Cloud Practitioner Challenge hecho por la comunidad** AWS User Group Medellín**.
> - [Redes sociales de la comunidad AWS User Group Medellín](https://linktr.ee/awsugmed "Redes sociales de la comunidad AWS User Group Medellín")
> - [Link de la charla en Yotube](https://www.youtube.com/watch?v=2cGwdSTdUqQ&list=PLhbdvasxz8wwO-b9nlRBYYzY6n5CvSOvj&index=8 "Link de la charla en Yotube")
> - [LinkedIn de Lorena Jimenez](https://www.linkedin.com/in/lorejimenezarq/ "LinkedIn de Lorena Jimenez")

---

## Contenido de la charla:

- **Principios de precios en AWS**
- **Generadores de costos en AWS**
- **Modelos de facturación: On-Demand, Reserved, Spot**
- **Uso de la calculadora de costos de AWS**
- **AWS Cost Explorer y AWS Budgets**

---

## Introducción

En esta sesión veremos una variedad de servicios y herramientas que lo ayudarán a tomar decisiones informadas sobre cómo y cuándo usar los diferentes recursos para optimizar sus costos en su entorno de AWS.

---

## 1. Principios de precios en AWS

AWS se basa en tres pilares fundamentales para su modelo de precios:

- **Pague por uso:**  Solo pagan por los recursos que consumen, sin contratos a largo plazo, le permite adaptarse fácilmente a las necesidades cambiantes del negocio sin comprometer y mejorando su capacidad de respuesta a los cambios. Por ejemplo, si usan una instancia EC2 por 10 minutos, pagan solo por esos 10 minutos. Esto les permite escalar según demanda real, sin adivinar necesidades futuras.

- **Ahorre al reservar:** Si saben que necesitarán un servidor por 1 o 3 años, reservarlo les da descuentos de hasta el 75%. Puedes programar cuándo quieres usar una instancia.¿Han notado que los boletos de avión son más baratos si se compran con anticipación? AWS aplica la misma lógica.

- **Pague menos utilizando más:** Por ejemplo, en S3, mientras más datos almacenen, menor será el costo por GB. Es como comprar al por mayor: a mayor volumen, mejor precio. Con AWS, puedes obtener descuentos por volumen y conseguir importantes ahorros a medida que aumenta tu uso.

 ---

## 2. CapEx vs OpEx:

Antes de la nube, las empresas invertían en servidores físicos (CapEx). Hoy, AWS convierte eso en gastos operativos (OpEx):

- **Gasto de capital (CapEx):** Se paga por adelantado. Es un coste fijo a fondo perdido. Es como comprar una casa: pagan todo por adelantado, asumen el riesgo de quedarse cortos o pagar de más, y si ya no la necesitan, venderla es complicado. En TI, esto se traduce en servidores subutilizados o obsoletos

- **Gasto operativo (OpEx):** se paga por lo que se utiliza. Es como alquilar: pagan mes a mes según uso. ¿Necesitan más capacidad? La activan en minutos. ¿Ya no la necesitan? La apagan. AWS opera así: electricidad, agua, gas... solo pagan por lo que consumen. Ejemplo: Una startup que usa OpEx puede invertir lo ahorrado en innovar, idea de negocio, en vender

---

## 3. Generadores de costo en AWS:

En AWS, los costos pueden provenir de varias fuentes, incluidos los recursos informáticos, el almacenamiento y la transferencia de datos.

- **Computación/ Informatica:** el uso de cpu, memoria que se cobra en hora en algunos casos hasta por segundos y que varia en función del tipo de instancia, es decir, que varía en función de las capacidades que estamos usando, a más o menos capacidad

- **Almacenamiento:** se cobra usualmente por cada gigabytes (gb) que nosotros utilizamos

- **Transferencia de datos:** y aquí es donde hay un factor importante que siempre debemos considerar, los datos de salida, se suman y se cobran

---

## 4. Modelos de facturacion en aws:

AWS ofrece opciones para todos los escenarios/ Usar el modelo de precios correcto según el trabajo

- **On-Demand**	Pagas mientras usas, sin compromisos
- **Savings Plans**	Descuentos si te comprometes 1-3 años
- **Spot Instances**	Ahorros grandes si eres flexible
- **Reserved Instances**	Descuentos por reservar con specs fijas

**Instancias bajo demanda:**

En el que se paga solo por el tiempo de uso (horas o segundos), sin pagos anticipados ni compromisos a largo plazo. Ofrecen máxima flexibilidad, permitiendo lanzar y detener instancias según necesidad, lo que las hace ideales para cargas de trabajo impredecibles. Sin embargo, esta comodidad tiene un coste más elevado en comparación con opciones de pago por reserva. Un ejemplo cotidiano sería compararlas con un taxi: lo usas cuando lo necesitas, sin ataduras, pero resulta más caro que otras alternativas con planificación previa.

**Instancias reservadas:**

Ofrecen un modelo de pago anticipado con un precio fijo durante un plazo determinado (1 o 3 años), independientemente del uso real. Permiten diferentes modalidades de pago (total por adelantado, parcial o sin pago inicial) y proporcionan un ahorro significativo frente a las instancias bajo demanda, especialmente para cargas de trabajo estables y predecibles. Además, garantizan disponibilidad al reservar capacidad en la nube. Algunas opciones incluso permiten flexibilidad, como las instancias convertibles, que admiten cambios en el tipo de instancia o región. Se asemejan a un leasing de coche: requieren compromiso a largo plazo, pero pueden reducir costes hasta en un 75%, siendo ideales para servicios que funcionan ininterrumpidamente, como bases de datos.

**Instancias Spot:**

Ofrecen capacidad de EC2 no utilizada con descuentos de hasta el 90% comparado con las instancias bajo demanda, operando bajo un modelo de puja. Los precios fluctúan según la demanda, complicando la estimación de costos a largo plazo.

Las instancias de spot son una opción económica si es flexible con respecto a cuándo es necesario ejecutar las aplicaciones y si las aplicaciones se pueden interrumpir.

Esta característica las hace ideales para cargas de trabajo flexibles y no críticas, como procesamiento por lotes, pruebas, donde las interrupciones son manejables. para análisis de datos, trabajos por lotes, procesamiento en segundo plano y tareas opcionales.

Su principal desventaja son impredecibles. 
Podríamos compararlas con "ofertas relámpago" en retail: excelentes precios, pero con disponibilidad limitada y sin garantías de permanencia.

**Saving Plans:**

Ofrecen un modelo de ahorro basado en compromiso, donde garantizas un uso mínimo (en USD/hora) durante 1 o 3 años a cambio de descuentos de hasta el 72% frente a tarifas bajo demanda. A diferencia de las Instancias Reservadas, proporcionan mayor flexibilidad al aplicar ese uso comprometido a diferentes tipos de instancias, regiones y servicios (incluyendo EC2 y SageMaker). Existen dos variantes: los Compute Saving Plans (para múltiples servicios) y los EC2 Instance Saving Plans (específicos para EC2). Funcionan como un "plan todo incluido" en la nube: aunque requieren un gasto mínimo garantizado, ofrecen ahorros predecibles con la libertad de distribuir ese compromiso según cambien tus necesidades.

---

## 5. Nivel Gratuito de AWS y Servicios sin Costo:

Prueba +60 servicios sin pagar 5GB gratis en S3 por un año Dos tipos: servicios SIEMPRE gratis y servicios gratis por 12 meses
12 meses de uso gratuito limitado

Servicios como VPC, IAM (usuarios, grupos, roles), Auto Scaling sin costo permanente 
Una VPC es una red virtual

AWS Auto Scaling monitoriza sus aplicaciones y ajusta automáticamente la capacidad para mantener un desempeño predecible y estable al menor costo posible

## 6. Herramientas para monitorear y reducir costos:

| Herramienta | Para qué sirve                | Beneficio principal                                  |
|---------|-----------------------------|----------------------------------------------|
| Cost Explorer | Ver y analizar gastos              | Identifica dónde gastas más       |
| AWS Budgets | Alertas de gastos        | Evita sorpresas en la factura        |
| Cost Reports  | Detalles de uso          | Analiza cada centavo gastado         |
| Organizations     | Control multi-cuenta | Una sola factura para todo |


- **Cost Explorer:** es como tu GPS financiero en AWS. Es gratis y te muestra exactamente dónde va tu dinero:

|Lo que hace|Cómo te ayuda|
|-------------|------------------|
|Filtra por servicio|Separa gastos de EC2, S3 y otros|
|Muestra datos por región|Identifica dónde gastas más|
|Crea gráficos|Te dice si gastas más o menos que antes|
|Hace predicciones|Te avisa cuánto podrías gastar el mes que viene|

- **AWS Budgets:** es como tener un guardia que vigila tus gastos 24/7

|Tipo|Función|Qué hace|
|---------|-----------------------------|----------------------------------------------|
|Dinero|Mide gastos reales|Te avisa al 80% del límite|
|Recursos|Cuenta uso de servicios|Manda SMS si te pasas|
|RIs|Supervisa instancias reservadas|Te informa cada día|
|Planes de ahorro|Monitorea tus planes|Te alerta según tus reglas|

- **Cost & Usage Report (CUR):** El CUR es como tu extracto bancario de AWS, pero MÁS detallado:

Se pone al día varias veces al día Guarda todo en S3 Te dice EXACTAMENTE cuánto gastas en cada servicio de AWS, recurso individual, etiqueta que hayas creado.

---

## Tips

- **Alarma de facturación:**
	- Las notificaciones se envían por correo electrónico cuando la factura alcanza una cantidad de dinero especificada

- **Etiqueta tus recursos:**
	- Las etiquetas y grupos de costos en AWS son como un sistema de organización que te ayuda a ver quién gasta qué.

|Tipo de Etiqueta|Para Qué Sirve|Ejemplo
|---------|-----------------------------|----------------------------------------------|
|AWS|Identifica creadores|aws:createdBy|
|Usuario|Marca equipos/proyectos|proyecto:alfa|
|Retroactiva|Marca recursos viejos|departamento:ventas|

- **Organizaciones AWS:**

	- Con Organizations manejas múltiples cuentas AWS como una sola, todo en un lugar, puedes administrar varias cuentas de AWS desde una ubicación central.
	- Proporciona facturación consolidada para que reciba una única factura para todas las cuentas de AWS de la organización. Esto le permite compartir precios de descuento por volumen.

|Función|Qué hace|Beneficio|
|---------|-----------------------------|----------------------------------------------|
|Factura Única|Une todas las facturas|Un solo pago mensual|
|Más Descuentos|Suma uso total|Pagas menos|
|Control Total|Maneja todo central|Mejor control|

"La facturación consolidada junta todos los gastos en una factura, haciendo más fácil ver y controlar costos."

- **Revisa mensualmente:**
	- Cómo obtener asistencia o información relacionada con la facturación ,ya que el nivel de soporte que tenga contratado el cliente afecta directamente a cómo puede obtener ayuda con problemas de facturación, optimización de costes y resolución de incidencias (Gravedad de los casos y tiempos de  respuesta). Si un cliente tiene un problema grave con su factura (ejemplo: cobro incorrecto, uso no autorizado), el plan de soporte determinará qué tan rápido AWS responderá:

	- **Business/Enterprise:**
	Gravedad "Urgente" (Ej.: Facturación incorrecta que genera sobrecostes): Respuesta en menos de 1 hora.
	Gravedad "Alta" (Consultas sobre cargos inesperados): Respuesta en menos de 4 horas.

	- **Básico/Desarrollador:**
	No garantiza soporte prioritario para facturación.


- **Relación entre Facturación y Soporte:**

	- **Diferentes niveles de soporte:** diferentes formas de obtener ayuda con la facturación.
	- **Básico:** Solo acceso a foros y documentación (limitado para resolver problemas complejos de facturación).
	- **Desarrollador/Business/Enterprise:** Permite abrir casos de soporte de facturación con distintos tiempos de respuesta.
	- **Enterprise:** Incluye un TAM (Gestor Técnico de Cuenta) que puede ayudar de forma proactiva con optimización de costes y disputas de facturación.
	- **Trusted Advisor** (Chequeos de optimización de costes)

---
