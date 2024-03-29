---
title: "Instalar [!DNL Live Search]"
description: '"Obtenga información sobre cómo instalar, actualizar y desinstalar [!DNL Live Search] de Adobe Commerce".'
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# Instalar [!DNL Live Search]

[!DNL Live Search] se instala como una extensión desde Adobe Marketplace. Después del [!DNL Live Search] El módulo de (con módulos de catálogo como dependencias) está instalado y configurado. [!DNL Commerce] comienza a compartir datos de catálogo y búsqueda con los servicios SaaS. En este punto, *Administrador* los usuarios pueden configurar, personalizar y administrar facetas de búsqueda, sinónimos y reglas de comercialización.

En este tema se proporcionan instrucciones para realizar las siguientes acciones:

* Instalar [!DNL Live Search] (Métodos 1 y 2)
* [Actualizar [!DNL Live Search]](#update)
* [Desinstalar [!DNL Live Search]](#uninstall)

## Antes de empezar {#before-you-begin}

Haga lo siguiente:

1. Confirme que [trabajos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) y [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) se están ejecutando.

1. Elija el método de incorporación que cumpla sus requisitos y siga las instrucciones.

   * [Método 1](#method-1): Instalar sin [!DNL OpenSearch]
   * [Método 2](#method-2): instale con [!DNL OpenSearch] (Sin tiempo de inactividad)

>[!IMPORTANT]
>
>Debido al anuncio de fin de soporte de Elasticsearch 7 para agosto de 2023, se recomienda que todos los clientes de Adobe Commerce migren al motor de búsqueda OpenSearch 2.x. Para obtener información sobre la migración del motor de búsqueda durante la actualización del producto, consulte [Migración a OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) en el _Guía de actualización_.

## Método 1: Instalar sin OpenSearch {#method-1}

Este método de incorporación se recomienda al instalar [!DNL Live Search] a un:

* Nuevo [!DNL Commerce] instalación
* Entorno de ensayo

En esta situación, las operaciones de tienda se interrumpen mientras que la variable [!DNL Live Search] el servicio indexa todos los productos del catálogo. Durante la instalación, [!DNL Live Search] Los módulos de están activados y [!DNL OpenSearch] módulos están desactivados.

1. Instalar Adobe Commerce 2.4.4+ sin [!DNL Live Search].

1. Para descargar `live-search` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/live-search
   ```

1. Ejecute los siguientes comandos para deshabilitar [!DNL OpenSearch] y módulos relacionados, e instale [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Mientras los datos están indexados y sincronizados, las operaciones de búsqueda y exploración de categorías no están disponibles en la tienda. Según el tamaño del catálogo, el proceso puede tardar al menos una hora desde el momento en que se realiza `cron` se ejecuta para sincronizar los datos con [!DNL Live Search] servicios.

1. Compruebe que lo siguiente [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) están configuradas como &quot;Actualizar según lo programado&quot;:

   * Fuente de productos
   * Fuente de variante del producto
   * Fuente de atributos de catálogo
   * Fuente de precios de productos
   * Fuente de datos del sitio web Ámbitos
   * Fuente de datos de grupos de clientes ámbitos
   * Fuente de categorías
   * Fuente de permisos de categoría

1. Configure su [Claves de API](#configure-api-keys) y compruebe que los datos del catálogo estén [sincronizado](#synchronize-catalog-data) con [!DNL Live Search] servicios.

1. Para que las facetas estén disponibles como filtros en la tienda, agregue [facetas](facets-add.md) necesita, de acuerdo con la [requisitos faceteados](facets.md).

   Debe poder agregar facetas después de `cron` ejecuta las fuentes de atributos y exporta los metadatos de atributos.

1. Ejecute el siguiente comando en este orden:

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

1. [Verificar](#verify-export) que los datos se han exportado.

1. [Prueba](#test-the-connection) la conexión desde la tienda.

## Método 2: Instalar con OpenSearch {#method-2}

Este método de incorporación se recomienda al instalar [!DNL Live Search] hasta:

* Una producción existente [!DNL Commerce] instalación

En este escenario, [!DNL OpenSearch] administra temporalmente las solicitudes de búsqueda de la tienda mientras que la variable [!DNL Live Search] El servicio indexa todos los productos en segundo plano, sin interrupciones en las operaciones normales de la tienda. [!DNL OpenSearch] está desactivado y [!DNL Live Search] se activa después de indexar y sincronizar todos los datos del catálogo.

1. Para descargar `live-search` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/live-search
   ```

1. Ejecute el siguiente comando para deshabilitar temporalmente la variable [!DNL Live Search] módulos de que sirven a resultados de búsqueda de tiendas.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] sigue administrando las solicitudes de búsqueda de la tienda mientras la variable [!DNL Live Search] El servicio sincroniza los datos del catálogo e indexa los productos en segundo plano.

1. Compruebe que lo siguiente [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) están configuradas como &quot;Actualizar según lo programado&quot;:

   * Fuente de productos
   * Fuente de variante del producto
   * Fuente de atributos de catálogo
   * Fuente de precios de productos
   * Fuente de datos del sitio web Ámbitos
   * Fuente de datos de grupos de clientes ámbitos

1. Configure su [Claves de API](#configure-api-keys) y compruebe que los datos del catálogo estén [sincronizado](#synchronize-catalog-data) con [!DNL Live Search] servicios.

1. Para que las facetas estén disponibles como filtros en la tienda, agregue [facetas](facets-add.md) necesita, de acuerdo con la [requisitos faceteados](facets.md).

   Debe poder agregar facetas después de `cron` ejecuta las fuentes de productos y atributos, y exporta los metadatos de atributos a [!DNL Live Search] servicios.

1. Ejecute el siguiente comando en este orden:

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

1. Una vez finalizada la sincronización, utilice el [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) con la consulta predeterminada para comprobar lo siguiente:

   * El recuento de productos devuelto está cerca de lo que se espera en la vista de la tienda.
   * Se devuelven las facetas.

1. Ejecute los siguientes comandos para habilitar [!DNL Live Search] módulos, deshabilitar [!DNL OpenSearch], y ejecute `setup`.

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

1. [Prueba](#test-the-connection) la conexión desde la tienda.

## Configuración de claves API {#configure-api-keys}

La clave de la API de Adobe Commerce y su clave privada asociada son necesarias para conectarse [!DNL Live Search] a una instalación de Adobe Commerce. La clave de API se genera y se mantiene en la cuenta de [!DNL Commerce] titular de la licencia, que puede compartirla con el desarrollador o SI. A continuación, el desarrollador puede crear y administrar los espacios de datos SaaS en nombre del titular de la licencia.  Si ya tiene un conjunto de claves API, no es necesario que las vuelva a generar.

### Titular de la licencia Adobe Commerce

Para generar una clave API y una clave privada, consulte [Conector de Commerce Services](../landing/saas.md).

### Desarrollador de Adobe Commerce o SI

El desarrollador o SI configura el espacio de datos de SaaS como se describe en la *Servicios de Commerce* de la configuración. En el *Administrador*, Commerce Services está disponible en *Configuración* barra lateral cuando hay un módulo SaaS instalado.

## Sincronización de datos de catálogo {#synchronize-catalog-data}

[!DNL Live Search] requiere datos de productos sincronizados para operaciones de búsqueda y datos de atributos sincronizados para configurar facetas. La sincronización inicial entre el catálogo de productos y el servicio de catálogo comienza cuando [!DNL Live Search] se conecta primero. Según el método de instalación y el tamaño del catálogo, los datos pueden tardar hasta 30 minutos en exportarse e indexarse mediante [!DNL Live Search]. La lista de datos sincronizados y compartidos con el servicio de catálogo se encuentra en el esquema, que se define en:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verificar exportación {#verify-export}

Para comprobar que los datos del catálogo se han exportado desde la instancia de Adobe Commerce y que están sincronizados para [!DNL Live Search], busque entradas en las tablas siguientes:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Para obtener ayuda adicional, consulte [[!DNL Live Search] catálogo no sincronizado](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) en la Base de conocimiento de asistencia.

### Futuras actualizaciones de productos

Después de la sincronización inicial, las actualizaciones incrementales de productos pueden tardar hasta 15 minutos en estar disponibles para la búsqueda de tiendas. Para obtener más información, vaya a [Indexación: actualizaciones de productos de streaming](indexing.md).

## Prueba de la conexión {#test-connection}

En la tienda, compruebe lo siguiente:

* El [!UICONTROL Search] devuelve los resultados correctamente
* La exploración de categorías devuelve los resultados correctamente
* Las facetas están disponibles como filtros en las páginas de resultados de búsqueda

Si todo funciona correctamente, ¡enhorabuena! [!DNL Live Search] está instalado, conectado y listo para usar.

Si encuentra problemas en la tienda, consulte la `var/log/system.log` para errores de comunicación de API o errores en el lado de los servicios.

Para permitir que Live Search pase por un cortafuegos, añada `commerce.adobe.io` a la lista de permitidos.

## Comprobación de la versión instalada

Antes de actualizar Live Search, ejecute lo siguiente desde la línea de comandos para comprobar la versión de Live Search instalada:

```bash
composer show magento/module-live-search | grep version
```

## Actualizando [!DNL Live Search] {#update}

Para actualizar [!DNL Live Search], ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/live-search --with-dependencies
```

Para actualizar a una versión principal como de 3.1.1 a 4.0.0, edite la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Si está instalado `magento/live-search` la versión es `3.1.1` o inferior, y está actualizando a la versión `4.0.0` O superior, ejecute el siguiente comando antes de la actualización:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Para obtener más información sobre el instalado actualmente `magento/live-search` versión, ejecute el siguiente comando:

   ```bash
   composer show magento/live-search
   ```

1. Abra la raíz `composer.json` archivo y buscar `magento/live-search`.

1. En el `require` , actualice el número de versión como se indica a continuación:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Desinstalación [!DNL Live Search] {#uninstall}

Para desinstalar [!DNL Live Search], consulte [Desinstalación de módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] paquetes {#packages}

| Paquete | Descripción |
|--- |--- |
| `module-live-search` | Permite a los comerciantes definir la configuración de búsqueda para facetas, sinónimos, reglas de consulta, etc., y proporciona acceso a un área de reproducción de GraphQL de solo lectura para probar consultas desde *Administrador*. |
| `module-live-search-adapter` | Enruta las solicitudes de búsqueda desde la tienda a [!DNL Live Search] y procesa los resultados en la tienda. <br />- Navegador de categorías - Enruta las solicitudes desde la tienda [navegación superior](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) al servicio de búsqueda.<br />- Búsqueda global: enruta solicitudes desde el [búsqueda rápida](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) situado en la esquina superior derecha de la tienda, junto al [!DNL Live Search] servicio. |
| `module-live-search-storefront-popover` | Una ventana emergente de &quot;búsqueda mientras escribe&quot; reemplaza la búsqueda rápida estándar y devuelve datos y miniaturas de los resultados de búsqueda principales. |

## [!DNL Live Search] dependencias {#dependencies}

Lo siguiente [!DNL Live Search] Las dependencias son capturadas por [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
