---
title: Configure las variables [!DNL Quick Checkout] para la extensión de Adobe Commerce
description: Conozca las opciones de configuración de la [!DNL Quick Checkout] y cómo incorporar y configurar correctamente la extensión de.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Quick Checkout] Configuración

[!DNL Quick Checkout] para Adobe Commerce y Magento Open Source proporciona una vista de configuración con toda la información necesaria para configurar la extensión.

Para acceder a estas opciones de configuración:

1. En el _Administrador_ barra lateral, vaya a **Tiendas** > _Configuración_ > **Configuración**.
1. En el panel izquierdo, expanda **Ventas** y seleccione **Finalizar compra**.

   ![Cierre de compra rápido](assets/config-new-logo-view.png)

Consulte la [Incorporación](../quick-checkout/onboarding.md) para obtener más información sobre cómo configurar el [!DNL Quick Checkout] para Adobe Commerce.

## Habilitar extensión

![Cierre de compra rápido](assets/enable-method.png)

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Enable] | sitio web | Habilitar o deshabilitar [!DNL Quick Checkout] para su sitio web. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | sitio web | Establezca el método o entorno para su [!DNL Quick Checkout]. Opciones: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## Credenciales de cuenta

![Cierre de compra rápido](assets/account-creds.png)

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL API key] | sitio web | Una clave privada utilizada por el back end para interactuar con [!DNL Bolt] API. |
| [!UICONTROL Publishable key] | sitio web | Una clave utilizada por el front-end para interactuar con [!DNL Bolt] API. |
| [!UICONTROL Signing secret] | sitio web | Se utiliza para la verificación de firmas en solicitudes recibidas de [!DNL Bolt]. |

{style="table-layout:auto"}

## Configuración del servicio

![Cierre de compra rápido](assets/service-settings.png)

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Añade el texto que se mostrará como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | sitio web | El [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | sitio web | Defina si Adobe Commerce permite que la información de seguimiento de cierre de compra se comparta con Bolt. Habilitado de forma predeterminada. Si se deshabilita, la creación de informes se verá afectada. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | sitio web | Cambie el flujo de navegación una vez que el cliente haya iniciado sesión. Opciones: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | sitio web | Definir si [!DNL Quick Checkout] permite el inicio de sesión automático durante el cierre de compra. Habilitado de forma predeterminada. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | sitio web | Seleccione la red en la que el cliente inicia sesión automáticamente. Perno activado de forma predeterminada. Opciones: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
