---
title: Entrega de tienda
description: La ventana emergente de tienda de Live Search devuelve dinámicamente los productos sugeridos y las miniaturas.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 10cea4389d685ce0e26b083872b13a1cd19ba2af
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Entrega de tienda

When [!DNL Live Search] es [instalado](install.md), aparece una ventana emergente en la tienda cuando los compradores escriben en la [Buscar](https://docs.magento.com/user-guide/catalog/search-quick.html) en la ventana Con cada carácter escrito, la ventana emergente se actualiza con productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda.

[!DNL Live Search] devuelve los resultados de una consulta de dos caracteres o más. Para una coincidencia parcial, el número máximo de caracteres por palabra es de 20. El número de caracteres de una consulta &quot;buscar mientras escribe&quot; no se puede configurar.

>[!NOTE]
>
>La variable [!DNL Live Search] la ventana emergente de tienda solo está disponible para las tiendas que usan la variable *Luma* o un tema personalizado basado en *Luma*. La variable *Luma* se incluye en el [!DNL Commerce] datos de ejemplo. La ventana emergente no admite la variable *En blanco* tema. Consulte [Trabajo con un tema modificado](#working-with-modified-theme) para obtener más información.

## Atributos que se pueden buscar

Para obtener resultados con objetivos muy precisos, revise el conjunto de [buscable](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`). Para garantizar la relevancia, haga que los atributos solo se puedan buscar si contienen contenido que tenga un significado claro y conciso. Evite utilizar atributos que contengan texto más largo y menos preciso, como `description`, que aunque la opción de búsqueda está activada de forma predeterminada, puede reducir la precisión de los resultados de búsqueda. Por ejemplo, si una persona busca &quot;pantalones cortos&quot; y hay camisas con una descripción que incluye el término &quot;mangas cortas&quot;, entonces las camisas se incluirán en los resultados de búsqueda.

Siempre se pueden buscar los atributos siguientes:

* `sku`
* `name`
* `categories`

![Opción de búsqueda en directo](assets/storefront-search-as-you-type.png)

## Tamaño de página emergente

El tamaño de página de la ventana emergente determina cuántas líneas de productos completados automáticamente se pueden devolver. Anteriormente, el tamaño de la página se codificaba como seis líneas. Sin embargo, la variable `page_size` ahora es una configuración que se puede configurar desde la variable *Administrador*. Durante la instalación de Live Search, la variable `page_size` cambia al valor actual del [Buscar en el catálogo](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` configuración.

De forma predeterminada, el valor Búsqueda en el catálogo - Límite de autocompletar está establecido en ocho líneas (o filas). Para cambiar el tamaño de la página de la ventana emergente, haga lo siguiente:

1. En el *Administrador* barra lateral, vaya a **Almacenes** > Configuración > **Configuración**.
1. En el panel izquierdo, expanda **Catálogo** y elija **Catálogo** de la lista de ajustes.
1. Expanda el *Buscar en el catálogo* para obtener más información.
1. Configure las variables **Límite de autocompletado** al número de líneas que desea permitir en la ventana emergente.
1. Cuando termine, haga clic en **Guardar configuración**.
