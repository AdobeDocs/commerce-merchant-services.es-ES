---
title: "Flujo de cierre de compra de un usuario de Bolt en Adobe Commerce"
description: Descripción general de [!DNL Quick Checkout] flujo para un usuario de Pernos en Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Usuarios invitados

La experiencia de cierre de compra de los invitados es diferente de la experiencia del usuario de Adobe. Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Quick Checkout] lo valida y encuentra un existente [!DNL Bolt] cuenta.

>[!WARNING]
>
> El [!DNL In-Store Pickup] (ISPU) no es compatible cuando el [!DNL Quick Checkout] está activada.

## Registrados [!DNL Bolt] account

Si un [!DNL Bolt] Se ha encontrado la cuenta de, los compradores continúan con su [!DNL Quick Checkout] experiencia de pago y envío perfecta:

1. Introduzca la contraseña única (OTP) que se le ha enviado [!DNL Bolt] dirección de correo electrónico o móvil de la cuenta, según [preferencias del usuario en la [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Ventana emergente OTP](assets/new-logo-otp-email.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] de, los detalles se añaden automáticamente:

   - Información de envío
   - Forma de pago

1. Realiza tu pedido.

>[!TIP]
>
> El usuario invitado realiza el pedido y, opcionalmente, puede registrarse en Adobe Commerce.

## Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] Cuando se encuentra una cuenta de, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador proporciona todos los detalles necesarios para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparecerá una casilla de verificación para registrarse en [!DNL Bolt] para pagos más rápidos antes de realizar el pedido. El comprador puede aceptar los términos y condiciones para crear su [!DNL Bolt] cuenta.
- El usuario invitado realiza el pedido y, opcionalmente, puede registrarse en Adobe Commerce.
