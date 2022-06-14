---
title: Varias configuraciones de sitio web y ámbito
description: Configure las existencias y los métodos de entrega para varios sitios web y ámbitos de almacenamiento.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Varias configuraciones de sitio web y ámbito

Puede configurar la variable [Ámbito](https://docs.magento.com/user-guide/configuration/scope.html) para que algunos elementos se adapten a varios sitios web, tiendas y vistas de tiendas:

- [Administrar stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html) por ámbito

- Administrar [!DNL Delivery Methods] por ámbito

Puede asignar existencias a un sitio web o a un ámbito de almacenamiento. A continuación, actualice los orígenes del almacén para establecer los métodos de envío disponibles (entrega a casa, recogida en el almacén).

Después de actualizar la configuración correctamente, las opciones de recogida de la tienda en la página de detalles del producto (PDP) de la tienda de Adobe Commerce solo se pueden seleccionar para los productos disponibles de una fuente de existencias que permita la recogida de la tienda.

## Administrar la configuración de recogida en la tienda

Habilitar o deshabilitar el [!UICONTROL In-Store Pickup] opciones para cada sitio web o ámbito de almacenamiento desde el [Configuraciones de métodos de entrega](enable-general.md#delivery-methods) en el menú

1. Vaya a **[!UICONTROL Stores > Configuration]**.

1. Seleccione el ámbito (Sitio web que desea almacenar) que desea configurar.

1. Con el ámbito seleccionado, vaya a **[!UICONTROL Sales > Delivery Methods]**.

1. Desactivar o habilitar el **[!UICONTROL In-Store Pickup]** Método de entrega.

También puede administrar si la recogida en la parte de la curva o en la tienda está disponible globalmente en esta sección.

Administre el [!UICONTROL In-Store Pickup] y [!UICONTROL Delivery Method] configuración por fuente de existencias. Hay muchas otras configuraciones que ofrecen flexibilidad total con respecto a la implementación.
