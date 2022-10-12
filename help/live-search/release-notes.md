---
title: "[!DNL Live Search] Notas de la versión"
description: '"La información de la última versión de [!DNL Live Search] de Adobe Commerce".'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: ab7bb72826ff3aee1ce93d30dde0a752ef8069de
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 1%

---

# [!DNL Live Search] Notas de la versión

Estas notas de la versión describen las versiones más recientes de [!DNL Live Search] e incluyen:

* ![Nuevo](../assets/new.svg) - Nuevas funciones
* ![Corrección](../assets/fix.svg) - Correcciones y mejoras
* ![Error](../assets/bug.svg) - Problemas conocidos

## [!DNL Live Search] 2.0.3

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

* ![Nuevo](../assets/new.svg) - La búsqueda en directo ahora admite las funciones B2B al cumplir los permisos de categoría, los catálogos compartidos y los precios específicos de los grupos de clientes.

Los comerciantes deben actualizar la versión de la extensión Live Search >= 2.0.3 para acceder a estas funciones.

Recomendamos a los usuarios que actualicen y prueben antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de comprobar los resultados de su entorno de prueba.

>[!NOTE]
>
>El soporte B2B se agregará por etapas a partir del 9 de agosto en los servicios back-end, y se espera que la migración se complete para fines de agosto. Si la extensión Live Search no se actualiza, su tienda seguirá funcionando normalmente pero sin funciones B2B.

### Limitaciones conocidas / Errores:

* ![Error](../assets/bug.svg) : las sugerencias provienen de productos que no se pueden mostrar al grupo de clientes.
* ![Error](../assets/bug.svg) - Los productos no se muestran si no se añaden al &quot;catálogo compartido predeterminado&quot;.
* ![Error](../assets/bug.svg) - El adaptador de búsqueda no representa el bloque &quot;No&quot; para los atributos booleanos de producto aunque los productos estén configurados con el atributo y el bloque &quot;No&quot; se devuelva en la respuesta.
* Aunque algunos productos y consultas pueden devolver resultados que no sean en inglés, actualmente no se admiten consultas en varios idiomas.
* B2B con Live Search para PWA Studio no estará disponible hasta que el PWA Studio añada soporte para él.
* Las anulaciones de productos y la fuente de atributos de producto pueden tener problemas de sincronización que requieren que los administradores se ejecuten `bin/magento indexer:reset` y `bin/magento indexer:reindex` para volver a sincronizar correctamente.
* Si activa o desactiva las funciones Permisos del catálogo/Catálogo compartido/B2B, la variable `catalog_data_exporter_product_overrides` el indexador no se actualiza y se marca incorrectamente como `valid`. Uso `bin/magento saas:resync --feed=productOverrides` para solucionar el problema.

## [!DNL Live Search] 2,0

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

Existente [!DNL Live Search] las instalaciones deben actualizarse a [!DNL Live Search] 2.0.0 para aprovechar las nuevas funciones, correcciones y mejoras siguientes:

* ![Nuevo](../assets/new.svg) - [!DNL Live Search] ahora es compatible con PHP 8.1 para instalaciones que ejecutan Adobe Commerce 2.4.4.
* ![Nuevo](../assets/new.svg) - El `Magento_ElasticsearchCatalogPermissionsGraphQl` se agrega a la lista de módulos que están desactivados durante la instalación.
* ![Nuevo](../assets/new.svg) - El número de líneas disponibles en la variable [[!DNL storefront popover]](quick-tour.md) se puede configurar desde el *Administrador*.
* ![Nuevo](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidad para [!DNL Live Search].
* ![Nuevo](../assets/new.svg) - El [!DNL Live Search] el proceso de instalación se actualiza con cambios de proceso avanzados.
* ![Corrección](../assets/fix.svg) - [Búsqueda avanzada](https://docs.magento.com/user-guide/catalog/search-advanced.html) vínculo eliminado del pie de página de la tienda.
* ![Error](../assets/bug.svg) - Los siguientes atributos de producto no son compatibles con [API de Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql) cuando se utiliza en relación con la versión beta de PWA: `description`, `name`, `short_description`
* ![Error](../assets/bug.svg) - La versión beta de PWA para [!DNL Live Search] no es compatible [gestión de eventos](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

* ![Corrección](../assets/fix.svg) - [Atributo de precio personalizado](https://docs.magento.com/user-guide/stores/attributes-input-types.html) ya no devuelve un error cuando se configura como [faceta]({% vínculo live-search/facets-add.md %}).
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema que provocaba un error al no [símbolo de moneda](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`).
* ![Corrección](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) ahora muestra la variable [Precio especial](https://docs.magento.com/user-guide/catalog/product-price-special.html) (precio final mínimo) cuando esté disponible.

## [!DNL Live Search] 1.3.0

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

* ![Nuevo](../assets/new.svg) - [Rendimiento](performance.md) tablero de informes proporciona información sobre los términos de búsqueda que utilizan los compradores.
* ![Nuevo](../assets/new.svg) - [!DNL Live Search] [SDK de eventos de tienda](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) proporciona acceso a una capa de datos común con servicios de publicación de eventos y suscripción, y métricas.
* ![Corrección](../assets/fix.svg) - El [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) tiene un nuevo `active` para la `.search-autocomplete` contenedor que controla la visibilidad.
* ![Corrección](../assets/fix.svg) - En la tienda, el [Términos de búsqueda](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) el vínculo de pie de página se elimina y su caché se deshabilita para [!DNL Live Search] instalaciones.
* ![Error](../assets/bug.svg) - El parche para el adaptador de búsqueda gestiona los productos duplicados.
* ![Error](../assets/bug.svg) - [!DNL Live Search] support [fuente única](https://docs.magento.com/user-guide/catalog/inventory-sources.html) ubicaciones de inventario (físicas) con múltiples (virtuales) [stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html). En este momento no se admiten varios orígenes de inventario.

## [!DNL Live Search] 1.2.0

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

* ![Nuevo](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) muestra productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda como consultas de tipo comprador en el cuadro Buscar .
* ![Nuevo](../assets/new.svg) - Comercio *Administrador* la sesión permanece abierta durante largos periodos de inactividad del teclado
* ![Nuevo](../assets/new.svg) - [!DNL Live Search] se activa automáticamente después de la incorporación
* ![Corrección](../assets/fix.svg) - El tiempo de indexación inicial es inferior a una hora
* ![Corrección](../assets/fix.svg) - Actualizaciones incrementales del producto casi en tiempo real (después de la instalación y configuración)
* ![Corrección](../assets/fix.svg) - Columnas que se pueden ordenar en el editor de sinónimos
* ![Corrección](../assets/fix.svg) - [!DNL Live Search] ya no genera un error si los criterios de búsqueda contienen un valor de orden vacío
* ![Corrección](../assets/fix.svg) - El filtrado del rango ya no se interrumpe si los códigos de atributo contienen cadenas &quot;to&quot; o &quot;from&quot;

## [!DNL Live Search] 1.1.0

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

* ![Error](../assets/bug.svg) - El [!DNL Live Search] solo admite el [moneda base](https://docs.magento.com/user-guide/stores/currency-configuration.html) de la instalación de Adobe Commerce.
* ![Error](../assets/bug.svg) - Al añadir una faceta, la fuente de atributos del producto no se actualiza correctamente cuando se establece en `Update on Save`. Para evitar este problema, vaya a [Administración de índices](https://docs.magento.com/user-guide/system/index-management.html) y establezca Fuente de atributos del producto en `Update by Schedule`.
* ![Error](../assets/bug.svg) - [!DNL Live Search] los sinónimos se definen por vista de tienda, pero actualmente se almacenan por sitio web y se identifican con una combinación de `environmentId` + `storeViewCode`. Como resultado, todos los sitios web y las vistas de las tiendas de la instalación de Adobe Commerce comparten el mismo conjunto de sinónimos. El conjunto de sinónimos creado más recientemente para la vista de tienda tiene prioridad.
* ![Error](../assets/bug.svg) - Si un término sinónimo contiene varias palabras, cada palabra se trata como un sinónimo separado. Por ejemplo, si define &quot;pieza temporal&quot; como sinónimo de &quot;reloj&quot;, tanto &quot;tiempo&quot; como &quot;pieza&quot; se tratan como sinónimos de reloj.

## Documentación

Para obtener más información:

* [Documentación para desarrolladores de Adobe Commerce](https://devdocs.magento.com/)
* [Guía del usuario de Adobe Commerce](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] en Marketplace](https://marketplace.magento.com/magento-live-search.html)
