---
title: "Notas técnicas de la faceta"
description: '"Notas técnicas sobre el uso de [!DNL Live Search] facetas".'
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Notas técnicas de faceta

Las facetas son un método de filtrado de alto rendimiento que utiliza varias dimensiones de valores de atributo estáticos y dinámicos que permiten búsqueda como criterios de búsqueda.

[!DNL Live Search] utiliza el `productSearch` consulta que devuelve facetas y otros datos específicos de [!DNL Live Search]. Consulte [`productSearch` query](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) para ejemplos de código.

## Agregación de facetas

La agregación de facetas se realiza de la siguiente manera: si la tienda tiene tres facetas (categorías, color y precio) y el comprador filtra las tres (color = azul, el precio es de 10,00 a 50,00 $, categorías = `promotions`).

* `categories` agregación: agregados `categories`, y aplica el `color` y `price` filtros, pero no el `categories` filtro.
* `color` agregación: agregados `color`, y aplica el`price` y `categories` filtros, pero no el `color` filtro.
* `price` agregación: agregados `price`, y aplica el `color` y `categories` filtros, pero no el `price` filtro.
