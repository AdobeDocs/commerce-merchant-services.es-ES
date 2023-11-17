---
title: Configuración de la zona protegida de pruebas
description: Utilizar una cuenta de zona protegida de PayPal [!DNL Payment Services] en modo de prueba.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install
source-git-commit: bfb49e3602cc80f97817a8fd8d7c4684a3a3bcd2
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Configuración de la zona protegida de pruebas

Antes de comenzar la incorporación a la zona protegida, debe registrarse para obtener una cuenta gratuita de desarrollador de PayPal y crear cuentas de comerciante (que se utilizarán para la incorporación) y de comprador (que se utilizarán para probar el cierre de compra). Si lo desea, puede crear varias cuentas de desarrollador.

Una cuenta de zona protegida de PayPal permite utilizar [!DNL Payment Services] en modo de prueba. PayPal requiere que uses una cuenta de prueba, un correo electrónico y una contraseña de zona protegida empresarial generados por el portal para desarrolladores de PayPal para la incorporación a la zona protegida. *No cree otra cuenta durante el proceso de incorporación a la zona protegida.*

## Integración de zona protegida

Para completar la incorporación a la zona protegida:

1. Vaya a [Página de cuenta de desarrollador de PayPal](https://developer.paypal.com/developer/accounts/).
1. Clic **[!UICONTROL Log in to Dashboard]** e inicie sesión con su cuenta de prueba de prueba de zona protegida empresarial generada por el PayPal Developer Portal existente o haga clic en **Registrarse** para crear una cuenta de.
1. Crear una cuenta de zona protegida de PayPal:
   1. Ir a _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. Haga clic **[!UICONTROL Create account]**.

      Si creó una cuenta de zona protegida de PayPal durante el proceso de incorporación a esta zona protegida, debe [restablecer la zona protegida de incorporación](#reset-your-sandbox-account) porque o no puede verificar su correo electrónico.

   1. Seleccionar **[!UICONTROL Business]** como Tipo de cuenta y haga clic en **[!UICONTROL Create]**.
   1. En el _[!UICONTROL Sandbox Accounts]_, haga clic en los tres puntos del_[!UICONTROL Manage accounts]_ para la cuenta de zona protegida que ha creado.
   1. Haga clic **[!UICONTROL View/edit account]**.

      ![PayPal: ver/editar cuenta de zona protegida](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Copie y guarde el ID de correo electrónico y la contraseña generados por el sistema para uso futuro.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Haga clic **[!UICONTROL Sandbox onboarding]**.

   Esta opción está visible si aún no ha completado la incorporación a la zona protegida de [!DNL Payment Services].

   La ID de comerciante de una zona protegida se genera automáticamente y se rellena en [configuración](settings.md). No cambie ni modifique este ID.

   Se le mostrará una ventana de PayPal para conectar una cuenta PayPal y comenzar a aceptar pagos.

1. Introduzca el correo electrónico y la contraseña de la cuenta de zona protegida de PayPal que generó en el paso 3 (no la información de su cuenta comercial de PayPal) y su país o región.
1. Haga clic **[!UICONTROL Next]**.

   ![PayPal: conecta tu cuenta PayPal para realizar pagos](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Siga el flujo de PayPal con las credenciales de la cuenta de la zona protegida guardada anteriormente.
1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   El **[!UICONTROL Sandbox onboarding]** ya no está visible y aparece el texto &quot;Pagos pendientes de zona protegida&quot;.

Cuando se apruebe la incorporación a la zona protegida de PayPal, debería ver una notificación que indique que su sistema de pago está actualmente en modo de zona protegida y no está procesando pagos activos.

>[!IMPORTANT]
>
>Si revoca el consentimiento a [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] para procesar tus pagos (en la configuración de tu cuenta PayPal), los pedidos de tu tienda no pueden ser procesados por [!DNL Payment Services]. En su página de inicio de Servicios de pago, aparece una alerta sobre el consentimiento revocado. Para descartar la alerta, haga clic en **[!UICONTROL Do not show again]**.

### Restablecer la cuenta de zona protegida

Si ha creado una cuenta de zona protegida de PayPal durante el proceso de incorporación a esta zona protegida, debe restablecer su zona protegida de incorporación porque o no puede verificar su correo electrónico.

Para restablecer la cuenta de la zona protegida:

1. Haga clic **[!UICONTROL Reset sandbox]**. [Crear una cuenta de zona protegida empresarial de PayPal](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Clic **[!UICONTROL Sandbox onboarding]** y complete el siguiente conjunto de pasos.

## Habilitar número de teléfono de contacto

El número de teléfono de contacto te permite obtener los números de teléfono de contacto que PayPal recopila de tus clientes. PayPal siempre recopila los números de teléfono de contacto de los titulares de cuentas de PayPal para ayudar a confirmar su identidad y ponerse en contacto con ellos para resolver problemas en sus cuentas o para completar sus procesos de cumplimiento. Sin embargo, PayPal desaconseja el uso de números de teléfono de contacto directamente del comerciante porque puede afectar negativamente a las ventas. Consulte la [PayPal obtener números de teléfono de contacto](https://www.sandbox.paypal.com/businessmanage/preferences/website) para obtener más información.

Esta función es `off` de forma predeterminada. Cuando lo habilita, los administradores de tiendas pueden ver los números de teléfono cuando un cliente completa un flujo de cierre de compra con marca fuera de la página de cierre de compra.

>[!IMPORTANT]
>
>Esta configuración no se aplica a otros flujos de cierre de compra.

## Realizar pruebas en un entorno limitado

Consulte [Prueba y validación](test-validate.md) para obtener más información.
