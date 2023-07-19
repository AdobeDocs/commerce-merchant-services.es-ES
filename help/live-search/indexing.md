---
title: "[!DNL Live Search] Indexando"
description: '"Aprenda cómo [!DNL Live Search] indexa las propiedades de atributos de producto".'
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Indexación

Las propiedades de atributos del producto (metadatos) determinan:

* Uso de un atributo en el catálogo
* Su aspecto y comportamiento en la tienda
* Los datos que se incluyen en las operaciones de transferencia de datos

El ámbito de los metadatos de atributos es `website/store/store view`.

El [!DNL Live Search] API permite a un cliente ordenar por cualquier atributo de producto que tenga la variable [propiedad de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` establezca en `Yes` en el Administrador de Adobe Commerce. Cuando está activada, `Search Weight` y `Visible in Advanced Search` se puede configurar para el atributo.

[!DNL Live Search] no indiza los productos eliminados ni los configurados en `Not Visible Individually`.

>[!NOTE]
>
> Clientes de Commerce con [!DNL Live Search] puede aprovechar las actualizaciones más rápidas de los cambios de precios y el tiempo de sincronización en sus sitios web con el [Indexador de precios SaaS](../price-index/index.md).

## Indexando canalización

El cliente llama al servicio de búsqueda desde la tienda para recuperar metadatos de índice (filtrables, ordenables). Solo atributos de producto en los que se puede buscar con *Uso en la navegación por capas* propiedad establecida en `Filterable (with results)` y *Utilizar para ordenar en la lista de productos* establezca en `Yes` El servicio de búsqueda puede llamar a.
Para construir una consulta dinámica, el servicio de búsqueda necesita saber qué atributos se pueden buscar y su peso. [!DNL Live Search] respeta los pesos de búsqueda de Adobe Commerce (1-10, donde 10 es la prioridad más alta). La lista de datos sincronizados y compartidos con el servicio de catálogo se encuentra en el esquema, que se define en:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] indexando diagrama de búsqueda de cliente](assets/indexing-pipeline.svg)

1. Consultar al comerciante [!DNL Live Search] derecho.
1. Obtenga vistas de la tienda con cambios en los metadatos de atributos.
1. Almacenar atributos de indexación.
1. Reindexe el índice de búsqueda.

### Índice completo

Cuándo [!DNL Live Search] está configurado y sincronizado durante la incorporación; puede tardar hasta 30 minutos en crear el índice inicial. Los catálogos grandes pueden tardar más en indexarse. El proceso comienza después de `cron` envía la fuente y termina de ejecutarse.

Los siguientes eventos almacenan en déclencheur una sincronización completa y la generación de índices:

* Incorporación [sincronización de datos de catálogo](install.md#synchronize-catalog-data)
* Cambios en los metadatos de atributos

Por ejemplo, si cambia el `Use in Search` propiedad del `color` atributo de `No` hasta `Yes` cambia los metadatos de atributo a `searchable=true`, y déclencheur una sincronización y reindexación completas. El siguiente déclencheur de metadatos de atributo genera una sincronización y reindexación completas cuando se cambia:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Transmisión de actualizaciones de productos

Después de crear el índice inicial durante [incorporación](install.md#synchronize-catalog-data), las siguientes actualizaciones incrementales de productos se sincronizan y reindexan continuamente:

* Nuevos productos añadidos al catálogo
* Cambios en los valores de atributos del producto

Por ejemplo, si se añade un nuevo valor de muestra al `color` El atributo se gestiona como una actualización de producto de flujo continuo.
Flujo de trabajo de actualización de streaming:

1. Los productos actualizados se sincronizan desde la instancia de Adobe Commerce al servicio de catálogo.
1. El servicio de indexación busca continuamente actualizaciones de productos del servicio de catálogo. Los productos actualizados se indexan a medida que llegan al servicio de catálogo.
1. La actualización de un producto puede tardar hasta 15 minutos en estar disponible en [!DNL Live Search].

## Búsqueda de clientes

El [!DNL Live Search] La API permite que un cliente ordene por cualquier atributo de producto que se pueda ordenar configurando la variable [propiedad de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Se usa para ordenar en listas de productos* hasta `Yes`. En función del tema, esta configuración hace que el atributo se incluya como opción en la variable [Ordenar por](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) control de paginación en páginas de catálogo. Se pueden indexar hasta 200 atributos de producto por [!DNL Live Search], con [propiedades de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que se pueden buscar y filtrar.
Los metadatos de índice se almacenan en la canalización de indexación y el servicio de búsqueda puede acceder a ellos.

![[!DNL Live Search] diagrama API de metadatos de índice](assets/index-metadata-api.svg)

### Flujo de trabajo de atributos ordenables

1. El cliente llama al servicio de búsqueda.
1. El servicio de búsqueda llama al servicio de administración de búsqueda.
1. El servicio de búsqueda llama a la canalización de indexación.

## Indexado para todos los productos

El orden de los campos de esta lista refleja el orden típico de las columnas en los datos de productos exportados.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

El siguiente campo está indexado para todos los productos configurables:

* `childrenSkus`
