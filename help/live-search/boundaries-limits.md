---
title: 'Límites y límites'
description: Obtenga información acerca de los límites y limitaciones de [!DNL Live Search] para garantizar que satisfaga las necesidades de su empresa.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: ba7e92d5b3aaabe6a8c71f86b0e4eab38aec9adf
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# Límites y límites

Cuando se trata de buscar sitios, Adobe Commerce le da opciones. Revise los límites y limitaciones siguientes para asegurarse de que [!DNL Live Search] y [!DNL Catalog Service] satisfaga las necesidades de su empresa. Si necesita funcionalidades de búsqueda avanzadas como búsqueda de contenido, traer su propio algoritmo (BYOA) o comercialización basada en atributos, considere una solución de búsqueda de terceros.

## General

- El [Búsqueda avanzada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) El módulo está desactivado cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
- [Precios de nivel](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) y [Precios especiales](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) no son compatibles con [!DNL Live Search] y Widget de la página de lista de productos.
- Los precios de los productos no incluyen el impuesto sobre el valor añadido (IVA).
- No se admite la búsqueda de contenido.
- Hay un límite de 10 000 productos que se pueden paginar.
- El adaptador de búsqueda no admite atributos de producto creados con un modelo de origen personalizado y utilizados como facetas. Para admitir esta funcionalidad, debe utilizar la variable [Widget de página de lista de productos](plp-styling.md).

## Indexación

- [!DNL Live Search] [índices](indexing.md) hasta un total de 450 atributos de producto por vista de tienda. Se distribuyen de la siguiente manera:
   - 50 atributos que se pueden ordenar
   - 200 atributos filtrables
   - 200 atributos en los que se puede buscar
- [!DNL Live Search] indexa solo los productos de la base de datos de Adobe Commerce.
- Las páginas de CMS no están indexadas.
- Los atributos SKU, nombre y categoría se pueden buscar de forma predeterminada y no se pueden excluir de la búsqueda. Asegúrese de anular la asignación de los productos de las categorías si no están pensados para estar en esas categorías.

## Facetas

- Se puede configurar un máximo de 100 atributos como facetas a partir de los 200 atributos filtrables que se pueden indexar.
- Dentro de una faceta, se puede devolver un máximo de 30 contenedores. Si es necesario devolver más de 30 contenedores, [crear una solicitud de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) por lo tanto, el Adobe puede analizar el impacto en el rendimiento y determinar si es factible aumentar este límite para su entorno.
- Las facetas dinámicas pueden causar problemas de rendimiento en índices grandes e índices con una alta ordinalidad. Si ha creado facetas dinámicas y observa algún deterioro del rendimiento o si la página no se carga con errores de tiempo de espera, intente cambiar las facetas a ancladas para determinar si esto resuelve el problema de rendimiento.
- Estado de stock (`quantity_and_stock_status`) no se admite como faceta. Puede utilizar `inStock: 'true'` para filtrar los productos sin existencias. Esto se admite de forma predeterminada en la `LiveSearchAdapter` cuando &quot;Mostrar productos sin existencias&quot; está establecido en &quot;Verdadero&quot; en la [!DNL Commerce] Administrador.
- Los atributos de tipo de fecha no se admiten como faceta.

## Consulta

- [!DNL Live Search] utiliza un único [Extremo de GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) para que las consultas admitan características como facetas dinámicas y búsqueda a medida que escribe. Aunque es similar a la [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Sin embargo, existen algunas diferencias y es posible que algunos campos no sean totalmente compatibles.
- El número máximo de resultados que se pueden devolver en una consulta de búsqueda es 10 000.
- No es posible filtrar los resultados mediante un atributo de tipo de fecha.

## Reglas

- Número máximo de comercialización de búsqueda [reglas](rules.md) la vista de tienda es 50.
- La comercialización de categorías puede tener una regla por categoría.
- El número máximo de condiciones por regla es 10.
- El número máximo de eventos por regla es 25.

## Sinónimos

- [!DNL Live Search] puede administrar hasta 200 [sinónimos](synonyms.md) por vista de tienda.
- Los sinónimos de varias palabras están limitados a 20 por vista de tienda.

## Comercialización por categorías

- Se puede crear una regla por categoría para cada vista de tienda. Cada regla puede tener:
   - Hasta diez condiciones
   - Hasta 25 eventos

## Permisos B2B y de categoría

- Los productos no se muestran si no se añaden a un catálogo compartido predeterminado.
- Para restringir los grupos de clientes que utilizan permisos de catálogo:
   - Los productos deben asignarse a la categoría Raíz.
   - El grupo de clientes &quot;Sin sesión iniciada&quot; debe tener permisos de navegación &quot;Permitir&quot;.
   - Para restringir productos al grupo de clientes &quot;Sin sesión iniciada&quot;, vaya a cada categoría y defina los permisos para cada grupo de clientes.
- En este momento no se admite la compatibilidad predeterminada con B2B con el widget PLP en el PWA Studio. Sin embargo, puede [usar la API](install.md#pwa-support) para implementar esta funcionalidad.
- Facetas de categoría en [!DNL Live Search] puede mostrar categorías que no se pueden mostrar a un grupo de clientes específico.

## [!DNL Storefront popover]

- El [[!DNL popover]](storefront-popover.md) solo está disponible para tiendas que utilizan el *Luma* o una temática personalizada que se base en *Luma*. Las rutas de exploración de la página de resultados de búsqueda no tendrán *Luma* estilo.
- El [!DNL popover] no es compatible con *Vacío* tema.
- El [!DNL popover] no es compatible con el formulario de pedido rápido.
- No se admiten listas de deseos ni comparaciones de productos.
