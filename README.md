# Arquitectura y Estructuración de Datos para Agencia de Viajes

![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Data Architecture](https://img.shields.io/badge/Data_Architecture-Relational-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## Resumen Ejecutivo
Este proyecto aborda la reestructuración del sistema de registro operativo y financiero para una agencia de viajes en etapa inicial. Se transformó un registro plano e ineficiente en una **arquitectura de datos relacional dentro de Microsoft Excel**, diseñada para eliminar la duplicidad de información, garantizar la integridad de los datos y permitir el control de margen financiero y vencimientos en tiempo real.

---

## Problema de Negocio y Objetivos
* **Problema:** La falta de un sistema centralizado provocaba amontonamiento de datos en celdas, errores de tipeo manuales y falta de visibilidad sobre los vencimientos de pago a proveedores (hoteles y transportes).
* **Objetivo:** Diseñar una solución ligera, escalable y sin costo de software adicional que ordene las operaciones de la empresa y prepare los datos para una futura migración a SQL o Power BI.

---

## Arquitectura de Datos y Modelo Relacional

En lugar de una tabla plana, la solución se estructuró en **3 entidades interconectadas mediante claves relacionales (IDs)**:

1. VIAJES (Entidad Principal)
Función: Control de cabecera de expedientes.

Campos clave: ID_Viaje, Nombre_Viaje, Fecha_Salida, Costo_Estimado, Precio_Venta, Estado.

Automatización: Cálculo automático de Margen ($) y % Margen. Controles de estado mediante validación de listas.

2. PASAJEROS (Relación 1 a Muchos)
Función: Registro detallado de clientes por viaje.

Clave Foránea: ID_Viaje (asocia múltiples pasajeros a un solo expediente sin saturar la vista principal).

3. SERVICIOS Y PAGOS (Control Operativo)
Función: Seguimiento individualizado de proveedores (hoteles, transportes, excursiones).

Control Financiero: Alertas de fechas de contrato y vencimientos de pago.

🛠️ Funcionalidades Clave e Impacto de Negocio
🚥 Control Visual de Pagos (Semáforo Condicional): Identificación automática de estados de pago (Pagado 🟢, Pendiente 🟡, Vencido 🔴) para prevenir la cancelación involuntaria de reservas.

🛡️ Calidad e Integridad de Datos: Restricción de entrada mediante Validación de Datos (listas desplegables estandarizadas), eliminando errores de tipeo.

📈 Escalabilidad: Formato nativo de Tablas Oficiales de Excel (Ctrl + T) para la propagación automática de fórmulas ante nuevas entradas.

Autor: Gonzalo Rodríguez Spuch
