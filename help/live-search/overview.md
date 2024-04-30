---
title: Qué es [!DNL Live Search]?
description: '"[!DNL Live Search] de Adobe Commerce ofrece una experiencia de búsqueda rápida, relevante e intuitiva".'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 8aca09aba13e32afb191169729dfc1fbd0087262
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# Qué es [!DNL Live Search]?

[!DNL Live Search] es una extensión de que sustituye a las funciones de búsqueda estándar de Adobe Commerce. El [!DNL Live Search] La extensión se instala con Composer y conecta la [!DNL Commerce] instalación en el [!DNL Live Search] [servicio](../landing/saas.md). Cuando está configurado, el campo de texto de búsqueda predeterminado se sustituye por el [!DNL Live Search] campo de texto. [!DNL Live Search] también instala el widget Página de lista de productos (PLP), que proporciona capacidades de filtrado sólidas al examinar los resultados de búsqueda.

Con [!DNL Live Search], puede:

- Cree experiencias de búsqueda significativas para ayudar a los compradores y compradores a encontrar lo que desean con el menor esfuerzo posible.
- Aproveche el faceteo dinámico con tecnología de IA y la reclasificación de los resultados de búsqueda en respuesta a los comportamientos de los compradores durante la sesión.
- Utilice un servicio ligero basado en SaaS que ofrezca actualizaciones sencillas y esté incluido en su licencia, lo que reduce el coste total de propiedad.
- Obtenga información técnica al habilitar la API de graphQL, la flexibilidad sin encabezado, los entornos de zona protegida de API y el SaaS ultrarrápido.

>[!IMPORTANT]
>
>Cuando se trata de buscar sitios, Adobe Commerce le da opciones. Asegúrese de leer [Límites y límites](boundaries-limits.md) antes de la implementación, para garantizar que [!DNL Live Search] es una solución adecuada para sus necesidades empresariales.

## Arquitectura

La parte de Adobe Commerce de la arquitectura de incluye el alojamiento de la búsqueda *Administrador*, sincronizando los datos del catálogo y ejecutando el servicio de consulta. Después [!DNL Live Search] está instalado y configurado, Adobe Commerce comienza a compartir datos de búsqueda y catálogo con los servicios SaaS. En este punto, los usuarios administradores pueden configurar, personalizar y administrar la búsqueda [facetas](facets.md), [sinónimos](synonyms.md), y [reglas de comercialización](category-merch.md).

![Flujo de datos de Live Search](assets/ls-cs-data-flow.png)

## Explicación rápida

Centrándose en la velocidad, la relevancia y la facilidad de uso, [!DNL Live Search] es un punto de inflexión tanto para compradores como para comerciantes. Siga a lo largo para un rápido recorrido de [!DNL Live Search] de la tienda.

### Buscar mientras escribe

[!DNL Live Search] responde con productos sugeridos y una imagen en miniatura de los principales resultados de búsqueda en una [popover](storefront-popover.md) a medida que los compradores escriben consultas en [Buscar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) cuadro. El [información del producto](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) La página aparece cuando los compradores hacen clic en un producto sugerido o destacado. A _Ver todo_ El vínculo situado en el pie de página de la ventana emergente muestra la página de resultados de la búsqueda.

[!DNL Live Search] devuelve los resultados de &quot;buscar mientras escribe&quot; para una consulta de dos o más caracteres. Para una coincidencia parcial, el número máximo de caracteres por palabra es 20. El número de caracteres de la consulta no se puede configurar. La ventana emergente incluye el`name`, `sku`, y `category_ids` campos.

![Ejemplo de tienda - buscar mientras escribes](assets/storefront-search-as-you-type.png)

### Ver todos los resultados de búsqueda

Para enumerar todos los productos devueltos por la consulta &quot;buscar mientras escribe&quot;, haga clic en _Ver todo_ al pie de la ventana emergente.

![Ejemplo de tienda: facetas de precio](assets/storefront-view-all-search-results.png)

### Búsqueda filtrada con facetas

La búsqueda filtrada utiliza varias dimensiones de valores de atributo o [facetas](facets.md), como criterios de búsqueda. La selección de filtros la define el comerciante y cambia según los productos devueltos, con las facetas más utilizadas ancladas en la parte superior de la lista.

Utilice facetas como parámetros de URL:`http://yourwebsite.com?color=red`y Live Search filtran los resultados en función de estos valores de atributo.

### Sinónimos

[Sinónimos](synonyms.md) amplíe el alcance y enfoque las consultas incluyendo palabras que los compradores pueden utilizar y que difieren de las del catálogo. Puede ajustar el diccionario de sinónimos para mantener a los compradores comprometidos y en el camino de compra.

### Reglas de comercialización

Comercialización [reglas](rules.md) dé forma a la experiencia de compra con instrucciones if-then que agregan lógica y eventos a la búsqueda. Puede impulsar o enterrar fácilmente productos para una promoción, una temporada u otro período de tiempo.

### Compatibilidad con términos de búsqueda

[!DNL Live Search] admite Commerce [buscar redirecciones de términos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). Por ejemplo, los usuarios pueden buscar un término como &quot;Tarifas de envío&quot; y ser llevados directamente a la página de tarifas de envío.

## Componentes de Live Search

- [!DNL Live Search] [widget emergente](storefront-popover.md) es el cuadro que se abre debajo del campo de búsqueda que contiene los resultados de la búsqueda.
- [Widget de página de lista de productos](plp-styling.md) proporciona una página de lista de productos en la que se puede buscar con soporte de facetas y sinónimos.
- [[!DNL Live Search] Administrador](workspace.md) es donde se configuran las reglas, las facetas y los sinónimos.

## [!DNL Live Search] workspace

El [!DNL Live Search] [workspace](workspace.md) es el área del Administrador donde se configura [!DNL Live Search] funciones como sinónimos, facetas y comercialización de categorías.

## Eventos

[!DNL Live Search] utiliza [eventos](events.md) para calcular [Comercialización inteligente](category-merch.md) y [rendimiento](performance.md) paneles. Los eventos se proporcionan con implementaciones predeterminadas. Los eventos para tiendas sin encabezado deben habilitarse manualmente.

## [!DNL Live Search] demostración

Vea este vídeo para obtener más información [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para ver un vídeo más detallado sobre cómo utilizar y configurar Live Search, consulte la [Demostración completa el [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) tema.
