---
title: "[!DNL Quick Checkout] para información para desarrolladores de Adobe Commerce"
description: '"[!DNL Quick Checkout] información para desarrolladores".'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] información para desarrolladores

Este tema contiene información para los desarrolladores que trabajan estrechamente con Adobe Commerce y [!DNL Magento Open Source] y desea obtener información detallada sobre el [!DNL Quick Checkout] extensión.

## Puntos de extensión

Utilice los puntos de extensión para personalizar la variable [!DNL Quick Checkout].

Mediante el uso de puntos de extensión, puede realizar personalizaciones sin alterar realmente los componentes principales del código de la aplicación.

## Paso de detalles de envío

Se puede utilizar un punto de extensión para personalizar la navegación por pasos automatizada después de iniciar sesión con [!DNL Bolt].

Una vez que un comprador inicia sesión con [!DNL Bolt], toda la información válida se rellena previamente y se redirige al paso de detalles de pago para realizar el pedido. Consulte la [flujo de cierre de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) para obtener más información.

Este punto de extensión permite evitar la navegación a un paso de pago y puede resultar útil en caso de que haya extensiones que requieran un comprador para realizar acciones adicionales en el paso de envío. Vea a continuación un ejemplo de cómo puede utilizar el punto de extensión con una mezcla:

1. Registre una nueva mezcla en el `require-config.js` archivo ubicado en `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Amplíe el modelo en el `can-navigate-to-payment.js` archivo ubicado en `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> Este es un ejemplo para un comprador en Alemania (DE) que desea permanecer en el paso de detalles de envío.

Marque [[!DNL Bolt] ayuda para desarrolladores](https://help.bolt.com/developers/) para obtener más información sobre [!DNL Bolt] para desarrolladores.
