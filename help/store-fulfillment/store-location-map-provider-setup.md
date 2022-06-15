---
title: Configuración del sistema de asignación y ubicación del almacén
description: Configure un proveedor de distancia para que admita la asignación de ubicación de tienda en la interfaz de usuario de tienda. Las soluciones de entrega de tiendas requieren un proveedor de distancia para habilitar la búsqueda de tiendas minoristas y otras capacidades de asignación y programación para el flujo de trabajo de cumplimiento de extremo a extremo.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Configuración de ubicación y asignación de tiendas

Habilite la ubicación de la tienda y las funcionalidades de asignación para el cumplimiento de la tienda configurando un [proveedor de distancia](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) para buscar ubicaciones de tiendas minoristas.

**Requisitos**

Durante el proceso de configuración, debe proporcionar una clave de API de Google para la plataforma Google Maps. Si no tiene uno, [genere uno desde la plataforma Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Para configurar el proveedor de distancia:

1. En el [!UICONTROL Stores > General] en Admin, añada la integración de Google Maps para el tipo de contenido Mapa .

   - Vaya a **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Añadir la clave de API de Google a **[!UICONTROL Google Maps API Key]** campo .

1. En el [!UICONTROL Stores > Inventory] en Administración, seleccione el proveedor de distancia para el cumplimiento de la tienda.

   - Vaya a **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expanda el **[!UICONTROL Distance Provider for Distance Based SSA]** para obtener más información.

   - Configure las variables **Proveedor** a **Mapa de Google**.

1. Configure las opciones de **[!UICONTROL Google Distance Provider]**.

   - Agregue la **Clave de API de Google**.

   - Establezca **[!UICONTROL Computation Mode]** a `Driving` y **[!UICONTROL Value]** a `Distance`
