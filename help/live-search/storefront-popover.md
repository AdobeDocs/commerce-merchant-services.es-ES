---
title: "[!DNL Storefront Popover]"
description: '"El [!DNL Live Search storefront popover] devuelve de forma dinámica productos sugeridos y miniaturas".'
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# [!DNL Storefront Popover]

When [!DNL Live Search] es [instalado](install.md), [!DNL popover] aparece en la tienda cuando los compradores escriben en la [Buscar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) en la ventana Con cada carácter escrito, la variable [!DNL popover] se actualiza con productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda.

[!DNL Live Search] devuelve los resultados de una consulta de dos caracteres o más. Para una coincidencia parcial, el número máximo de caracteres por palabra es de 20. El número de caracteres de una consulta &quot;buscar mientras escribe&quot; no se puede configurar.

## Atributos que se pueden buscar

Para obtener resultados con objetivos muy precisos, revise el conjunto de [buscable](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`). Para garantizar la relevancia, haga que los atributos solo se puedan buscar si contienen contenido que tenga un significado claro y conciso. Evite utilizar atributos que contengan texto más largo y menos preciso, como `description`, que aunque la opción de búsqueda está activada de forma predeterminada, puede reducir la precisión de los resultados de búsqueda. Por ejemplo, si una persona busca &quot;pantalones cortos&quot; y hay camisas con una descripción que incluye el término &quot;mangas cortas&quot;, entonces las camisas se incluirán en los resultados de búsqueda.

Siempre se pueden buscar los atributos siguientes:

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] tamaño de página

El tamaño de página de la variable [!DNL popover] determina cuántas líneas de productos completados automáticamente se pueden devolver. Anteriormente, el tamaño de la página se codificaba como seis líneas. Sin embargo, la variable `page_size` ahora es una configuración que se puede configurar desde la variable *Administrador*. Durante la instalación de Live Search, la variable `page_size` cambia al valor actual del [Buscar en el catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuración.

De forma predeterminada, el valor Búsqueda en el catálogo - Límite de autocompletar está establecido en ocho líneas (o filas). Para cambiar el tamaño de página de la variable [!DNL popover], haga lo siguiente:

1. En el *Administrador* barra lateral, vaya a **Almacenes** > Configuración > **Configuración**.
1. En el panel izquierdo, expanda **Catálogo** y elija **Catálogo** de la lista de ajustes.
1. Expanda el *Buscar en el catálogo* para obtener más información.
1. Configure las variables **Límite de autocompletado** al número de líneas que desea permitir en la variable [!DNL popover].
1. Cuando termine, haga clic en **Guardar configuración**.

## Limitaciones

* La variable [!DNL Live Search] [!DNL storefront popover] solo está disponible para las tiendas que usan la variable *Luma* o un tema personalizado basado en *Luma*.
* La variable [!DNL popover] no admite la variable *En blanco* tema. Consulte [Estilo [!DNL Popover] Elementos](storefront-popover-styling.md) para obtener más información.
* La variable [!DNL popover] no es compatible con el formulario de pedido rápido.
* Los comerciantes pueden personalizar y ampliar las utilidades o los elementos de tienda (por ejemplo: integración de muestras de color en resultados de búsqueda activa) utilizando la variable [Servicio de catálogo](../catalog-service/overview.md) La API de tienda, pero esto no está disponible para el equipo de asistencia de Adobe.
