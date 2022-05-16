---
title: Incorpore el [!DNL Express Checkout] para la extensión de Adobe Commerce
description: Aprenda a [!DNL Express Checkout] podría beneficiar a su instancia de Adobe Commerce y cómo incorporar y configurar correctamente la extensión.
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# [!DNL Express Checkout] Incorporación

>[!IMPORTANT]
>
> Esta función es para usuarios del Programa de Adoptadores Anticipados (EAP, por sus siglas en inglés) y aún no es accesible para todos los clientes. Actualmente está limitado a los clientes de EE. UU. Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.

Para empezar a usar la variable [!DNL Express Checkout] para la extensión de Adobe Commerce, debe completar algunos pasos de incorporación para conectar su instancia con nuestra funcionalidad de cierre de compra.

1. [Obtener extensión](#get-extension).
1. [Cree una cuenta de comercialización de producción o de simulación de pruebas con [!DNL Bolt]](#create-account-with-bolt). Proporcione toda la información necesaria para verificar su identidad.
1. [Proporcione la clave de API y la clave de publicación únicas generadas en [!DNL Bolt]](#obtain-api-credentials).
1. [Configure un proveedor de pagos en la variable [!DNL Bolt] account](#configure-payment-providers).
1. [Establezca Habilitar menú desplegable en Sí](#enable-extension) para activar la extensión.
1. [Definir la configuración del servicio](#complete-admin-configuration) para configurar la variable [!DNL Express Checkout] extensión.
1. [Haga clic en el botón Guardar configuración .](#enable-live-express-checkout) para habilitar la extensión.

>[!NOTE]
>
> Si no configura su [!DNL Bolt] (paso 2 anterior) no puede configurar entornos de simulación de pruebas o de producción.

## Requisitos previos

Para usar la variable [!DNL Express Checkout], debe tener lo siguiente disponible para [!DNL Bolt]:

- Proveedores de pagos admitidos
- Cuenta de comercialización y producción en [!DNL Bolt]
- API y clave de publicación generadas en [!DNL Bolt]

Consulte la [requisitos previos](../express-checkout/prerequisites.md) para obtener más información.

Consulte [Credenciales de API](#obtain-api-credentials) para aprender a crear o acceder a sus claves de API para su instancia.

## Obtener extensión

Consulte la [instalar](../express-checkout/install.md) para obtener información detallada sobre la obtención de la extensión.

## Crear cuenta con Bolt

Antes de configurar la variable [!DNL Express Checkout] en el administrador de Adobe Commerce, es necesario crear un [entorno limitado](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} y [producción](https://merchant.bolt.com/register){target=&quot;_blank&quot;} cuenta de comerciante en [!DNL Bolt]. Proporcione todos los detalles necesarios para crear una cuenta en [!DNL Bolt].

Consulte la [probar y validar](../express-checkout/testing.md) para obtener más información.

## Obtener credenciales de API

Para usar la variable [!DNL Express Checkout] necesita [!DNL Bolt] claves únicas. Obtenga las siguientes claves de API navegando hasta **Desarrolladores** > **API** > **Claves** en el **Panel de comercialización del perno**.

- Clave de API: Una clave privada utilizada por el back end para interactuar con [!DNL Bolt] API.
- Clave pública: Una clave utilizada por el front-end para interactuar con [!DNL Bolt] API.

Consulte la [[!DNL Bolt] detalles del entorno](https://help.bolt.com/developers/references/environment-details/#about-keys)página {target=&quot;_blank&quot;} para obtener más información sobre las claves API y Publicable para la [!DNL Express Checkout] extensión.

>[!CAUTION]
>
> Debe crear claves de API para entornos de entorno limitado y de producción.

## Configuración de proveedores de pagos

Para conectar a su proveedor de servicios de pago, siga los pasos descritos en la sección [configuración del procesador](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} desarrollador [!DNL Bolt] página.

## Habilitar extensión

1. En el _Administrador_ barra lateral, vaya a **Almacenes** > **Configuración** > **Cierre de compra** para acceder a la página de configuración de administración de cierre de compra .

   ![Cierre de compra exprés](assets/admin-view.png)

1. En el [!DNL Express Checkout] vista, conjunto **Habilitar** a `Yes`.
1. Seleccione el método (Simulador para pruebas o Producción) que desea utilizar.

   - Simulador para pruebas y desarrollo
   - Producción para procesar transacciones con el procesador de pagos activos

1. Valide las credenciales después de proporcionar la API única y las claves editables.

>[!CAUTION]
>
> Debe proporcionar claves API y Publicables únicas antes de activar la extensión. De lo contrario, los clientes verán un formulario de pago y no podrán realizar un pedido.

## Completar la configuración de administración

1. En el _Administrador_ barra lateral, vaya a **Almacenes** > **Configuración** > **Cierre de compra** para acceder a la página de configuración general del administrador de cierre de compra .
1. En el _Configuración del servicio_ , proporcione todos los detalles necesarios para habilitar la extensión.
1. Establezca _Acción de pago_ como:

   - Autorizar: No capturar la transacción automáticamente tras la autorización.
   - Autorizar y capturar: Capturar la transacción automáticamente tras la autorización.

Para obtener más información sobre las opciones de cierre de compra estándar de Adobe Commerce, consulte la [cierre de compra](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tema.

## Habilitar el cierre de compra en directo

Para habilitar la variable [!DNL Express Checkout] para la extensión de Adobe Commerce:

1. Haga clic en **Guardar configuración**.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

## Obtener ayuda

El proceso de incorporación está diseñado para guiarle por los pasos necesarios para configurar y habilitar el [!DNL Express Checkout] funcionalidad. Contacto [!DNL Adobe Commerce] equipo de ingeniería a través del Slack asignado [Canal Programas beta de Adobe](http://adobe-beta-programs.slack.com/) para cualquier ayuda.

Consulte la [probar y validar](../express-checkout/testing.md) para obtener más información.
