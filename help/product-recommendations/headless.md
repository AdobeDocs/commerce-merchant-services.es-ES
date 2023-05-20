---
title: Headless
description: Aprenda a integrar [!DNL Product Recommendations] en una tienda sin encabezado.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Headless

Se puede integrar [!DNL Product Recommendations] en una tienda sin encabezado con [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) o una tecnología de front-end personalizada, como React o Vue JS.

Los integradores personalizados y sin encabezado deben consultar estas instrucciones de Luma y del PWA como una implementación sugerida. Existen muchas maneras de implementar Product Recommendations en soluciones sin encabezado, y esta documentación no cubre todos los escenarios. Los integradores deben cubrir eventos, diseño y pruebas para sus implementaciones.

[!DNL Product Recommendations] requerir [datos de catálogo y comportamiento](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) para operar. El proceso de sincronización de datos del catálogo permanece sin cambios en una implementación sin encabezado, pero se necesitan cambios para la recopilación de datos de comportamiento.

>[!NOTE]
>
>Las instancias sin encabezado deben implementar eventos para activar el tablero de Product Recommendations.

Para integrar [!DNL Product Recommendations] en una tienda sin encabezado, debes:

1. Envíe datos de comportamiento a Adobe Sensei para analizar y calcular los resultados de recomendaciones de productos. También puede enviar datos adicionales para habilitar la recomendación de productos [informes de métricas](workspace.md).

1. Busque resultados de recomendaciones de productos y procese esos resultados en la página.

Puede realizar ambas acciones utilizando los SDK disponibles como se describe en el siguiente flujo de trabajo.

1. [Instalar](install-configure.md) el [!DNL Product Recommendations] módulo.

1. Instalación y uso de [SDK de eventos de Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) para activar el [eventos de comportamiento](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   El mínimo de eventos requeridos para devolver [!DNL Product Recommendations] resultados:

   | Evento | Categoría |
   |--- | ---|
   | `view` | producto |
   | `add-to-cart` | producto |
   | `place-order` | pago y envío |

   Para habilitar [informes de métricas](workspace.md), se requieren los siguientes eventos adicionales:

   | Evento | Categoría |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | recommendation-unit (si hay un botón &quot;Agregar al carro de compras&quot; en la plantilla de recomendaciones) |

1. Cuando se activen los eventos, utilice el [Recopilador de eventos de Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) para gestionar los eventos y enviarlos a Adobe Sensei.

1. Una vez recopilados los datos de comportamiento, puede [crear](create.md) [!DNL Product Recommendations] en el Administrador.

1. Utilice el [SDK de Recommendations](https://developer.adobe.com/commerce/services/product-recommendations/) para recuperar las unidades de recomendación en la tienda. El SDK devuelve los datos de producto necesarios para procesar las unidades de recomendación en una página.
