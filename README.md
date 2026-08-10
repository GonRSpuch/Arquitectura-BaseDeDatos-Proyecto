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

```text
[ VIAJES ] (1) <---> (N) [ PASAJEROS ]
    |
    +-----> (N) [ SERVICIOS Y PAGOS ]
