---
title: "Flujo de cierre de compra para un usuario de Adobe Commerce"
description: "Descripción general de la variable [!DNL Quick Checkout] flujo para un usuario de Adobe Commerce."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Un usuario de Adobe Commerce existente: Funcionamiento

Un usuario de Adobe Commerce existente puede seleccionar los detalles de envío y pago guardados al realizar un pedido con la variable [!DNL Quick Checkout] para una experiencia de cierre de compra más rápida.

Cuando un comprador introduce su dirección de correo electrónico al cerrar la compra, la variable [!DNL Quick Checkout] la valida y encuentra una [!DNL Bolt] cuenta.

## Usuario registrado en Adobe Commerce y [!DNL Bolt]

Cuando un comprador es un usuario registrado tanto en Adobe Commerce como en [!DNL Bolt] redes, ambas redes se proporcionan almacenadas de envío y detalles de pago.

Si [!DNL Bolt] se encuentra durante el cierre de compra, los compradores pueden continuar con su [!DNL Quick Checkout] experiencia de cierre de compra optimizada:

1. Introduzca la contraseña única (OTP) enviada a esa [!DNL Bolt] dirección de correo electrónico de la cuenta o móvil, según [preferencias del usuario en la [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Ventana emergente de OTP](assets/pop-up.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] , los detalles se añaden automáticamente:

   - Información de envío
   - Método de pago

1. Realice su pedido.

>[!NOTE]
>
> La ventana emergente OTP de perno solo aparece cuando el comprador está en la página de cierre de compra. El comprador puede optar por no iniciar sesión en Bolt cerrando esa ventana emergente.

Si el comprador ha iniciado sesión en Adobe Commerce antes del cierre de compra, la variable [!DNL Bolt] La ventana emergente de OTP no aparecerá durante el cierre de compra, pero aparecerá un mensaje sugiriendo al comprador que inicie sesión para acceder a su billetera de Bolt.

Si tiene problemas al realizar un pedido como usuario de Adobe Commerce existente, consulte la [Solución de problemas de cierre de compra rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) en el Centro de ayuda de Adobe Commerce.

## Inicio de sesión automático

El componente Inicio de sesión automático detecta cuándo un comprador tiene una sesión de tornillo activa y registra automáticamente al comprador. Esto omite los pasos de detección de cuenta y código de paso único (OTP) porque el comprador los completó en una sesión anterior.

Es posible configurar un inicio de sesión automático para [!DNL Quick Checkout] usuarios. Puede activar una configuración para iniciar sesión automáticamente en un usuario durante el cierre de compra.

1. En el _Administrador_ barra lateral, vaya a **Almacenes** > **Configuración** > **Cierre de compra** para acceder a la página de configuración general del administrador de cierre de compra .
1. En el _Configuración del servicio_ para [!DNL Quick Checkout], proporcione todos los detalles necesarios para configurar el inicio de sesión automático.

Consulte [[!DNL Quick Checkout] configurar configuración de servicio](../quick-checkout/onboarding.md#configure-service-settings) para obtener más información.

>[!NOTE]
>
> Inicio de sesión por primera vez **inicio de sesión automático** está habilitado requiere el consentimiento del usuario para autorizarlo aceptando una ventana emergente.

## Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] se encuentra la cuenta, los compradores continúan con su cierre de compra predeterminado predeterminado y el comprador selecciona todos los detalles necesarios de su información guardada para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- La opción para registrarse en [!DNL Bolt] para cierres de compra más rápidos, antes de realizar el pedido aparecerá. El comprador puede aceptar los términos y condiciones para crear su [!DNL Bolt] cuenta.

   ![Recordar [!DNL Bolt]](assets/checkbox-remember-bolt.png)
