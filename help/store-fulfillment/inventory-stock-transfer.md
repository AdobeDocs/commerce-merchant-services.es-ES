---
title: Transferencia de origen de Inventory management
description: '"Configuración de stock para [!DNL Store Fulfillment solution] con Adobe Commerce Inventory management. Configure un nuevo inventario de stock y transfiéralo fuera del stock predeterminado para que pueda asignarlo a fuentes configuradas para habilitar las funciones de recogida de tienda requeridas por la solución de adquisición de tiendas".'
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# Transferencia de origen de Inventory management

El [!DNL Store Fulfillment] utiliza Adobe Commerce Inventory management nativo. De forma predeterminada, la variable [!DNL Commerce] La configuración de asigna todo el inventario web a las existencias predeterminadas, que no pueden tener fuentes adicionales asignadas. Dado que a un sitio web solo se le puede asignar un único inventario de stock, un comerciante debe configurar un nuevo inventario de stock y, opcionalmente, transferir su inventario de origen predeterminado a un origen que esté asignado al ámbito adecuado. A continuación, el origen se puede asignar al nuevo stock.

>[!IMPORTANT]
>
>Los comerciantes deben mantener el origen predeterminado para todos los productos incluidos en los tipos de producto de grupo y paquete. Estos productos necesitan una cantidad de inventario que cumpla el umbral de cantidad mínima para los artículos en stock e incluya un estado de stock de [!UICONTROL In Stock].

Estos cambios de configuración le ayudan a lograr tres cosas:

1. [Transferir inventario al origen](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) para mover el inventario del stock/origen predeterminado al nuevo stock/origen.

1. [Asignar orígenes en lote](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) para añadir las nuevas fuentes para todos los productos.

1. [Actualizaciones masivas completas de los atributos del producto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) para añadir el `Allow Store Pickup` y `Allow Home Delivery` atributos a productos existentes. Cuando se instala la solución, los atributos tienen el valor óptimo *predeterminado* valores. Sin embargo, estos atributos no se aplican a los productos existentes hasta que complete el proceso de actualizaciones masivas.

El inventario se deduce del origen seleccionado (ubicación de tienda minorista o almacén de comercio electrónico). Las fuentes utilizadas como almacenes de comercio electrónico deben asignarse a las mismas existencias que la ubicación de recogida de la tienda y priorizarse antes que las ubicaciones de venta minorista. Para obtener más información, consulte [Priorización de orígenes para una acción](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Para obtener más información sobre la administración del inventario, los inventarios de stock y los orígenes, consulte la documentación del usuario de Adobe Commerce:

- [Administración del inventario](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Gestión de Cantidades de Inventario](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Administración de stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Administración de fuentes](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorización de orígenes para una acción](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Actualizaciones masivas de atributos de producto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Cambiar la configuración para las fuentes de inventario y stock también puede tener un impacto descendente en los sistemas integrados. Asegúrese de comprender cómo afectan los cambios en la configuración de inventario a estos sistemas.
