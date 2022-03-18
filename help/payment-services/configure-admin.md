---
title: Configurar en el administrador
description: Después de la instalación, puede configurar [!DNL Payment Services] en el menú
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Configurar en el administrador

Puede personalizar [!DNL Payment Services] a sus necesidades con opciones de configuración útiles en Administración.

Al configurar [!DNL Payment Services] para Adobe Commerce y el Magento Open Source en la administración, estas configuraciones solo se aplican al entorno que está configurado en la variable [!UICONTROL Method] campo [!UICONTROL General Configuration]. Los cambios que realice en los campos de configuración no dependerán del cambio de [!UICONTROL Method] selección (selection): si cambia el método, las selecciones no se restablecen.

Consulte la [[!UICONTROL General Configuration] sección](#general-configuration) para obtener más información.

## Configuración general

Puede habilitar [!DNL Payment Services] para su tienda y habilite pruebas de entorno limitado o pagos activos en la variable [!UICONTROL General Configuration] para obtener más información.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Payment Methods]**.

   ![Vista Métodos](assets/methods-view.png)

1. Expanda el _[!UICONTROL Recommended Solutions]_para obtener más información.
1. En el _[!UICONTROL [!DNL Payment Services]]_, expanda la sección_[!UICONTROL General Configuration]_ para obtener más información.
1. Para **Habilitar**, configúrelo en `Yes` para habilitar [!DNL Payment Services] para su tienda.
1. Para **Método**, configúrelo en `Sandbox` si todavía está probando [!DNL Payment Services] para su tienda o `Production` si está listo para activar los pagos en directo.

   >[!WARNING]
   >
   >Su [!UICONTROL Sandbox Merchant ID] y [!UICONTROL Production Merchant ID] se generan automáticamente y están presentes en sus respetables campos cuando haya terminado la incorporación para el entorno limitado o la producción. No elimine o cambie estos ID.

1. Haga clic en **[!UICONTROL Save Config]** para guardar los cambios.

### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Enable] | sitio web | Habilitar o deshabilitar [!DNL Payment Services] para su sitio web. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | vista de tienda | Defina el método o el entorno para su tienda. Opciones: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vista de tienda | El ID del comerciante del simulador de pruebas, que se genera automáticamente durante la incorporación al simulador de pruebas. No cambie ni modifique este ID. |
| [!UICONTROL Production Merchant ID] | vista de tienda | El ID del comerciante de producción, que se genera automáticamente durante la incorporación al entorno limitado. No cambie ni modifique este ID. |

## [!UICONTROL Credit Card Fields]

La variable [!UICONTROL Credit Card Fields] las opciones de pago proporcionan un cierre de compra simple y seguro para los métodos de pago con tarjeta de crédito o tarjeta de débito.

Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

### Configuración de campos de tarjeta de crédito

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Payment Methods]**.
1. Expanda el _[!UICONTROL Recommended Solutions]_para obtener más información.
1. En el _[!UICONTROL Payment Services]_, expanda la sección_[!UICONTROL Credit Card Fields]_ para obtener más información.
1. Para **[!UICONTROL Title]**, escriba el texto (si es necesario) para cambiar el nombre del método de pago como se muestra durante el cierre de compra.
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), seleccione **[!UICONTROL Authorize]** o **Autorizar y capturar**.
1. Para **Modo de depuración**, elija `Yes` para activar el modo de depuración (o `No` para desactivarlo).
1. Haga clic en **[!UICONTROL Save Config]** para guardar los cambios.

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto para mostrarlo como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

La variable [!DNL PayPal Smart Buttons] las opciones de pago proporcionan un proceso de cierre de compra simple, rápido y seguro para su cliente.

Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

### Configurar los botones inteligentes de PayPal

Puede activar y configurar las opciones de pago de los botones inteligentes de PayPal en el Administrador:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Payment Methods]**.
1. Expanda el _[!UICONTROL Recommended Solutions]_para obtener más información.
1. En el _[!UICONTROL Payment Services]_, expanda la sección_[!UICONTROL PayPal Smart Buttons]_ para obtener más información.
1. Para cambiar el nombre del método de pago como se muestra durante el cierre de compra, edite el _[!UICONTROL Title]_campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), seleccione **[!UICONTROL Authorize]** o **[!UICONTROL Authorize and Capture]**.
1. Para desactivar el [Mensajería de pago posterior](payments-options.md#pay-later-button) (si lo desea), seleccione `No` para **[!UICONTROL Display Pay Later Message]**.
1. Para habilitar el modo de depuración, seleccione `Yes` para el **[!UICONTROL Debug Mode]** (`No` lo deshabilita).
1. Para guardar los cambios, haga clic en **[!UICONTROL Save Config]** .

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto que se mostrará como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: campo de texto |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | sitio web | Habilite o deshabilite el mensaje Pagar después en el carro de compras, la página del producto, el minicarro y durante el flujo de cierre de compra. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | vista de tienda | Active o desactive la opción de pago de venmo donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | vista de tienda | Active o desactive el aspecto de la opción de pago posterior donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página de detalles del producto. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini cart preview] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la vista previa de minicart. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página del carro de compras. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
