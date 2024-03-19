---
title: Notas de la versión
description: La información de la versión más reciente de [!DNL Data Connection] de Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: ace61fa579404962a9ca3eb97f61ed50bc43db52
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Notas de la versión

>[!IMPORTANT]
>
>Se ha cambiado el nombre del conector del Experience Platform a [!DNL Data Connection].

Estas notas de la versión contienen actualizaciones de [!DNL Data Connection] e incluye:

![Nuevo](../assets/new.svg) - Nuevas funciones
![Fix](../assets/fix.svg) - Correcciones y mejoras
![Error](../assets/bug.svg) - Problemas conocidos

Para ver cambios y correcciones de funciones relacionados con las extensiones utilizadas por [!DNL Data Connection] extensión, consulte **Actualizaciones de servicios compatibles**.

Consulte [Próximas versiones](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para obtener más información sobre las programaciones de versiones y la compatibilidad.

Consulte la documentación para desarrolladores para [descubra qué versiones de Commerce admiten este módulo](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Actualizaciones de servicios compatibles

Estas notas de la versión describen cambios y correcciones de funciones relacionados con las extensiones utilizadas por [!DNL Data Connection] extensión.

+++Actualizaciones de servicios compatibles

_24 de enero de 2024_

![Nuevo](../assets/new.svg) - Se ha actualizado el `data-services-b2b` para incluir un nuevo evento de solicitud llamado [deleteRequisitionList](events.md#deleterequisitionlist) para comerciantes B2B.

_16 de noviembre de 2023_

![Fix](../assets/fix.svg) - Se ha corregido un problema por el que un mensaje de error aparecía incorrectamente cuando realizaba un pedido con varias direcciones de envío.
![Fix](../assets/fix.svg) - Se ha corregido un problema en el [productPageView](events.md#productpageview) evento en el que la variable `productListItems.priceTotal` el campo de evento no convertía el precio después de cambiar la moneda en la vista de la tienda.
![Fix](../assets/fix.svg) - Se ha corregido un problema en el `productListItems` campo de evento en el que el código de divisa no se actualizaba cuando el comerciante cambió de vista de tienda.

_10 de octubre de 2023_

![Nuevo](../assets/new.svg) - Se han añadido nuevos eventos de estado de pedidos: [Pedido facturado](events-backoffice.md#orderinvoiced), [Devolución de artículo de pedido iniciada](events-backoffice.md#orderitemsreturninitiated), y [Devolución de artículo de pedido completada](events-backoffice.md#orderitemreturncompleted).
![Fix](../assets/fix.svg) - Se ha corregido un problema en el cual los cambios de configuración de moneda no se reflejaban en los eventos después de actualizar la caché.
![Fix](../assets/fix.svg) - Se ha corregido un error cuando el mensaje de confirmación de pedido no aparece si la colocación asincrónica de pedidos está activada.
![Nuevo](../assets/new.svg) - Se agregaron datos a [addToRequisitionList](events.md#addtorequisitionlist) para productos simples en la página de la vista Categoría.
![Fix](../assets/fix.svg) - Se ha corregido un problema en el `selectedOptions` datos en la [addToRequisitionList](events.md#addtorequisitionlist) evento cuando se añaden productos desde la página de confirmación del pedido.
![Nuevo](../assets/new.svg) - Se han añadido datos de productos a [addToRequisitionList](events.md#addtorequisitionlist) evento cuando los productos se añaden a la lista de solicitudes desde la página de consulta Categoría.
![Nuevo](../assets/new.svg) - Añadido [addToRequisitionList](events.md#addtorequisitionlist) evento cuando se añaden productos configurables a la lista de solicitudes desde la página Vista de productos.
![Nuevo](../assets/new.svg) - Añadido [addToRequisitionList](events.md#addtorequisitionlist) y [removeFromRequisitionList](events.md#removefromrequisitionlist) eventos en los que la cantidad de productos aumenta o disminuye a partir de una lista de solicitudes.

_10 de junio de 2023_

![Fix](../assets/fix.svg) - Se ha corregido un problema que se producía al `orderId` no pasó en el contexto debido a prefijos en el identificador de pedido de Commerce.
![Fix](../assets/fix.svg) - Configuraciones actualizadas de la política de seguridad de contenido.

_30 de marzo de 2023_

![Nuevo](../assets/new.svg) - Se ha añadido una extensión llamada `data-services-b2b` que incluye [eventos de lista de solicitudes](events.md#b2b-events) para comerciantes B2B.
![Nuevo](../assets/new.svg) - Se ha añadido el `uniqueIdentifier` field a [búsqueda](events.md#search-events) eventos. Este nuevo campo permite a los comerciantes hacer referencias cruzadas entre solicitudes de búsqueda y respuestas de búsqueda.

_12 de octubre de 2022_

![Nuevo](../assets/new.svg) - Se agregaron dos [eventos de tienda](events.md), `openCart` y `removeFromCart`, al SDK y recopilador de eventos de tienda de Adobe Commerce.
![Nuevo](../assets/new.svg) - Se ha añadido la compatibilidad con un [AEM tienda de artículos para el hogar](overview.md#aem-support).

+++

## 3.1.1.

_19 de marzo de 2024_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con PHP 8.3.

## 3.2.0-beta2

_4 de marzo de 2024_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) - Si participa en la versión beta, asegúrese de que `composer.json` tiene lo siguiente en el nivel raíz: ` "minimum-stability": "beta"`.
![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de [añadir atributos personalizados](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de [recopilación y envío de registros de perfil](connect-data.md#send-customer-profile-data) y datos al Experience Platform.

## 3.1.0

_16 de noviembre de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) - Se ha cambiado el nombre del conector del Experience Platform a [!DNL Data Connection].
![Fix](../assets/new.svg) - Se ha agregado la capacidad de registrar la respuesta de error si Adobe IMS no puede generar el token de acceso.
![Fix](../assets/new.svg) - Se ha agregado un mensaje de notificación si intenta sincronizar pedidos históricos pero no ha especificado credenciales de cuenta.

## 3.0.0

_10 de octubre de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

Esta es una versión principal. [Editar](install.md#update-the-data-connection) el archivo root composer.json del proyecto.

![Nuevo](../assets/new.svg) - Disponibilidad general para [enviar pedido histórico](connect-data.md#send-historical-order-data) datos y estado al Experience Platform.
![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con OAuth 2.0 al [configurar](connect-data.md#connect-commerce-data-to-adobe-experience-platform) el [!DNL Data Connection] extensión.
![Nuevo](../assets/new.svg) - Finalizó la compatibilidad con Adobe Commerce 2.4.3.

## 2.3.0

_27 de junio de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de [desactivar el envío de eventos de tienda](connect-data.md#data-collection) al Experience Platform.
![Fix](../assets/fix.svg) - Configuraciones actualizadas de la política de seguridad de contenido.
![Fix](../assets/fix.svg) - Se ha corregido la compatibilidad con eventos de back office en la versión 2.4.7 de Commerce.
![Nuevo](../assets/new.svg) - Se ha añadido un mensaje de notificación sobre la invalidación de la caché al guardar los cambios en la [!DNL Data Connection] formulario de extensión.


## 3.0.0-beta1 (solo interno)

_13 de junio de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - (Beta) Se ha agregado la capacidad de [enviar pedido histórico](connect-data.md#beta-send-historical-order-data) datos y estado al Experience Platform.

## 2.2.0

_30 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Agrupado el `commerce-data-export` y `saas-export` dependencias con el `experience-platform-connector` extensión. Anteriormente, tenía que instalar estas dependencias por separado. Estas dependencias, junto con la configuración del comerciante, permiten el procesamiento en el servidor de [eventos de back office](events-backoffice.md).
![Nuevo](../assets/new.svg) - Se ha añadido un nuevo evento de back office llamado [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28 de febrero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Añadido soporte para PHP 8.2 para todos [!DNL Data Connection] extensiones.

## 2.1.0

_17 de enero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Se ha actualizado el [[!DNL Data Connection] Administrador de extensiones](connect-data.md) para que pueda especificar su propio SDK web de AEP (alloy).
![Fix](../assets/fix.svg) Se ha cambiado a uso de `identityMap` en lugar de `personID` al establecer la identidad principal para cualquier dato insertado en el perímetro de.

## 2.0.1

_10 de noviembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) - Ahora el contexto de Adobe Experience Platform se establece solo después de que el Recopilador de eventos de tienda y el SDK de eventos de tienda se hayan cargado correctamente.

## 2.0.0

_12 de octubre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de especificar su propio SDK web de AEP al [conectador](connect-data.md) Envíe la instancia de Adobe Commerce al Experience Platform.
![Fix](../assets/fix.svg) : Se ha actualizado el requisito de ámbito de secuencia de datos para que las ID de secuencia de datos deban vincularse al sitio web en lugar de a la vista de tienda.

## 1.0.0

_9 de agosto de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) - Versión de disponibilidad general.
