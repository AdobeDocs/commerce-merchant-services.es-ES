---
title: Introducción a [!DNL Live Search]
description: '"[!DNL Live Search] de Adobe Commerce ofrece una experiencia de búsqueda rápida, relevante e intuitiva".'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: d5df2a098dbbb2ecfb68c36dd12843c963d46b17
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Introducción a [!DNL Live Search]

[!DNL Live Search] es un servicio para Adobe Commerce que sustituye a las funciones de búsqueda estándar. El [!DNL Live Search] El módulo se instala con Composer y conecta el [!DNL Commerce] instalación en el [!DNL Live Search] [servicio](../landing/saas.md). Cuando está configurado, el campo de texto de búsqueda predeterminado se sustituye por el [!DNL Live Search] campo de texto. [!DNL Live Search] también instala el widget Página de lista de productos (PLP) que proporciona capacidades de filtrado sólidas al examinar los resultados de búsqueda.

[!DNL Live Search] aparece en la *Marketing* menú debajo de *SEO y búsqueda* en el [!DNL Commerce] *Administrador*.

La parte de Adobe Commerce de la arquitectura de incluye el alojamiento de la búsqueda *Administrador*, sincronizando los datos del catálogo y ejecutando el servicio de consulta. Después [!DNL Live Search] está instalado y configurado, Adobe Commerce comienza a compartir datos de búsqueda y catálogo con los servicios SaaS. En este punto, los usuarios administradores pueden configurar, personalizar y administrar la búsqueda [facetas](facets.md), [sinónimos](synonyms.md), y [reglas de comercialización](category-merch.md).

## Componentes de Live Search

* [!DNL Live Search] [widget emergente](storefront-popover.md) es el cuadro que se abre debajo del campo de búsqueda que contiene los resultados de la búsqueda.
* [Widget de página de lista de productos](plp-styling.md) proporciona una página de lista de productos en la que se puede buscar con soporte de facetas y sinónimos.
* AEM CIF Componentes de la: [Widget emergente](https://github.com/adobe/aem-cif-guides-venia/pull/319) y el [Widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEM permitir que los sitios aprovechen las ventajas [!DNL Live Search].
* [[!DNL Live Search] Administrador](workspace.md) es donde se configuran las reglas, las facetas y los sinónimos.

## Resumen de flujo de trabajo

[!DNL Live Search] funciona moviendo datos de catálogo a la infraestructura de SaaS de Adobe Commerce y creando índices que se utilizan para entregar rápidamente resultados de búsqueda a medida que los usuarios escriben.

### 1. Instalación

[!DNL Live Search] es [instalado](install.md) en la instancia de Adobe Commerce mediante [Compositor](https://getcomposer.org/). Esto instala los módulos necesarios que se conectan al servicio y configura la instancia de Commerce para que anule el campo de búsqueda predeterminado. También instala las opciones de administración de Commerce para configurar el servicio.

### 2. Sincronizar datos

[!DNL Live Search] mueve los datos del catálogo a la infraestructura de SaaS de Adobe. Los datos se indexan y los resultados de búsqueda se envían desde este índice directamente a la tienda. Según el tamaño y la complejidad, la indexación puede tardar entre 30 minutos y un par de horas.

### 3. Configurar datos

Configurar correctamente los datos del producto garantiza buenos resultados de búsqueda para los clientes. Se requieren un par de pasos de configuración: asignación de categorías y configuración de atributos.

#### Asignar categorías

Producto devuelto en [!DNL Live Search] debe tener asignado un [categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). En Luma, por ejemplo, los productos se clasifican en categorías como &quot;Hombres&quot;, &quot;Mujeres&quot; y &quot;Equipos&quot;. También se configuran subcategorías para &quot;Tops&quot;, &quot;Bottom&quot; y &quot;Watches&quot;. Esto permite una mejor granularidad al filtrar.

#### Campos que se pueden buscar y filtrar

Se asignan los productos [atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que se puede utilizar para buscar y filtrar. Los atributos son elementos como &quot;Color&quot;, &quot;Tamaño&quot; o &quot;Tipo de material&quot;. Con estos atributos, los usuarios pueden buscar &quot;tapas verdes&quot;. Cada producto puede tener muchos atributos definidos en el administrador de comercio.

Cada uno de estos atributos se puede definir como [&quot;buscable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) en el administrador. Cuando se establece como &quot;en los que se pueden realizar búsquedas&quot;, esos atributos están disponibles para su búsqueda [!DNL Live Search].

[Facetas](facets.md) son atributos de producto definidos en [!DNL Live Search] para poder filtrar. Cualquier atributo filtrable puede definirse como una faceta en [!DNL Live Search] pero hay límites a la cantidad de facetas que se pueden buscar al mismo tiempo.

[Sinónimos](synonyms.md) son términos que puede definir para ayudar a guiar a los usuarios hacia el producto correcto. Los usuarios que buscan pantalones pueden escribir &quot;pantalones&quot; o &quot;pantalones&quot;. Puede establecer sinónimos para que estos términos de búsqueda lleven a los usuarios a los resultados de &quot;pantalones&quot;.

## [!DNL Live Search] workspace

El [!DNL Live Search] [workspace](workspace.md) es el área del Administrador donde se configura [!DNL Live Search] funciones como sinónimos, facetas y comercialización de categorías.

## Eventos

[!DNL Live Search] utiliza [eventos](events.md) para calcular [Comercialización inteligente](category-merch.md) y [rendimiento](performance.md) paneles. Los eventos se proporcionan con implementaciones predeterminadas. Los eventos para tiendas sin encabezado deben habilitarse manualmente.

## Personalización de widgets

La mayoría de los propietarios de tiendas querrán asegurarse de que las [!DNL Live Search] Los widgets se ajustan a la apariencia de su tienda.

Los widgets de la ventana emergente y el PLP se pueden diseñar definiendo reglas CSS personalizadas según sea necesario. Consulte [Estilo de elementos emergentes](storefront-popover-styling.md) y [Widget de página de lista de productos](plp-styling.md).

Si desea ampliar la funcionalidad de los widgets, el código fuente de cada uno está disponible en un repositorio público.
En este escenario, puede personalizar JavaScript para sus propias necesidades y, a continuación, alojar el código personalizado en el sitio. Este script personalizado se comunica con el [!DNL Live Search] y devuelve los resultados como de costumbre, lo que le permite controlar la funcionalidad del widget.

* [Repositorio de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
* [Buscar repositorio de barra](https://github.com/adobe/storefront-search-as-you-type)

Obtenga más información sobre [!DNL Live Search] en el [Información general técnica](technical-overview.md).

## [!DNL Live Search] demostración

Vea este vídeo para obtener más información [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para ver un vídeo más detallado sobre cómo utilizar y configurar Live Search, consulte la [Demostración completa el [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) tema.
