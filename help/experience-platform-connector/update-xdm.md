---
title: Añadir grupos de campos al esquema XDM
description: Aprenda a añadir grupos de campos específicos de Adobe Commerce a un esquema XDM.
source-git-commit: 4d6a4cec81dbb1e71718066be2ba13a4d292aea3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Añadir grupos de campos al esquema XDM

Uno de los [requisitos previos](overview.md#prereqs) para utilizar el conector del Experience Platform es acceder al espacio de trabajo del conjunto de datos y [crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) que es específico de Adobe Commerce. Al crear ese conjunto de datos, también debe seleccionar un esquema XDM que represente los datos que desea introducir. En este tema se proporcionan los grupos de campos que debe incluir el esquema XDM para recopilar correctamente los datos proporcionados por la tienda de Adobe Commerce [events](events.md).

1. Si aún no tiene un esquema XDM, [crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) uno. De lo contrario, [editar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) el esquema XDM existente en la interfaz de usuario de Adobe Experience Platform.
1. [Agregar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) los siguientes grupos de campos específicos de comercio:

   - Comercio
   - Búsqueda del sitio
   - Visitar página web
   - Proceso de inicio de sesión del usuario
   - Claves de referencia
   - Detalles de contacto personal
   - Detalles del comercio
   - Comercio de eventos de Adobe Analytics Experience (si desea enviar datos a Adobe Analytics)
   - Identificador de persona

   El esquema XDM ahora contiene grupos de campos específicos del comercio, de modo que los datos recopilados de la tienda de comercio [events](events.md) está representado en el XDM.
1. Ahora debería [crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) y seleccione el esquema XDM que contiene los grupos de campos específicos de comercio.
