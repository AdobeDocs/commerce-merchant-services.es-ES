---
title: Actualizar esquema de registro de perfil para la ingesta de datos de Commerce
description: Obtenga información sobre cómo crear un esquema, un conjunto de datos y un conjunto de datos para recopilar y enviar datos de registro de perfil de Commerce al Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 8456f9b81812cf8ace55b7406d8b4fe50332c17a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Actualizar esquema de registro de perfil para la ingesta de datos de Commerce

>[!NOTE]
>
>Esta función está en versión beta. Si desea unirse al programa beta, envíe una solicitud a [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Cuando los compradores crean un perfil en el sitio de Commerce, se crea un registro de perfil y se capturan datos. Debe crear un esquema y un conjunto de datos específicos para ese registro de perfil para poder transmitir esos datos de perfil al Experience Platform.

1. [Crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) Cree un esquema y establezca la clase en. **Perfil individual**.

1. [Añadir](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de perfil:

   - identityMap
   - Datos demográficos
   - Datos personales de contacto
   - Detalles de cuenta de usuario

1. [Activar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) el esquema para el perfil.

   Cuando un esquema está habilitado para el perfil, cualquier conjunto de datos creado a partir de este esquema participa en Real-Time CDP, que combina datos de fuentes dispares para construir una vista completa de cada cliente.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en función del esquema que haya creado o actualizado.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

Con el esquema y el conjunto de datos configurados para los datos de registro de perfil del cliente, puede [configurar](connect-data.md#data-collection) Cree una instancia de Commerce para recopilar y enviar esos datos a Experience Platform.

Para crear un esquema, un conjunto de datos y un conjunto de datos para los datos de evento de comportamiento y de back office, consulte [actualizar esquemas de eventos de series temporales para la ingesta de datos de Commerce](update-xdm.md).
