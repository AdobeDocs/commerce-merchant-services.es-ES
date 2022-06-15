---
title: '"Flujo de cierre de compra"'
description: '"Descripción general de la variable [!DNL Quick Checkout] en Adobe Commerce".'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: c0b1185a53cb84be2335e2e1beb392c9f23070c9
workflow-type: tm+mt
source-wordcount: '553'
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

- Usuario invitado con un registro [!DNL Bolt] cuenta.
- Usuario invitado con un [!DNL Bolt] cuenta.
- Un usuario de Adobe Commerce existente con o sin una cuenta registrada [!DNL Bolt] cuenta.

## Cierre de compra del usuario invitado: Funcionamiento

La experiencia de cierre de compra de invitado es diferente a la experiencia de inicio de sesión. Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Quick Checkout] lo valida para encontrar un [!DNL Bolt] cuenta.

### Registrados [!DNL Bolt] account

Si [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su [!DNL Quick Checkout] experiencia de cierre de compra optimizada:

1. Introduzca la contraseña única (OTP) enviada a esa [!DNL Bolt] dirección de correo electrónico o móvil de la cuenta, según las preferencias del usuario en la [!DNL Bolt] cuenta.
1. Una vez que haya iniciado sesión con su [!DNL Bolt] rellena automáticamente los detalles de cierre de compra:

   - Información de envío
   - Método de pago

1. Realizar pedido.

>[!TIP]
>
> El usuario invitado realiza el pedido y puede registrarse en Adobe Commerce.

### Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado y el comprador proporciona todos los detalles necesarios para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparece una casilla de verificación para registrarse en [!DNL Bolt] para cierres de compra más rápidos antes de realizar el pedido. Pueden aceptar los términos y condiciones para crear sus [!DNL Bolt] cuenta.

   ![Recordar [!DNL Bolt]](assets/checked-bolt.png)

- El usuario invitado realiza el pedido y puede registrarse en Adobe Commerce.

## Un usuario de Adobe Commerce existente: Funcionamiento

Un usuario existente puede seleccionar detalles existentes cuando el usuario realiza un pedido con la variable [!DNL Quick Checkout] para una experiencia de cierre de compra más rápida.

Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Quick Checkout] lo valida para encontrar un [!DNL Bolt] cuenta.

### Registrados [!DNL Bolt] cuenta con un usuario de Adobe Commerce

Si [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador proporciona todos los detalles necesarios y luego realiza el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago

Si tiene problemas al realizar un pedido como usuario de Adobe Commerce existente, consulte la [Solución de problemas de cierre de compra rápido](https://support.magento.com/hc/en-us/articles/6909450342541) en el Centro de ayuda de Adobe Commerce.

>[!NOTE]
>
> Si el usuario tiene un [!DNL Bolt] La cuenta y el correo electrónico no aparecen como registrados en Adobe Commerce, sino que se déclencheur el inicio de sesión con una contraseña única (OTP). Consulte la [registrado [!DNL Bolt] account](#registered-bolt-account) flujo.

### Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador selecciona todos los detalles necesarios de su información guardada para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparece una casilla de verificación para registrarse en [!DNL Bolt] para cierres de compra más rápidos antes de realizar el pedido. Pueden aceptar los términos y condiciones para crear sus [!DNL Bolt] cuenta.

   ![Recordar [!DNL Bolt]](assets/checked-bolt.png)

## Obtener ayuda

Contacto [Asistencia de Adobe Commerce](mailto:quick-checkout-support@adobe.com) para cualquier ayuda.
