---
title: Notas técnicas de faceta
description: Notas técnicas sobre el uso de facetas de búsqueda activa.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Notas técnicas de faceta

La faceta es un método de filtrado de alto rendimiento que utiliza varias dimensiones de valores de atributos estáticos y dinámicos que se pueden buscar como criterios de búsqueda.

[!DNL Live Search] utiliza la variable `productSearch` consulta que devuelve facetas y otros datos específicos de [!DNL Live Search]. Consulte [`productSearch` query](https://devdocs.magento.com/live-search/product-search.html) para ver ejemplos de código.

## Acumulación de facetas

La agregación de facetas se realiza de la siguiente manera si la tienda tiene tres facetas (categorías, color y precio) y el comprador filtra las tres (color = azul, precio es de $10.00 a 50.00, categorías = `promotions`).

* `categories` agregación - Agregados `categories`, se aplica `color` y `price` filtros, pero no el `categories` filtro.
* `color` agregación - Agregados `color`, se aplica `price` y `categories` filtros, pero no el `color` filtro.
* `price` agregación - Agregados `price`, se aplica `color` y `categories` filtros, pero no el `price` filtro.

## Valores de atributo predeterminados

Los siguientes atributos de producto tienen algunas [propiedades de tienda](https://docs.magento.com/user-guide/stores/attributes-product.html) que están activados de forma predeterminada.

| Propiedad | Propiedad Storefront | Atributo |
|---|---|---|
| Ordenable | Se utiliza para ordenar en la lista de productos | `price` |
| Buscable | Usar en la búsqueda | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Uso en navegación por capas - filtrable (con resultados) | `price`<br />`visibility`<br />`category_name` |
