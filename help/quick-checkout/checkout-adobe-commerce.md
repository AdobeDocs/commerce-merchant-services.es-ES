---
title: '"Flujo de cierre de compra"'
description: '"Descripción general de la variable [!DNL Quick Checkout] flujo para un usuario de Adobe Commerce."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Un usuario de Adobe Commerce existente: Funcionamiento

Un usuario de Adobe Commerce existente puede seleccionar los detalles de envío y pago guardados al realizar un pedido con la variable [!DNL Quick Checkout] para una experiencia de cierre de compra más rápida.

Cuando un comprador introduce su dirección de correo electrónico al cerrar la compra, la variable [!DNL Quick Checkout] la valida y encuentra una [!DNL Bolt] cuenta.

## Registrados [!DNL Bolt] cuenta con un usuario de Adobe Commerce

Si [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su [!DNL Quick Checkout] experiencia de cierre de compra optimizada:

1. Introduzca la contraseña única (OTP) enviada a esa [!DNL Bolt] dirección de correo electrónico de la cuenta o móvil, según [preferencias del usuario en la [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Una vez que haya iniciado sesión con su [!DNL Bolt] , los detalles se añaden automáticamente:

   - Información de envío
   - Método de pago

1. Realice su pedido.

Si tiene problemas al realizar un pedido como usuario de Adobe Commerce existente, consulte la [Solución de problemas de cierre de compra rápido](https://support.magento.com/hc/en-us/articles/6909450342541) en el Centro de ayuda de Adobe Commerce.

## Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado predeterminado y el comprador selecciona todos los detalles necesarios de su información guardada para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- La opción para registrarse en [!DNL Bolt] para cierres de compra más rápidos, antes de realizar el pedido aparecerá. El comprador puede aceptar los términos y condiciones para crear su [!DNL Bolt] cuenta.

   ![Recordar [!DNL Bolt]](assets/checked-bolt.png)
