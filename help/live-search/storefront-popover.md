---
title: "[!DNL Storefront Popover]"
description: "La [!DNL Live Search storefront popover] devuelve dinámicamente productos sugeridos y miniaturas."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 92889130fd7482e0b99fb08746e6fd2830b0345e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Cuándo [!DNL Live Search] es [instalado](install.md), a [!DNL popover] aparece en la tienda cuando los compradores escriben el [Buscar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) cuadro. Con cada carácter escrito, la variable [!DNL popover] se actualiza con productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda.

[!DNL Live Search] devuelve los resultados de una consulta de dos caracteres o más. Para una coincidencia parcial, el número máximo de caracteres por palabra es 20. El número de caracteres de una consulta &quot;buscar mientras escribe&quot; no se puede configurar.

## Atributos de búsqueda

Para obtener resultados con objetivos muy precisos, revise el conjunto de [investigable](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) atributos del producto. Para garantizar la relevancia, haga que los atributos solo se puedan buscar si contienen contenido que tenga un significado claro y conciso. Evite utilizar atributos que contengan texto menos preciso y largo, como `description`, que aunque la búsqueda está habilitada de forma predeterminada, puede reducir la precisión de los resultados de búsqueda. Por ejemplo, si una persona busca &quot;pantalones cortos&quot; y hay camisas con una descripción que incluye el término &quot;mangas cortas&quot;, entonces las camisas se incluirán en los resultados de búsqueda.

Siempre se pueden buscar los atributos siguientes:

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] tamaño de página

El tamaño de página del [!DNL popover] determina cuántas líneas de productos autocompletados se pueden devolver. Anteriormente, el tamaño de página estaba codificado como seis líneas. Sin embargo, la variable `page_size` ahora es una configuración que se puede configurar desde el *Administrador*. Durante la instalación de Live Search, la variable `page_size` el valor cambia al valor actual de [Búsqueda en catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuración.

De forma predeterminada, el valor Búsqueda en el catálogo: Límite de autocompletar está establecido en ocho líneas (o filas). Para cambiar el tamaño de página de [!DNL popover], haga lo siguiente:

1. En el *Administrador* barra lateral, vaya a **Tiendas** > Configuración > **Configuración**.
1. En el panel izquierdo, expanda **Catálogo** y elija **Catálogo** de la lista de configuraciones.
1. Expanda el *Búsqueda en catálogo* sección.
1. Configure las variables **Límite de autocompletar** al número de líneas que desea permitir en el [!DNL popover].
1. Cuando termine, haga clic en **Guardar configuración**.

## Limitaciones

* El [!DNL Live Search] [!DNL storefront popover] solo está disponible para tiendas que utilizan el *Luma* o una temática personalizada que se base en *Luma*.
* El [!DNL popover] no es compatible con *Vacío* tema. Consulte [Estilo [!DNL Popover] Elementos](storefront-popover-styling.md) para obtener más información.
* El [!DNL popover] no es compatible con el formulario de pedido rápido.
