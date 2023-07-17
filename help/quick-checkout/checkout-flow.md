---
title: "Flujo de cierre de compra en Adobe Commerce"
description: '"Descripción general del [!DNL Quick Checkout] en Adobe Commerce".'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] Flujo

Esta sección proporciona información general sobre la experiencia típica de cierre de compra con [!DNL Quick Checkout] para la extensión de Adobe Commerce.

Un exitoso [!DNL Quick Checkout] El flujo de trabajo consiste en los siguientes pasos:

1. Abre tu tienda y agrega artículos al carro de compras.
1. Continúe con el cierre de compra.

![Finalizar compra](assets/proceed-checkout.png)

>[!NOTE]
>
> Puede activar el inicio de sesión automático para su comerciante. Consulte [Tema Activar inicio de sesión automático de perno](https://help.bolt.com/products/embedded/direct-api/auto-login/) para obtener más información.

1. Cuando se le solicite, introduzca una dirección de correo electrónico asociada a un [!DNL Bolt] cuenta.
1. Introduzca la contraseña única (OTP) que se le ha enviado [!DNL Bolt] dirección de correo electrónico o número de teléfono de la cuenta.

![Ventana emergente OTP](assets/new-logo-otp-email.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] cuenta, los detalles de cierre de compra se rellenan automáticamente:

   - Información de envío
   - Forma de pago

   >[!NOTE]
   >
   > Puede utilizar la información de su cartera existente (dirección o información de tarjeta de crédito) incluso si los datos de su pago se rellenan automáticamente.

1. Realizar pedido.

El [!DNL Quick Checkout] es compatible con las opciones de cierre de compra adicionales estándar de Adobe Commerce, como [tarjetas regalo](https://docs.magento.com/user-guide/catalog/product-gift-card.html) o [códigos de descuento](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] casos de uso

El [!DNL Quick Checkout] permite varios casos de uso durante un flujo de cierre de compra:

- [Usuario invitado](../quick-checkout/checkout-bolt.md) con un registrado o nuevo [!DNL Bolt] cuenta.
- Un existente [usuario de Adobe Commerce](../quick-checkout/checkout-adobe-commerce.md) con o sin registro [!DNL Bolt] cuenta.

## Obtener ayuda

Póngase en contacto con el Soporte técnico de Adobe Commerce a través de [Centro de ayuda de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) para cualquier ayuda.
