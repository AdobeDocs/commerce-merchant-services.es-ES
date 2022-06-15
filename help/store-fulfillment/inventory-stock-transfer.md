---
title: Transferencia de fuentes de Inventory management
description: '"Configure las existencias para el [!DNL Store Fulfillment solution] con Adobe Commerce Inventory management. Configure un nuevo inventario de existencias y transfiera el inventario de existencias predeterminado para que pueda asignarlo a fuentes configuradas para habilitar las capacidades de Recogida de tiendas requeridas por la solución de entrega de tiendas".'
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Transferencia de fuentes de Inventory management

La variable [!DNL Store Fulfillment] utiliza Adobe Commerce Inventory management nativo. De forma predeterminada, la variable [!DNL Commerce] asigna todo el inventario web al inventario predeterminado, que no puede tener asignados orígenes adicionales. Dado que a un sitio web solo se le puede asignar un único inventario, un comerciante debe configurar un nuevo inventario de existencias y, opcionalmente, transferir su inventario de origen predeterminado a un origen asignado al ámbito apropiado. A continuación, la fuente se puede asignar al nuevo inventario de existencias.

Estos cambios de configuración le ayudan a realizar tres tareas:

1. [Transferir inventario a origen](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) para mover el inventario del origen/stock predeterminado al nuevo origen/stock.

1. [Fuentes de asignación masiva](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) para agregar las nuevas fuentes para todos sus productos.

1. [Completar actualizaciones masivas de atributos de producto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) para agregar la variable `Allow Store Pickup` y `Allow Home Delivery` atributos a productos existentes. Cuando se instala la solución, los atributos tienen la *default* valores. Sin embargo, estos atributos no se aplican a productos existentes hasta que no complete el proceso de actualizaciones masivas.

El inventario se resta del origen seleccionado (ubicación de tienda minorista o almacén de comercio electrónico). Las fuentes utilizadas como almacenes de comercio electrónico deben asignarse a las mismas existencias que la ubicación de recogida de tiendas y priorizarse antes de las ubicaciones de venta minorista. Para obtener más información, consulte [Priorización de fuentes para un inventario](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Para obtener más información sobre la administración de inventarios, existencias y fuentes, consulte la documentación del usuario de Adobe Commerce:

- [Administración de inventario](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Administración de Cantidades de Inventario](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Gestión de stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Administración de fuentes](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorización de fuentes para un inventario](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Actualizaciones masivas para atributos de producto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Cambiar la configuración de las fuentes de inventario y existencias también puede tener un impacto descendente en los sistemas integrados. Asegúrese de comprender cómo afectan los cambios en la configuración del inventario a estos sistemas.
