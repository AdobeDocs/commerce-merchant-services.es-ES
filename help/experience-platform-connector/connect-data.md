---
title: Conexión de datos de comercio a Adobe Experience Platform
description: Obtenga información sobre cómo conectar los datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Conexión de datos de Commerce a Adobe Experience Platform {#connectaep}

Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, debe proporcionar un ID de organización y un ID de almacén de datos.

![Configuración del conector del Experience Platform](assets/epc-config.png)

1. Inicie sesión en su cuenta de Adobe en [Conector de Commerce Services](../landing/saas.md#organizationid) y seleccione su ID de organización.

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Ámbito** , seleccione el contexto o el &quot;ámbito&quot; de la vista de tienda.

1. En el **ID de organización** , verá el ID asociado a su cuenta de Adobe Experience Platform, tal como se configura en la variable [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. En el **ID de almacén de datos** , pegue el ID del almacén de datos [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) en Adobe Experience Platform.

## Relación entre el ID de almacén de datos y su vista de almacén de la instancia de comercio

El ID de almacén de datos permite el reenvío de eventos de Adobe Experience Platform a otros productos DX de Adobe y se puede asociar a una vista de tienda específica dentro de la instancia específica de Adobe Commerce. También puede asociar varias vistas de almacén al mismo ID de almacén de datos. Depende de lo que tenga más sentido para su negocio. [Más información](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) acerca del reenvío de eventos.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Vista específica del almacén en la que desea aplicar los ajustes de configuración. |
| ID de organización (global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula la instancia de Adobe Commerce con Adobe Experience Platform. |
| ID de almacén de datos (vista de almacén) | ID que permite el flujo de datos de Adobe Experience Platform a otros productos DX de Adobe. Este ID se puede asociar a una vista de tienda específica dentro de la instancia de Adobe Commerce específica. |

Con la extensión del conector del Experience Platform instalada, el vínculo entre Adobe Commerce y Adobe Experience Platform creado y el ID de almacén de datos especificado, los datos de comercio empiezan a fluir al borde de Adobe Experience Platform y a otros productos DX de Adobe.

>[!NOTE]
>
> La cantidad de tiempo que tardan los datos en fluir desde el borde a otros productos DX de Adobe puede variar.

## Datos de comercio en el extremo

Cuando los datos de comercio se envían al perímetro de Adobe Experience Platform, puede crear informes como los siguientes:

![Datos de comercio en Adobe Experience Manager](assets/aem-data-1.png)
_Datos de comercio en Adobe Experience Manager_
