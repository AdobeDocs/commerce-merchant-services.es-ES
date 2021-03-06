---
title: Notas de la versión
description: La información de la última versión de [!DNL Product Recommendations] de Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 78f469dda853a6f46394d5969f879100cf22f8bb
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# Notas de la versión

Las notas de la versión contienen actualizaciones de las siguientes [!DNL Product Recommendations] módulos:

* A partir de marzo de 2021, [!DNL Product Recommendations] ahora son compatibles con [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) tiendas.
* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Compatibilidad del Creador de páginas con [!DNL Product Recommendations] (opcional): `magento/module-page-builder-product-recommendations`
* Compatibilidad del tipo de recomendación de similitud visual con [!DNL Product Recommendations] (opcional): `magento/module-visual-product-recommendations`

Las notas de la versión incluyen:

* ![Nuevo](../assets/new.svg) - Nuevas funciones
* ![Corrección](../assets/fix.svg) - Correcciones y mejoras

Consulte la documentación para desarrolladores para [obtenga información sobre la compatibilidad del producto](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x y 2.4.x

## 4.0.0 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Agregado [indicadores de disponibilidad](create.md) para ayudarle a visualizar el progreso de la formación de cada tipo de recomendación.
* ![Nuevo](../assets/new.svg) : Esta es una versión principal. Debe [editar](install-configure.md#update) la raíz `composer.json` para su proyecto. Esta versión también requiere que proporcione dos claves de API al instalar y configurar Product Recommendations: [una clave de producción y una clave de entorno limitado](../landing/saas.md).

## 3.3.7 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con PHP 8.1
* ![Nuevo](../assets/new.svg) - Se ha mejorado el cambio de tamaño de la imagen para que las imágenes de distintos tamaños se gestionen de forma más coherente en la plantilla de visualización de referencia

## 3.3.6 de magento/recomendaciones de productos

* ![Nuevo](../assets/new.svg) - Optimizado [!DNL Product Recommendations] metapackage enumerando explícitamente las dependencias

### 3.3.5 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Agregado [Compatibilidad con B2B](onboarding.md#b2bsupport) en Product Recommendations
* ![Nuevo](../assets/new.svg) - Se han añadido nuevas fuentes a [sincronizar datos del catálogo](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) a Commerce Services a través de la línea de comandos

### 3.3.3 de magento/recomendaciones de productos

* ![Nuevo](../assets/new.svg) - Se ha añadido un nuevo [tipos de recomendación](type.md): Conversión (vista al carro de compras), Conversión (vista para comprar) y Vista reciente. Estos nuevos tipos de recomendación están disponibles en la `magento/product-recommendations` módulo 3.2.2 y posterior.
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema por el que el cortafuegos de la aplicación web de Finfinite (WAF) bloqueaba incorrectamente una cookie
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema por el cual los productos asignados a la vista de tienda no predeterminada no se mostraban en la _Vista previa del producto de Recommendations_ al crear una recomendación para esa vista de almacén específica
* ![Corrección](../assets/fix.svg) - Se corrigió un problema en el cual algunos nombres de unidades de recomendación en el Creador de páginas impedía que la unidad de recomendación se mostrara en la tienda

### 3.3.2 de magento/recomendaciones de productos

* ![Corrección](../assets/fix.svg) - Se ha corregido la dependencia que faltaba para la compatibilidad con B2B

### 3.3.1 de magento/recomendaciones de productos

* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con los precios de grupo de clientes B2B. Al configurar un [filtro de precios](filters.md) en una unidad de recomendación, los clientes B2B que hayan iniciado sesión verán el conjunto de precios de grupo de clientes para los productos mostrados.

### 3.3.0 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con la capa de datos del cliente de Adobe para estandarizar la recopilación de datos de comportamiento en todas las funciones y servicios de Adobe Commerce. Consulte la [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) para obtener más información.

### 3.2.6 de magento/recomendaciones de productos

* ![Corrección](../assets/fix.svg) - Se ha corregido un error modal de JavaScript
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema por el que el cortafuegos de la aplicación web de Finfinite (WAF) bloqueaba incorrectamente una cookie

### 3.2.5 de magento/recomendaciones de productos

* ![Nuevo](../assets/new.svg) - Se ha cambiado el nombre de los servicios de Magento a [Servicios de comercio](https://docs.magento.com/user-guide/system/saas.html) y una mayor facilidad de uso en el administrador

### 3.2.4 de magento/recomendaciones de productos

* ![Corrección](../assets/fix.svg) - Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de producto configurables&quot; al indexar atributos de producto

### 3.2.3 de magento/recomendaciones de productos

* ![Corrección](../assets/fix.svg) - Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de producto configurables&quot; durante la sincronización del catálogo
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema en el cual el código de tienda no se establecía correctamente cuando habilitaba la configuración &quot;Añadir código de tienda a URL&quot;
* ![Corrección](../assets/fix.svg) - Se ha mejorado la detección de cambios en la configuración del panel de administración para garantizar que estos cambios se reflejen en los datos de sincronización del catálogo

### 3.2.2 de magento/recomendaciones de productos

* ![Nuevo](../assets/new.svg) - Se ha añadido la capacidad de [vista previa de los resultados de la recomendación](create.md) en el momento de la creación. Esto puede requerir que actualice el módulo a la versión más reciente.
* ![Nuevo](../assets/new.svg) - Se ha añadido la capacidad de [monitorizar y administrar](https://docs.magento.com/user-guide/system/catalog-sync.html) el proceso de sincronización del catálogo desde el administrador.
* ![Nuevo](../assets/new.svg) - Agregado [filtros](filters.md) para controlar qué productos se muestran en recomendaciones.
* ![Nuevo](../assets/new.svg) - Se ha añadido la variable [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.2.1 de magento/module-page-builder-product-recommendations para Page Builder

* ![Nuevo](../assets/new.svg) - Se ha añadido compatibilidad con la versión 3.2.0 o posterior de la variable `magento/product-recommendations` módulo

### 3.1.0 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Se ha añadido la capacidad de [resync](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) su catálogo a los servicios SaaS a través de la línea de comandos.
* ![Nuevo](../assets/new.svg) - Se ha agregado compatibilidad con prefijos de tabla de base de datos
* ![Corrección](../assets/fix.svg) - Se ha eliminado la compatibilidad con PHP 7.1

### 3.0.8 de magento/product-recommendations

* ![Corrección](../assets/fix.svg) - Se ha corregido un problema por el cual se enviaban eventos para la recopilación de datos antes de que se configurara el módulo, lo que provocaba un tráfico no válido

### 3.0.6 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - **(Beta)** Incluye compatibilidad con [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.0.0 de magento/module-visual-product-recommendations

* ![Nuevo](../assets/new.svg) - **(Beta)** [Similitud visual](type.md#visualsim). Con la variable _Similitud visual_ tipo de recomendación, puede implementar una unidad de recomendación en la página de detalles del producto que muestre productos que sean visualmente similares al producto que se está viendo.

### 3.0.5 de magento/product-recommendations

* ![Corrección](../assets/fix.svg) - Se ha corregido el error &quot;No se pueden recuperar los datos de las opciones del producto&quot; que se podía producir durante la exportación del catálogo.
* ![Corrección](../assets/fix.svg) - El símbolo de moneda de la variable _Ingresos_ en la columna _Recommendations de producto_ ahora, el panel refleja correctamente la moneda base configurada.

### 3.0.4 de magento/product-recommendations

* ![Corrección](../assets/fix.svg) - Se ha añadido compatibilidad con Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

* ![Corrección](../assets/fix.svg) - Implementación de símbolos mejorada en la plantilla de tienda

### 1.0.4 de magento/module-page-builder-product-recommendations para Page Builder

* ![Nuevo](../assets/new.svg) - Se ha añadido el nombre de recomendación de producto al editar el tipo de contenido de Page Builder

### 3.0.2 magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Se ha añadido una columna de estado en la cuadrícula al seleccionar Unidades de recomendación en el Creador de páginas
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema con los protocolos http/https incorrectos en las URL de producto e imagen

### 3.0.1 de magento/product-recommendations

Esta es una versión principal. Debe [editar](install-configure.md#update) el archivo raíz composer.json de su proyecto.

* ![Nuevo](../assets/new.svg) - Buscar [!DNL Product Recommendations] desde espacios de datos de SaaS alternativos. Esto le permite usar recomendaciones de productos calculadas en el entorno del producto en otros entornos que no sean de producción. [Cambio de espacios de datos SaaS](settings.md) describe más detalladamente esta función.

* ![Corrección](../assets/fix.svg) - Se ha corregido un problema en el cual se inhibió el cierre de compra para compradores que usaban uBlock Origin
* ![Corrección](../assets/fix.svg) - Se ha corregido un problema que hacía que se enviaran eventos adicionales al carro de compras superfluos

### 1.0.3 de magento/module-page-builder-product-recommendations para Page Builder

* ![Nuevo](../assets/new.svg) - Compatibilidad con el Creador de páginas. Con la integración del Creador de páginas, puede colocar de forma precisa y granulada las unidades de Recomendaciones en cualquier ubicación arbitraria del contenido creado por el Creador de páginas. También puede aplicar estilo a los encabezados y las unidades de recomendación. Vaya a [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) para obtener más información.

### 2.0.0 de magento/product-recommendations

* ![Nuevo](../assets/new.svg) - Versión de disponibilidad general

## Documentación

Para obtener más información sobre [!DNL Product Recommendations] y [!DNL Product Recommendations] desarrollo:

* [Guía del usuario](overview.md)
* [Documentación para desarrolladores](https://devdocs.magento.com/recommendations/product-recs.html)
