---
title: "[!DNL Live Search] Límites y límites"
description: '"Conozca los límites y limitaciones de [!DNL Live Search] para garantizar que satisface las necesidades de su empresa".'
role: Admin, Developer
source-git-commit: 8aca09aba13e32afb191169729dfc1fbd0087262
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Límites y límites

Cuando se trata de buscar sitios, Adobe Commerce le da opciones. Revise los límites y limitaciones siguientes para asegurarse de que [!DNL Live Search] y [!DNL Catalog Service] satisfaga las necesidades de su empresa. Si necesita funcionalidades de búsqueda avanzadas como búsqueda de contenido, traer su propio algoritmo (BYOA) o comercialización basada en atributos, considere una solución de búsqueda de terceros.

## General

- El [Búsqueda avanzada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) El módulo está desactivado cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
- [Precios de nivel](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) y [Precios especiales](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) no son compatibles con [!DNL Live Search] y Widget de la página de lista de productos.
- [!DNL Live Search] no se pueden agregar datos de inventario de varios orígenes.
- Los precios de los productos no incluyen el impuesto sobre el valor añadido (IVA).
- No se admite la búsqueda de contenido.
- Hay un límite de 10 000 productos que se pueden paginar.

## Indexación

- [!DNL Live Search] [índices](indexing.md) hasta un total de 450 atributos de producto por vista de tienda. Se distribuyen de la siguiente manera:
   - 50 atributos que se pueden ordenar
   - 200 atributos filtrables
   - 200 atributos en los que se puede buscar
- [!DNL Live Search] indexa solo los productos de la base de datos de Adobe Commerce.
- Las páginas de CMS no están indexadas.

## Facetas

- Se puede configurar un máximo de 100 atributos como facetas a partir de los 200 atributos filtrables que se pueden indexar.
- Dentro de una faceta, se puede devolver un máximo de 30 contenedores. Si es necesario devolver más de 30 contenedores, [crear una solicitud de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) por lo tanto, el Adobe puede analizar el impacto en el rendimiento y determinar si es factible aumentar este límite para su entorno.
- Las facetas dinámicas pueden causar problemas de rendimiento en índices grandes e índices con una alta ordinalidad. Si ha creado facetas dinámicas y observa algún deterioro del rendimiento o si la página no se carga con errores de tiempo de espera, intente cambiar las facetas a ancladas para determinar si esto resuelve el problema de rendimiento.
- Estado de stock (`quantity_and_stock_status`) no se admite como faceta. Puede utilizar `inStock: 'true'` para filtrar los productos sin existencias. Esto se admite de forma predeterminada en la `LiveSearchAdapter` cuando &quot;Mostrar productos sin existencias&quot; está establecido en &quot;Verdadero&quot; en la [!DNL Commerce] Administrador.

## Consulta

- [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación por capas estén fuera de su alcance.
- [!DNL Live Search] utiliza un único [Extremo de GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) para que las consultas admitan características como facetas dinámicas y búsqueda a medida que escribe. Aunque es similar a la [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Sin embargo, existen algunas diferencias y es posible que algunos campos no sean totalmente compatibles.
- El número máximo de resultados que se pueden devolver en una consulta de búsqueda es 10 000.

## Reglas

- Número máximo de comercialización de búsqueda [reglas](rules.md) la vista de tienda es 50.
- La comercialización de categorías puede tener una regla por categoría.
- El número máximo de condiciones por regla es 10.
- El número máximo de eventos por regla es 25.

## Sinónimos

- [!DNL Live Search] puede administrar hasta 200 [sinónimos](synonyms.md) por vista de tienda.
- No se admiten sinónimos de varias palabras.

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
- En este momento no se admite la compatibilidad con B2B con Live Search para PWA Studio.
