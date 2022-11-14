---
title: "Flujo de cierre de compra en Adobe Commerce"
description: '"Descripción general de la variable [!DNL Quick Checkout] en Adobe Commerce".'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: d28e8ccd4362b4e32b2eb8c6e1faf38d7c99a4c2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] flujo

En esta sección se ofrece una descripción general de la experiencia de cierre de compra típica mediante el uso de la variable [!DNL Quick Checkout] para la extensión de Adobe Commerce.

Un éxito [!DNL Quick Checkout] consiste en los siguientes pasos:

1. Abra la tienda y añada artículos al carro de compras.
1. Continúe con el cierre de compra.

![Cierre de compra](assets/proceed-checkout.png)

1. Cuando se le solicite, introduzca una dirección de correo electrónico asociada a un [!DNL Bolt] cuenta.
1. Introduzca la contraseña única (OTP) enviada a esa [!DNL Bolt] dirección de correo electrónico o número de teléfono de la cuenta.

![Ventana emergente de OTP](assets/pop-up.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] cuenta, los detalles de cierre de compra se rellenan automáticamente:

   - Información de envío
   - Método de pago

   >[!NOTE]
   >
   > Puede usar la información existente de la cartera (dirección o información de la tarjeta de crédito) incluso si los detalles de su pago se rellenan automáticamente.

1. Realizar pedido.

La variable [!DNL Quick Checkout] es compatible con las opciones de cierre de compra adicionales estándar de Adobe Commerce, como [tarjetas regalo](https://docs.magento.com/user-guide/catalog/product-gift-card.html) o [códigos de descuento](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] casos de uso

La variable [!DNL Quick Checkout] permite varios casos de uso durante un flujo de cierre de compra:

- [Usuario invitado](../quick-checkout/checkout-bolt.md) con un [!DNL Bolt] cuenta.
- Una [Usuario de Adobe Commerce](../quick-checkout/checkout-adobe-commerce.md) con o sin un registro [!DNL Bolt] cuenta.

## Obtener ayuda

Póngase en contacto con el servicio de asistencia de Adobe Commerce a través de la [Centro de ayuda de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) para cualquier ayuda.
