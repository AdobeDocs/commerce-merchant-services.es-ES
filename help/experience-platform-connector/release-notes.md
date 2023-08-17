---
title: Notas de la versión
description: La información de la versión más reciente del conector de Adobe Experience Platform de Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---

# Notas de la versión

Estas notas de la versión contienen actualizaciones en el conector del Experience Platform e incluyen:

* ![Nuevo](../assets/new.svg) - Nuevas funciones
* ![Fix](../assets/fix.svg) - Correcciones y mejoras
* ![Error](../assets/bug.svg) - Problemas conocidos

Para ver los cambios y correcciones de funciones relacionados con las extensiones utilizadas por el conector del Experience Platform, consulte **Actualizaciones de servicios compatibles**.

Consulte [Próximas versiones](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para obtener más información sobre las programaciones de versiones y la compatibilidad.

Consulte la documentación para desarrolladores para [obtenga información acerca de la compatibilidad del producto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Actualizaciones de servicios compatibles

En estas notas de la versión se describen cambios y correcciones de funciones relacionados con las extensiones que utiliza el conector del Experience Platform.

+++Actualizaciones de servicios compatibles

_10 de junio de 2023_

* ![Fix](../assets/fix.svg) - Se ha corregido un problema que se producía al `orderId` no pasaba en el contexto debido a prefijos en el identificador de pedido de Commerce.
* ![Fix](../assets/fix.svg) - Configuraciones actualizadas de la política de seguridad de contenido.

_30 de marzo de 2023_

* ![Nuevo](../assets/new.svg) - Se ha añadido una nueva extensión llamada `data-services-b2b` que incluye [eventos de lista de solicitudes](events.md#b2b-events) para comerciantes B2B.
* ![Nuevo](../assets/new.svg) - Se ha añadido el `uniqueIdentifier` field a [búsqueda](events.md#search-events) eventos. Este nuevo campo permite a los comerciantes hacer referencia a qué solicitudes de búsqueda corresponden cada respuesta de búsqueda.

_12 de octubre de 2022_

* ![Nuevo](../assets/new.svg) - Se agregaron dos [eventos de tienda](events.md): `openCart` y `removeFromCart` Vaya al SDK y recopilador de eventos de tienda de Adobe Commerce.
* ![Nuevo](../assets/new.svg) - Se ha añadido la compatibilidad con un [AEM tienda de artículos para el hogar](overview.md#aem-support).

+++

## 2.3.0

_27 de junio de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de [desactivar el envío de eventos de tienda](connect-data.md#data-collection) al Experience Platform.
* ![Fix](../assets/fix.svg) - Configuraciones actualizadas de la política de seguridad de contenido.
* ![Fix](../assets/fix.svg) - Se ha corregido la compatibilidad con eventos de back office en la versión 2.4.7 de Commerce.
* ![Nuevo](../assets/new.svg) - Se ha añadido un mensaje de notificación sobre la invalidación de la caché al guardar los cambios en el formulario Conector de Experience Platform.


## 3.0.0-beta1 (solo interno)

_13 de junio de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - (Beta) Se ha agregado la capacidad de [enviar pedido histórico](connect-data.md#beta-send-historical-order-data) datos y estado al Experience Platform. Esta función solo está disponible para usuarios beta. Puede unirse a la versión beta enviando un correo electrónico a la siguiente dirección: [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

## 2.2.0

_30 de marzo de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Agrupado el `commerce-data-export` y `saas-export` dependencias con el `experience-platform-connector` extensión. Anteriormente, tenía que instalar estas dependencias por separado. Estas dependencias, junto con la configuración del comerciante, permiten el procesamiento en el servidor de [eventos de back office](events.md#back-office-events).
* ![Nuevo](../assets/new.svg) - Se ha añadido un nuevo evento de back office llamado [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 de febrero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con PHP 8.2 para todas las extensiones de conector de Experience Platform.

## 2.1.0

_17 de enero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Se ha actualizado el [Administrador del conector del Experience Platform](connect-data.md) para que pueda especificar su propio SDK web de AEP (alloy).
* ![Fix](../assets/fix.svg) Se ha cambiado a uso de `identityMap` en lugar de `personID` al establecer la identidad principal para cualquier dato insertado en el perímetro de.

## 2.0.1

_10 de noviembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Problema corregido](../assets/fix.svg) - Ahora el contexto de Adobe Experience Platform se establece solo después de que el Recopilador de eventos de tienda y el SDK de eventos de tienda se hayan cargado correctamente.

## 2.0.0

_12 de octubre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de especificar su propio SDK web de AEP al [conectador](connect-data.md) Envíe la instancia de Adobe Commerce al Experience Platform.
* ![Fix](../assets/fix.svg) : Se ha actualizado el requisito de ámbito de secuencia de datos para que las ID de secuencia de datos deban vincularse al sitio web en lugar de a la vista de tienda.

## 1.0.0

_9 de agosto de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Nuevo](../assets/new.svg) - Versión de disponibilidad general.
