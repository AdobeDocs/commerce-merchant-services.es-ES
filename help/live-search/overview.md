---
title: Introducción a [!DNL Live Search]
description: '"[!DNL Live Search] de Adobe Commerce ofrece una experiencia de búsqueda rápida, relevante e intuitiva".'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Introducción a [!DNL Live Search]

[!DNL Live Search] es un servicio para Adobe Commerce que sustituye a las funciones de búsqueda estándar. El [!DNL Live Search] El módulo se instala con Composer y conecta el [!DNL Commerce] instalación en el [!DNL Live Search] [servicio](../landing/saas.md). Cuando está configurado, el campo de texto de búsqueda predeterminado se sustituye por el [!DNL Live Search] campo de texto. [!DNL Live Search] también instala el widget Página de lista de productos (PLP) que proporciona capacidades de filtrado sólidas al examinar los resultados de búsqueda.

[!DNL Live Search] aparece en la *Marketing* menú debajo de *SEO y búsqueda* en el [!DNL Commerce] *Administrador*.

La parte de Adobe Commerce de la arquitectura de incluye el alojamiento de la búsqueda *Administrador*, sincronizando los datos del catálogo y ejecutando el servicio de consulta. Después [!DNL Live Search] está instalado y configurado, Adobe Commerce comienza a compartir datos de búsqueda y catálogo con los servicios SaaS. En este punto, los usuarios administradores pueden configurar, personalizar y administrar la búsqueda [facetas](facets.md), [sinónimos](synonyms.md), y [reglas de comercialización](category-merch.md).

![Diagrama de arquitectura de Live Search](assets/architecture-diagram.svg)

## Componentes de Live Search

* [!DNL Live Search] [popover](storefront-popover.md) es el cuadro que se abre debajo del campo de búsqueda que contiene los resultados de la búsqueda.
* [Widget de página de lista de productos](plp-styling.md) proporciona una página de lista de productos en la que se puede buscar con soporte de facetas y sinónimos.
* AEM CIF Componentes de la: [Widget emergente](https://github.com/adobe/aem-cif-guides-venia/pull/319) y el [Widget PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEM permitir que los sitios aprovechen las ventajas [!DNL Live Search].
* [[!DNL Live Search] Administrador](workspace.md) es donde se configuran las reglas, las facetas y los sinónimos.
* Search Adapter es la implementación predeterminada de [!DNL Live Search]. Recomendado para implementaciones personalizadas y sin encabezado.

## [!DNL Live Search] demostración

Vea este vídeo para obtener más información [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para ver un vídeo más detallado sobre cómo utilizar y configurar Live Search, consulte la [Demostración completa el [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) tema.
