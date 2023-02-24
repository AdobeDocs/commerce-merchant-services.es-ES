---
title: Administración de existencias de productos
description: Configure los mensajes de stock de comerciantes y las funciones disponibles para los clientes.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Administración de existencias de productos

Como comerciante, puede utilizar Adobe Commerce [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) opciones de origen y existencias. Además, puede usar la solución de satisfacción de la tienda para controlar otras opciones de disponibilidad del inventario relacionadas con las operaciones de la tienda de mercantes.

- Opción de entrega a domicilio de las tiendas de mercadotecnia

- Permitir / Disponible para la recogida de tiendas

- UPC / SKU / otros identificadores de producto únicos

- Umbral fuera de existencias

- Disminución del inventario de ubicaciones específicas según el pedido

Configure las opciones de Product Stock desde el administrador: **[!UICONTROL Catalog > Products > Select Product]**

## **Opciones de existencias de productos**

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Disponible para la entrega a domicilio** | Establece la disponibilidad de Entrega en Casa (Envío desde tienda) para el producto. Cuando está habilitado, cualquier ubicación de tienda de mercantes asignada con inventario disponible para el producto se considera elegible para la opción Entrega a en casa . Cuando esta opción está desactivada, el producto nunca es apto para la entrega a domicilio.</br></br>En la mayoría de los casos, es suficiente configurar esta opción en el nivel de tienda del comerciante. Sin embargo, puede haber casos únicos para productos específicos, como los que están sujetos a restricciones federales de transporte marítimo, que no deberían ser elegibles para la entrega a domicilio. | Sitio web | No |
| **[!UICONTROL Available for Store Pickup]** | Configure la disponibilidad de la colección de almacenamiento para el producto. Cuando está habilitado, cualquier ubicación de tienda de mercantes asignada con inventario disponible para el producto se considera elegible para la opción Recogida de tiendas . Cuando está desactivado, el producto nunca es apto para la recogida en tiendas.</br></br>Esta opción puede resultar útil para rastrear el inventario de comerciantes del sistema que no desea vender desde el canal de comercio electrónico. | Sitio web | No |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Este atributo ya debe existir como atributo de producto y está relacionado con la variable **[!UICONTROL Barcode Source / Barcode Type]** configuración. Este atributo se utiliza para rastrear un código de barras analizable para sus productos. Este valor puede enviarse cuando se envía un pedido a las tiendas de mercadotecnia para su selección. Los asociados del almacén pueden utilizar el valor con la lista de selección para hacer coincidir los productos del estante utilizando un escáner de códigos de barras. | Vista de la tienda | No |

{style=&quot;table-layout:auto&quot;}

## Fuentes para inventario de productos

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Defina el umbral de existencias para el elemento dentro de cada origen. Cuando las existencias se encuentran por debajo del umbral, se considera que no hay existencias en el origen.</br></br>Para utilizar la configuración global de almacenamiento, marque la casilla **[!UICONTROL Use Default]** . | Global | No |
| **[!UICONTROL Allow Store Pickup]** | Establece explícitamente si el artículo está disponible para la recogida en la tienda, independientemente de la configuración de ubicación de la tienda o del inventario disponible.</br></br> Para utilizar la configuración de nivel de producto, desmarque la casilla [!UICONTROL Use Default] y realice la selección. De lo contrario, esta configuración se elige según la configuración de **[!UICONTROL Allow In-Store Pickup]** que se establece en el origen de existencias. | Global | No |

{style=&quot;table-layout:auto&quot;}

