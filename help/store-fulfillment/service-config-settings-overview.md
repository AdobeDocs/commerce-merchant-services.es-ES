---
title: Información general sobre la configuración para Store Fulfillment
description: Obtenga información sobre los tipos de ajustes de configuración de administración disponibles para personalizar las funciones de cumplimiento ampliadas que proporciona la solución Store Fulfillment y vincule a las instrucciones para completar la configuración.
role: User, Admin
level: Intermediate
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Información general sobre la configuración para Store Fulfillment

En el Administrador de Adobe Commerce, los ajustes de configuración de Servicios de adquisición de tiendas de Walmart Commerce Technologies se clasifican por tipo.

**Almacenar valores de configuración de cumplimiento por tipo**

| **Tipo** | **Descripción** | **API configurable** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Configuración general](enable-general.md) | Integración general configurada para la solución Store Fulfillment, sus funciones activas y credenciales para conectarse a los servicios de cumplimiento. | No |
| [Configuración de correo electrónico de ventas](sales-emails.md) | Configure plantillas de correo electrónico adicionales para las notificaciones de clientes enviadas durante el proceso de registro. | No |
| [Configuración de tienda de comerciantes](merchant-store-configuration.md) | Configure fuentes de Inventory management mejoradas como tiendas comerciales. | Sí |
| [Administración de stock de productos](product-stock.md) | Configure las funciones y la mensajería de existencias del comerciante disponibles para los clientes. | Sí |
| [Transferencia de origen de Inventory management](inventory-stock-transfer.md) | Configurar un nuevo stock, transferir inventario fuera del stock predeterminado. | Sí |
| [Configuración de varios sitios web/ámbitos](multi-site-and-scope-config.md) | Configure las existencias y los métodos de envío para varios sitios web o ámbitos de tienda. | No |
| [Configuración del sistema de procesos en segundo plano](background-processes.md) | Configure las programaciones para los procesos en segundo plano utilizados en la sincronización de datos con los servicios de cumplimiento. | No |
| [Configuración de asignación y ubicación de almacenamiento](store-location-map-provider-setup.md) | Configure la capacidad de utilizar un proveedor de distancia para buscar tiendas minoristas y mostrar esta información en el mapa SLS | Sí |
| [Configuración de la experiencia de registro](check-in-experience-setup.md) | Configure el color del coche y las opciones de fabricación del coche que estarán disponibles durante el proceso de facturación | Sí |
| [Configuración de usuario](user-setup.md) | Administre las cuentas de usuario, las funciones y los permisos de los socios de tienda que usan la aplicación Store Assist. ámbitos. | Sí |
| [Configuración de aplicación](app-setup.md) | Revise las configuraciones disponibles de la aplicación de asistencia de tienda necesarias para completar el proceso de incorporación. Estas opciones no se pueden configurar desde el administrador de Adobe Commerce. | Sí |

## Usar la referencia de configuración

Vea la referencia de configuración para cada tipo de configuración seleccionando el nombre del tipo en la _Almacenar valores de configuración de cumplimiento por tipo_ tabla.

En la referencia de configuración de cada tipo, los detalles de configuración se muestran en una tabla con los siguientes encabezados de columna:

- **Campo** hace referencia al nombre del campo que desea configurar

- **Descripción** proporciona detalles importantes sobre el propósito y el comportamiento del campo

- **Ámbito** indica el ámbito de configuración de Adobe Commerce para la configuración (global, sitio web, tienda)

- **Requerido** value indica si se debe establecer un valor en el campo

Para obtener una referencia técnica, también puede encontrar la ruta de configuración interna para cada campo.
