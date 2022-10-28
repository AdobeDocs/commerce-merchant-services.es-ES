---
title: Recopilación de datos
description: Descubra cómo los eventos recopilan datos para recomendaciones de productos.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Recopilación de datos

Al instalar y configurar funciones de Adobe Commerce basadas en SaaS como [Recommendations de producto](install-configure.md) o [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), los módulos implementan la recopilación de datos de comportamiento en su tienda. Este mecanismo recopila datos de comportamiento anónimos de sus compradores y potencia las recomendaciones de productos. Por ejemplo, la variable `view` se utiliza para calcular la variable `Viewed this, viewed that` tipo de recomendación y la variable `place-order` se utiliza para calcular la variable `Bought this, bought that` tipo de recomendación.

>[!NOTE]
>
>La recopilación de datos a efectos de las recomendaciones de productos no incluye información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

Los siguientes eventos no son específicos de Product Recommendations, pero son necesarios para devolver resultados:

- `view`
- `add-to-cart`
- `place-order`

La variable [Recopilador de eventos de tienda de Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) enumera todos los eventos implementados en su tienda. Sin embargo, a partir de esa lista, hay un subconjunto de eventos específicos de Product Recommendations. Estos eventos recopilan datos cuando los compradores interactúan con las unidades de recomendación de la tienda y potencian las métricas utilizadas para ayudarle a analizar el rendimiento de las recomendaciones.

| Evento | Descripción | [¿Se utiliza para las métricas?](workspace.md) |
| --- | --- | --- |
| `impression-render` | La unidad de recomendación se representa en la página. | Sí |
| `rec-add-to-cart-click` | El cliente hace clic en el botón **Agregar al carro** para un artículo de la unidad de recomendación. | Sí, cuando **Agregar al carro** está presente en la plantilla de recomendaciones. |
| `rec-click` | El cliente hace clic en un producto en la unidad de recomendaciones. | Sí |
| `view` | La unidad de recomendación puede verse en la página, por ejemplo, si se desplaza a la vista. | Sí |

Si la tienda se implementa con PWA Studio, consulte la [documentación del PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si utiliza una tecnología de front-end personalizada, como React o Vue JS, consulte la guía del usuario para aprender a integrar Product Recommendations en un [headless](headless.md) entorno.

Los bloqueadores de anuncios y la configuración de privacidad pueden impedir que `magento/product-recommendations` desde la captura de eventos y podría causar la participación y los ingresos [métricas](workspace.md) que se van a subregistrar.

>[!NOTE]
>
>If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está habilitado, Adobe Commerce no recopila datos de comportamiento hasta que el comprador consienta en usar cookies. Si el modo de restricción de cookies está desactivado, Adobe Commerce recopila datos de comportamiento de forma predeterminada.
