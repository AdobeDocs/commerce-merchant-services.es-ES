---
title: Flujo de cierre de compra
description: Información general sobre [!DNL Express Checkout] en Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# [!DNL Express Checkout] flujo

>[!IMPORTANT]
>
> Esta función es para usuarios del Programa de Adoptadores Anticipados (EAP, por sus siglas en inglés) y aún no es accesible para todos los clientes. Actualmente está limitado a los clientes de EE. UU. Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.

En esta sección se ofrece una descripción general de la experiencia de cierre de compra típica mediante el uso de la variable [!DNL Express Checkout] para la extensión de Adobe Commerce.

Un éxito [!DNL Express Checkout] consiste en los siguientes pasos:

1. Abra la tienda y añada artículos al carro de compras.
1. Continúe con el cierre de compra.

![Cierre de compra](../assets/proceed-checkout.png)

1. Cuando se le solicite, introduzca una dirección de correo electrónico asociada a una cuenta de Bolt.
1. Introduzca la contraseña única (OTP) enviada a la dirección de correo electrónico o el número de teléfono de esa cuenta de Bolt.
1. Una vez que haya iniciado sesión con su cuenta de Bolt, los detalles de cierre de compra se rellenan automáticamente:

   - Información de envío
   - Método de pago

   >[!NOTE]
   >
   > Puede usar la información existente de la cartera (dirección o información de la tarjeta de crédito) incluso si los detalles de su pago se rellenan automáticamente.

1. Realizar pedido.

La variable [!DNL Express Checkout] es compatible con las opciones de cierre de compra adicionales estándar de Adobe Commerce, como [tarjetas regalo](https://docs.magento.com/user-guide/catalog/product-gift-card.html) o [códigos de descuento](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] casos de uso

La variable [!DNL Express Checkout] permite varios casos de uso durante un flujo de cierre de compra:

- Usuario invitado con una cuenta de Bolt registrada.
- Usuario invitado con una nueva cuenta de Bolt.
- Un usuario de Adobe Commerce existente con o sin una cuenta de Bolt registrada.

## Cierre de compra del usuario invitado: Funcionamiento

La experiencia de cierre de compra de invitado es diferente a la experiencia de inicio de sesión. Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Express Checkout] lo valida para encontrar una cuenta de Bolt existente.

### Cuenta de Bolt registrada

Si se encuentra una cuenta de Bolt, los compradores continúan con su [!DNL Express Checkout] experiencia de cierre de compra optimizada:

1. Introduzca la contraseña única (OTP) enviada a la dirección de correo electrónico o móvil de esa cuenta de Bolt, según las preferencias del usuario en la cuenta de Bolt.
1. Una vez que haya iniciado sesión con su cuenta de Bolt, rellenará automáticamente los detalles de cierre de compra:

   - Información de envío
   - Método de pago

1. Realizar pedido.

>[!TIP]
>
> El usuario invitado realiza el pedido y puede registrarse en Adobe Commerce.

### Nueva cuenta de perno

Si no se encuentra ninguna cuenta de Bolt, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador proporciona todos los detalles necesarios para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparece una casilla de verificación para registrarse en Bolt para realizar cierres de compra más rápidos antes de realizar el pedido. Pueden aceptar los términos y condiciones para crear su cuenta de Bolt.

   ![Recordar perno](../assets/checked-bolt.png)

- El usuario invitado realiza el pedido y puede registrarse en Adobe Commerce.

## Un usuario de Adobe Commerce existente: Funcionamiento

Un usuario existente puede seleccionar detalles existentes cuando el usuario realiza un pedido con la variable [!DNL Express Checkout] para una experiencia de cierre de compra más rápida.

Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Express Checkout] lo valida para encontrar una cuenta de Bolt existente.

### Cuenta de Bolt registrada con un usuario de Adobe Commerce

Si se encuentra una cuenta de Bolt, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador proporciona todos los detalles necesarios y luego realiza el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago

Consulte la [solución de problemas](../express-checkout/troubleshooting.md) para obtener más información si tiene problemas al realizar un pedido como usuario de Adobe Commerce existente.

>[!NOTE]
>
> Si el usuario tiene una cuenta de Bolt y el correo electrónico no aparece como registrado en Adobe Commerce, se déclencheur el inicio de sesión con la contraseña única (OTP). Consulte la [cuenta de Bolt registrada](#registered-bolt-account) flujo.

### Nueva cuenta de perno

Si no se encuentra ninguna cuenta de Bolt, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador selecciona todos los detalles necesarios de su información guardada para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparece una casilla de verificación para registrarse en Bolt para realizar cierres de compra más rápidos antes de realizar el pedido. Pueden aceptar los términos y condiciones para crear su cuenta de Bolt.

   ![Recordar perno](../assets/checked-bolt.png)

## Obtener ayuda

Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.
