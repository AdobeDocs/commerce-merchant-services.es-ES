---
title: '''[!DNL Live Search] Notas de la versión'
description: '"La información de la última versión de [!DNL Live Search] de Adobe Commerce".'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: fd3f71a1b3d958f3aa79f0ba6603d30e16e70507
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---

# [!DNL Live Search] Notas de la versión

Estas notas de la versión describen las versiones más recientes de [!DNL Live Search] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Corrección](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos


## Versión principal actual

### [!DNL Live Search] 2.0.5 {#205}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Corrección](../assets/fix.svg) La búsqueda activa generaría un error cuando los recursos del SDK no estaban disponibles debido a problemas de red. Este error se ha corregido.

Los comerciantes deben actualizar la versión de la extensión Live Search >= 2.0.5 para acceder a estas funciones.

Se recomienda a los usuarios que actualicen y prueben antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de comprobar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.4 {#204}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Nuevo](../assets/new.svg) La búsqueda activa ahora admite el filtrado mediante la configuración &quot;Mostrar productos sin existencias&quot; del administrador. Si &quot;Mostrar productos fuera de existencias&quot; está establecido en false, `inStock = true` se agrega al filtro.
![Corrección](../assets/fix.svg) Para mejorar el rendimiento, el bloque &quot;Sugerencias&quot; se ha eliminado de la ventana emergente Búsqueda activa. Los datos aún se pasan a través de GraphQL, en caso de que desee reemplazar la función.
![Corrección](../assets/fix.svg) `categories` y `categoryPath` han reemplazado `categoryIds` para el filtrado de categorías. Obtenga más información en la [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) tema.
![Corrección](../assets/fix.svg) Anteriormente, un usuario vinculado a una empresa B2B recibía un código de grupo de clientes incorrecto al realizar búsquedas. La búsqueda activa ahora devuelve el valor correcto.
![Corrección](../assets/fix.svg) Anteriormente, al buscar un término que no existe, la búsqueda activa devolvía un error. Ese error ya está solucionado.

Los comerciantes deben actualizar la versión de la extensión Live Search >= 2.0.4 para acceder a estas funciones.

Se recomienda a los usuarios que actualicen y prueben antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de comprobar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.3 {#203}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Nuevo](../assets/new.svg) La búsqueda activa ahora admite funciones B2B al cumplir los permisos de categoría, catálogos compartidos y precios específicos de grupos de clientes.

Los comerciantes deben actualizar la versión de la extensión Live Search >= 2.0.3 para acceder a estas funciones.

Se recomienda a los usuarios que actualicen y prueben antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de comprobar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0 {#20}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

Existente [!DNL Live Search] las instalaciones deben actualizarse a [!DNL Live Search] 2.0.0 para aprovechar las nuevas funciones, correcciones y mejoras siguientes:

![Nuevo](../assets/new.svg) [!DNL Live Search] ahora es compatible con PHP 8.1 para instalaciones que ejecutan Adobe Commerce 2.4.4.
![Nuevo](../assets/new.svg) La variable `Magento_ElasticsearchCatalogPermissionsGraphQl` se agrega a la lista de módulos que están desactivados durante la instalación.
![Nuevo](../assets/new.svg) El número de líneas disponibles en la variable [[!DNL storefront popover]](quick-tour.md) se puede configurar desde el *Administrador*.
![Nuevo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidad para [!DNL Live Search].
![Nuevo](../assets/new.svg) La variable [!DNL Live Search] el proceso de instalación se actualiza con cambios de proceso avanzados.
![Corrección](../assets/fix.svg) [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) vínculo eliminado del pie de página de la tienda.
![Error](../assets/bug.svg) Los siguientes atributos de producto no son compatibles con [API de Commerce GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) cuando se utiliza en relación con la versión beta de PWA: `description`, `name`, `short_description`
![Error](../assets/bug.svg) La versión beta de PWA para [!DNL Live Search] no es compatible [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

## Versiones anteriores

++1.3.1 y anteriores

### [!DNL Live Search] 1.3.1 {#131}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Corrección](../assets/fix.svg) [Atributo de precio personalizado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) ya no devuelve un error cuando se configura como [faceta]({% vínculo live-search/facets-add.md %}).
![Corrección](../assets/fix.svg) Se ha corregido un problema que provocaba un error cuando no se mostraba [símbolo de moneda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`).
![Corrección](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) ahora muestra la variable [Precio especial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (precio final mínimo) cuando esté disponible.

### [!DNL Live Search] 1.3.0 {#130}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Nuevo](../assets/new.svg) [Rendimiento](performance.md) tablero de informes proporciona información sobre los términos de búsqueda que utilizan los compradores.
![Nuevo](../assets/new.svg) [!DNL Live Search] [SDK de eventos de tienda](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) proporciona acceso a una capa de datos común con servicios de publicación de eventos y suscripción, y métricas.
![Corrección](../assets/fix.svg) La variable [[!DNL Storefront popover]](storefront-popover.md) tiene un nuevo `active` para la `.search-autocomplete` contenedor que controla la visibilidad.
![Corrección](../assets/fix.svg) En la tienda, el [Términos de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) el vínculo de pie de página se elimina y su caché se deshabilita para [!DNL Live Search] instalaciones.
![Error](../assets/bug.svg) El parche del adaptador de búsqueda gestiona los productos duplicados.
![Error](../assets/bug.svg) [!DNL Live Search] support [fuente única](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) ubicaciones de inventario (físicas) con múltiples (virtuales) [stock](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Ahora no se admiten varios orígenes de inventario.

### [!DNL Live Search] 1.2.0 {#120}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Nuevo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) muestra productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda como consultas de tipo comprador en el cuadro Buscar .
![Nuevo](../assets/new.svg) Comercio *Administrador* la sesión permanece abierta durante largos periodos de inactividad del teclado
![Nuevo](../assets/new.svg) [!DNL Live Search] se activa automáticamente después de la incorporación
![Corrección](../assets/fix.svg) El tiempo de indexación inicial es inferior a una hora
![Corrección](../assets/fix.svg) Actualizaciones incrementales de productos casi en tiempo real (después de la instalación y configuración)
![Corrección](../assets/fix.svg) Columnas que se pueden ordenar en el editor de sinónimos
![Corrección](../assets/fix.svg) [!DNL Live Search] ya no genera un error si los criterios de búsqueda contienen un valor de orden vacío
![Corrección](../assets/fix.svg) El filtrado del rango ya no se rompe si los códigos de atributo contienen cadenas &quot;to&quot; o &quot;from&quot;

### [!DNL Live Search] 1.1.0 {#110}

* Compatible con Adobe Commerce (EE): 2.4.x
* Compatible con Adobe Commerce para Cloud (ECE): 2.4.x
* Estabilidad: Estable

![Error](../assets/bug.svg) La variable [!DNL Live Search] solo admite el [moneda base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) de la instalación de Adobe Commerce.
![Error](../assets/bug.svg) Al añadir una faceta, la fuente de atributos del producto no se actualiza correctamente cuando se establece en `Update on Save`. Para evitar este problema, vaya a [Administración de índices](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) y establezca Fuente de atributos del producto en `Update by Schedule`.
![Error](../assets/bug.svg) [!DNL Live Search] los sinónimos se definen por vista de tienda, pero actualmente se almacenan por sitio web y se identifican con una combinación de `environmentId` + `storeViewCode`. Como resultado, todos los sitios web y las vistas de las tiendas de la instalación de Adobe Commerce comparten el mismo conjunto de sinónimos. El conjunto de sinónimos creado más recientemente para la vista de tienda tiene prioridad.
![Error](../assets/bug.svg) Si un término sinónimo contiene varias palabras, cada palabra se trata como un sinónimo separado. Por ejemplo, si define &quot;pieza temporal&quot; como sinónimo de &quot;reloj&quot;, tanto &quot;tiempo&quot; como &quot;pieza&quot; se tratan como sinónimos de reloj.

+++

## Documentación

Para obtener más información:

* [Documentación para desarrolladores de Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] en Marketplace](https://marketplace.magento.com/magento-live-search.html)
