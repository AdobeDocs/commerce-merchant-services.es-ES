---
title: Agregar grupos de campos al esquema XDM
description: Aprenda a añadir grupos de campos específicos de Adobe Commerce a un esquema XDM.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 90356cc593653cf4583da86bc29d69112fc948ba
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Añadir grupos de campos al esquema XDM

Uno de los [pasos de incorporación](overview.md#onboarding-steps) para utilizar el conector del Experience Platform es acceder al espacio de trabajo del conjunto de datos y [crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) que es específico de Adobe Commerce. Al crear ese conjunto de datos, también debe seleccionar un esquema XDM que represente los datos que desea introducir. En este tema se proporcionan los grupos de campos que debe incluir el esquema XDM para recopilar correctamente los datos proporcionados por la tienda de Adobe Commerce [events](events.md).

1. Si aún no tiene un esquema XDM, [crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) uno. De lo contrario, [editar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) el esquema XDM existente en la interfaz de usuario de Adobe Experience Platform.

1. [Agregar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de comercio:

   - Búsqueda del sitio
   - Visitar página web
   - Proceso de inicio de sesión del usuario
   - Claves de referencia
   - Detalles de contacto personal
   - Detalles del comercio
   - Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)
   - Mapa de identidad

   >[!NOTE]
   >
   > No establezca ningún grupo de campos específico de comercio como `Primary identity`. Al hacerlo, identifica el campo como necesario y el Experience Platform espera que ese campo se muestre en todos los eventos. Si ese campo está ausente, se produce un error en el consumo de datos.

   El esquema XDM ahora contiene grupos de campos específicos del comercio, de modo que los datos recopilados de la tienda de comercio [events](events.md) está representado en el XDM.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basado en el esquema creado o actualizado.

   Un conjunto de datos es una construcción de almacenamiento y administración para una recopilación de datos, normalmente una tabla, que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de comercio y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.
