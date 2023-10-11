---
title: "Facetas"
description: '"[!DNL Live Search] las facetas utilizan varias dimensiones de valores de atributo como criterios de búsqueda".'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 4eddad715405f35ea063bab3cf4651fec3beeae5
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Facetas

Las facetas son un método de filtrado de alto rendimiento que utiliza varias dimensiones de valores de atributo como criterios de búsqueda. La búsqueda con facetas es similar, pero considerablemente &quot;más inteligente&quot; que el estándar [navegación por capas](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). La lista de filtros disponibles viene determinada por la variable [atributos filtrables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) de productos devueltos en los resultados de búsqueda.

[!DNL Live Search] utiliza el `productSearch` consulta, que devuelve facetas y otros datos específicos de [!DNL Live Search]. Consulte [`productSearch` query](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) en la documentación para desarrolladores para ver ejemplos de código.

![Resultados de búsqueda filtrados](assets/storefront-search-results-run.png)

Cualquier faceta definida puede utilizarse como parámetro de URL y los resultados se filtrarán según los valores del parámetro: `http://yourstore.com?brand=acme&color=red`.

## Requisitos de faceteado

Los requisitos de atributos de categoría y producto para faceteado son similares a los atributos filtrables utilizados para la navegación por capas. Las propiedades de tienda de cada atributo deben establecerse en `filterable (with results)`.

[!DNL Live Search] admite hasta:

* 100 atributos configurados como facetas
* 50 atributos que se pueden ordenar
* 200 atributos filtrables
* 200 atributos en los que se puede buscar

| Configuración | Descripción |
|--- |--- |
| [Configuración de visualización de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Anclaje - `Yes` |
| [Propiedades de atributo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Tipo de entrada de catálogo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (solo widget), `Text swatch` (solo widget) |
| Propiedades de tienda de atributos | Uso en la navegación por capas de resultados de búsqueda - `Yes` |

## Agregación de facetas

La agregación de facetas se realiza de la siguiente manera: si la tienda tiene tres facetas (categorías, color y precio) y el comprador filtra las tres (color = azul, el precio es de 10,00 a 50,00 $, categorías = `promotions`).

* `categories` agregación: agregados `categories`, y aplica el `color` y `price` filtros, pero no el `categories` filtro.
* `color` agregación: agregados `color`, y aplica el`price` y `categories` filtros, pero no el `color` filtro.
* `price` agregación: agregados `price`, y aplica el `color` y `categories` filtros, pero no el `price` filtro.

## Valores de atributo predeterminados

Los siguientes atributos de producto tienen [propiedades de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que utilizan los usuarios [!DNL Live Search] y activada de forma predeterminada.

| Propiedad | Propiedad Storefront | Atributo |
|---|---|---|
| Ordenable | Se utiliza para ordenar en la lista de productos | `price` |
| Buscable | Uso en la búsqueda | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Uso en la navegación por capas: filtrable (con resultados) | `price`<br />`visibility`<br />`category_name` |

## Propiedades de atributo predeterminadas que no son del sistema

En la tabla siguiente se muestran las propiedades de búsqueda y filtrado predeterminadas de los atributos que no son del sistema, incluidos los que son específicos de los datos de ejemplo de Luma. Configuración de la *Uso en la búsqueda* atribuir propiedad a `Yes` permite búsquedas en el atributo en ambos [!DNL Live Search] y Adobe Commerce nativo.

| Código de atributo | Buscable | Uso en la navegación por capas |
|--- |--- |--- |
| actividad | Sí | Filtrable (con resultados) |
| attributes_brand | Sí | No |
| marca | Sí | No |
| clima | Sí | Filtrable (con resultados) |
| collar | Sí | Filtrable (con resultados) |
| color | Sí | Filtrable (con resultados) |
| coste | Sí | No |
| eco_collection | Sí | Filtrable (con resultados) |
| género | Sí | Filtrable (con resultados) |
| fabricante | Sí | Filtrable (con resultados) |
| material | Sí | Filtrable (con resultados) |
| propósito | Sí | Filtrable (con resultados) |
| strap_bags | Sí | Filtrable (con resultados) |
| style_general | Sí | Filtrable (con resultados) |

## Propiedades predeterminadas de atributos del sistema

En la tabla siguiente se muestran la búsqueda predeterminada y las propiedades filtrables de los atributos del sistema.

| Código de atributo | Buscable | Uso en la navegación por capas |
|--- |--- |--- |
| allow_open_amount | Sí | Filtrable (con resultados) |
| description | Sí | No |
| name | Sí | No |
| precio | Sí | Filtrable (con resultados) |
| short_description | Sí | No |
| sku | Sí | No |
| status | Sí | No |
| tax_class_id | Sí | No |
| url_key | Sí | No |
| peso | Sí | No |
