---
title: Sin encabezado
description: Aprenda a integrar [!DNL Product Recommendations] en una tienda sin cabeza.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Sin encabezado

Puede integrar [!DNL Product Recommendations] en una tienda sin encabezado que utilice [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) o una tecnología de front-end personalizada, como React o Vue JS.

[!DNL Product Recommendations] requerir [datos de comportamiento y catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) para funcionar. El proceso de sincronización de datos del catálogo permanece sin cambios en una implementación sin objetivos, pero se necesitan cambios para la recopilación de datos de comportamiento.

Para integrar [!DNL Product Recommendations] en una tienda sin periféricos, debe:

1. Envíe datos de comportamiento a Adobe Sensei para analizar y calcular los resultados de Recomendaciones de productos. También puede enviar datos adicionales para habilitar la recomendación del producto [informes de métricas](workspace.md).

1. Busque los resultados de recomendaciones de productos y represente esos resultados en la página.

Puede realizar ambas acciones utilizando los SDK disponibles, tal como se describe en el flujo de trabajo siguiente.

1. [Instalar](install-configure.md) el [!DNL Product Recommendations] módulo.

1. Instale y use el [SDK de Evento de tienda de Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) para activar el [eventos de comportamiento](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   El mínimo de eventos necesarios para devolver [!DNL Product Recommendations] resultados:

   | Evento | Categoría |
   |--- | ---|
   | `view` | producto |
   | `add-to-cart` | producto |
   | `place-order` | cierre de compra |

   Para habilitar [informes de métricas](workspace.md), se requieren los siguientes eventos adicionales:

   | Evento | Categoría |
   |--- | ---|
   | `impression-render` | unidad de recomendación |
   | `view` | unidad de recomendación |
   | `rec-click` | unidad de recomendación |
   | `rec-add-to-cart-click` | unidad de recomendación (si hay un botón agregar al carro en la plantilla de recomendaciones) |

1. Cuando se activen los eventos, utilice la variable [Recopilador de eventos de tienda de Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) para gestionar los eventos y enviarlos a Adobe Sensei.

1. Una vez recopilados los datos de comportamiento, puede [crear](create.md) [!DNL Product Recommendations] en el menú

1. Utilice la variable [SDK de Recommendations](https://developer.adobe.com/commerce/services/product-recommendations/) para recuperar las unidades de recomendación en la tienda. El SDK devuelve los datos de producto necesarios para procesar las unidades de recomendación en una página.
