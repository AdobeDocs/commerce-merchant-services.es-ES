---
title: "Incorporar el [!DNL Quick Checkout] para la extensión de Adobe Commerce"
description: "Descubra cómo [!DNL Quick Checkout] podría beneficiar a su instancia de Adobe Commerce y cómo incorporar y configurar correctamente la extensión."
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# [!DNL Quick Checkout] Incorporación

Para empezar a utilizar [!DNL Quick Checkout] para la extensión de Adobe Commerce, debe completar algunos pasos de incorporación para conectar su instancia con la funcionalidad de cierre de compra.

![Cierre de compra rápido](assets/overview-admin-panel.png)

1. [Obtener extensión](#get-extension).
1. [Cree una cuenta de comerciante de producción o de zona protegida con [!DNL Bolt]](#create-account-with-bolt). Proporcione toda la información necesaria para comprobar su identidad.
1. [Proporcionar el único [!DNL API Key] y [!DNL Publishable Key]](#obtain-api-credentials) generado en [!DNL Bolt].
1. [Configure un proveedor de pagos en [!DNL Bolt] account](#configure-payment-providers).
1. [Establezca el menú desplegable Habilitar en Sí.](#enable-extension) para activar la extensión de.
1. [Defina la configuración de servicio](#complete-admin-configuration) para configurar el [!DNL Quick Checkout] extensión.
1. [Haga clic en Guardar configuración](#enable-live-quick-checkout) para activar la extensión.
1. Cambiar ámbito a **Sitio web principal** y [haga clic en Configurar URL de devolución de llamada](#check-shopper-valid-account) botón.

Si Gainsight está habilitada, el déclencheur de la variable **Haga el recorrido** botón en su [!DNL Quick Checkout] Panel de administración acerca de [!DNL Quick Checkout] para Adobe Commerce:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > Avanzado:

   ![Cierre de compra rápido](assets/gainsight-admin.png)

Si Gainsight no está habilitada, continúe con los pasos de incorporación.

Consulte la [[!DNL Quick Checkout] Panel de administración](../quick-checkout/admin-panel.md) para obtener más información.

>[!NOTE]
>
> Si no configura su [!DNL Bolt] cuentas no puede configurar los entornos de zona protegida o producción.

## Requisitos previos

Para utilizar la variable [!DNL Quick Checkout], debe tener lo siguiente disponible para [!DNL Bolt]:

- Proveedores de pago admitidos
- Cuenta de comerciante y producción en [!DNL Bolt]
- API y [!DNL Publishable key] generado en [!DNL Bolt]

Consulte la [requisitos previos](../quick-checkout/prerequisites.md) para obtener más información.

Consulte [Credenciales de API](#obtain-api-credentials) para obtener información sobre cómo crear o acceder a su [!DNL API keys] para su instancia.

## Obtener extensión

Consulte la [instalar](../quick-checkout/install.md) para obtener información detallada sobre la obtención de la extensión.

## Crear cuenta con [!DNL Bolt]

Antes de configurar [!DNL Quick Checkout] En el administrador de Adobe Commerce, es necesario crear un [espacio aislado](https://merchant-sandbox.bolt.com/register?platform=magento2){target="_blank"} and [production](https://merchant.bolt.com/register?platform=magento2){target="_blank"}  cuentas de comerciante en [!DNL Bolt]. Proporcione todos los detalles necesarios para crear una cuenta en [!DNL Bolt].

Consulte la [prueba y validación](../quick-checkout/testing.md) para obtener más información.

## Obtener credenciales de API

Para usar la variable [!DNL Quick Checkout] necesita [!DNL Bolt] claves únicas y [!DNL signing secret]. Obtenga lo siguiente [!DNL API keys] navegando a **Desarrolladores** > **API** > **Claves** en el **Tablero del comerciante de pernos**.

- [!DNL API key]: Una clave privada utilizada por el back end para interactuar con [!DNL Bolt] API.
- [!DNL Publishable key]: Una clave utilizada por el front-end para interactuar con [!DNL Bolt] API.
- [!DNL Signing secret]: se utiliza para la verificación de firmas en solicitudes recibidas de [!DNL Bolt].

  ![Cierre de compra rápido](assets/account-credentials.png)

Consulte la [[!DNL Bolt] detalles del entorno](https://help.bolt.com/developers/references/environment-details/#about-keys){target="_blank"} página para obtener más información sobre las claves y el secreto de firma de [!DNL Bolt] para el [!DNL Quick Checkout] extensión.

>[!CAUTION]
>
> Debe crear [!DNL API keys] para entornos de zona protegida y producción.

## Configuración de proveedores de pagos

Para conectar a su proveedor de servicios de pago, siga los pasos descritos en la sección [configuración del procesador](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target="_blank"} promotor [!DNL Bolt] página.

## Habilitar extensión

1. En el _Administrador_ barra lateral, vaya a **Tiendas** > _Configuración_ > **Configuración**.
1. En el panel izquierdo, expanda **Ventas** y seleccione **Finalizar compra**.
1. En el [!DNL Quick Checkout] ver, establecer **Activar** hasta `Yes`.

![Cierre de compra rápido](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> Los campos de cierre de compra rápido solo están visibles cuando **Activar** se establece en `Yes`.

1. Seleccione el método (zona protegida o producción) que desee utilizar.

   - Zona protegida para fines de prueba y desarrollo
   - Producción para procesar transacciones con el procesador de pagos en vivo

1. Valide las credenciales después de proporcionar su API única y [!DNL Publishable keys].

![Cierre de compra rápido](assets/quick-checkout-main-view.png)

Consulte la [Configuración](../quick-checkout/settings-quick-checkout.md) para obtener más información sobre las opciones de configuración de [!DNL Quick Checkout] para la extensión de Adobe Commerce.

>[!CAUTION]
>
> Debe proporcionar una API única y [!DNL Publishable] claves antes de activar la extensión; de lo contrario, los clientes verán un formulario de pago y no podrán realizar un pedido.

## Configuración de administración completa

1. En el _Administrador_ barra lateral, navegue hasta **Tiendas** > **Configuración** > **Finalizar compra** para acceder a la página general Configuración de administración de cierre de compra.
1. En el _Configuración del servicio_ , proporcione todos los detalles necesarios para habilitar la extensión.
1. Establecer _Acción de pago_ a cualquiera de las opciones:

   - `Authorize`: No capture la transacción automáticamente tras la autorización.
   - `Authorize and Capture`: captura la transacción automáticamente tras la autorización.

Para obtener más información sobre las opciones de desprotección estándar de Adobe Commerce, consulte la [pago y envío](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tema.

## Habilitar cierre rápido de compra en directo

Para habilitar la variable [!DNL Quick Checkout] para la extensión de Adobe Commerce:

1. Compruebe que la variable [!UICONTROL Enable] La lista desplegable está configurada en **Sí** para activar la extensión de.
1. Clic **Guardar configuración**.

## Comprueba que la cuenta del comprador sea válida

Para comprobar si el comprador tiene un [!DNL Bolt] cuenta:

1. Cambiar el ámbito a **Sitio web principal**.
1. Haga clic en **Configurar URL de devolución de llamada** botón. Esto habilita [!DNL Bolt] para determinar si el comprador tiene una cuenta de. Si es así, aparecerá la ventana emergente OTP.

   >[!CAUTION]
   >
   > Cambiar el ámbito a **Sitio web principal** garantiza que se ha establecido la dirección URL correcta. Cada sitio web puede tener varios dominios.

Consulte la [Sitio, tienda y vista de ámbito](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target="_blank"} para obtener más información sobre los ámbitos en Adobe Commerce.

## Configurar ajustes del servicio

![Cierre de compra rápido](assets/service-settings.png)

1. Establecer **Activar seguimiento de cierre de compra** hasta `Yes`.

   >[!CAUTION]
   >
   > Si se deshabilita esta opción, los informes se verán afectados porque Adobe Commerce no puede compartir la información de seguimiento de cierre de compra con Bolt.

1. Seleccione el **Fase siguiente tras el inicio de sesión** para cambiar el flujo de navegación después de que el cliente haya iniciado sesión. De forma predeterminada, se establece en **Pagos** página.
1. Definir si [!DNL Quick Checkout] permite el **inicio de sesión automático** durante el cierre de compra. De forma predeterminada, está habilitado para iniciar sesión automáticamente en [!DNL Bolt] red.

   >[!NOTE]
   >
   > Consulte [Documentación de activación del inicio de sesión automático de Bolt](https://help.bolt.com/products/embedded/direct-api/auto-login/) para obtener más información.

## Obtener ayuda

El proceso de incorporación está diseñado para guiarle a través de los pasos necesarios para configurar y habilitar el [!DNL Express Checkout] funcionalidad.

Póngase en contacto con el Soporte técnico de Adobe Commerce a través de [Centro de ayuda de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) para cualquier ayuda.

Consulte la [prueba y validación](../quick-checkout/testing.md) para obtener más información.
