---
title: Conexión de datos de comercio a Adobe Experience Platform
description: Obtenga información sobre cómo conectar los datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Conexión de datos de Commerce a Adobe Experience Platform {#connectaep}

Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, debe proporcionar un ID de organización y un ID de almacén de datos.

![Configuración del conector del Experience Platform](assets/epc-config.png)

1. Inicie sesión en su cuenta de Adobe en [Conector de Commerce Services](../landing/saas.md#organizationid) y seleccione su ID de organización.

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Ámbito** menú desplegable, establezca el contexto en **Sitio web**.

1. En el **ID de organización** , verá el ID asociado a su cuenta de Adobe Experience Platform, tal como se configura en la variable [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. En el **ID de almacén de datos** , pegue el ID del almacén de datos [created](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) en Adobe Experience Platform.

   >[!NOTE]
   >
   >El ámbito del ID del conjunto de datos debe establecerse en el nivel del sitio web o en un nivel superior. En ese nivel, se utiliza el mismo ID de conjunto de datos para cada sitio web de la jerarquía. No se puede establecer el ámbito del ID del conjunto de datos en el nivel de vista previa.

1. (Opcional) Si no tiene un SDK web de AEP implementado en su sitio, deje este campo en blanco y el conector del Experience Platform lo implemente. De lo contrario, añada el nombre de su SDK web de AEP.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Sitio web específico al que desea aplicar la configuración. |
| ID de organización (global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula la instancia de Adobe Commerce con Adobe Experience Platform. |
| ID de almacén de datos (sitio web) | ID que permite el flujo de datos de Adobe Experience Platform a otros productos DX de Adobe. Este ID debe estar asociado a un sitio web específico de la instancia de Adobe Commerce específica. |
| Nombre del SDK web de AEP (global) | Si no tiene un SDK web de AEP implementado en su sitio, deje este campo en blanco y el conector del Experience Platform lo implemente por usted. Si ya tiene implementado un SDK web de AEP en su sitio, especifique el nombre de ese SDK en este campo. Esto permite que el recopilador de eventos de tienda y el SDK de evento de tienda utilicen su SDK web de AEP en lugar de la versión implementada por el conector del Experience Platform. |

Con la extensión del conector del Experience Platform instalada, el vínculo entre Adobe Commerce y Adobe Experience Platform creado y el ID de almacén de datos especificado, los datos de comercio empiezan a fluir al borde de Adobe Experience Platform y a otros productos DX de Adobe.

>[!NOTE]
>
> La cantidad de tiempo que tardan los datos en fluir desde el borde a otros productos DX de Adobe puede variar.

## Datos de comercio en el extremo

Cuando los datos de comercio se envían al perímetro de Adobe Experience Platform, puede crear informes como los siguientes:

![Datos de comercio en Adobe Experience Manager](assets/aem-data-1.png)
_Datos de comercio en Adobe Experience Manager_
