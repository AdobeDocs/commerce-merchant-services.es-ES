---
title: Conexión de datos de comercio a Adobe Experience Platform
description: Obtenga información sobre cómo conectar los datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 5f8fcc3d6d05cdd854eadd14f53e1ca13625dae3
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Conexión de datos de Commerce a Adobe Experience Platform {#connectaep}

Antes de conectar los datos de Adobe Commerce a Adobe Experience Platform, debe iniciar sesión en la cuenta de Adobe en [Conector de Commerce Services](../landing/saas.md#organizationid). Una vez que inicie sesión y seleccione su ID de organización, puede especificar el ámbito y el ID de conjunto de datos en la variable **Conector del Experience Platform** en la página Administración.

![Configuración del conector del Experience Platform](assets/epc-config.png)

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Ámbito** , seleccione el contexto o el &quot;ámbito&quot; de la vista de tienda.

   El ID de organización de IMS es global. Solo se puede asociar un ID de organización de IMS por instancia de Adobe Commerce.

1. En el **ID de organización IMS** , verá el ID asociado a su cuenta de Adobe Experience Platform, tal como se configura en la variable [Conector de Commerce Services](../landing/saas.md#organizationid).

1. En el **ID de almacén de datos** , pegue el ID del almacén de datos [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) en Adobe Experience Platform.

## Relación entre el ID de almacén de datos y su vista de almacén de instancia de comercio

El ID de almacén de datos permite el reenvío de eventos de Adobe Experience Platform a otros productos DX de Adobe y se puede asociar a una vista de tienda específica dentro de la instancia específica de Adobe Commerce. También puede asociar varias vistas de almacén al mismo ID de almacén de datos. Depende de lo que tenga más sentido para su negocio. [Más información](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) acerca del reenvío de eventos.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Vista específica del almacén en la que desea aplicar los ajustes de configuración. |
| Organización IMS (Global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula la instancia de Adobe Commerce con Adobe Experience Platform. |
| ID de almacén de datos (vista de almacén) | ID que permite el flujo de datos de Adobe Experience Platform a otros productos DX de Adobe. Este ID se puede asociar a un storeView específico de la instancia de Adobe Commerce específica. |

Con la extensión del conector del Experience Platform instalada, el vínculo entre Adobe Commerce y Adobe Experience Platform creado y el ID de almacén de datos especificado, los datos de comercio empiezan a fluir al borde de Adobe Experience Platform y a otros productos DX de Adobe.

## Datos de comercio en el extremo

Cuando los datos de comercio se envían al perímetro de Adobe Experience Platform, puede crear informes como los siguientes:

![Datos de comercio en Adobe Experience Manager](assets/aem-data-1.png)
_Datos de comercio en Adobe Experience Manager_
