---
title: "Flujo de cierre de compra para un usuario de Adobe Commerce"
description: '"Descripción general del [!DNL Quick Checkout] flujo para un usuario de Adobe Commerce".'
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Un usuario de Adobe Commerce existente: Cómo funciona

Un usuario existente de Adobe Commerce puede seleccionar los detalles de envío y pago guardados al realizar un pedido con [!DNL Quick Checkout] para una experiencia de cierre de compra más rápida.

Cuando un comprador introduce su dirección de correo electrónico al cerrar la compra, la variable [!DNL Quick Checkout] lo valida y encuentra un existente [!DNL Bolt] cuenta.

## Usuario registrado en Adobe Commerce y [!DNL Bolt]

Si un comprador es un usuario registrado de Adobe Commerce y [!DNL Bolt] redes, ambas redes se proporcionan datos de envío y pago almacenados.

Si un [!DNL Bolt] se encuentra durante el cierre de compra, los compradores pueden continuar con su [!DNL Quick Checkout] experiencia de pago y envío perfecta:

1. Introduzca la contraseña única (OTP) que se le ha enviado [!DNL Bolt] dirección de correo electrónico o móvil de la cuenta, según [preferencias del usuario en la [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Ventana emergente OTP](assets/new-logo-otp-email.png)

1. Una vez que haya iniciado sesión con su [!DNL Bolt] de, los detalles se añaden automáticamente:

   - Información de envío
   - Forma de pago

1. Realiza tu pedido.

>[!NOTE]
>
> La ventana emergente OTP de pernos solo aparece cuando el comprador se encuentra en la página de pago. El comprador puede desactivar el inicio de sesión en Bolt cerrando esa ventana emergente.

Si el comprador ha iniciado sesión en Adobe Commerce antes del cierre de compra, la variable [!DNL Bolt] La ventana emergente OTP no aparecerá durante el cierre de compra, pero aparecerá un mensaje sugiriendo al comprador que inicie sesión para acceder a su cartera de pernos.

Si tiene problemas al realizar un pedido como usuario de Adobe Commerce existente, consulte la [Solucionar problemas de cierre rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) artículo en el Centro de ayuda de Adobe Commerce.

## Inicio de sesión automático

El componente Inicio de sesión automático detecta cuándo un comprador tiene una sesión de Bolt activa y registra automáticamente al comprador. Esto omite los pasos de detección de cuenta y de código de acceso único (OTP) porque el comprador los completó en una sesión anterior.

Es posible configurar un inicio de sesión automático para [!DNL Quick Checkout] usuarios. Puede habilitar una configuración para que inicie sesión automáticamente en un usuario durante el cierre de compra.

1. En el _Administrador_ barra lateral, navegue hasta **Tiendas** > **Configuración** > **Finalizar compra** para acceder a la página general Configuración de administración de cierre de compra.
1. En el _Configuración del servicio_ sección para [!DNL Quick Checkout], proporcione todos los detalles necesarios para configurar el inicio de sesión automático.

Consulte [[!DNL Quick Checkout] configurar los ajustes del servicio](../quick-checkout/onboarding.md#configure-service-settings) para obtener más información.

>[!NOTE]
>
> Primer inicio de sesión al **inicio de sesión automático** está habilitada requiere el consentimiento del usuario para autorizarla mediante la aceptación de una ventana emergente.

## Nuevo [!DNL Bolt] account

Si no [!DNL Bolt] Cuando se encuentra una cuenta de, los compradores continúan con su cierre de compra predeterminado de Adobe Commerce y el comprador selecciona todos los detalles necesarios de su información guardada para realizar el pedido:

- Información de envío y facturación
- Método de envío
- Revisar método de pago
- La opción para registrarse en [!DNL Bolt] para cierres de compra más rápidos antes de que aparezca el pedido. El comprador puede aceptar los términos y condiciones para crear su [!DNL Bolt] cuenta.

  ![Recordar [!DNL Bolt]](assets/checkbox-remember-bolt.png)
