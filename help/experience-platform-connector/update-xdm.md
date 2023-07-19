---
title: Adición de grupos de campos al esquema XDM
description: Aprenda a añadir grupos de campos específicos de Adobe Commerce a un esquema XDM.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Adición de grupos de campos al esquema XDM

Uno de los [pasos de incorporación](overview.md#onboarding-steps) para utilizar el conector del Experience Platform es para acceder al espacio de trabajo del conjunto de datos y [crear un flujo de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) que es específico de Adobe Commerce. Al crear ese conjunto de datos, también debe seleccionar un esquema XDM que represente los datos que desea introducir. Este tema le proporciona los grupos de campos que debe incluir el esquema XDM para recopilar correctamente los datos proporcionados por la tienda de Adobe Commerce [eventos](events.md).

1. Si aún no tiene un esquema XDM, [crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) uno. De lo contrario, [editar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Cree su esquema XDM existente en la interfaz de usuario de Adobe Experience Platform.

1. [Añadir](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de Commerce:

   - Búsqueda del sitio
   - Visite la página web
   - Proceso de inicio de sesión del usuario
   - Claves de referencia
   - Datos personales de contacto
   - Detalles de comercio
   - Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)
   - Mapa de identidad

   >[!NOTE]
   >
   > No establezca ningún grupo de campos específico de Commerce como `Primary identity`. Al hacerlo, el campo se identifica como obligatorio y el Experience Platform espera que ese campo esté disponible en cada evento. Si ese campo está ausente, se produce un error en la ingesta de datos.

   El esquema XDM ahora contiene grupos de campos específicos de Commerce para que los datos recopilados de la tienda de Commerce [eventos](events.md) se representa en el XDM.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en función del esquema que haya creado o actualizado.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla, que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Creación de una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de Commerce y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.
