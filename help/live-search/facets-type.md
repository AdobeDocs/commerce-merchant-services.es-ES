---
title: "Tipos de facetas"
description: '"[!DNL Live Search] las facetas son dinámicas y aparecen en la lista Filtros cuando son relevantes".'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: f96f94a16e1926b7dd2f1ee94f124ac0c823a9e0
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Tipos de facetas

[!DNL Live Search] utiliza una variedad de tipos de facetas, que aparecen en la variable *Filtros* enumere solo cuando sea relevante. La lista de facetas disponibles cambia según los productos devueltos. Las siguientes características afectan su presentación y comportamiento:

* Facetas ancladas: las facetas más utilizadas se pueden anclar al principio de la lista. Las facetas restantes se enumeran en *Tipo de orden* orden después de las facetas ancladas.
* Facetas dinámicas: atributos de producto que [Adobe Sensei](https://www.adobe.com/sensei.html) busca lo más relevante para un conjunto de productos y una consulta. El cálculo tiene en cuenta los metadatos de atributos de todo el catálogo y determina, en el momento de la consulta, las facetas más relevantes para la misma.
* Facetas populares: atributos de producto que están presentes con mayor frecuencia en los resultados de búsqueda.
* Facetas de precio - Devolver productos por rango de precios. Puede especificar el número de selecciones y el intervalo de rango de precios en la [*Configuración*](settings.md) workspace.

En el momento de la consulta, [!DNL Live Search] genera los resultados de búsqueda en grupos de facetas dinámicas y populares.

![Facetas: precio](assets/storefront-search-results-run-price.png)

## Opciones de tienda y sin encabezado

Facetas que se representan para [!DNL Commerce] el adaptador de búsqueda procesa las tiendas, que enruta las solicitudes y procesa los resultados en la tienda. Todo [!DNL Commerce] las facetas de tienda se ordenan alfabéticamente con opciones de selección única, independientemente del tipo de entrada asignado al atributo correspondiente. Las facetas disponibles en la tienda se procesan según la temática actual y reflejan las personalizaciones realizadas en la presentación de la navegación por capas.

Por el contrario, [acéfalo](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) La API procesa las implementaciones de y admite opciones adicionales. Las facetas sin encabezado se pueden ordenar alfabéticamente o por recuento, y pueden tener opciones de selección única o múltiple.

### Etiquetas de faceta

Para [!DNL Commerce] en las tiendas, la etiqueta de faceta está determinada por la variable [*Propiedades de atributo*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). En las tiendas con varias vistas, se pueden definir etiquetas adicionales en *Administrar etiquetas*. Para implementaciones sin encabezado, las etiquetas se editan desde el [faceting workspace](faceting-workspace.md).

### Tipo de orden

Todas las facetas representadas para la tienda se ordenan alfabéticamente. Para implementaciones sin encabezado, las facetas se pueden ordenar alfabéticamente o por recuento.

| Tipo de orden | Descripción |
|--- |--- |
| Alfabético | En la tienda *Filtros* , las facetas se ordenan alfabéticamente. |
| Recuento | (Solo sin encabezado) Para implementaciones sin encabezado, las facetas también se pueden ordenar por el número de valores encontrados por faceta en el conjunto actual de productos devueltos. |
