---
title: "Facetas"
description: "[!DNL Live Search] las facetas utilizan varias dimensiones de valores de atributos como criterios de búsqueda."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Facetas

Las facetas son un método de filtrado de alto rendimiento que utiliza varias dimensiones de valores de atributos como criterios de búsqueda. La búsqueda por facetas es similar, pero considerablemente &quot;más inteligente&quot; que la [navegación por capas](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). La lista de filtros disponibles viene determinada por la variable [atributos filtrables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) de productos devueltos en los resultados de búsqueda.

![Resultados de búsqueda filtrados](assets/storefront-search-results-run.png)

## Requisitos de facetas

Los requisitos de categoría y atributos de producto para facetas son similares a los atributos filtrables utilizados para la navegación en capas. Las propiedades de tienda de cada atributo deben establecerse en `filterable (with results)`.

Live Search admite hasta:

* 100 atributos configurados como facetas
* 50 atributos que se pueden ordenar
* 200 atributos filtrables
* 200 atributos que se pueden buscar

| Configuración | Descripción |
|--- |--- |
| [Configuración de visualización de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Anclaje - `Yes` |
| [Propiedades de atributo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Tipo de entrada de catálogo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Propiedades de tienda de atributos | Usar en navegación por capas de resultados de búsqueda - `Yes` |

## Valores de atributo predeterminados

Los siguientes atributos de producto tienen [propiedades de tienda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que usa [!DNL Live Search] y activada de forma predeterminada.

| Propiedad | Propiedad Storefront | Atributo |
|---|---|---|
| Ordenable | Se utiliza para ordenar en la lista de productos | `price` |
| Buscable | Usar en la búsqueda | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Uso en navegación por capas - filtrable (con resultados) | `price`<br />`visibility`<br />`category_name` |

## Propiedades de atributo predeterminadas que no son del sistema

La tabla siguiente muestra la búsqueda predeterminada y las propiedades filtrables de atributos que no son del sistema, incluidos los que son específicos de los datos de ejemplo de Luma. Configuración de la variable *Usar en la búsqueda* attribute, propiedad `Yes` hace que el atributo se pueda buscar en ambos [!DNL Live Search] y Adobe Commerce nativo.

| Código de atributo | Buscable | Uso en navegación por capas |
|--- |--- |--- |
| actividad | Sí | Filtrable (con resultados) |
| attributes_brand | Sí | No |
| marca | Sí | No |
| clima | Sí | Filtrable (con resultados) |
| cuello | Sí | Filtrable (con resultados) |
| color | Sí | Filtrable (con resultados) |
| coste | Sí | No |
| eco_collection | Sí | Filtrable (con resultados) |
| sexo | Sí | Filtrable (con resultados) |
| fabricante | Sí | Filtrable (con resultados) |
| material | Sí | Filtrable (con resultados) |
| propósito | Sí | Filtrable (con resultados) |
| strap_bags | Sí | Filtrable (con resultados) |
| style_general | Sí | Filtrable (con resultados) |

## Propiedades de atributos del sistema predeterminadas

La siguiente tabla muestra la búsqueda predeterminada y las propiedades filtrables de los atributos del sistema.

| Código de atributo | Buscable | Uso en navegación por capas |
|--- |--- |--- |
| allow_open_amount | Sí | Filtrable (con resultados) |
| descripción | Sí | No |
| name | Sí | No |
| precio | Sí | Filtrable (con resultados) |
| short_description | Sí | No |
| sku | Sí | No |
| status | Sí | No |
| tax_class_id | Sí | No |
| url_key | Sí | No |
| weight | Sí | No |
