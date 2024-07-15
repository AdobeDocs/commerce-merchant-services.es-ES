---
title: Configuración del sistema de asignación y ubicación de almacenamiento
description: Configure un proveedor de distancia para que admita la asignación de ubicación de tienda en la interfaz de usuario de la tienda. Las soluciones Store Fulfillment requieren un proveedor a distancia que habilite la búsqueda en tiendas minoristas y otras capacidades de asignación y programación para el flujo de trabajo de entrega de extremo a extremo.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# Configuración de asignación y ubicación de almacenamiento

Habilite la ubicación de tiendas y las funcionalidades de asignación para la satisfacción de pedidos de tiendas configurando un [proveedor de distancia](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) para buscar ubicaciones de tiendas minoristas.

**Requisitos**

Durante el proceso de configuración, se proporciona una clave de API de Google para la plataforma Google Maps. Si no dispone de uno, [genere uno desde la plataforma Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Para configurar el proveedor de distancia:

1. En la configuración **[!UICONTROL Stores > General]** del administrador, agregue la integración de Google Maps para el tipo de contenido Mapa.

   - Ir a **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Agregue su clave API de Google al campo **[!UICONTROL Google Maps API Key]**.

1. En la configuración **[!UICONTROL Stores > Inventory]** del administrador, seleccione el proveedor de distancia para la realización de la tienda.

   - Ir a **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expanda la sección **[!UICONTROL Distance Provider for Distance Based SSA]**.

   - Establezca **Provider** en **Google Map**.

1. Configure las opciones de **[!UICONTROL Google Distance Provider]**.

   - Agregue su **clave de API de Google**.

   - Establecer **[!UICONTROL Computation Mode]** en `Driving` y **[!UICONTROL Value]** en `Distance`
