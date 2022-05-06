---
title: Instalar Live Search
description: Obtenga información sobre cómo instalar, actualizar y desinstalar Live Search de Adobe Commerce.
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: ec68feaebc911c097bd643aabfc61ec586a7e099
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# Instalar [!DNL Live Search]

Live Search se instala como una extensión desde Adobe Marketplace. Después de la [!DNL Live Search] (con módulos de catálogo como dependencias) está instalado y configurado, [!DNL Commerce] comienza a compartir datos de búsqueda y catálogo con los servicios SaaS. En este punto, *Administrador* los usuarios pueden configurar, personalizar y administrar facetas de búsqueda, sinónimos y reglas de comercialización.

En este tema se proporcionan instrucciones para hacer lo siguiente:

* Instalar [!DNL Live Search] (Métodos 1 y 2)
* [Actualizar [!DNL Live Search]](#update)
* [Desinstalar [!DNL Live Search]](#uninstall)

## Antes de empezar {#before-you-begin}

Haga lo siguiente:

1. Confirme que [trabajos cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) y [indexadores](https://docs.magento.com/user-guide/system/index-management.html) se están ejecutando.

1. Elija el método de incorporación que cumpla sus necesidades y siga las instrucciones.

   * [Método 1](#method-1): Instalar sin [!DNL Elasticsearch]
   * [Método 2](#method-2): Instale con [!DNL Elasticsearch] (Sin tiempo de inactividad)

## Método 1: Instalar sin Elasticsearch {#method-1}

Se recomienda este método de incorporación al instalar [!DNL Live Search] a:

* Nuevo [!DNL Commerce] instalación
* Entorno de ensayo

En este escenario, las operaciones de tienda se interrumpen mientras el [!DNL Live Search] service indexa todos los productos del catálogo. Durante la instalación, [!DNL Live Search] los módulos están habilitados y [!DNL Elasticsearch] los módulos están desactivados.

>[!TIP]
>
>Para evitar errores de escritura, pase el ratón por encima del extremo derecho del cuadro de código y haga clic en el botón [!UICONTROL **Copiar**] y péguelo en la línea de comandos.

1. Instalación de Adobe Commerce 2.4.x sin [!DNL Live Search].

1. Para descargar el `live-search` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/live-search
   ```

   Para obtener más información, consulte la lista de [!DNL Live Search] [dependencias](#dependencies) que captura [!DNL Composer].

1. Ejecute los siguientes comandos para deshabilitar [!DNL Elasticsearch] y módulos relacionados, e instalar [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Aunque los datos están indexados y sincronizados, las operaciones de búsqueda y exploración de categoría no están disponibles en la tienda. Según el tamaño del catálogo, el proceso puede tardar al menos una hora desde el momento en que se realiza `cron` se ejecuta para sincronizar los datos [!DNL Live Search] servicios.

1. Compruebe que: [indexadores](https://docs.magento.com/user-guide/system/index-management.html) están configurados en `Update by Schedule`:

   * Fuente de productos
   * Fuente de variante del producto
   * Fuente de atributos del catálogo

1. Configure las [Claves de API](#configure-api-keys) y compruebe que los datos del catálogo son [sincronizar](#synchronize-catalog-data) con [!DNL Live Search] servicios.

1. Para que las facetas estén disponibles como filtros en la tienda, agregue la variable [facetas](facets-add.md) necesita, según el [requisitos de facetas](facets.md).

   Debe poder añadir facetas después de `cron` ejecuta las fuentes de atributos y exporta los metadatos de atributos.

1. Espere al menos una hora después `cron` se ejecuta para sincronizar datos. A continuación, [verify](#verify-export) que los datos se exportaron.

1. [Prueba](#test-the-connection) la conexión desde la tienda.

## Método 2: Instalar con el Elasticsearch {#method-2}

Se recomienda este método de incorporación al instalar [!DNL Live Search] a:

* Una producción existente [!DNL Commerce] instalación

En este escenario, [!DNL Elasticsearch] administra temporalmente las solicitudes de búsqueda de la tienda mientras [!DNL Live Search] el servicio indexa todos los productos en segundo plano, sin interrupciones en las operaciones normales de tienda. [!DNL Elasticsearch] está desactivado y [!DNL Live Search] se activa después de indexar y sincronizar todos los datos del catálogo.

>[!TIP]
>
>Para evitar errores de escritura, pase el ratón por encima del extremo derecho del cuadro de código y haga clic en el botón [!UICONTROL **Copiar**] y péguelo en la línea de comandos.

1. Para descargar el `live-search` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/live-search
   ```

   Para obtener más información, consulte la lista de [!DNL Live Search] [dependencias](#live-search-dependencies) que captura [!DNL Composer].

1. Ejecute el siguiente comando para deshabilitar temporalmente el [!DNL Live Search] módulos que proporcionan resultados de búsqueda de tienda.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] continúa administrando las solicitudes de búsqueda desde la tienda mientras que la variable [!DNL Live Search] sincroniza los datos del catálogo y los productos de los índices en segundo plano.

1. Compruebe que: [indexadores](https://docs.magento.com/user-guide/system/index-management.html) están configurados en `Update by Schedule`:

   * Fuente de productos
   * Fuente de variante del producto
   * Fuente de atributos del catálogo

1. Configure las [Claves de API](#configure-api-keys) y compruebe que los datos del catálogo son [sincronizar](#synchronize-catalog-data) con [!DNL Live Search] servicios.

1. Para que las facetas estén disponibles como filtros en la tienda, agregue la variable [facetas](facets-add.md) necesita, según el [requisitos de facetas](facets.md).

   Debe poder añadir facetas después de `cron` ejecuta las fuentes de productos y atributos y exporta metadatos de atributos a [!DNL Live Search] servicios.

1. Espere al menos una hora para que los datos se indexen y sincronicen. A continuación, utilice el [Zona de reproducción de GraphQL](https://devdocs.magento.com/live-search/graphql-support.html) con la consulta predeterminada para verificar lo siguiente:

   * El recuento de productos devuelto está cerca de lo que espera para la vista de tienda.
   * Se devuelven facetas.

1. Ejecute los siguientes comandos para habilitar [!DNL Live Search] módulos, desactivar [!DNL Elasticsearch]y ejecutar `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Prueba](#test-the-connection) la conexión desde la tienda.

## Configuración de claves de API {#configure-api-keys}

La clave de API de Adobe Commerce y su clave privada asociada son necesarias para conectarse [!DNL Live Search] a una instalación de Adobe Commerce. La clave de API se genera y se mantiene en la cuenta de [!DNL Commerce] titular de licencia, que puede compartirlo con el desarrollador o SI. A continuación, el desarrollador puede crear y administrar los espacios de datos SaaS en nombre del titular de la licencia.  Si ya tiene un conjunto de claves de API, no es necesario regenerarlas.

### Titular de la licencia de Adobe Commerce

Para generar una clave de API y una clave privada, consulte [Conector de Commerce Services](../landing/saas.md).

### Desarrollador de Adobe Commerce o SI

El desarrollador o SI configura el espacio de datos SaaS como se describe en la *Servicios de comercio* de la configuración. En el *Administrador*, Commerce Services está disponible en la *Configuración* barra lateral cuando está instalado un módulo SaaS.

## Sincronizar datos de catálogo {#synchronize-catalog-data}

[!DNL Live Search] requiere datos de producto sincronizados para operaciones de búsqueda y datos de atributos sincronizados para configurar facetas. La sincronización inicial entre el catálogo de productos y el servicio de catálogo comienza cuando [!DNL Live Search] está conectado por primera vez. Según el método de instalación y el tamaño del catálogo, los datos pueden tardar hasta ocho horas en exportarse e indizarse mediante [!DNL Live Search]. La lista de datos sincronizados y compartidos con el servicio de catálogo se puede encontrar en el esquema , que se define en:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verificar exportación {#verify-export}

Para comprobar que los datos del catálogo se han exportado desde la instancia de Adobe Commerce y se han sincronizado para [!DNL Live Search], busque entradas en las tablas siguientes:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Para obtener más ayuda, consulte [[!DNL Live Search] catálogo no sincronizado](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) en la Base de conocimientos de soporte.

### Actualizaciones de productos futuras

Después de la sincronización inicial, las actualizaciones de productos incrementales pueden tardar hasta quince minutos en estar disponibles para la búsqueda en tiendas. Para obtener más información, vaya a [Indexación: Actualizaciones de productos de transmisión](indexing.md).

## Probar la conexión {#test-connection}

En la tienda, compruebe lo siguiente:

* La variable [!UICONTROL Search] El cuadro devuelve los resultados correctamente
* El examen de categoría devuelve los resultados correctamente
* Las facetas están disponibles como filtros en las páginas de resultados de búsqueda

Si todo funciona correctamente, ¡felicitaciones! [!DNL Live Search] está instalado, conectado y listo para usar.

Si tiene problemas en la tienda, consulte la `var/log/system.log` para errores o errores de comunicación de API en el lado de los servicios.

## Comprobación de la versión instalada

Antes de actualizar Live Search, ejecute lo siguiente desde la línea de comandos para comprobar la versión de Live Search que está instalada actualmente:

```bash
composer show magento/module-live-search | grep version
```

## Actualización [!DNL Live Search] {#update}

Para actualizar [!DNL Live Search], ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/live-search --with-dependencies
```

Para actualizar a una versión principal como de 1.0.0 a 2.0.0, edite la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Si su `magento/live-search` versión es `1.3.1` o inferior, y está actualizando a la versión `2.0.0` o superior, ejecute el siguiente comando antes de la actualización:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Para obtener información acerca de la instalación actual `magento/live-search` , ejecute el siguiente comando:

   ```bash
   composer show magento/live-search
   ```

1. Abra la raíz `composer.json` y busque `magento/live-search`.

1. En el `require` , actualice el número de versión de la siguiente manera:

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## Desinstalación [!DNL Live Search] {#uninstall}

Para desinstalar [!DNL Live Search], consulte [Desinstalar módulos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] paquetes {#packages}

| Paquete | Descripción |
|--- |--- |
| `module-live-search` | Permite a los comerciantes configurar las opciones de búsqueda para facetas, sinónimos, reglas de consulta, etc., y proporciona acceso a un área de reproducción de GraphQL de solo lectura para probar consultas desde la *Administrador*. |
| `module-live-search-adapter` | Envía las solicitudes de búsqueda desde la tienda hasta el [!DNL Live Search] y procesa los resultados en la tienda. <br />- Exploración de categorías: Enruta solicitudes desde la tienda [navegación superior](https://docs.magento.com/user-guide/catalog/navigation-top.html) al servicio de búsqueda.<br />- Búsqueda global: envía solicitudes desde la [búsqueda rápida](https://docs.magento.com/user-guide/catalog/search-quick.html) en la parte superior derecha de la tienda, a la [!DNL Live Search] servicio. |
| `module-live-search-storefront-popover` | Una ventana emergente de &quot;búsqueda a medida que escribe&quot; reemplaza a la búsqueda rápida estándar y devuelve sugerencias de productos dinámicas y miniaturas de los principales resultados de búsqueda. |

## [!DNL Live Search] dependencias {#dependencies}

Lo siguiente [!DNL Live Search] las dependencias son capturadas por [!DNL Composer]:

| Dependencia | Descripción |
|--- |--- |
| Exportación de módulos | Los siguientes módulos recopilan y sincronizan datos de catálogo:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Necesario para configurar la conexión a Commerce Services. |
| `module-services-id` | Necesario para configurar la conexión a Commerce Services. |
