---
title: "[!DNL Storefront Popover]"
description: "La [!DNL Live Search storefront popover] devuelve dinámicamente productos sugeridos y miniaturas."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Cuándo [!DNL Live Search] es [instalado](install.md), a [!DNL popover] aparece en la tienda cuando los compradores escriben el [Buscar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) cuadro. Con cada carácter escrito, la variable [!DNL popover] se actualiza con productos sugeridos e imágenes en miniatura de los principales resultados de búsqueda.

[!DNL Live Search] devuelve los resultados de una consulta de dos caracteres o más. Para una coincidencia parcial, el número máximo de caracteres por palabra es 20. El número de caracteres de una consulta &quot;buscar mientras escribe&quot; no se puede configurar.

De forma predeterminada, [!DNL Live Search] admite [buscar redirecciones de términos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Obtenga información sobre cómo establecer atributos de producto tal como se pueden buscar en la [Configuración de Live Search](workspace.md) artículo.

## [!DNL Popover] tamaño de página

El tamaño de página del [!DNL popover] determina cuántas líneas de productos autocompletados se pueden devolver. Durante la instalación de Live Search, la variable `page_size` el valor cambia al valor actual de [Búsqueda en catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuración.

De forma predeterminada, el valor Búsqueda en el catálogo: Límite de autocompletar está establecido en ocho líneas (o filas). Para cambiar el tamaño de página de [!DNL popover], haga lo siguiente:

1. En el *Administrador* barra lateral, vaya a **Tiendas** > Configuración > **Configuración**.
1. En el panel izquierdo, expanda **Catálogo** y elija **Catálogo** de la lista de configuraciones.
1. Expanda el *Búsqueda en catálogo* sección.
1. Configure las variables **Límite de autocompletar** al número de líneas que desea permitir en el [!DNL popover].
1. Cuando termine, haga clic en **Guardar configuración**.

## Estilo [!DNL Popover] ejemplo

Puede personalizar el aspecto del diseño. [!DNL Popover] para que coincida con el estilo de su empresa y las directrices de marca.

El [!DNL storefront popover] siempre muestra el producto `name` y `price`y la selección de campos no se puede configurar. Sin embargo, [!DNL popover] Los elementos de se pueden diseñar utilizando [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) clases. Por ejemplo, las siguientes declaraciones cambian el color de fondo del [!DNL popover] contenedor y pie de página.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilidad del contenedor

El componente principal del `.livesearch.popover-container` es `.search-autocomplete`.  El `.active` indica la visibilidad del contenedor. El `.active` se añade condicionalmente cuando el [!DNL popover] está abierto.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Para obtener más información sobre el estilo de elementos de tienda, consulte [Hojas de estilos en cascada (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) en el [Guía para desarrolladores de Frontend](https://developer.adobe.com/commerce/frontend-core/guide/).

## Selectores de clase

Puede utilizar los siguientes selectores de clase para aplicar estilo al contenedor y a los elementos de producto en la [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

### Selectores de clase de contenedor

#### .livessearch.popover-container

![[!DNL Popover] contenedor](assets/livesearch-popover-container.png)

#### .livessearch.view-all-footer

![Ver todo el pie de página](assets/livesearch-view-all-footer.png)

### Selectores de clase de producto

#### .livessearch.products-container

![Contenedor de producto](assets/livesearch-product-container.png)

#### .livessearch.product-result

![Resultado del producto](assets/livesearch-product-result.png)

#### .livessearch.product-name

![Nombre del producto](assets/livesearch-product-name.png)

#### .livessearch.product-price

![Precio del producto](assets/livesearch-product-price.png)

#### .livessearch product-link

![Resultado del producto](assets/livesearch-product-link.png)

## Trabajar con una temática modificada {#working-with-modified-theme}

Puede usar el complemento [!DNL storefront popover] con un personalizado [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) que hereda los archivos necesarios de *Luma*. El `top.search` bloque en el `header-wrapper` de la `Magento_Search` El módulo no se debe modificar.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Desactivación de la [!DNL popover]

Para deshabilitar la variable [!DNL popover] y restaurar el estándar [Búsqueda rápida](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) , introduzca el siguiente comando:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## Implementaciones sin encabezado

Para las implementaciones sin encabezado, puede instalar el [!DNL Live Search popover] uso de un [npm package](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
