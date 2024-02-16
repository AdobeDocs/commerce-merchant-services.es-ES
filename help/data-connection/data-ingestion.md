---
title: Tipos de datos de Commerce
description: Conozca los tipos de datos que puede recopilar y enviar al Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Tipos de datos de Commerce

El [Extensión de conexión de datos](overview.md) conecta los datos de Commerce con el Experience Platform. Los datos que se van a usar en el Experience Platform se agrupan en dos tipos de comportamiento: datos de series temporales, que pertenecen al **Evento de experiencia** y registrar datos, que pertenecen a la clase **Perfil individual** clase.

Más información sobre [comportamiento de datos](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) y [clases](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) en Experience Platform.

## Datos de series temporales

Los datos de series temporales proporcionan una instantánea del sistema en el momento en que un sujeto del registro realizó una acción, ya sea directa o indirectamente. Por ejemplo, cuando un comprador explora un producto en su sitio, agrega un producto al carro de compras, realiza un pedido, etc. Los datos de series temporales se incorporan al Experience Platform mediante un esquema que tiene la clase configurada como **Evento de experiencia**.

### Datos de series temporales capturadas

Consulte [eventos de comportamiento](events.md) y [eventos de back office](events-backoffice.md) para conocer qué datos se capturan cuando se genera un evento de serie temporal.

### Esquema necesario para introducir datos de eventos de series temporales

Obtenga información sobre cómo [creación de un esquema](update-xdm.md) que puede introducir datos de eventos de series temporales de comportamiento y back office.

## Registrar datos

>[!NOTE]
>
>Esta función está en versión beta. Si desea unirse al programa beta, envíe una solicitud a [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Los datos de registro proporcionan información sobre los atributos de un asunto. Un sujeto podría ser una organización o un individuo. Por ejemplo, un comprador del sitio crea una cuenta de y que genera datos de registro. Estos datos se incorporan al Experience Platform mediante un esquema que tiene la clase configurada como **Perfil individual**. Puede enviar esos datos de registro al servicio de segmentación y administración de perfiles de Adobe: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### Datos de registro de perfil capturados

Consulte [datos de registro de perfil de cliente](events-profilerecord.md) para saber qué datos se capturan cuando se genera un registro de perfil.

### Esquema necesario para introducir datos de registro de perfil

Obtenga información sobre cómo [creación de un esquema](profile-data.md) que pueden introducir datos de registro de perfil.
