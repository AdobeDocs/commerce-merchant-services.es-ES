---
title: '[!DNL Live Search] Notas de la versión'
description: '"La información de la última versión de [!DNL Live Search] de Adobe Commerce".'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 94e5d59061477440e62a8f1eb055090e0179d395
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 0%

---

# [!DNL Live Search] Notas de versión

Estas notas de la versión describen las versiones más recientes de [!DNL Live Search] e incluir:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

## [!DNL Live Search] 3.0.1 {#301}

_14 de marzo de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

### Nuevas funciones

* Tarjeta del elemento de producto en la previsualización de reglas
* [Widget de página de lista de productos](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [Opciones de filtrado de categorías](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* Se ha añadido la capacidad de arrastrar y soltar para crear eventos Pin
* Nuevas acciones de anclaje:
   * Fijar en el punto: botón Fijar para crear un evento Fijar con un clic
   * Anclar a la parte superior: coloca el producto en la primera posición
   * Fijar para abajo: coloca el producto en la parte inferior de los resultados
   * Desanclar un evento con un clic
* [Clasificación inteligente para reglas](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### Actualizaciones

* Configurar reglas ahora ordena automáticamente las posiciones de forma única
* Al eliminar un evento existente, ahora se actualiza la previsualización
* Se pueden guardar reglas sin eventos
* Quitar selector de facetas &quot;Seleccionar tipo&quot;
* Se ha añadido el nuevo estado &quot;Edición&quot; para reglas no guardadas

### Correcciones

* Se ha corregido un error del servidor cuando hay un evento no finalizado durante la operación de guardar
* Se ha corregido correctamente la eliminación de un evento específico cuando hay varios eventos
* Se ha corregido el evento de regla existente que no se actualizaba cuando se agregaba un nuevo evento
* Se ha corregido un segundo clic en &quot;Editar&quot; en los detalles, [!DNL Live Search] página que requiere recarga
* Sinónimos: se ha corregido un problema por el que, cuando un usuario hacía clic fuera de la entrada, no podía devolver el enfoque al campo
* Otras correcciones de errores menores y actualizaciones de rendimiento


* ![Error](../assets/bug.svg) - La clasificación por &quot;Recomendado para ti&quot; solo se admite dentro de los widgets de Live Search. No es compatible con la funcionalidad predeterminada de búsqueda de LUMA y PWA.
* ![Error](../assets/bug.svg) : Las facetas de atributos de precio personalizadas no se representan correctamente en LUMA, pero la API filtra correctamente en ellas.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 3.0.1 para acceder a estas funciones.

Se recomienda actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

## Versiones anteriores

+++2.0.5 y anteriores

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

* ![Fix](../assets/fix.svg) : Live Search generaría un error cuando los recursos del SDK no estaban disponibles debido a problemas de red. Este error se ha corregido.

Los comerciantes deben actualizar la versión de la extensión de Live Search >= 2.0.5 para acceder a estas funciones.

Se recomienda actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Live Search ahora admite el filtrado por la configuración &quot;Mostrar productos sin existencias&quot; en el administrador. Si &quot;Mostrar productos sin existencias&quot; está establecido en falso, `inStock = true` se añade al filtro.
![Fix](../assets/fix.svg) Para mejorar el rendimiento, el bloque &quot;Sugerencias&quot; se ha eliminado de la ventana emergente de Live Search. Los datos se siguen pasando a través de GraphQL, en caso de que desee reemplazar la función.
![Fix](../assets/fix.svg) `categories` y `categoryPath` haber reemplazado `categoryIds` para el filtrado de categorías. Obtenga más información en la [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) tema.
![Fix](../assets/fix.svg) Anteriormente, un usuario vinculado a una empresa B2B recibía un código de grupo de clientes incorrecto al realizar búsquedas. Live Search ahora devuelve el valor correcto.
![Fix](../assets/fix.svg) Anteriormente, al buscar un término que no existe, Live Search devolvía un error. Ese error ya está solucionado.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 2.0.4 para acceder a estas funciones.

Se recomienda a los usuarios actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Live Search ahora admite funciones B2B al respetar los permisos de categoría, los catálogos compartidos y los precios específicos de grupos de clientes.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 2.0.3 para acceder a estas funciones.

Se recomienda a los usuarios actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

Existente [!DNL Live Search] las instalaciones deben actualizarse a [!DNL Live Search] 2.0.0 para aprovechar las siguientes nuevas funciones, correcciones y mejoras:

![Nuevo](../assets/new.svg) [!DNL Live Search] ahora es compatible con PHP 8.1 para instalaciones que ejecutan Adobe Commerce 2.4.4.
![Nuevo](../assets/new.svg) El `Magento_ElasticsearchCatalogPermissionsGraphQl` Este módulo se añade a la lista de módulos desactivados durante la instalación.
![Nuevo](../assets/new.svg) El número de líneas disponibles en la [[!DNL storefront popover]](quick-tour.md) se puede configurar desde el *Administrador*.
![Nuevo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidad para [!DNL Live Search].
![Nuevo](../assets/new.svg) El [!DNL Live Search] El proceso de instalación de se actualiza con cambios avanzados en el proceso.
![Fix](../assets/fix.svg) [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) vínculo eliminado del pie de página de la tienda.
![Error](../assets/bug.svg) Los siguientes atributos de producto no son compatibles con [API de Commerce GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) cuando se utiliza en relación con la versión beta de PWA: `description`, `name`, `short_description`
![Error](../assets/bug.svg) La versión beta de PWA para [!DNL Live Search] no admite [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) [Atributo de precio personalizado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) ya no devuelve un error cuando se configura como [faceta]({% link live-search/facets-add.md %}).
![Fix](../assets/fix.svg) Se ha corregido un problema que provocaba que se produjera un error cuando no [símbolo de moneda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) está disponible.
![Fix](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) ahora muestra el [Precio especial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (precio mínimo final) cuando esté disponible.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) [Rendimiento](performance.md) el panel de informes proporciona una perspectiva de los términos de búsqueda que utilizan los compradores.
![Nuevo](../assets/new.svg) [!DNL Live Search] [SDK de eventos de tienda](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) proporciona acceso a una capa de datos común con servicios de publicación de eventos, suscripción y métricas.
![Fix](../assets/fix.svg) El [[!DNL Storefront popover]](storefront-popover.md) tiene un nuevo `active` clase para el `.search-autocomplete` contenedor que controla la visibilidad.
![Fix](../assets/fix.svg) En la tienda, la variable [Términos de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) El vínculo de pie de página se ha eliminado y su caché está deshabilitada para [!DNL Live Search] instalaciones.
![Error](../assets/bug.svg) El parche para el adaptador de búsqueda gestiona los productos duplicados.
![Error](../assets/bug.svg) [!DNL Live Search] admite [de un solo origen](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) ubicaciones de inventario (físicas) con varias (virtuales) [acciones](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Ahora no se admiten varios orígenes de inventario.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) muestra productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda a medida que los compradores escriben consultas en el cuadro Buscar.
![Nuevo](../assets/new.svg) Comercio *Administrador* la sesión permanece abierta durante largos periodos de inactividad del teclado
![Nuevo](../assets/new.svg) [!DNL Live Search] se activa automáticamente después de la incorporación
![Fix](../assets/fix.svg) El tiempo de indexación inicial es inferior a una hora
![Fix](../assets/fix.svg) Actualizaciones incrementales de productos casi en tiempo real (después de la instalación y configuración)
![Fix](../assets/fix.svg) Columnas ordenables en el editor de sinónimos
![Fix](../assets/fix.svg) [!DNL Live Search] ya no genera un error si los criterios de búsqueda contienen un valor de criterio de ordenación vacío
![Fix](../assets/fix.svg) El filtrado de intervalos ya no se interrumpe si los códigos de atributo contienen cadenas &quot;a&quot; o &quot;desde&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Error](../assets/bug.svg) El [!DNL Live Search] El servicio solo admite [divisa base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) de la instalación de Adobe Commerce.
![Error](../assets/bug.svg) Al añadir una faceta, la Fuente de atributos del producto no se actualiza correctamente cuando se establece en `Update on Save`. Para evitar este problema, vaya a [Administración de índices](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) y establezca la Fuente de atributos del producto en `Update by Schedule`.
![Error](../assets/bug.svg) [!DNL Live Search] los sinónimos se definen por vista de tienda, pero actualmente se almacenan por sitio web y se identifican con una combinación de `environmentId` y `storeViewCode`. Como resultado, todos los sitios web y las vistas de tienda dentro de la instalación de Adobe Commerce comparten sinónimos. El conjunto de sinónimos creado más recientemente para la vista de tienda tiene prioridad.
![Error](../assets/bug.svg) Si un término de sinónimo contiene varias palabras, cada palabra se trata como un sinónimo independiente. Por ejemplo, si define &quot;reloj&quot; como sinónimo de &quot;reloj&quot;, tanto &quot;tiempo&quot; como &quot;pieza&quot; se tratan como sinónimos de reloj.

+++

## Documentación

Para obtener más información:

* [Documentación para desarrolladores de Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] en Marketplace](https://marketplace.magento.com/magento-live-search.html)
