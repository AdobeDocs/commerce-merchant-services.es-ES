---
title: '"Incorpore el [!DNL Quick Checkout] para la extensión de Adobe Commerce"'
description: '"Aprenda a usar la variable [!DNL Quick Checkout] podría beneficiar a su instancia de Adobe Commerce y cómo incorporar y configurar correctamente la extensión."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# [!DNL Quick Checkout] Incorporación

Para empezar a usar la variable [!DNL Quick Checkout] para la extensión de Adobe Commerce, debe completar algunos pasos de incorporación para conectar su instancia con nuestra funcionalidad de cierre de compra.

1. [Obtener extensión](#get-extension).
1. [Cree una cuenta de comercialización de producción o de simulación de pruebas con [!DNL Bolt]](#create-account-with-bolt). Proporcione toda la información necesaria para verificar su identidad.
1. [Proporcione la variable única [!DNL API Key] y [!DNL Publishable Key] generado en [!DNL Bolt]](#obtain-api-credentials).
1. [Configure un proveedor de pagos en la variable [!DNL Bolt] account](#configure-payment-providers).
1. [Establezca Habilitar menú desplegable en Sí](#enable-extension) para activar la extensión.
1. [Definir la configuración del servicio](#complete-admin-configuration) para configurar la variable [!DNL Quick Checkout] extensión.
1. [Haga clic en el botón Guardar configuración .](#enable-live-quick-checkout) para habilitar la extensión.

>[!NOTE]
>
> Si no configura su [!DNL Bolt] no puede configurar entornos de simulación de pruebas o de producción.

## Requisitos previos

Para usar la variable [!DNL Quick Checkout], debe tener lo siguiente disponible para [!DNL Bolt]:

- Proveedores de pagos admitidos
- Cuenta de comercialización y producción en [!DNL Bolt]
- API y [!DNL Publishable key] generado en [!DNL Bolt]

Consulte la [requisitos previos](../quick-checkout/prerequisites.md) para obtener más información.

Consulte [Credenciales de API](#obtain-api-credentials) para aprender a crear o acceder a su [!DNL API keys] para su instancia.

## Obtener extensión

Consulte la [instalar](../quick-checkout/install.md) para obtener información detallada sobre la obtención de la extensión.

## Crear cuenta con [!DNL Bolt]

Antes de configurar la variable [!DNL Quick Checkout] en el administrador de Adobe Commerce, es necesario crear un [entorno limitado](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} y [producción](https://merchant.bolt.com/register){target=&quot;_blank&quot;} cuentas comerciales en [!DNL Bolt]. Proporcione todos los detalles necesarios para crear una cuenta en [!DNL Bolt].

Consulte la [probar y validar](../quick-checkout/testing.md) para obtener más información.

## Obtener credenciales de API

Para usar la variable [!DNL Quick Checkout] necesita [!DNL Bolt] claves únicas. Obtenga lo siguiente [!DNL API keys] navegando a **Desarrolladores** > **API** > **Claves** en el **Panel de comercialización del perno**.

- [!DNL API key]: Una clave privada utilizada por el back end para interactuar con [!DNL Bolt] API.
- [!DNL Publishable key]: Una clave utilizada por el front-end para interactuar con [!DNL Bolt] API.

Consulte la [[!DNL Bolt] detalles del entorno](https://help.bolt.com/developers/references/environment-details/#about-keys)página {target=&quot;_blank&quot;} para obtener más información sobre API y [!DNL Publishable keys] para el [!DNL Quick Checkout] extensión.

>[!CAUTION]
>
> Debe crear [!DNL API keys] para entornos de simulación de pruebas y de producción.

## Configuración de proveedores de pagos

Para conectar a su proveedor de servicios de pago, siga los pasos descritos en la sección [configuración del procesador](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} desarrollador [!DNL Bolt] página.

## Habilitar extensión

1. En el _Administrador_ barra lateral, vaya a **Almacenes** > **Configuración** > **Cierre de compra** para acceder a la página de configuración de administración de cierre de compra .

   ![Cierre rápido](assets/admin-view.png)

1. En el [!DNL Quick Checkout] vista, conjunto **Habilitar** a `Yes`.
1. Seleccione el método (Simulador para pruebas o Producción) que desea utilizar.

   - Simulador para pruebas y desarrollo
   - Producción para procesar transacciones con el procesador de pagos activos

1. Valide las credenciales después de proporcionar su API única y [!DNL Publishable keys].

>[!CAUTION]
>
> Debe proporcionar una API única y [!DNL Publishable keys] antes de activar la extensión, los clientes verán un formulario de pago y no podrán realizar un pedido.

## Completar la configuración de administración

1. En el _Administrador_ barra lateral, vaya a **Almacenes** > **Configuración** > **Cierre de compra** para acceder a la página de configuración general del administrador de cierre de compra .
1. En el _Configuración del servicio_ , proporcione todos los detalles necesarios para habilitar la extensión.
1. Establezca _Acción de pago_ a cualquiera de las opciones:

   - `Authorize`: No capturar la transacción automáticamente tras la autorización.
   - `Authorize and Capture`: Capturar la transacción automáticamente tras la autorización.

Para obtener más información sobre las opciones de cierre de compra estándar de Adobe Commerce, consulte la [cierre de compra](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tema.

## Habilitar el cierre de compra rápido activo

Para habilitar la variable [!DNL Quick Checkout] para la extensión de Adobe Commerce:

1. Compruebe que la variable [!UICONTROL Enable] lista desplegable está configurada como **Sí** para activar la extensión.
1. Haga clic en **Guardar configuración**.

## Obtener ayuda

El proceso de incorporación está diseñado para guiarle por los pasos necesarios para configurar y habilitar el [!DNL Express Checkout] funcionalidad. Póngase en contacto con el equipo de ingeniería de Adobe Commerce a través de su Slack asignado [Canal Programas beta de Adobe](http://adobe-beta-programs.slack.com/) canal para obtener ayuda.

Consulte la [probar y validar](../quick-checkout/testing.md) para obtener más información.
