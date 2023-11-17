---
title: '[!DNL Live Search] Eventos'
description: Descubra cómo los eventos recopilan datos para [!DNL Live Search].
feature: Services, Eventing
source-git-commit: c14ba55bee54954ffcfe760e26dc1d69646ecd69
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# [!DNL Live Search] Eventos

[!DNL Live Search] utiliza eventos para activar algoritmos de búsqueda como &quot;Más visitados&quot; y &quot;Visualizó esto, Visualizó aquello&quot;. Mientras que los usuarios de LUMA obtienen eventos de forma predeterminada, las implementaciones sin encabezado y otras implementaciones personalizadas tienen que implementar eventos para sus propias necesidades.

Desde [!DNL Live Search] y [!DNL Product Recommendations] Si se utiliza el mismo algoritmo de backend, algunos eventos se comparten en ambos servicios. Algunos eventos de Product Recommendations son necesarios para rellenar el panel de Recommendations.

## Eventos

En esta tabla se describen los eventos que utiliza [!DNL Live Search] estrategias.

| Estrategia | Productos | Eventos | Página |
| --- | --- | --- | ---|
| Más visitados | Live Search<br>Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Más comprados | Live Search<br>Recs. de producto | vista de página<br>completar pago y envío | Carro/cierre de compra |
| Más añadidos al carro | Live Search<br>Recs. de producto | vista de página<br>añadir al carro | Página de detalles del producto<br>Página de lista de productos<br>Carrito<br>Lista de deseos |
| Vio esto, vio aquello. | Live Search<br>Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Tendencia | Live Search<br>Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Vio esto, compró aquello. | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto<br>Carro/cierre de compra |
| Compré esto, compré aquello. | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver para comprar | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver para comprar | Recs. de producto | vista de página<br>completar pago y envío | Carro/cierre de compra |
| Conversión: Ver al carro | Recs. de producto | vista de página<br>vista de producto | Página de detalles del producto |
| Conversión: Ver al carro | Recs. de producto | vista de página<br>añadir al carro | Página de detalles del producto<br>Página de lista de productos<br>Carrito<br>Lista de deseos |

>[!NOTE]
>
>Recopilación de datos a los efectos de [!DNL Live Search] no incluye información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

## Eventos de panel requeridos

Algunos eventos son necesarios para rellenar la variable [Tablero de Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/performance.html)

| Área de panel | Eventos |
| ----- | ---- | 
| Búsquedas únicas | `search-request-sent`,`search-response-received` |
| Búsquedas sin resultados | `search-request-sent`,`search-response-received` |
| Tasa de resultados cero | `search-request-sent`,`search-response-received` |
| Búsquedas frecuentes | `search-request-sent`,`search-response-received` |
| El Promedio de posición del clic | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Tasa de pulsaciones | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Tasa de conversión | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click`,`product-view`,`add-to-cart`,`place-order` |

### Contextos requeridos

Todos los eventos requieren lo siguiente `Page` y `Storefront` contextos. Esto debería suceder en el nivel de página/capa de aplicación de tienda en lugar de cuando se generan eventos individuales (por ejemplo, en una tienda PHP, el contenedor de la aplicación PHP es responsable de configurarlos durante la ejecución).

## Uso

Esta es una implementación de ejemplo de `search-request-sent` evento:

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

Los bloqueadores de anuncios y la configuración de privacidad pueden impedir que se capturen eventos y podrían causar participación e ingresos [métricas](workspace.md) que no se notifiquen suficientemente.

Eventing no registra todas las transacciones que se realizan en el sitio del comerciante. El objetivo de los eventos es dar al comerciante una idea general de los eventos que están ocurriendo en el sitio.

Las implementaciones sin encabezado deben implementar eventos para activar el [Tablero de Product Recommendations](../product-recommendations/events.md).

>[!NOTE]
>
>If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está activada, Adobe Commerce no recopilará datos de comportamiento hasta que el comprador acepte el uso de cookies. Si el modo de restricción de cookies está deshabilitado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.
