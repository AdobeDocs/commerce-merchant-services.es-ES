---
title: '"Estilo [!DNL Popover] Elementos"'
description: '"Notas técnicas sobre la personalización de la variable [!DNL Live Search storefront popover]"'
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Estilo [!DNL Popover] Elementos

La variable [[!DNL storefront popover]](storefront-popover.md) muestra siempre el producto `name` y `price`, y la selección de campos no se puede configurar. Sin embargo, [!DNL popover] los elementos se pueden diseñar utilizando clases CSS. Por ejemplo, las siguientes declaraciones cambian el color de fondo del [!DNL popover] contenedor y pie de página.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilidad del contenedor

El componente principal del `.livesearch.popover-container` es `.search-autocomplete`.  La variable `.active` indica la visibilidad del contenedor. La variable `.active` se agrega condicionalmente cuando la variable [!DNL popover] está abierto.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Para obtener más información sobre el estilo de los elementos de tienda, consulte [Hojas de estilo en cascada (CSS)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) en el [Guía para desarrolladores de Frontend](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

## Selectores de clases

Los siguientes selectores de clase se pueden usar para aplicar estilo a los elementos de contenedor, sugerencia y producto en la [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.suggestions-container`
* `.livesearch.suggestions-header`
* `.livesearch.suggestion`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Selectores de clase de contenedor

`.livesearch.popover-container`

![[!DNL Popover] container](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![Ver todo el pie de página](assets/livesearch-view-all-footer.png)

### Selectores de clases de sugerencias

`.livesearch.suggestions-container`
![Contenedor de sugerencias](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`
![Encabezado Sugerencias](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`
![Sugerencia](assets/livesearch-suggestion.png)

### Selectores de clase de producto

`.livesearch.products-container`
![Contenedor de producto](assets/livesearch-product-container.png)

`.livesearch.product-result`
![Resultado del producto](assets/livesearch-product-result.png)

`.livesearch.product-name`
![Nombre del producto](assets/livesearch-product-name.png)

`.livesearch.product-price`
![Precio del producto](assets/livesearch-product-price.png)

## Trabajo con un tema modificado {#working-with-modified-theme}

La variable [!DNL storefront popover] se puede usar con un [tema](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) que hereda los archivos necesarios de *Luma*. La variable `top.search` en el `header-wrapper` del `Magento_Search` no debe modificarse.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Desactivación de la función [!DNL popover]

Para desactivar el [!DNL popover] y restaurar el estándar [Búsqueda rápida](https://docs.magento.com/user-guide/catalog/search-quick.html) , introduzca el siguiente comando:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
