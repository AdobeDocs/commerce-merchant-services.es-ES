---
title: Actualización de esquemas de eventos de series temporales para la ingesta de datos de Commerce
description: Obtenga información sobre cómo crear un esquema, un conjunto de datos y un conjunto de datos para recopilar y enviar datos de evento de series temporales para la ingesta de datos de Commerce.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 90ddfdd41958b254fc0c2f3e0891385193f1bb9c
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Actualización de esquemas de eventos de series temporales para la ingesta de datos de Commerce

Uno de los [pasos de incorporación](overview.md#onboarding-steps) para usar la extensión [!DNL Data Connection] es tener acceso al espacio de trabajo de la secuencia de datos y [crear una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) específica de Adobe Commerce. Al crear ese conjunto de datos, también debe seleccionar un esquema que describa los datos que desea introducir. Ese esquema debe incluir grupos de campos específicos del comercio.

Este artículo proporciona los grupos de campos que debe incluir el esquema para recopilar correctamente los siguientes datos de series temporales proporcionados por los eventos de Adobe Commerce:

- [Comportamiento](events.md): incluye eventos de tienda, perfil, búsqueda y B2B.
- [Back office](events-backoffice.md): incluye el estado del pedido y los eventos de perfil.

Más información sobre [datos de series temporales](data-ingestion.md).

Obtenga más información acerca de los [conceptos básicos de la composición de esquemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Actualizar esquema con datos de comportamiento de series temporales y datos de eventos de back office

En esta sección, aprenderá a actualizar el esquema existente o a crear un esquema para incluir datos de evento de comportamiento y de back office.

>[!NOTE]
>
>Consulte [datos de evento de perfil de serie temporal](#time-series-profile-event-data) para obtener información sobre cómo agregar campos específicos de perfil.

1. Si todavía no tiene un esquema, [cree](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) uno con la clase establecida en **Evento de experiencia**.

1. [Agregue](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de Commerce (o edite el esquema existente y agregue estos grupos de campos):

   - Búsqueda del sitio
   - Visite la página web
   - Proceso de inicio de sesión del usuario
   - Claves de referencia
   - Datos personales de contacto
   - Detalles del canal
   - Detalles de Commerce
   - Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)

   >[!NOTE]
   >
   > No establezca ningún grupo de campos específico de Commerce como `Primary identity`. Al hacerlo, el campo se identifica como obligatorio y el Experience Platform espera que ese campo esté disponible en cada evento. Si ese campo está ausente, se produce un error en la ingesta de datos.

   El esquema ahora contiene grupos de campos específicos de Commerce para que los datos de series temporales recopilados de los eventos de Commerce [comportamiento](events.md) y [back office](events-backoffice.md) se representen en el esquema.

1. [Habilite](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) el esquema para el perfil.

   Cuando un esquema está habilitado para el perfil, cualquier conjunto de datos creado a partir de este esquema participa en Real-Time CDP, que combina datos de fuentes dispares para construir una vista completa de cada cliente.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basado en el esquema que creó o actualizó.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Cree una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) y seleccione el esquema que contiene los grupos de campos específicos de Commerce y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.

Con los esquemas, conjuntos de datos y flujos de datos configurados para los datos de comportamiento y de back office, puede [configurar](connect-data.md#data-collection) su instancia de Commerce para recopilar y enviar esos datos al Experience Platform.

Para incluir la información de perfil del comprador, consulte [datos de evento de perfil de serie temporal](#time-series-profile-event-data).

### Añadir atributos personalizados

Puede utilizar atributos personalizados si desea pasar datos de evento de back office personalizados de la instancia de Commerce al Experience Platform.

Los atributos personalizados se admiten en dos niveles:

- Nivel de pedido
- Nivel de artículo de pedido

>[!NOTE]
>
>Adobe Commerce admite atributos personalizados que tienen un tipo de datos de cadena o matriz de cadenas.

1. Agregue y habilite un módulo adicional en la aplicación [!DNL Commerce]. Ver el siguiente [ejemplo](https://github.com/shiftedreality/beacon-backoffice-custom-events/blob/main/BeaconDemo/Plugin/ModifyOrder.php).

   Debe modificar el código de ejemplo para exponer atributos personalizados adicionales. La implementación varía en función de dónde se almacenan estos atributos y la lógica necesaria para extraerlos.

1. Amplíe el esquema XDM existente. Consulte la siguiente [guía](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) para crear atributos personalizados para los niveles de artículo Pedido y Pedido. El campo ID de inquilino se genera dinámicamente, pero la estructura del campo debe ser similar al ejemplo proporcionado.

   >[!IMPORTANT]
   >
   >Los atributos personalizados de XDM deben coincidir con los atributos enviados desde [!DNL Commerce].

1. Asegúrese de que la secuencia de datos asociada con el esquema XDM sea la misma especificada en la pestaña [Recopilación de datos](connect-data.md#data-collection).

1. Haga clic en **[!UICONTROL Save]** en la ficha **Recopilación de datos** para recuperar los atributos personalizados que haya especificado.

## Datos de evento de perfil de series temporales

Los datos de eventos de perfil de series temporales se generan a partir de los siguientes eventos:

- [&quot;accountCreated&quot;](events-backoffice.md#accountcreated)
- [&quot;accountUpdated&quot;](events-backoffice.md#accountupdated)
- [&quot;accountDeleted&quot;](events-backoffice.md#accountdeleted)

Si desea introducir los datos de evento de perfil del cliente en el Experience Platform, puede actualizar el esquema de Commerce existente y utilizar el mismo conjunto de datos ya configurado, o puede crear un conjunto de datos y un esquema específicos de perfil. Esa decisión se basa en el control de datos de su empresa. Las dos secciones siguientes lo guían a través de cualquier caso.

### Envíe datos de eventos de perfil de series temporales al Experience Platform mediante el conjunto de datos existente

Si desea agregar datos de evento de perfil del lado del servidor [de la serie temporal ](events-backoffice.md#customer-profile-events-server-side) a su secuencia de datos de Commerce existente, agregue el grupo de campos `Demographic Details` al esquema. El esquema ahora contiene los siguientes grupos de campos específicos de Commerce:

- Búsqueda del sitio
- Visite la página web
- Proceso de inicio de sesión del usuario
- Claves de referencia
- Datos personales de contacto
- Detalles del canal
- Detalles de Commerce
- Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)
- Nuevo: **Detalles demográficos**

Con la adición del grupo de campos `Demographic Details` en el esquema de Commerce existente, el conjunto de datos y el conjunto de datos ya asociados con el esquema de Commerce se utilizan para estos datos de perfil de serie temporal.

### Enviar datos de evento de perfil de series temporales al Experience Platform en un conjunto de datos independiente

Si desea agregar [datos de evento de perfil del lado del servidor](events-backoffice.md#customer-profile-events-server-side) a un nuevo esquema y flujo de datos específico del perfil, complete los siguientes pasos.

1. [Cree](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) un esquema y establezca la clase en **Evento de experiencia**.

1. [Agregar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de perfiles:

   - Datos demográficos
   - Datos personales de contacto
   - Detalles del canal
   - Detalles de Commerce

1. [Habilite](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) el esquema para el perfil.

   Cuando un esquema está habilitado para el perfil, cualquier conjunto de datos creado a partir de este esquema participa en Real-Time CDP, que combina datos de fuentes dispares para construir una vista completa de cada cliente.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basado en el esquema que creó.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Cree una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de Commerce y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.

Con los esquemas, conjuntos de datos y flujos de datos configurados para los datos de perfil del cliente, puede [configurar](connect-data.md#data-collection) su instancia de Commerce para recopilar y enviar esos datos al Experience Platform.

Para crear un esquema, un conjunto de datos y una secuencia de datos para los datos de registro de perfil, consulte [enviar datos de registro de perfil al Experience Platform](profile-data.md).
