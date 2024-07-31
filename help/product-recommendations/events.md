---
title: Recopilar datos
description: Descubra cómo los eventos recopilan datos para las recomendaciones de productos.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 67296ea42bfddb10b0c86cb1ca47324f5fec7825
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Recopilar datos

Al instalar y configurar características de Adobe Commerce basadas en SaaS como [Product Recommendations](install-configure.md) o [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), los módulos implementan la recopilación de datos de comportamiento en su tienda. Este mecanismo recopila datos de comportamiento anónimos de los compradores y potencia las recomendaciones de productos. Por ejemplo, el evento `view` se usa para calcular el tipo de recomendación `Viewed this, viewed that`, y el evento `place-order` se usa para calcular el tipo de recomendación `Bought this, bought that`.

>[!NOTE]
>
>La recopilación de datos a los efectos de las Recomendaciones del producto no incluye información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. Más información [más](https://www.adobe.com/privacy/experience-cloud.html).

Los siguientes eventos no son específicos de Product Recommendations, pero son necesarios para devolver resultados:

- `view`
- `add-to-cart`
- `place-order`

El [Recopilador de eventos de Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) enumera todos los eventos implementados en tu tienda. Sin embargo, en esa lista hay un subconjunto de eventos específicos de Product Recommendations. Estos eventos recopilan datos cuando los compradores interactúan con las unidades de recomendación en la tienda y alimentan las métricas utilizadas para ayudarle a analizar el rendimiento de sus recomendaciones.

| Evento | Descripción | ¿Se utiliza para métricas? |
| --- | --- | --- |
| `impression-render` | La unidad de recomendación se representa en la página. | Sí |
| `rec-add-to-cart-click` | El cliente hace clic en el botón **Agregar al carro** de un artículo de la unidad de recomendación. | Sí, cuando hay un botón **Agregar al carro** en la plantilla de recomendaciones. |
| `rec-click` | El cliente hace clic en un producto de la unidad de recomendación. | Sí |
| `view` | La unidad de recomendación se vuelve visible en la página, por ejemplo, desplazándose hasta la vista. | Sí |

Se requieren los siguientes eventos para rellenar correctamente el panel.

| Columna del panel | Eventos | Campo de combinación |
| ---------------- | --------- | ----------- |
| Impresiones | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId |
| Vistas | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId |
| Clics | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | unitId |
| Ingresos | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| Ingresos LT | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Si su tienda está implementada con PWA Studio, consulte la [documentación del PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si usa tecnología de front-end personalizada como React o Vue JS, consulte la guía del usuario para aprender a integrar [Product Recommendations en un entorno sin encabezado](headless.md).

## Advertencias

Los bloqueadores de anuncios y la configuración de privacidad pueden impedir que el módulo `magento/product-recommendations` capture eventos y podrían provocar que las [métricas](workspace.md) de participación e ingresos no se informen correctamente.

Eventing no registra todas las transacciones que se realizan en el sitio del comerciante. El objetivo de los eventos es dar al comerciante una idea general de los eventos que están ocurriendo en el sitio.

Las implementaciones sin encabezado deben implementar eventos para activar el tablero de Product Recommendations.

>[!NOTE]
>
>Si el [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está habilitado, Adobe Commerce no recopilará datos de comportamiento hasta que el comprador acepte el uso de cookies. Si el modo de restricción de cookies está deshabilitado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.
