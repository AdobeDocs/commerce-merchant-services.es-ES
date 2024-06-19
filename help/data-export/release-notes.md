---
title: "[!DNL SaaS Data Export Extension] Notas de la versión"
description: La información de la versión más reciente de [!DNL Data Export Extension] para Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Notas de la versión de extensión

Estas notas de la versión describen las versiones más recientes de [!DNL SaaS data export] extensión. Se proporciona soporte para la versión publicada principal actual. Las notas de la versión de las versiones anteriores se proporcionan como referencia.

Las actualizaciones incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos


>[!NOTE]
>
>La extensión de exportación de datos SaaS es una colección de módulos que se instalan automáticamente con Live Search, Product Recommendations y el servicio de catálogo. Puede comprobar la versión instalada en el sistema con Composer. En algunos casos, es posible que desee actualizar la extensión de exportación de datos en el sistema para recoger correcciones o nuevas funciones sin actualizar la versión del servicio de Commerce.

## Versión principal actual

## Versión 103.3.5

![Fix](../assets/fix.svg) Establezca la dependencia para la última versión de exportación de datos compatible para el módulo común SaaS.

![Fix](../assets/fix.svg) Reemplazado `ScopeConfig` instancia con `ServiceConfigInterface` para admitir distintas configuraciones de servicio.

## Versión 103.3.4

![Fix](../assets/fix.svg) Mejore el registro de exportación de datos SaaS de Commerce añadiendo más detalles sobre el proceso de reindexación.

## Versión 103.3.3

![Nuevo](../assets/new.svg) La exportación de datos de SaaS ahora almacena en caché los atributos Entity-Attribute-Value (EAV) para la consulta de metadatos de atributos.

![Fix](../assets/fix.svg) Se ha corregido un problema por el que `InventoryStockStatus` la fuente no se guardó durante el reintento si se eliminaba el producto.

## Versión 103.3.2

![Fix](../assets/fix.svg) Se ha corregido un problema por el que `modifiedAt` faltaba el campo en las fuentes de entidades eliminadas.

## Versión 103.3.1

![Fix](../assets/fix.svg) Se ha corregido un problema que provocaba un error `Invalid Template File` mensaje que aparece durante la reindexación de fuentes de productos cuando se instala Page Builder.

## Versión 103.3.0

![Nuevo](../assets/new.svg) Se han migrado tablas de fuentes de exportación inmediatas a la estructura unificada:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Nuevo](../assets/new.svg) Fuentes de catálogo e inventario migradas a la solución de exportación inmediata.

![Nuevo](../assets/new.svg) Se ha cambiado el nombre de los trabajos cron de fuente de exportación inmediata a `*_feed_resend_failed_items`.

![Nuevo](../assets/new.svg) Se ha cambiado el nombre de las tablas de registro de cambios y fuentes de exportación inmediatas.

![Fix](../assets/fix.svg) Establecer `modified_at` campo en los datos de fuente solo para las fuentes que lo requieren.

![Fix](../assets/fix.svg) Modifique la `productAttributes` consulta para recuperar únicamente atributos de producto.

## Versión 103.2.6

![Fix](../assets/fix.svg) Se ha corregido un problema que impedía que las fuentes se reindexaran cuando las tablas tenían un prefijo.

## Versión 103.2.5

![Fix](../assets/fix.svg) Se ha optimizado la consulta Precio.

## Versión 103.2.4

![Fix](../assets/fix.svg) Se ha corregido un estado de Stock incorrecto que se mostraba para un producto cuando Commerce Inventory management estaba habilitado.

## Versión 103.2.3

![Fix](../assets/fix.svg) Precios especiales fijos a nivel de sitio web.
![Fix](../assets/fix.svg) Se ha añadido la exclusión mutua para todas las fuentes que se procesan.


## Versión 103.2.2

![Fix](../assets/fix.svg) Se ha mejorado la estrategia de agrupamiento de fuentes para catálogos grandes. La tabla de lotes ahora se rellena con un número limitado de ID para reducir el uso de memoria.

![Fix](../assets/fix.svg) Se ha eliminado la dependencia de CommerceInventoryDataExporter a los módulos MSI.

![Fix](../assets/fix.svg) Mejorado `commerce-data-exporter` Registros para recopilar más información y organizar por diferentes etapas de exportación.

## Versión 103.2.1

- Versión actualizada publicada.

## Versión 103.2.0

- Se ha agregado la sincronización de datos multiproceso para productos y precios.

