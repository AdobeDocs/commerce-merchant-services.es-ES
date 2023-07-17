---
title: "[!DNL Quick Checkout] para información de desarrollador de Adobe Commerce"
description: '"[!DNL Quick Checkout] información para desarrolladores".'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
feature: Checkout, Services
role: Developer
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] Información del desarrollador

Este tema contiene información para desarrolladores que trabajan en estrecha colaboración con Adobe Commerce y [!DNL Magento Open Source] y desea obtener información detallada sobre el [!DNL Quick Checkout] extensión.

## Puntos de extensión

Utilice puntos de extensión para personalizar [!DNL Quick Checkout].

Mediante los puntos de extensión, puede realizar personalizaciones sin alterar realmente los componentes principales del código de la aplicación.

## Paso Detalles de envío

Se puede utilizar un punto de extensión para personalizar la navegación automatizada por pasos después de iniciar sesión con [!DNL Bolt].

Una vez que un comprador inicia sesión con [!DNL Bolt], toda la información válida se rellena previamente y se redirige al paso de detalles de pago para realizar el pedido. Consulte la [flujo de cierre de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) para obtener más información.

Este punto de extensión permite evitar la navegación a un paso de pago y puede resultar útil en caso de que haya extensiones que requieran que un comprador realice acciones adicionales en el paso de envío. Consulte el siguiente ejemplo sobre cómo puede utilizar el punto de extensión con un mixin:

1. Registre un nuevo mixin en `require-config.js` archivo ubicado en `app/code/Vendor/ModuleName/view/frontend/`.

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

1. Amplíe el modelo en la `can-navigate-to-payment.js` archivo ubicado en `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> Este es un ejemplo para un comprador en Alemania (DE) que desea permanecer en el paso Detalles de envío.

Marque [[!DNL Bolt] ayuda para desarrolladores](https://help.bolt.com/developers/) para obtener más información sobre [!DNL Bolt] para desarrolladores.
