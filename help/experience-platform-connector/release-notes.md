---
title: Notas de la versión
description: La información de la última versión del conector Adobe Experience Platform de Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 735fd14fad22826b04320644e120d296de19a211
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# Notas de la versión

Estas notas de la versión contienen actualizaciones del conector del Experience Platform e incluyen:

* ![Nuevo](../assets/new.svg) - Nuevas funciones
* ![Corrección](../assets/fix.svg) - Correcciones y mejoras
* ![Error](../assets/bug.svg) - Problemas conocidos

Para ver los cambios y correcciones de funciones relacionados con las extensiones utilizadas por el conector del Experience Platform, consulte **Actualizaciones de servicio compatibles**.

Consulte [Próximas versiones](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) para obtener más información sobre los programas de versiones y la asistencia técnica.

Consulte la documentación para desarrolladores para [obtenga información sobre la compatibilidad del producto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Actualizaciones de servicio compatibles

Estas notas de la versión describen cambios y correcciones de funciones relacionados con las extensiones utilizadas por el conector del Experience Platform.

+++Actualizaciones de servicio compatibles

_30 de marzo de 2023_

* ![Nuevo](../assets/new.svg) - Se ha añadido una nueva extensión denominada `data-services-b2b` que incluye [eventos de lista de solicitudes](events.md#b2b-events) para comerciantes B2B
* ![Nuevo](../assets/new.svg) - Se ha añadido la variable `uniqueIdentifier` campo a [búsqueda](events.md#search-events) eventos. Este nuevo campo permite que los comerciantes hagan referencia cruzada a qué solicitudes de búsqueda corresponden a qué respuestas de búsqueda.

_12 de octubre de 2022_

* ![Nuevo](../assets/new.svg) - Se agregaron dos [eventos de tienda](events.md): `openCart` y `removeFromCart` al SDK y el recopilador de eventos de tienda de Adobe Commerce
* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con un [AEM tienda](overview.md#aem-support)

+++

## 2.2.0

_30 de marzo de 2023_

* ![Nuevo](../assets/new.svg) - Paquete el `commerce-data-export` y `saas-export` dependencias con la variable `experience-platform-connector` extensión. Anteriormente, era necesario instalar estas dependencias por separado. Estas dependencias, junto con la configuración del comerciante, permiten el procesamiento en el servidor de [eventos de back office](events.md#back-office-events).
* ![Nuevo](../assets/new.svg) - Se ha añadido un nuevo evento de back office llamado [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 de febrero de 2023_

* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con PHP 8.2 para todos los módulos de conector de Experience Platform

## 2.1.0

_17 de enero de 2023_

* ![Nuevo](../assets/new.svg) - Se ha actualizado el [Administrador del conector del Experience Platform](connect-data.md) para que pueda especificar su propio SDK web de AEP (alloy). Además, se ha agregado una opción para que los comerciantes inscritos en nuestro programa beta de back office envíen [datos de eventos de back office](connect-data.md#data-collection) al borde. Estos eventos contienen [información de estado de pedido](events.md#beta-order-status-events) acerca de un pedido, como si se hubiera realizado, cancelado, reembolsado o enviado un pedido.
* ![Corrección](../assets/fix.svg) Se ha cambiado a `identityMap` en lugar de `personID` al establecer la identidad principal para cualquier dato insertado en el borde.

## 2.0.1

_10 de noviembre de 2022_

* ![Se ha corregido un problema](../assets/fix.svg) - Ahora el contexto de Adobe Experience Platform se establece solo después de que el recopilador de eventos de tienda y el SDK de evento de tienda se hayan cargado correctamente.

## 2.0.0

_12 de octubre de 2022_

* ![Nuevo](../assets/new.svg) - Se ha agregado la capacidad de especificar su propio SDK web de AEP al [conexión](connect-data.md) la instancia de Adobe Commerce al Experience Platform
* ![Corrección](../assets/fix.svg) - Se ha actualizado el requisito del ámbito del conjunto de datos para que los ID del conjunto de datos deban incluirse en el ámbito del sitio web en lugar de en la vista del almacén

## 1.0.0

_9 de agosto de 2022_

* ![Nuevo](../assets/new.svg) - Versión de disponibilidad general

## Documentación

Para obtener más información:

* [Documentación para desarrolladores de Adobe Commerce](https://devdocs.magento.com/)
* [Guía del usuario de Adobe Commerce](https://docs.magento.com/user-guide/)
