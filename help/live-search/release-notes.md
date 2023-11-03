---
title: "[!DNL Live Search] Notas de la versión"
description: '"La información de la última versión de [!DNL Live Search] de Adobe Commerce".'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 8bac6f053cddd3d47c3aa279abf7c96c79ffcd81
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 0%

---

# [!DNL Live Search] Notas de la versión

Estas notas de la versión describen las versiones más recientes de [!DNL Live Search].
Se proporciona soporte para la versión publicada principal actual. Las notas de la versión de las versiones anteriores se proporcionan como referencia.
Las actualizaciones incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

## Actualizaciones de servicios alojados

Estas notas describen las actualizaciones que se publicaron fuera de una versión con versiones o las mejoras realizadas en el servicio alojado.

_27 de octubre de 2023_

![Nuevo](../assets/new.svg) El [!DNL Live Search] El widget PLP ahora admite muestras de color.

_12 de octubre de 2023_

![Nuevo](../assets/new.svg) Los administradores de Commerce ahora pueden especificar el idioma del índice para [!DNL Live Search]. Consulte [Configuración](settings.md).
![Fix](../assets/fix.svg) Se cambió el nombre de la pestaña &quot;Reglas de búsqueda&quot; a &quot;Buscar comercialización&quot;.

_13 de junio de 2023_

![Fix](../assets/fix.svg) Se ha corregido un problema por el cual algunos caracteres, como comillas o apóstrofos, causaban problemas de clasificación. La reindexación resolverá estos problemas.

_25 de abril de 2023_

![Nuevo](../assets/new.svg) [!DNL Live Search] Los clientes de ahora pueden aprovechar las nuevas [Indexador de precios SaaS](../price-index/index.md).

## [!DNL Live Search] 3.1.1 {#311}

_15 de septiembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

### Nuevas funciones

![Nuevo](../assets/new.svg) Se ha añadido una nueva pestaña de comercialización de categorías. Los usuarios ahora pueden añadir clasificaciones inteligentes y clasificaciones manuales (fijar, aumentar, enterrar, ocultar) por categoría
![Nuevo](../assets/new.svg) Los usuarios pueden agregar una regla de una sola categoría con clasificación inteligente o manual
![Nuevo](../assets/new.svg) Los usuarios ahora pueden agregar reglas de clasificación inteligente a las subcategorías
![Nuevo](../assets/new.svg) Se proporciona información detallada al eliminar subcategorías con clasificación inteligente
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de eliminar reglas para estrategias de clasificación heredadas
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de eliminar reglas para una sola categoría
![Nuevo](../assets/new.svg) Los usuarios ahora pueden buscar por nombre de categoría al agregar una regla
![Nuevo](../assets/new.svg) Con la vista de árbol de categorías, los usuarios ahora pueden ver qué categoría tiene reglas aplicadas.
![Nuevo](../assets/new.svg) La vista previa de categorías solo muestra la categoría seleccionada.
![Nuevo](../assets/new.svg) AEM CIF [Widget emergente](https://github.com/adobe/aem-cif-guides-venia/pull/319) y [Widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEM componentes permiten que los sitios de la comunidad de datos aprovechen las ventajas de [!DNL Live Search].

### Actualizaciones

![Fix](../assets/fix.svg) El tamaño de la tabla de los productos y las fuentes de precios se han reducido considerablemente. Tablas `catalog_data_exporter_products` y `catalog_data_exporter_product_prices` debería ver una reducción sustancial de tamaño.
![Fix](../assets/fix.svg) Se cambia el nombre de la pestaña Reglas a Reglas de búsqueda
![Fix](../assets/fix.svg) Al clasificar por &quot;tendencias&quot;, ahora puede elegir entre: * 3 días (predeterminado) * 14 días * 30 días
![Fix](../assets/fix.svg) Se ha cambiado el nombre de &#39;Eventos&#39; (Amplificar/Fijar/Enterrar/Ocultar) a &#39;Clasificación manual&#39;
![Fix](../assets/fix.svg) Se ha cambiado el nombre de &#39;Tipo de clasificación&#39; a &#39;Clasificación inteligente&#39;
![Fix](../assets/fix.svg) Correcciones de errores menores

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 3.1.1 para acceder a estas funciones.

Después de instalar la versión 3.1.1, se deben habilitar estos nuevos indexadores:

* Fuente de precios de productos
* Fuente de datos del sitio web Ámbitos
* Fuente de datos de grupos de clientes ámbitos

Se recomienda actualizar y probar en control de calidad o ensayo antes de aplicar cambios en producción.

## Versiones anteriores

+++3.1.0 y anteriores

## [!DNL Live Search] 3.1.0 {#310}

_1 de septiembre de 2023_

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

### Actualizaciones

![Fix](../assets/fix.svg) El widget de lista de productos se ha actualizado para usar la variable [API del servicio de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7 de agosto de 2023_

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

### Nuevas funciones

![Nuevo](../assets/new.svg) Los siguientes valores se han agregado a `storeDetails` objeto:

* &quot;Permitir todos los productos por página&quot;
* Tipo de cambio
* &quot;Productos por página en la cuadrícula Valores permitidos&quot;
* &quot;Productos por página en valor predeterminado de cuadrícula&quot;
* Idioma del almacén

### Actualizaciones

![Fix](../assets/fix.svg) Se han agregado módulos de servicio de catálogo al metapaquete para admitir la recuperación avanzada de datos.
![Fix](../assets/fix.svg) El **Mi cuenta** La navegación por páginas ya no desaparece al utilizar el widget de página de lista de productos.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 3.0.2 para acceder a estas funciones.

Se recomienda actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### Limitaciones

El uso del widget de página de lista de productos de Live Search provocará que Google Tag Manager falle. Utilice el adaptador de búsqueda predeterminado si se necesita el Administrador de etiquetas de Google.

## [!DNL Live Search] 3.0.1 {#301}

_14 de marzo de 2023_

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

### Nuevas funciones

![Nuevo](../assets/new.svg) Tarjeta del elemento de producto en la previsualización de reglas
![Nuevo](../assets/new.svg) [Widget de página de lista de productos](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
![Nuevo](../assets/new.svg) [Opciones de filtrado de categorías](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de arrastrar y soltar para crear eventos Pin
![Nuevo](../assets/new.svg) Nuevas acciones de anclaje: * Anclar a punto: botón Anclar para crear un evento de anclaje con un clic * Anclar al principio - Coloca el producto en la primera posición * Anclar al final - Coloca el producto en la parte inferior de los resultados * Desanclar un evento con un clic
![Nuevo](../assets/new.svg) [Clasificación inteligente para reglas](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)
![Nuevo](../assets/new.svg) [!DNL Live Search] ahora admite full [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) en Commerce (anteriormente conocido como Multi-Source Inventory o MSI). Para habilitar la compatibilidad total, debe [actualizar](install.md#update) el módulo de dependencia `commerce-data-export` a la versión 102.2.0+.

### Actualizaciones

![Fix](../assets/fix.svg) Configurar reglas ahora ordena automáticamente las posiciones de forma única
![Fix](../assets/fix.svg) Al eliminar un evento existente, ahora se actualiza la previsualización
![Fix](../assets/fix.svg) Se pueden guardar reglas sin eventos
![Fix](../assets/fix.svg) Quitar selector de facetas &quot;Seleccionar tipo&quot;
![Fix](../assets/fix.svg) Se ha añadido el nuevo estado &quot;Edición&quot; para reglas no guardadas

### Correcciones

![Fix](../assets/fix.svg) Se ha corregido un error del servidor cuando hay un evento no finalizado durante la operación de guardar
![Fix](../assets/fix.svg) Se ha corregido correctamente la eliminación de un evento específico cuando hay varios eventos
![Fix](../assets/fix.svg) Se ha corregido el evento de regla existente que no se actualizaba cuando se agregaba un nuevo evento
![Fix](../assets/fix.svg) Se ha corregido un segundo clic en &quot;Editar&quot; en los detalles, [!DNL Live Search] página que requiere recarga
![Fix](../assets/fix.svg) Sinónimos: se ha corregido un problema por el que, cuando un usuario hacía clic fuera de la entrada, no podía devolver el enfoque al campo
![Fix](../assets/fix.svg) Otras correcciones de errores menores y actualizaciones de rendimiento


![Error](../assets/bug.svg) - La clasificación por &quot;Recomendado para ti&quot; solo se admite dentro de los widgets de Live Search. No es compatible con la funcionalidad de búsqueda predeterminada de Luma y PWA.
![Error](../assets/bug.svg) : Las facetas de atributos de precio personalizados no se representan correctamente en Luma, pero la API filtra correctamente en ellas.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 3.0.1 para acceder a estas funciones.

Se recomienda actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Fix](../assets/fix.svg) : Live Search generaría un error cuando los recursos del SDK no estaban disponibles debido a problemas de red. Este error se ha corregido.

Los comerciantes deben actualizar la versión de la extensión de Live Search >= 2.0.5 para acceder a estas funciones.

Se recomienda actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Nuevo](../assets/new.svg) Live Search ahora admite el filtrado por la configuración &quot;Mostrar productos sin existencias&quot; en el administrador. Si &quot;Mostrar productos sin existencias&quot; está establecido en falso, `inStock = true` se añade al filtro.
![Fix](../assets/fix.svg) Para mejorar el rendimiento, el bloque &quot;Sugerencias&quot; se ha eliminado de la ventana emergente de Live Search. Los datos se siguen pasando a través de GraphQL, en caso de que desee reemplazar la función.
![Fix](../assets/fix.svg) `categories` y `categoryPath` haber reemplazado `categoryIds` para el filtrado de categorías. Obtenga más información en la [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) tema.
![Fix](../assets/fix.svg) Anteriormente, un usuario vinculado a una empresa B2B recibía un código de grupo de clientes incorrecto al realizar búsquedas. Live Search ahora devuelve el valor correcto.
![Fix](../assets/fix.svg) Anteriormente, al buscar un término que no existe, Live Search devolvía un error. Ese error ya está solucionado.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 2.0.4 para acceder a estas funciones.

Se recomienda a los usuarios actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Nuevo](../assets/new.svg) Live Search ahora admite funciones B2B al respetar los permisos de categoría, los catálogos compartidos y los precios específicos de grupos de clientes.

Los comerciantes deben actualizar el [!DNL Live Search] versión de la extensión >= 2.0.3 para acceder a estas funciones.

Se recomienda a los usuarios actualizar y probar antes de pasar a producción. Considere la posibilidad de actualizar el entorno de producción durante las horas de menor actividad después de verificar los resultados de su entorno de prueba.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

Existente [!DNL Live Search] las instalaciones deben actualizarse a [!DNL Live Search] 2.0.0 para aprovechar las siguientes nuevas funciones, correcciones y mejoras:

![Nuevo](../assets/new.svg) [!DNL Live Search] ahora es compatible con PHP 8.1 para instalaciones que ejecutan Adobe Commerce 2.4.4.
![Nuevo](../assets/new.svg) El `Magento_ElasticsearchCatalogPermissionsGraphQl` Este módulo se añade a la lista de módulos desactivados durante la instalación.
![Nuevo](../assets/new.svg) El número de líneas disponibles en la [[!DNL storefront popover]](quick-tour.md) se puede configurar desde el *Administrador*.
![Nuevo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatible con [!DNL Live Search].
![Nuevo](../assets/new.svg) El [!DNL Live Search] El proceso de instalación de se actualiza con cambios avanzados en el proceso.
![Fix](../assets/fix.svg) [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) vínculo eliminado del pie de página de la tienda.
![Error](../assets/bug.svg) Los siguientes atributos de producto no son compatibles con [API de Commerce GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) cuando se utiliza en relación con la versión beta de PWA: `description`, `name`, `short_description`
![Error](../assets/bug.svg) La versión beta de PWA para [!DNL Live Search] no admite [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Fix](../assets/fix.svg) [Atributo de precio personalizado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) ya no devuelve un error cuando se configura como [faceta]({% link live-search/facets-add.md %}).
![Fix](../assets/fix.svg) Se ha corregido un problema que provocaba que se produjera un error cuando no [símbolo de moneda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) está disponible.
![Fix](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) ahora muestra el [Precio especial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (precio mínimo final) cuando esté disponible.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Nuevo](../assets/new.svg) [Rendimiento](performance.md) el panel de informes proporciona una perspectiva de los términos de búsqueda que utilizan los compradores.
![Nuevo](../assets/new.svg) [!DNL Live Search] [SDK de eventos de tienda](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) proporciona acceso a una capa de datos común con servicios de publicación de eventos, suscripción y métricas.
![Fix](../assets/fix.svg) El [[!DNL Storefront popover]](storefront-popover.md) tiene un nuevo `active` clase para el `.search-autocomplete` contenedor que controla la visibilidad.
![Fix](../assets/fix.svg) En la tienda, la variable [Términos de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) El vínculo de pie de página se ha eliminado y su caché está deshabilitada para [!DNL Live Search] instalaciones.
![Error](../assets/bug.svg) El parche para el adaptador de búsqueda gestiona los productos duplicados.
![Error](../assets/bug.svg) [!DNL Live Search] admite [de un solo origen](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) ubicaciones de inventario (físicas) con varias (virtuales) [acciones](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Ahora no se admiten varios orígenes de inventario.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Nuevo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) muestra productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda a medida que los compradores escriben consultas en el cuadro Buscar.
![Nuevo](../assets/new.svg) Comercio *Administrador* la sesión permanece abierta durante largos periodos de inactividad del teclado
![Nuevo](../assets/new.svg) [!DNL Live Search] se activa automáticamente después de la incorporación
![Fix](../assets/fix.svg) El tiempo de indexación inicial es inferior a una hora
![Fix](../assets/fix.svg) Actualizaciones incrementales de productos casi en tiempo real (después de la instalación y configuración)
![Fix](../assets/fix.svg) Columnas ordenables en el editor de sinónimos
![Fix](../assets/fix.svg) [!DNL Live Search] ya no genera un error si los criterios de búsqueda contienen un valor de criterio de ordenación vacío
![Fix](../assets/fix.svg) El filtrado de intervalos ya no se interrumpe si los códigos de atributo contienen cadenas &quot;a&quot; o &quot;desde&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Admitido]{type="Informativo" tooltip="Admitido"}

![Error](../assets/bug.svg) El [!DNL Live Search] El servicio solo admite [divisa base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) de la instalación de Adobe Commerce.
![Error](../assets/bug.svg) Al añadir una faceta, la Fuente de atributos del producto no se actualiza correctamente cuando se establece en `Update on Save`. Para evitar este problema, vaya a [Administración de índices](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) y establezca la Fuente de atributos del producto en `Update by Schedule`.
![Error](../assets/bug.svg) [!DNL Live Search] los sinónimos se definen por vista de tienda, pero actualmente se almacenan por sitio web y se identifican con una combinación de `environmentId` y `storeViewCode`. Como resultado, todos los sitios web y las vistas de tienda dentro de la instalación de Adobe Commerce comparten sinónimos. El conjunto de sinónimos creado más recientemente para la vista de tienda tiene prioridad.
![Error](../assets/bug.svg) Si un término de sinónimo contiene varias palabras, cada palabra se trata como un sinónimo independiente. Por ejemplo, si define &quot;reloj&quot; como sinónimo de &quot;reloj&quot;, tanto &quot;tiempo&quot; como &quot;pieza&quot; se tratan como sinónimos de reloj.

+++

## Documentación

Para obtener más información:

* [Documentación para desarrolladores de Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] en Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
