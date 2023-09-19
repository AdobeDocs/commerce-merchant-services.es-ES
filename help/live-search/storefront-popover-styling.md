---
title: "Estilo [!DNL Popover] Elementos"
description: "Notas técnicas sobre la personalización de [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Estilo [!DNL Popover] Elementos

El [[!DNL storefront popover]](storefront-popover.md) siempre muestra el producto `name` y `price`y la selección de campos no se puede configurar. Sin embargo, [!DNL popover] Los elementos de se pueden diseñar con clases CSS. Por ejemplo, las siguientes declaraciones cambian el color de fondo del [!DNL popover] contenedor y pie de página.

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

Los siguientes selectores de clase se pueden utilizar para aplicar estilo al contenedor y a los elementos de producto en la [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

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

## Trabajar con una temática modificada {#working-with-modified-theme}

El [!DNL storefront popover] se puede utilizar con un personalizado [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) que hereda los archivos necesarios de *Luma*. El `top.search` bloque en el `header-wrapper` de la `Magento_Search` El módulo no se debe modificar.

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
