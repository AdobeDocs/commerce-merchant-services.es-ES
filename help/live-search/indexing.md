---
title: "[!DNL Live Search] Indexación"
description: '"Descubra cómo [!DNL Live Search] indexa propiedades de atributos del producto".'
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Indexación

Las propiedades de atributos del producto (metadatos) determinan:

* Cómo se puede utilizar un atributo en el catálogo
* Su aspecto y comportamiento en la tienda
* Los datos que se incluyen en las operaciones de transferencia de datos

El ámbito de los metadatos de atributo es `website/store/store view`.

La variable [!DNL Live Search] La API permite que un cliente ordene por cualquier atributo de producto que tenga la variable [propiedad storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` configure como `Yes` en el Administrador de Adobe Commerce. Cuando está habilitado, `Search Weight` y `Visible in Advanced Search` se puede configurar para el atributo .

>[!NOTE]
>
>[!DNL Live Search] no indexa los productos eliminados ni los configurados en `Not Visible Individually`.

## Canalización de indexación

El cliente llama al servicio de búsqueda desde la tienda para recuperar (filtrables, clasificables) los metadatos de índice. Solo los atributos de producto en los que se puede buscar con la variable *Uso en navegación por capas* propiedad establecida en `Filterable (with results)` y *Usar para ordenar en lista de productos* configure como `Yes` puede ser invocado por el servicio de búsqueda.
Para construir una consulta dinámica, el servicio de búsqueda debe saber qué atributos son buscables y su peso. [!DNL Live Search] respeta los pesos de búsqueda de Adobe Commerce (1-10, donde 10 es la prioridad más alta). La lista de datos sincronizados y compartidos con el servicio de catálogo se puede encontrar en el esquema , que se define en:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] indexación del diagrama de búsqueda de cliente](assets/indexing-pipeline.svg)

1. Comprobar comercialización para [!DNL Live Search] .
1. Obtenga vistas de tienda con cambios en los atributos de los metadatos.
1. Almacene los atributos de indexación.
1. Reindexe el índice de búsqueda.

### Índice completo

When [!DNL Live Search] se configura y sincroniza durante la incorporación, puede tardar hasta ocho horas en crear el índice inicial. El proceso comienza después de `cron` envía la fuente y termina de ejecutarse.

Los siguientes eventos déclencheur una sincronización completa y una compilación de índice:

* Incorporación [sincronización de datos del catálogo](install.md#synchronize-catalog-data)
* Cambios en los metadatos de atributos

Por ejemplo, al cambiar la variable `Use in Search` propiedad de la variable `color` atributo de `No` a `Yes` cambia los metadatos de atributo a `searchable=true`, y déclencheur una sincronización completa y reindexan. Los siguientes metadatos de atributo déclencheur una sincronización completa y reindexan cuando se cambian:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Actualizaciones de productos de transmisión

Después de crear el índice inicial durante [Incorporación](install.md#synchronize-catalog-data), las siguientes actualizaciones de productos incrementales se sincronizan y reindexan continuamente:

* Nuevos productos agregados al catálogo
* Cambios en los valores de atributos del producto

Por ejemplo, si agrega un nuevo valor de muestra a la variable `color` se gestiona como una actualización de producto de flujo continuo.
Flujo de trabajo de actualización de flujo de trabajo:

1. Los productos actualizados se sincronizan desde la instancia de Adobe Commerce al servicio de catálogo.
1. El servicio de indexación busca continuamente actualizaciones de productos desde el servicio de catálogo. Los productos actualizados se indexan a medida que llegan al servicio de catálogo.
1. Una actualización de producto puede tardar hasta 15 minutos en estar disponible en [!DNL Live Search].

## Búsqueda de cliente

La variable [!DNL Live Search] La API permite que un cliente ordene según cualquier atributo de producto que se pueda ordenar configurando la variable [propiedad storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Se utiliza para ordenar en listas de productos* a `Yes`. En función del tema, esta configuración hace que el atributo se incluya como opción en la variable [Ordenar por](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) control de paginación en páginas de catálogo. Se pueden indexar hasta 300 atributos de producto mediante [!DNL Live Search], con [propiedades de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que se pueden buscar y filtrar.
Los metadatos de índice se almacenan en la canalización de indexación y el servicio de búsqueda puede acceder a ellos.

![[!DNL Live Search] diagrama de API de metadatos de índice](assets/index-metadata-api.svg)

### Flujo de trabajo de atributos ordenables

1. El cliente llama al servicio de búsqueda.
1. El servicio de búsqueda llama al servicio de administración de búsqueda.
1. El servicio de búsqueda llama a la canalización de indexación.

## Indexado para todos los productos

El orden de los campos de esta lista refleja el orden típico de las columnas de los datos de productos exportados.

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
