---
title: "Introducción a  [!DNL Live Search]"
description: '"Conoce los requisitos del sistema y los pasos de instalación de  [!DNL Live Search] de Adobe Commerce".'
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: aba1f41965e6c430f569adcf9d940cf399b50b73
workflow-type: tm+mt
source-wordcount: '2266'
ht-degree: 0%

---

# Configurado correctamente con [!DNL Live Search]

Adobe Commerce [!DNL Live Search] y [[!DNL Catalog Service]](../catalog-service/guide-overview.md) trabajan juntos para proporcionar una solución de búsqueda eficaz, relevante e intuitiva que permita a sus clientes encontrar rápidamente lo que necesitan exactamente. Específicamente, [!DNL Catalog Service] muestra los datos del catálogo para servicios SaaS, como [!DNL Live Search] para usar.

Este artículo proporciona instrucciones paso a paso para implementar [!DNL Live Search] con [!DNL Catalog Service].

>[!IMPORTANT]
>
>Cuando se trata de buscar sitios, Adobe Commerce le da opciones. Asegúrese de leer [Límites y límites](boundaries-limits.md) antes de implementar, para asegurarse de que [!DNL Live Search] sea adecuado para sus necesidades comerciales.

## Público

Este artículo está dirigido al desarrollador o integrador de sistemas de su equipo, responsable de instalar y configurar la instancia de Adobe Commerce.

## Requisitos

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1/8.2/8.3
- [!DNL Composer]

## Plataformas compatibles

- Adobe Commerce en la nube (ECE) : 2.4.4+
- Adobe Commerce local (EE) : 2.4.4+

## Resumen de flujo de trabajo

En un nivel superior, la incorporación de [!DNL Live Search] requiere que:

![Flujo de trabajo de Live Search](assets/livesearch-workflow.png)

## 1. Instale la extensión [!DNL Live Search]

[!DNL Live Search] está instalado como una extensión desde [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) hasta [Composer](https://getcomposer.org/). Después de instalar y configurar [!DNL Live Search], el Adobe [!DNL Commerce] comienza a compartir los datos de la búsqueda y del catálogo con los servicios SaaS. En este punto, los usuarios de *Admin* pueden configurar, personalizar y administrar las facetas de búsqueda, los sinónimos y las reglas de comercialización.

>[!NOTE]
>
>A partir de [!DNL Live Search] 3.0.2, la extensión [!DNL Catalog Service] está incluida en la instalación de [!DNL Live Search].

1. Confirme que se están ejecutando [trabajos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) y [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management).

   >[!IMPORTANT]
   >
   >Debido al anuncio de fin de soporte de Elasticsearch 7 para agosto de 2023, se recomienda que todos los clientes de Adobe Commerce migren al motor de búsqueda OpenSearch 2.x. Para obtener información sobre cómo migrar el motor de búsqueda durante una actualización de producto, consulte [Migración a OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) en la _Guía de actualización_.

1. Descargue el paquete `live-search` de [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/live-search
   ```

   Si agrega la extensión [!DNL Live Search] a una instalación de **new** Adobe Commerce, ejecute lo siguiente para deshabilitar [!DNL OpenSearch] y los módulos relacionados e instale [!DNL Live Search]. A continuación, continúe con el paso 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Si está agregando la extensión [!DNL Live Search] a una instalación de Adobe Commerce **existente**, ejecute lo siguiente para deshabilitar temporalmente los módulos [!DNL Live Search] que sirven para los resultados de búsqueda de la tienda. A continuación, continúe con el paso 4:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] continúa administrando solicitudes de búsqueda desde la tienda mientras el servicio [!DNL Live Search] sincroniza los datos del catálogo e indexa los productos en segundo plano.

1. Ejecute lo siguiente:

   ```bash
   bin/magento setup:upgrade
   ```

1. Compruebe que los siguientes [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) estén configurados en &quot;Actualizar según lo programado&quot;:

   - Fuente de productos
   - Fuente de variante del producto
   - Fuente de atributos de catálogo
   - Fuente de precios de productos
   - Fuente de datos del sitio web Ámbitos
   - Fuente de datos de grupos de clientes ámbitos
   - Fuente de categorías
   - Fuente de permisos de categoría

1. Si va a instalar [!DNL Live Search] en una nueva instancia de Commerce, ha terminado y puede saltar a [2. Sección Configurar claves API ](#2-configure-api-keys). Si va a instalar Live Search en una instancia de Commerce existente, continúe con el siguiente paso.

1. Ejecute los siguientes comandos para habilitar la extensión [!DNL Live Search], deshabilitar [!DNL OpenSearch] y ejecutar `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

## 2. Configurar las claves API

La clave de API de Adobe Commerce y su clave privada asociada son necesarias para conectar [!DNL Live Search] a una instalación de Adobe Commerce. La clave de API se genera y se mantiene en la cuenta del titular de la licencia [!DNL Commerce], que puede compartirla con el desarrollador o el integrador de sistemas. A continuación, el desarrollador puede crear y administrar los espacios de datos SaaS en nombre del titular de la licencia. Si ya tiene un conjunto de claves API, no es necesario que las vuelva a generar.

Aprenda a configurar las claves API en el artículo [Conector de servicios de Commerce](../landing/saas.md).

## 3. Sincronizar los datos del catálogo {#synchronize-catalog-data}

[!DNL Live Search] mueve los datos del catálogo a la infraestructura SaaS de Adobe. Los datos se indexan y los resultados de búsqueda se envían desde este índice directamente a la tienda. Según el tamaño y la complejidad, la indexación puede tardar entre 30 minutos y un par de horas.

Para comenzar la sincronización inicial de los datos del catálogo con los servicios SaaS, ejecute los siguientes comandos en este orden:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

Al ejecutar estos comandos, comienza la sincronización inicial de los datos del catálogo con los servicios SaaS.

>[!WARNING]
>
> Mientras los datos están indexados y sincronizados, las operaciones de búsqueda y exploración de categorías no están disponibles en la tienda. Según el tamaño del catálogo, el proceso puede tardar al menos una hora desde el momento en que se ejecuta `cron` para sincronizar los datos con los servicios SaaS.

### Monitorización del progreso de sincronización

Puede ver los datos que se sincronizan y comparten mediante [Panel de administración de datos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Este tablero proporciona información valiosa sobre la disponibilidad de los datos de productos para su tienda, lo que garantiza que se puedan mostrar rápidamente a sus compradores.

![Panel de administración de datos](assets/data-management-dashboard.png)

#### Futuras actualizaciones de productos

Después de la sincronización inicial, las actualizaciones incrementales de productos pueden tardar hasta 15 minutos en estar disponibles para la búsqueda de tiendas. Para obtener más información, consulte [Indexación - Actualizaciones de productos de streaming](indexing.md).

## 4. Compruebe que los datos se han exportado {#verify-export}

Para comprobar que los datos del catálogo se han exportado desde la instancia de Adobe Commerce y que están sincronizados para [!DNL Live Search], tiene un par de opciones:

- Busque entradas en las tablas siguientes:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Use [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) con la consulta predeterminada para comprobar lo siguiente:

   - El recuento de productos devuelto está cerca de lo que se espera en la vista de la tienda.
   - Se devuelven las facetas.

Para obtener ayuda adicional, consulte [[!DNL Live Search] catálogo no sincronizado](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) en la Base de conocimiento de soporte técnico.

## 5. Configurar los datos

Configurar correctamente los datos del producto garantiza buenos resultados de búsqueda para los clientes. En esta sección, se habilitan los widgets de la lista de productos y se asignan categorías.

### Activar widgets de lista de productos

Al instalar [!DNL Live Search] 4.0.0+, los widgets de lista de productos se habilitan de forma predeterminada. Cuando los widgets están habilitados, se utiliza un componente de interfaz de usuario diferente para la página de resultados de búsqueda y la página de exploración de categorías Lista de productos. Este componente de interfaz de usuario realiza llamadas directas a la [API del servicio de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), lo que resulta en tiempos de respuesta más rápidos.

Si tiene una versión de [!DNL Live Search] anterior a la 4.0.0 o posterior, debe habilitar manualmente el widget de lista de productos.

1. Desde *Admin*, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En **[!UICONTROL Live Search]**, seleccione **[!UICONTROL Storefront Features]**.
1. Establezca **[!UICONTROL Enable Product Listing Widgets]** en `Yes`.

   ![Habilitar widgets de lista de productos](assets/ls-admin-enable-widget.png)

Al cambiar esta configuración, aparece el mensaje `Page cache is invalidated`. Debe vaciar la caché del Magento para guardar el cambio.

1. Para tener acceso a la página [Administración de caché](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management), siga uno de estos procedimientos:

   - Haga clic en el vínculo **[!UICONTROL Cache Management]** en el mensaje situado encima del área de trabajo.
   - En la barra lateral _Admin_, vaya a **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Seleccione la **configuración** [!UICONTROL Cache Type] y haga clic en **[!UICONTROL Flush Magento Cache]**.

   Los cambios en la tienda son inmediatos después de vaciar la caché.

### Asignar categorías

Los productos devueltos en [!DNL Live Search] deben asignarse a una [categoría](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). En Luma, por ejemplo, los productos se clasifican en categorías como &quot;Hombres&quot;, &quot;Mujeres&quot; y &quot;Equipos&quot;. También se configuran subcategorías para &quot;Tops&quot;, &quot;Bottom&quot; y &quot;Watches&quot;. Esto permite una mejor granularidad al filtrar.

## 6. Compruebe la conexión {#test-connection}

Con los datos del catálogo ahora en SaaS, pruebe para asegurarse de que los datos del producto se devuelvan en los siguientes casos:

- La casilla [!UICONTROL Search] devuelve los resultados correctamente
- La exploración de categorías devuelve los resultados correctamente
- Las facetas están disponibles como filtros en las páginas de resultados de búsqueda

Si todo funciona correctamente, [!DNL Live Search] está instalado, conectado y listo para usarse.

Si encuentra problemas en la tienda, compruebe en el archivo `var/log/system.log` si hay errores de comunicación de API o errores en el lado de los servicios.

Para permitir que [!DNL Live Search] pase a través de un firewall, agregue `commerce.adobe.io` a la lista de permitidos.

## 7. Personalizar para tu tienda

Ha instalado la extensión [!DNL Live Search], ha sincronizado, validado y configurado los datos. Ahora, debe asegurarse de que los widgets de [!DNL Live Search] se ajusten al aspecto y la presentación de su tienda.

Puede aplicar estilo a los widgets de ventana emergente y PLP definiendo reglas CSS personalizadas según sea necesario. Consulte [Elementos emergentes de estilo](storefront-popover.md#styling-popover-example) y [Widget de la página de listado de productos](plp-styling.md#styling-example).

Si desea ampliar la funcionalidad de los widgets, el código fuente de cada uno está disponible en un repositorio público.
En esta situación, puede personalizar JavaScript para sus propias necesidades y, a continuación, alojar su código personalizado en su CDN. Este script personalizado se comunica con el servicio [!DNL Live Search] y devuelve los resultados como de costumbre, lo que le permite controlar la funcionalidad del widget.

- [repositorio de widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Repositorio de la barra de búsqueda](https://github.com/adobe/storefront-search-as-you-type)

## Actualizando [!DNL Live Search] {#update}

Antes de actualizar Live Search, ejecute lo siguiente desde la línea de comandos para comprobar la versión de Live Search instalada:

```bash
composer show magento/module-live-search | grep version
```

Para actualizar [!DNL Live Search], ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/live-search --with-dependencies
```

Para actualizar a una versión principal como de la 3.1.1 a la 4.0.0, edite el archivo raíz [!DNL Composer] `.json` del proyecto de la siguiente manera:

1. Si su versión de `magento/live-search` instalada actualmente es `3.1.1` o inferior y está actualizando a la versión `4.0.0` o superior, ejecute el siguiente comando antes de la actualización:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Para obtener información acerca de la versión de `magento/live-search` instalada actualmente, ejecute el siguiente comando:

   ```bash
   composer show magento/live-search
   ```

1. Abra el archivo raíz `composer.json` y busque `magento/live-search`.

1. En la sección `require`, actualice el número de versión de la siguiente manera:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. Guardar `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Desinstalando [!DNL Live Search] {#uninstall}

Para desinstalar [!DNL Live Search], consulte [Desinstalar módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] paquetes {#packages}

La extensión [!DNL Live Search] consta de los siguientes paquetes:

| Paquete | Descripción |
|--- |--- |
| `module-live-search` | Permite a los comerciantes definir la configuración de búsqueda para facetas, sinónimos, reglas de consulta, etc., y proporciona acceso a un área de reproducción de GraphQL de solo lectura para probar consultas de *Admin*. |
| `module-live-search-adapter` | Enruta las solicitudes de búsqueda de la tienda al servicio [!DNL Live Search] y procesa los resultados en la tienda. <br /> - Examen de categorías - Enruta las solicitudes desde la tienda [navegación superior](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) al servicio de búsqueda.<br /> - Búsqueda global: enruta las solicitudes desde el cuadro de [búsqueda rápida](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) en la parte superior derecha de la tienda al servicio [!DNL Live Search]. |
| `module-live-search-storefront-popover` | Una ventana emergente de &quot;búsqueda mientras escribe&quot; reemplaza la búsqueda rápida estándar y devuelve datos y miniaturas de los resultados de búsqueda principales. |

## Dependencias de [!DNL Live Search] {#dependencies}

[!DNL Composer] captura las siguientes dependencias [!DNL Live Search].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Conceptos avanzados

Las secciones siguientes proporcionan temas más avanzados al utilizar [!DNL Live Search] y [!DNL Catalog Service].

### Extremo

[!DNL Live Search] se comunica a través del extremo en `https://catalog-service.adobe.io/graphql`.

Como [!DNL Live Search] no tiene acceso a la base de datos de productos completa, [!DNL Live Search] GraphQL y Commerce Core GraphQL no tendrán paridad completa.

Se recomienda llamar a las API de SaaS directamente, específicamente al extremo del servicio de catálogo.

- Obtenga rendimiento y reduzca la carga del procesador omitiendo el proceso de Graphql/base de datos de Commerce
- Aproveche la federación [!DNL Catalog Service] para llamar a [!DNL Live Search], [!DNL Catalog Service] y [!DNL Product Recommendations] desde un único extremo.

En algunos casos de uso, es mejor llamar a [!DNL Catalog Service] para obtener detalles del producto y casos similares. Consulte [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) para obtener más información.

Si tiene una implementación personalizada sin encabezado, consulte las implementaciones de referencia de [!DNL Live Search]:

- [widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Campo de Live Search](https://github.com/adobe/storefront-search-as-you-type)

AEM CIF Si no utiliza los componentes predeterminados, como el adaptador de búsqueda o los widgets en Luma, o los widgets de la, los eventos (datos del flujo de navegación que alimentan a Adobe Sensei para las métricas de rendimiento y comercialización inteligentes) no funcionarán de forma predeterminada y requieren desarrollo personalizado para implementar eventos sin encabezado.

La última versión de [!DNL Live Search] ya usa [!DNL Catalog Service].

### Compatibilidad de idiomas

[!DNL Live Search] widgets admiten los siguientes idiomas:

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
| Polaco | Polonia | pl_PL | pl_PL |
| Portugués | Brasil | pt_BR | pt_BR |
| Portugués | Portugal | pt_PT | pt_PT |
| Rumano | Rumanía | ro_RO | ro_RO |
| Ruso | Rusia | ru_RU | ru_RU |
| Sueco | Suecia | sv_SE | sv_SE |
| Tailandés | Tailandia | th_TH | th_TH |
| Turco | Turquía | tr_TR | tr_TR |
| Chino | China | zh_CN | zh_Hans_CN |
| Chino | Taiwán | zh_TW | zh_Hant_TW |

Si el widget detecta que la configuración del idioma de administración de Commerce (_Tiendas_ > Configuración > _Configuración_ > _General_ > Opciones de país) coincide con un idioma compatible, el valor predeterminado será ese idioma. De lo contrario, los widgets se muestran en inglés de forma predeterminada.

Los administradores también pueden establecer el idioma de [índice de búsqueda](settings.md#language) para garantizar mejores resultados de búsqueda.

### Repositorio de código Widget

El widget de página de lista de productos y el widget de campo de Live Search están disponibles para su descarga en el repositorio de github.

Esto permite a los desarrolladores personalizar completamente la funcionalidad y el estilo. Estos usuarios alojan el código ellos mismos sin dejar de aprovechar el servicio [!DNL Live Search].

- [widget PLP](https://github.com/adobe/storefront-product-listing-page)
- [Barra de búsqueda](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] admite las funciones de [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) en Commerce (anteriormente conocido como Multi-Source Inventory o MSI). Para habilitar la compatibilidad total, debe [actualizar](install.md#update) el módulo de dependencia `commerce-data-export` a la versión 102.2.0+.

[!DNL Live Search] devuelve un valor booleano que indica si un producto está disponible en Inventory management, pero no contiene información sobre el origen que tiene las existencias.

### Indexador de precios

Los clientes de Live Search pueden usar el nuevo [indexador de precios SaaS](../price-index/price-indexing.md), que ofrece actualizaciones de cambio de precios y tiempo de sincronización más rápidos.

### Tarifa soportada

Los widgets de Live Search admiten la mayoría de los tipos de precio admitidos por Adobe Commerce, pero no todos.

Actualmente, se admiten precios básicos. Los precios avanzados que no son compatibles son:

- Coste
- Precio Mínimo Anunciado

Consulte [Malla de API](../catalog-service/mesh.md) para cálculos de precios más complejos.

El formato de precio admite la configuración regional en la instancia de Commerce: *Tiendas* > Configuración > *Configuración* > General > *General* > Opciones locales > Configuración regional.

### Compatibilidad con tienda sin encabezado

Opcionalmente, es posible que tenga que instalar el módulo `module-data-services-graphql` que expande la cobertura de GraphQL existente de la aplicación para incluir los campos necesarios para la recopilación de datos de comportamiento de la tienda.

```bash
composer require magento/module-data-services-graphql
```

Este módulo agrega contextos adicionales a las consultas de GraphQL:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### Compatibilidad con B2B

[!DNL Live Search] admite [funcionalidad B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) con [limitaciones](boundaries-limits.md#b2b-and-category-permissions) adicionales.

### soporte de PWA

[!DNL Live Search] funciona con el PWA Studio, pero los usuarios pueden ver pequeñas diferencias en comparación con otras implementaciones de Commerce. La funcionalidad básica, como la página de búsqueda y la lista de productos, funciona en Venia, pero es posible que algunas permutaciones de Graphql no funcionen correctamente. También puede haber diferencias de rendimiento.

- La implementación actual del PWA [!DNL Live Search] requiere más tiempo de procesamiento para devolver resultados de búsqueda que [!DNL Live Search] con la tienda nativa de Commerce.
- [!DNL Live Search] en el PWA no admite [control de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Como resultado, los informes de búsqueda y la comercialización inteligente funcionarán.
- El filtrado directo en `description`, `name`, `short_description` no es compatible con GraphQL cuando se usa con [PWA](https://developer.adobe.com/commerce/pwa-studio/), pero se devuelve con un filtro más general.

Para usar [!DNL Live Search] con el PWA Studio, los integradores también deben:

1. Instalar [livessearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Establezca `environmentId` en el objeto `storeDetails`.

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

### Cookies

[!DNL Live Search] recopila datos de interacción del usuario como parte de su funcionalidad base y se utilizan cookies para almacenar estos datos. Al recopilar cualquier información de usuario, el usuario debe aceptar almacenar cookies. [!DNL Live Search] y [!DNL Product Recommendations] comparten el flujo de datos y, por lo tanto, el mismo mecanismo de cookies. Obtenga más información al respecto en [Controlar restricciones de cookies](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
