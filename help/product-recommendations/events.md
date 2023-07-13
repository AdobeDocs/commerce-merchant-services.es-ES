---
title: Recopilar datos
description: Descubra cómo los eventos recopilan datos para las recomendaciones de productos.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Recopilar datos

Al instalar y configurar funciones de Adobe Commerce basadas en SaaS como [Product Recommendations](install-configure.md) o [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), los módulos implementan la recopilación de datos de comportamiento en la tienda. Este mecanismo recopila datos de comportamiento anónimos de los compradores y potencia las recomendaciones de productos. Por ejemplo, la variable `view` se utiliza para calcular el `Viewed this, viewed that` tipo de recomendación y el `place-order` se utiliza para calcular el `Bought this, bought that` tipo de recomendación.

>[!NOTE]
>
>La recopilación de datos a los efectos de las Recomendaciones del producto no incluye información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

Los siguientes eventos no son específicos de Product Recommendations, pero son necesarios para devolver resultados:

- `view`
- `add-to-cart`
- `place-order`

El [Recopilador de eventos de Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) enumera todos los eventos implementados en la tienda. Sin embargo, en esa lista hay un subconjunto de eventos específicos de Product Recommendations. Estos eventos recopilan datos cuando los compradores interactúan con las unidades de recomendación en la tienda y alimentan las métricas utilizadas para ayudarle a analizar el rendimiento de sus recomendaciones.

| Evento | Descripción | [¿Se utiliza para métricas?](workspace.md) |
| --- | --- | --- |
| `impression-render` | La unidad de recomendación se representa en la página. | Sí |
| `rec-add-to-cart-click` | El cliente hace clic en **Añadir al carro de compras** para un artículo en la unidad de recomendación. | Sí, cuando un **Añadir al carro de compras** está presente en la plantilla de recomendaciones. |
| `rec-click` | El cliente hace clic en un producto de la unidad de recomendación. | Sí |
| `view` | La unidad de recomendación se vuelve visible en la página, por ejemplo, desplazándose hasta la vista. | Sí |

Si la tienda está implementada con PWA Studio, consulte la [Documentación del PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si utiliza una tecnología de front-end personalizada como React o Vue JS, consulte la guía del usuario para aprender a integrar Product Recommendations en una [acéfalo](headless.md) entorno.

## Advertencias

Los bloqueadores de anuncios y la configuración de privacidad pueden evitar que `magento/product-recommendations` captura de eventos y podría causar la participación y los ingresos [métricas](workspace.md) que no se informe lo suficiente.

Eventing no registra todas las transacciones que se realizan en el sitio del comerciante. El objetivo de los eventos es dar al comerciante una idea general de los eventos que están ocurriendo en el sitio.

Las implementaciones sin encabezado deben implementar eventos para activar el tablero de Product Recommendations.

>[!NOTE]
>
>If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está activada, Adobe Commerce no recopilará datos de comportamiento hasta que el comprador acepte el uso de cookies. Si el modo de restricción de cookies está deshabilitado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.
