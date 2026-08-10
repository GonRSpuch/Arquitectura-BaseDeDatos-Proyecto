### 0. Descargo de Responsabilidad (Disclaimer)

Toda la información presentada en este repositorio ha sido completamente anonimizada y modificada para proteger la confidencialidad institucional y comercial. Los datos, figuras, registros y conclusiones no representan el desempeño real de la organización y tienen un propósito exclusivamente educativo, analítico y de demostración técnica.


## 1. Visión General del Proyecto (Project Overview)

Muchas agencias de viajes y PyMEs operativas dependen de planillas de cálculo para gestionar expedientes, clientes y contrataciones con proveedores. Sin embargo, con el tiempo, estas hojas de trabajo tienden a acumular inconsistencias, datos fragmentados, errores de tipeo manuales y celdas sobrecargadas de texto. Esto degrada la confiabilidad de la información, haciendo complejo el seguimiento del margen operativo por viaje, el control de vencimientos de pago y la coordinación oportuna de los servicios.

Este proyecto aborda estos desafíos mediante el diseño de una **arquitectura de datos relacional y estandarizada en Microsoft Excel**. El objetivo es estructurar el registro operativo en entidades interconectadas, eliminando la duplicidad de datos, automatizando el control financiero y garantizando la integridad de los registros desde la carga inicial.

Los resultados e insights generados a través de esta estructura son especialmente valiosos para:
* **Equipos Operativos y de Venta:** Para gestionar clientes y reservas asociadas a un viaje sin saturar las planillas principales ni perder trazabilidad.
* **Coordinación y Finanzas:** Para identificar vencimientos de pago a hoteles, transportes, excursiones, operadores externos en tiempo real, evitando penalizaciones o cancelaciones de reservas.
* **Administración y Gerencia:** Para evaluar la rentabilidad real y el margen de ganancia de cada expedición o paquete turístico antes y después de su ejecución.

Toda la solución está optimizada para servir como una base de datos limpia y lista para ser migrada a sistemas relacionales SQL o conectada a tableros de control interactivos en **Power BI**.


## 2. Objetivos del Proyecto (Project Goals)

Este proyecto fue diseñado en torno a tres objetivos estratégicos orientados a optimizar la gestión operativa, garantizar la calidad de la información y proteger el margen financiero de la agencia:

### 1. Estandarización e Integridad de la Base de Datos
* **Diseñar un modelo relacional de datos** que elimine el amontonamiento de texto en celdas únicas y reduzca a cero la duplicidad de información.
* **Restringir errores de carga manual** mediante la implementación de reglas de validación estandarizadas (listas desplegables para estados operativos, tipos de servicio y pagos).
* **Asegurar la escalabilidad de los registros** mediante el uso de estructuras de datos oficiales (Tablas de Excel) que propaguen fórmulas y formatos automáticamente.

### 2. Control Financiero y Trazabilidad de Margen
* **Automatizar el cálculo de rentabilidad** para cada paquete turístico o expedición, permitiendo visibilidad inmediata de los márgenes en pesos ($) y en porcentaje (%).
* **Identificar de forma temprana viajes con márgenes inferiores al umbral mínimo** de rentabilidad deseado antes de la confirmación al cliente.
* **Proporcionar métricas claras de costos estimados vs. precios de venta** para respaldar la toma de decisiones en la fijación de tarifas.

### 3. Gestión de Riesgo Operativo y Control de Proveedores
* **Implementar un sistema visual de alertas (Semáforo de Pagos)** para clasificar compromisos con proveedores en `Pagado` 🟢, `Pendiente` 🟡 y `Vencido` 🔴.
* **Facilitar el seguimiento de fechas críticas de vencimiento** con hoteles, transportes y operadores para prevenir cancelaciones involuntarias de reservas o penalizaciones por mora.
* **Estructurar la información operativa** de forma limpia para que pueda ser migrada directamente a una base de datos SQL o conectada a un tablero interactivo en Power BI.


## 3. Levantamiento de Requerimientos y Metodología (Requirement Gathering)

El desarrollo del proyecto comenzó con una etapa de alineación operativa y relevamiento de necesidades junto a la Dirección / Jefatura Operativa de la agencia. 

### Solicitud Inicial del Negocio (Requerimientos Críticos)
Para centralizar la gestión de las operaciones, se definió inicialmente un listado de **22 variables/campos clave** que la empresa necesitaba registrar para cada expediente:

1. `Nombre del viaje`
2. `Fecha creación`
3. `Fecha salida`
4. `Extensión (días)`
5. `Pasajeros`
6. `Destinos`
7. `Transporte`
8. `Fecha contrato transporte`
9. `Vencimiento pago transporte`
10. `Hoteles`
11. `Fecha contrato hotel`
12. `Vencimiento pago hotel`
13. `Operador exterior`
14. `Contacto operador`
15. `Fecha confirmación`
16. `Itinerario (archivo)`
17. `Responsable`
18. `Costo estimado`
19. `Precio de venta`
20. `Margen ($)`
21. `Margen (%)`
22. `Estado`

---

### Diagnóstico Técnico: El Riesgo de la "Tabla Plana"
Al analizar la lista de requerimientos delegada, se identificó un problema estructural clásico en la gestión de datos: **intentar volcar los 22 campos en una sola tabla continua (Flat Table)**.

Este enfoque tradicional presentaba tres fallas críticas de diseño:
1. **Saturación y falta de atomicidad:** Agrupar múltiples pasajeros o múltiples hoteles/transportes dentro de una sola celda impide filtrar, contar o auditar la información correctamente.
2. **Duplicidad de datos y redundancia:** Si un viaje incluye 3 hoteles y 2 transportes, repetir la fila principal para cada proveedor genera inconsistencias financieras en los montos totales.
3. **Alto riesgo de error humano:** Escribir textos extensos o fechas de vencimiento de forma desestructurada impide generar alertas automáticas de pago.

---

### Decisión de Arquitectura: Normalización y Modelo Relacional
Ante este diagnóstico, se propuso a la jefatura reestructurar el requerimiento original pasando de un registro plano a un **Modelo de Datos Relacional de 3 Entidades**, separando la cabecera del viaje, el detalle de pasajeros y el control individualizado de servicios/proveedores.




