---
title: Información general sobre la configuración para el cumplimiento de la tienda
description: Obtenga información sobre los tipos de configuración de administración disponibles para personalizar las capacidades de cumplimiento extendidas que proporciona la solución de cumplimiento de almacenamiento y vincule las instrucciones para completar la configuración.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Información general sobre la configuración para el cumplimiento de la tienda

En el administrador de Adobe Commerce, los ajustes de configuración para los servicios de cumplimiento de tiendas de Walmart Commerce Technologies se clasifican por tipo.

**Almacenar los ajustes de configuración de cumplimiento por tipo**

| **Tipo** | **Descripción** | **Configuración de API** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Configuración general](enable-general.md) | Integración general configurada para la solución Store Fulfillment, sus funciones activas y credenciales para conectarse a los servicios de cumplimiento. | No |
| [Configuración de correo electrónico de ventas](sales-emails.md) | Configure plantillas de correo electrónico adicionales para las notificaciones de clientes enviadas durante el proceso de registro. | No |
| [Configuración de Merchant Store](merchant-store-configuration.md) | Configure fuentes Inventory management mejoradas como tiendas de mercantes. | Sí |
| [Administración de existencias de productos](product-stock.md) | Configure los mensajes de stock de comerciantes y las funciones disponibles para los clientes. | Sí |
| [Transferencia de fuentes de Inventory management](inventory-stock-transfer.md) | Configure un nuevo inventario, transfiera el inventario de existencias de existencias predeterminadas. | Sí |
| [Configuración de múltiples sitios web/Ámbito](multi-site-and-scope-config.md) | Configure las existencias y los métodos de entrega para varios sitios web/ámbitos de almacenamiento. | No |
| [Configuración del sistema del proceso en segundo plano](background-processes.md) | Configure las programaciones para los procesos en segundo plano utilizados en la sincronización de datos con los servicios de cumplimiento. | No |
| [Configuración de ubicación y asignación de tiendas](store-location-map-provider-setup.md) | Configure la capacidad de usar un proveedor de distancia para buscar tiendas minoristas y mostrar esta información en el mapa de SLS | Sí |
| [Configuración de la experiencia de registro](check-in-experience-setup.md) | Configure el color del coche y cree las opciones que estarán disponibles durante el proceso de registro | Sí |
| [Configuración de usuario](user-setup.md) | Administre las cuentas de usuario, las funciones y los permisos de los asociados de la tienda que utilicen la aplicación de ayuda de la tienda. ámbitos. | Sí |
| [Configuración de la aplicación](app-setup.md) | Revise las configuraciones disponibles para la aplicación de asistencia de tienda necesaria para completar el proceso de incorporación. Estos ajustes no se pueden configurar desde el administrador de Adobe Commerce. | Sí |

## Usar la referencia de configuración

Para ver la referencia de configuración de cada tipo de configuración, seleccione el nombre del tipo en la variable _Almacenar los ajustes de configuración de cumplimiento por tipo_ tabla.

En la referencia de configuración de cada tipo, los detalles de configuración se muestran en una tabla con los siguientes encabezados de columna:

- **Campo** hace referencia al nombre del campo que se va a configurar

- **Descripción** proporciona detalles importantes sobre el propósito y el comportamiento del campo

- **Ámbito** indica el ámbito de configuración de Adobe Commerce para la configuración (global, sitio web, tienda)

- **Requerido** indica si se debe configurar un valor en el campo

Para referencia técnica, también puede encontrar la ruta de configuración interna para cada campo.
