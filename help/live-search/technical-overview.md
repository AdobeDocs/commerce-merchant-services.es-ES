---
title: "Información general técnica"
description: "[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 3d2b63280c2a890d7f84208efe3687c0d99e8e38
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Información general técnica

En este tema se analizan los requisitos técnicos y las sugerencias para la instalación y optimización [!DNL Live Search] para Adobe Commerce.

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce local (EE) : 2.4.4+
* Adobe Commerce en la nube (ECE) : 2.4.4+

## Extremo

[!DNL Live Search] se comunica a través del punto final en `https://catalog-service.adobe.io/graphql`.

Como [!DNL Live Search] no tiene acceso a la base de datos de productos completa, [!DNL Live Search] GraphQL y Commerce Core GraphQL no tendrán paridad completa.

Se recomienda llamar directamente a la API de SaaS, específicamente al punto final del servicio de catálogo.

* Obtenga rendimiento y reduzca la carga del procesador omitiendo el proceso de Graphql/base de datos de Commerce
* Aproveche las ventajas de [!DNL Catalog Service] federación a la que llamar [!DNL Live Search], [!DNL Catalog Service], y [!DNL Product Recommendations] desde un único punto final.

En algunos casos de uso, quizá sea mejor llamar a [!DNL Catalog Service] para obtener detalles del producto y casos similares. Consulte [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) para obtener más información.

Si tiene una implementación personalizada sin encabezado, consulte la [!DNL Live Search] implementaciones de referencia:

* [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
* [Campo Live Search](https://github.com/adobe/storefront-search-as-you-type)

AEM CIF Si no utiliza los componentes predeterminados, como el adaptador de búsqueda o los widgets en Luma, o los widgets de la, tenga en cuenta que los eventos (datos del flujo de navegación que alimentan a Adobe Sensei para las métricas de rendimiento y comercialización inteligentes) no funcionarán de forma predeterminada y requieren desarrollo personalizado para implementar eventos sin encabezado.
La versión más reciente de [!DNL Live Search] ya utiliza [!DNL Catalog Service] y las instalaciones [!DNL Catalog Service] módulos.

## Límites y umbrales

Actualmente, la variable [!DNL Live Search] La API de búsqueda/categoría tiene los siguientes límites admitidos y límites estáticos:

### Indexación

* [Índices](indexing.md) hasta 300 atributos de producto por vista de tienda.
* Indexa solo los productos de la base de datos de Adobe Commerce.
* Las páginas de CMS no están indexadas.

### Consulta

* [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación por capas estén fuera de su alcance.
* [!DNL Live Search] utiliza un extremo único de GraphQL para que las consultas admitan características como facetas dinámicas y búsqueda mientras escribe. Aunque es similar a la [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Sin embargo, existen algunas diferencias y es posible que algunos campos no sean totalmente compatibles.

Para restringir los grupos de clientes que utilizan permisos de catálogo:

* Los productos deben asignarse a la categoría Raíz.
* El grupo de clientes &quot;Sin sesión iniciada&quot; debe tener permisos de navegación &quot;Permitir&quot;.
* Para restringir productos al grupo de clientes Sin sesión iniciada, vaya a cada categoría y defina los permisos para cada grupo de clientes.

### Reglas

* Número máximo de comercialización de búsqueda [reglas](rules.md) la vista de tienda es 50.
* La comercialización de categorías puede tener una regla por categoría.
* El número máximo de condiciones por regla es de 10.
* El número máximo de eventos por regla es de 25.

### Sinónimos

* [!DNL Live Search] puede administrar hasta 200 [sinónimos](synonyms.md) por vista de tienda.

## Compatibilidad de idiomas

[!DNL Live Search] los widgets admiten los siguientes idiomas:

|  |  |  |  |
|--- |--- |--- |--- |
| Idioma | Región | Código de idioma | Configuración regional del Magento |
| Búlgaro | Bulgaria | bg_BG | bg_BG |
| Catalán | España | ca_ES | ca_ES |
| Checo | República Checa | cs_CZ | cs_CZ |
| Danés | Dinamarca | da_DK | da_DK |
| Alemán | Alemania | de_DE | de_DE |
| Griego | Grecia | el_GR | el_GR |
| Inglés | Reino Unido | en_GB | en_GB |
| Inglés | Estados Unidos | en_US | en_US |
| Español | España | es_ES | es_ES |
| Estonio | Estonia | et_EE | et_EE |
| Vasco | España | eu_ES | eu_ES |
| persa | Irán | fa_IR | fa_IR |
| Finés | Finlandia | fi_FI | fi_FI |
| francés | Francia | fr_FR | fr_FR |
| Gallego | España | gl_ES | gl_ES |
| Hindi | India | hi_IN | hi_IN |
| Húngaro | Hungría | hu_HU | hu_HU |
| Indonesio | Indonesia | id_ID | id_ID |
| Italiano | Italia | it_IT | it_IT |
| Coreano | Corea del Sur | ko_KR | ko_KR |
| Lituano | Lituania | lt_LT | lt_LT |
| Letón | Letonia | lv_LV | lv_LV |
| Noruego | Noruega Bokmal | nb_NO | nb_NO |
| Neerlandés | Países Bajos | nl_NL | nl_NL |
| Portugués | Brasil | pt_BR | pt_BR |
| Portugués | Portugal | pt_PT | pt_PT |
| Rumano | Rumanía | ro_RO | ro_RO |
| Ruso | Rusia | ru_RU | ru_RU |
| Sueco | Suecia | sv_SE | sv_SE |
| Tailandés | Tailandia | th_TH | th_TH |
| Turco | Turquía | tr_TR | tr_TR |
| Chino | China | zh_CN | zh_Hans_CN |
| Chino | Taiwán | zh_TW | zh_Hant_TW |

Si el widget detecta que la configuración de idioma de administración de Commerce (_Tiendas_ > Configuración > _Configuración_ > _General_ > Opciones de país) coincide con un idioma admitido; el valor predeterminado es ese idioma. De lo contrario, los widgets se muestran en inglés de forma predeterminada.

Los administradores también pueden establecer el idioma de [índice de búsqueda](settings.md#language), para garantizar mejores resultados de búsqueda.

## Comercialización por categorías

[Comercialización por categorías](category-merch.md) le permite configurar [!DNL Live Search] para trabajar en el nivel de categoría del producto.

Este vídeo es una introducción a la comercialización de categorías.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Repositorio de código Widget

El widget de página de lista de productos y el widget de ventana emergente de búsqueda están disponibles para su descarga en el repositorio de github.

Esto permite a los desarrolladores personalizar completamente la funcionalidad y el estilo. Estos usuarios alojan el código ellos mismos sin dejar de aprovechar el [!DNL Live Search] servicio.

* [Widget PLP](https://github.com/adobe/storefront-product-listing-page)
* [Barra de búsqueda](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] admite [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) en Commerce (anteriormente conocido como Multi-Source Inventory o MSI). Para habilitar la compatibilidad total, debe [actualizar](install.md#update) el módulo de dependencia `commerce-data-export` a la versión 102.2.0+.

[!DNL Live Search] devuelve un valor booleano que indica si un producto está disponible en Inventory management, pero no contiene información sobre el origen que tiene las existencias.

## Indexador de precios

Los clientes de Live Search pueden usar el nuevo [Indexador de precios SaaS](../price-index/index.md), que ofrece actualizaciones de precios y tiempos de sincronización más rápidos.

## Tarifa soportada

Los widgets de Live Search admiten la mayoría de los tipos de precio admitidos por Adobe Commerce, pero no todos.

Actualmente, se admiten precios básicos. Los precios avanzados que no son compatibles son:

* Coste
* Precio Mínimo Anunciado

Observe lo siguiente [API Mesh](../catalog-service/mesh.md) para cálculos de precios más complejos.

## soporte de PWA

[!DNL Live Search] funciona con PWA Studio, pero los usuarios pueden ver pequeñas diferencias en comparación con otras implementaciones de Commerce. La funcionalidad básica, como la página de búsqueda y la lista de productos, funciona en Venia, pero es posible que algunas permutaciones de Graphql no funcionen correctamente. También puede haber diferencias de rendimiento.

* La implementación PWA actual de [!DNL Live Search] requiere más tiempo de procesamiento para devolver resultados de búsqueda que [!DNL Live Search] con la tienda nativa de Commerce.
* [!DNL Live Search] el PWA in no admite [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Como resultado, los informes de búsqueda y la comercialización inteligente funcionarán.
* Filtrado directamente en `description`, `name`, `short_description` no es compatible con GraphQL cuando se utiliza con [PWA](https://developer.adobe.com/commerce/pwa-studio/), pero se devuelven con un filtro más general.

Para usar [!DNL Live Search] con PWA Studio, los integradores también deben:

1. Instalar [livessearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Configure las variables `environmentId` en el `storeDetails` objeto.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

## Actualmente no es compatible

* El [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) El módulo está desactivado cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
* [Precios de nivel](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) y [Precios especiales](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) no son compatibles con [!DNL Live Search] Widget de la página de lista de productos y ventana emergente.

## Cookies

[!DNL Live Search] recopila datos de interacción del usuario como parte de su funcionalidad base y se utilizan cookies para almacenar estos datos. Al recopilar cualquier información de usuario, el usuario debe aceptar almacenar cookies. [!DNL Live Search] y [!DNL Product Recommendations] compartir el flujo de datos y, por lo tanto, el mismo mecanismo de cookies. Obtenga más información al respecto en [Controlar restricciones de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
