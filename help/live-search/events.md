---
title: '[!DNL Live Search] eventos'
description: Descubra cómo los eventos recopilan datos para  [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] eventos

[!DNL Live Search] utiliza eventos para activar algoritmos de búsqueda como &quot;Más visitados&quot; y &quot;Visualizó esto, Visualizó aquello&quot;. Mientras que los usuarios de LUMA obtienen eventos de forma predeterminada, las implementaciones sin encabezado y otras implementaciones personalizadas tienen que implementar eventos para sus propias necesidades.

Dado que [!DNL Live Search] y [!DNL Product Recommendations] utilizan el mismo algoritmo de backend, algunos eventos son compartidos por ambos servicios. Algunos eventos de Product Recommendations son necesarios para rellenar el panel de Recommendations.

En esta tabla se describen los eventos utilizados por las estrategias de [!DNL Live Search].

| Estrategia | Productos | Eventos | Página |
| --- | --- | --- | ---|
| Más visitados | Live Search<br>Notas de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Más comprados | Live Search<br>Notas de producto | vista de página<br>cierre de compra completo | Carro/cierre de compra |
| Más añadidos al carro | Live Search<br>Notas de producto | vista de página<br>agregar al carro de compras | Página de detalles del producto<br>Página de lista de productos<br>Carro<br>Lista de deseos |
| Vio esto, vio aquello. | Live Search<br>Notas de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Tendencia | Live Search<br>Notas de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Vio esto, compró aquello. | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto<br>Carro/Cierre de compra |
| Compré esto, compré aquello. | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver para comprar | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver para comprar | Recs. de producto | vista de página<br>cierre de compra completo | Carro/cierre de compra |
| Conversión: Ver al carro | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver al carro | Recs. de producto | vista de página<br>agregar al carro de compras | Página de detalles del producto<br>Página de lista de productos<br>Carro<br>Lista de deseos |

>[!NOTE]
>
>La recopilación de datos a los efectos de [!DNL Live Search] no incluye información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

## Eventos de panel requeridos

Se requieren algunos eventos para rellenar el [tablero de Live Search](performance.md)

| Área de panel | Eventos | Campo de combinación |
| ------------------- | ------------- | ---------- |
| Búsquedas únicas | `page-view`, `search-request-sent`, | searchRequestId |
| Búsquedas sin resultados | `page-view`, `search-request-sent`, | searchRequestId |
| Tasa de resultados cero | `page-view`, `search-request-sent`, | searchRequestId |
| Búsquedas frecuentes | `page-view`, `search-request-sent`, | searchRequestId |
| El Promedio de posición del clic | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| Tasa de pulsaciones | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| Tasa de conversión | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### Contextos requeridos

Todos los eventos requieren los contextos `Page` y `Storefront`. Esto debería suceder en el nivel de página/capa de aplicación de tienda en lugar de cuando se generan eventos individuales (por ejemplo, en una tienda PHP, el contenedor de la aplicación PHP es responsable de configurarlos durante la ejecución).

## Uso

Esta es una implementación de ejemplo del evento `search-request-sent`:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Advertencias

Los bloqueadores de anuncios y la configuración de privacidad pueden impedir que se recopilen eventos y provocar que las [métricas](workspace.md) de participación e ingresos no se comuniquen correctamente.

Eventing no registra todas las transacciones que se realizan en el sitio del comerciante. El objetivo de los eventos es dar al comerciante una idea general de los eventos que están ocurriendo en el sitio.

Las implementaciones sin encabezado deben implementar eventos para activar [el tablero de Recommendations del producto](../product-recommendations/events.md).

>[!NOTE]
>
>Si el [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está habilitado, Adobe Commerce no recopilará datos de comportamiento hasta que el comprador acepte el uso de cookies. Si el modo de restricción de cookies está deshabilitado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.
