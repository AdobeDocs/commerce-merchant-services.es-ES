---
title: Configuración del sistema de asignación y ubicación de almacenamiento
description: Configure un proveedor de distancia para que admita la asignación de ubicación de tienda en la interfaz de usuario de la tienda. Las soluciones Store Fulfillment requieren un proveedor a distancia que habilite la búsqueda en tiendas minoristas y otras capacidades de asignación y programación para el flujo de trabajo de entrega de extremo a extremo.
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Configuración de asignación y ubicación de almacenamiento

Habilite las funciones de asignación y ubicación de tienda para la satisfacción de pedidos configurando una [proveedor de distancia](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) para buscar ubicaciones de tiendas.

**Requisitos**

Durante el proceso de configuración, se proporciona una clave de API de Google para la plataforma Google Maps. Si no tiene uno, [genere uno desde la plataforma Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Para configurar el proveedor de distancia:

1. Desde el **[!UICONTROL Stores > General]** En la configuración de administración, añada la integración de Google Maps para el tipo de contenido Mapa.

   - Ir a **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Añada su clave de API de Google a **[!UICONTROL Google Maps API Key]** field.

1. Desde el **[!UICONTROL Stores > Inventory]** En la configuración de, seleccione el proveedor de distancia para la realización de la tienda.

   - Ir a **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expanda el **[!UICONTROL Distance Provider for Distance Based SSA]** sección.

   - Configure las variables **Proveedor** hasta **Google Map**.

1. Configure las opciones de **[!UICONTROL Google Distance Provider]**.

   - Añada su **Clave de API de Google**.

   - Establecer **[!UICONTROL Computation Mode]** hasta `Driving` y **[!UICONTROL Value]** hasta `Distance`
