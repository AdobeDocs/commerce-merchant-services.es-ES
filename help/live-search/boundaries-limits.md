---
title: 'Límites y límites'
description: Conozca los límites y limitaciones de [!DNL Live Search] para asegurarse de que cumple con las necesidades de su empresa.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 2f28b77691e5b125875f1ce39301bfebd093a922
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Límites y límites

Cuando se trata de buscar sitios, Adobe Commerce le da opciones. Revise los límites y limitaciones siguientes para asegurarse de que [!DNL Live Search] y [!DNL Catalog Service] satisfacen las necesidades de su empresa. Si necesita funcionalidades de búsqueda avanzadas como búsqueda de contenido, traer su propio algoritmo (BYOA) o comercialización basada en atributos, considere una solución de búsqueda de terceros.

## General

- El módulo [Búsqueda avanzada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) se deshabilita al instalar [!DNL Live Search] y se quita el vínculo Búsqueda avanzada del pie de página de la tienda.
- [Precios de nivel](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) y [Precios especiales](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) no son compatibles con el campo [!DNL Live Search] y el widget de página de lista de productos.
- Los precios de los productos no incluyen el impuesto sobre el valor añadido (IVA).
- No se admite la búsqueda de contenido.
- Hay un límite de 10 000 productos que se pueden paginar.
- Hay un límite estricto de 1 MB por atributo, incluida la descripción y los atributos personalizados.
- El adaptador de búsqueda no admite atributos de producto creados con un modelo de origen personalizado y utilizados como facetas. Para admitir esta funcionalidad, debe usar el [Widget de la página de lista de productos](plp-styling.md).

## Indexación

- [!DNL Live Search] [índices](indexing.md) hasta un total de 450 atributos de producto por vista de tienda. Se distribuyen de la siguiente manera:
   - 50 atributos que se pueden ordenar
   - 200 atributos filtrables
   - 200 atributos en los que se puede buscar
- [!DNL Live Search] solo indexa productos de la base de datos de Adobe Commerce.
- Las páginas de CMS no están indexadas.
- Los atributos SKU, nombre y categoría se pueden buscar de forma predeterminada y no se pueden excluir de la búsqueda. Asegúrese de anular la asignación de los productos de las categorías si no están pensados para estar en esas categorías.

## Facetas

- Se puede configurar un máximo de 100 atributos como facetas a partir de los 200 atributos filtrables que se pueden indexar.
- Dentro de una faceta, se puede devolver un máximo de 30 contenedores. Si es necesario devolver más de 30 contenedores, [cree un vale de soporte técnico](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para que el Adobe pueda analizar el impacto en el rendimiento y determinar si es factible aumentar este límite para su entorno.
- Las facetas dinámicas pueden causar problemas de rendimiento en índices grandes e índices con una alta ordinalidad. Si ha creado facetas dinámicas y observa algún deterioro del rendimiento o si la página no se carga con errores de tiempo de espera, intente cambiar las facetas a ancladas para determinar si esto resuelve el problema de rendimiento.
- El estado de las existencias (`quantity_and_stock_status`) no se admite como faceta. Puede usar `inStock: 'true'` para filtrar productos sin existencias. Esto se admite de forma predeterminada en el módulo `LiveSearchAdapter` cuando &quot;Mostrar productos sin existencias&quot; está establecido en &quot;Verdadero&quot; en el administrador [!DNL Commerce].
- Los atributos de tipo de fecha no se admiten como faceta.

## Consulta

- [!DNL Live Search] usa un único [extremo de GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) para que las consultas admitan características como facetas dinámicas y búsqueda mientras escribe. Aunque es similar a la [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), existen algunas diferencias y algunos campos pueden no ser totalmente compatibles.
- El número máximo de resultados que se pueden devolver en una consulta de búsqueda es 10 000.
- No es posible filtrar los resultados mediante un atributo de tipo de fecha.

## Reglas

- El número máximo de [reglas](rules.md) de comercialización de búsqueda por vista de tienda es 50.
- La comercialización de categorías puede tener una regla por categoría.
- El número máximo de condiciones por regla es 10.
- El número máximo de eventos por regla es 25.
- Para evitar resultados impredecibles en respuestas paginadas, el número de productos anclados no debe superar el tamaño de página solicitado.

## Sinónimos

- [!DNL Live Search] puede administrar hasta 200 [sinónimos](synonyms.md) por vista de tienda.
- Es posible que los sinónimos de varias palabras no siempre funcionen según lo esperado. Asegúrese de probar estos sinónimos en el entorno de ensayo antes de utilizarlos en la producción, ya que pueden tener un efecto adverso en la relevancia.

## Comercialización por categorías

- Se puede crear una regla por categoría para cada vista de tienda. Cada regla puede tener:
   - Hasta diez condiciones
   - Hasta 25 eventos

## Permisos B2B y de categoría

- Los productos no se muestran si no se añaden a un catálogo compartido predeterminado.
- Para restringir grupos de clientes que usen [permisos de categoría](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions):
   - Los productos deben asignarse a la categoría raíz.
   - El grupo de clientes &quot;Sin sesión iniciada&quot; debe tener permisos de navegación &quot;Permitir&quot;.
   - Para restringir productos al grupo de clientes &quot;No se inició sesión&quot;, vaya a cada categoría y establezca permisos para cada [grupo de clientes](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- En este momento no se admite la compatibilidad predeterminada con B2B con el widget PLP en el PWA Studio. Sin embargo, puede [usar la API](install.md#pwa-support) para implementar esta funcionalidad.
- Las facetas de categoría de [!DNL Live Search] pueden mostrar categorías que no se pueden mostrar a un [grupo de clientes](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) específico.
- [!DNL Live Search] admite hasta 1000 grupos de clientes.

## [!DNL Storefront popover]

- [[!DNL popover]](storefront-popover.md) solo está disponible para tiendas que usen el tema *Luma* o un tema personalizado basado en *Luma*. Las rutas de exploración de la página de resultados de búsqueda no tendrán el estilo *Luma*.
- [!DNL popover] no admite el tema *En blanco*.
- [!DNL popover] no es compatible con el formulario de pedido rápido.
- No se admiten listas de deseos ni comparaciones de productos.
