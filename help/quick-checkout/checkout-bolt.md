---
title: "Flujo de cierre de compra de un usuario de Bolt en Adobe Commerce"
description: Información general sobre [!DNL Quick Checkout] flujo para un usuario de Bolt en Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: 7c99f1aa4bed9878625d855509448494d5547d56
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Usuarios invitados

La experiencia de cierre de compra de invitado es diferente de la experiencia del usuario de Adobe. Cuando un comprador introduce una dirección de correo electrónico en el cierre de compra, la variable [!DNL Quick Checkout] la valida y encuentra una [!DNL Bolt] cuenta.

## Registrados [!DNL Bolt] account

Si [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su [!DNL Quick Checkout] experiencia de cierre de compra optimizada:

1. Introduzca la contraseña única (OTP) enviada a esa [!DNL Bolt] dirección de correo electrónico de la cuenta o móvil, según [preferencias del usuario en la [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Ventana emergente de OTP](assets/pop-up.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] , los detalles se añaden automáticamente:

   - Información de envío
   - Método de pago

1. Realice su pedido.

>[!TIP]
>
> El usuario invitado realiza el pedido y, opcionalmente, puede registrarse en Adobe Commerce.

## Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador proporciona todos los detalles necesarios para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- Aparece una casilla de verificación para registrarse en [!DNL Bolt] para cierres de compra más rápidos antes de realizar el pedido. El comprador puede aceptar los términos y condiciones para crear su [!DNL Bolt] cuenta.

   ![Recordar [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- El usuario invitado realiza el pedido y, opcionalmente, puede registrarse en Adobe Commerce.
