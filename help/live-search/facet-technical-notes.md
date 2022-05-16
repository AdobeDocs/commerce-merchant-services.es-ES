---
title: '"Notas técnicas de faceta"'
description: '"Notas técnicas sobre el uso de [!DNL Live Search] facetas".'
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '112'
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
