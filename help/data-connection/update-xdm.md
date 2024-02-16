---
title: Actualización de esquemas de eventos de series temporales para la ingesta de datos comerciales
description: Obtenga información sobre cómo crear un esquema, un conjunto de datos y un conjunto de datos para recopilar y enviar datos de eventos de series temporales para la ingesta de datos de Commerce.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# Actualización de esquemas de eventos de series temporales para la ingesta de datos comerciales

Uno de los [pasos de incorporación](overview.md#onboarding-steps) para usar el [!DNL Data Connection] La extensión de es para acceder al espacio de trabajo del flujo de datos y [crear un flujo de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) que es específico de Adobe Commerce. Al crear ese conjunto de datos, también debe seleccionar un esquema que describa los datos que desea introducir. Ese esquema debe incluir grupos de campos específicos del comercio.

Este artículo proporciona los grupos de campos que debe incluir el esquema para recopilar correctamente los siguientes datos de series temporales proporcionados por los eventos de Adobe Commerce:

- [Comportamiento](events.md) : incluye eventos de tienda, perfil, búsqueda y B2B.
- [Back office](events-backoffice.md) : incluye el estado del pedido y los eventos de perfil.

Más información sobre [datos de series temporales](data-ingestion.md).

Obtenga más información acerca de [conceptos básicos de composición de esquemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Actualizar esquema con datos de comportamiento de series temporales y datos de eventos de back office

En esta sección, aprenderá a actualizar el esquema existente o a crear un esquema para incluir datos de evento de comportamiento y de back office.

>[!NOTE]
>
>Consulte [datos de eventos de perfil de series temporales](#time-series-profile-event-data) para obtener información sobre cómo añadir campos específicos de perfil.

1. Si todavía no tiene un esquema, [crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) uno con la clase configurada como **Evento de experiencia**.

1. [Añadir](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) Agregue los siguientes grupos de campos específicos de Commerce (o edite el esquema existente y agregue estos grupos de campos):

   - Búsqueda del sitio
   - Visite la página web
   - Proceso de inicio de sesión del usuario
   - Claves de referencia
   - Datos personales de contacto
   - Detalles del canal
   - Detalles de comercio
   - Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)

   >[!NOTE]
   >
   > No establezca ningún grupo de campos específico de Commerce como `Primary identity`. Al hacerlo, el campo se identifica como obligatorio y el Experience Platform espera que ese campo esté disponible en cada evento. Si ese campo está ausente, se produce un error en la ingesta de datos.

   El esquema ahora contiene grupos de campos específicos de Commerce para que los datos de series temporales recopilados de Commerce [conductual](events.md) y [back office](events-backoffice.md) events se representa en el esquema.

1. [Activar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) el esquema para el perfil.

   Cuando un esquema está habilitado para el perfil, cualquier conjunto de datos creado a partir de este esquema participa en Real-Time CDP, que combina datos de fuentes dispares para construir una vista completa de cada cliente.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en función del esquema que haya creado o actualizado.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Creación de una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) y seleccione el esquema que contiene los grupos de campos específicos de Commerce y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.

1. **Beta** (Opcional) Puede utilizar atributos personalizados si desea pasar datos de evento de back-office personalizados de su instancia de Commerce al Experience Platform. Esta función está en versión beta. Si desea unirse al programa beta, envíe una solicitud a [dataconnection@adobe.com](mailto:dataconnection@adobe.com). En su solicitud, incluya lo siguiente:

   - Su [ID de organización de Adobe](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Por ejemplo `organization_id@AdobeOrg`.
   - Lista de atributos personalizados de nivel de pedido.
   - Lista de atributos de nivel de artículo de pedido.

   El equipo de Adobe Commerce se pondrá en contacto con usted para proporcionarle más información y los pasos siguientes.

Con los esquemas, conjuntos de datos y flujos de datos configurados para los datos de comportamiento y de back office, puede [configurar](connect-data.md#data-collection) Seleccione la instancia de Commerce para recopilar y enviar esos datos al Experience Platform.

Para incluir la información de perfil del comprador, consulte la siguiente sección.

## Datos de evento de perfil de series temporales

>[!NOTE]
>
>Esta función está en versión beta. Si desea unirse al programa beta, envíe una solicitud a [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Los datos de eventos de perfil de series temporales se generan a partir de los siguientes eventos:

- [&quot;accountCreated&quot;](events-backoffice.md#accountcreated)
- [&quot;accountUpdated&quot;](events-backoffice.md#accountupdated)
- [&quot;accountDeleted&quot;](events-backoffice.md#accountdeleted)

Si desea introducir los datos de evento de perfil del cliente en el Experience Platform, puede actualizar el esquema de Commerce existente y utilizar el mismo conjunto de datos ya configurado, o puede crear un conjunto de datos y un esquema específicos de perfil. Esa decisión se basa en el control de datos de su empresa. Las dos secciones siguientes lo guían a través de cualquier caso.

### Envíe datos de eventos de perfil de series temporales al Experience Platform mediante el conjunto de datos existente

Si desea agregar series temporales [datos de evento del perfil de servidor](events-backoffice.md#customer-profile-events-server-side) a su secuencia de datos de Commerce existente, añada la variable `Demographic Details` grupo de campos al esquema. El esquema ahora contiene los siguientes grupos de campos específicos de Commerce:

- Búsqueda del sitio
- Visite la página web
- Proceso de inicio de sesión del usuario
- Claves de referencia
- Datos personales de contacto
- Detalles del canal
- Detalles de comercio
- Adobe Analytics ExperienceEvent Commerce (si desea enviar datos a Adobe Analytics)
- Nuevo: **Datos demográficos**

Con la adición de `Demographic Details` grupo de campos en el esquema de Commerce existente, el conjunto de datos y el conjunto de datos ya asociados con el esquema de Commerce se utilizan para estos datos de perfil de series temporales.

### Enviar datos de evento de perfil de series temporales al Experience Platform en un conjunto de datos independiente

Si desea agregar [datos de evento del perfil de servidor](events-backoffice.md#customer-profile-events-server-side) para crear un nuevo esquema y conjunto de datos específico para un perfil, complete los siguientes pasos.

1. [Crear](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) Cree un esquema y establezca la clase en. **Evento de experiencia**.

1. [Añadir](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) los siguientes grupos de campos específicos de perfil:

   - Datos demográficos
   - Datos personales de contacto
   - Detalles del canal
   - Detalles de comercio

1. [Activar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) el esquema para el perfil.

   Cuando un esquema está habilitado para el perfil, cualquier conjunto de datos creado a partir de este esquema participa en Real-Time CDP, que combina datos de fuentes dispares para construir una vista completa de cada cliente.

1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basado en el esquema que ha creado.

   Un conjunto de datos es una construcción de almacenamiento y administración para una colección de datos, normalmente una tabla que contiene un esquema (columnas) y campos (filas). Los conjuntos de datos también contienen metadatos que describen varios aspectos de los datos que almacenan.

1. [Creación de una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de Commerce y el conjunto de datos correspondiente.

   El conjunto de datos reenvía los datos recopilados al conjunto de datos. Los datos se representan en el conjunto de datos en función del esquema seleccionado.

Con los esquemas, conjuntos de datos y flujos de datos configurados para los datos de perfil del cliente, puede [configurar](connect-data.md#data-collection) Cree una instancia de Commerce para recopilar y enviar esos datos a Experience Platform.

Para crear un esquema, un conjunto de datos y un conjunto de datos para los datos de registro de perfil, consulte [enviar datos de registro de perfil al Experience Platform](profile-data.md).
