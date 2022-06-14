---
title: Configuración de servicios de pago
description: Después de la instalación, puede configurar [!DNL Payment Services] en la página de inicio.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 724abe973094c1aa631ca34bd8096052fa1e9195
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Configuración

Puede personalizar [!DNL Payment Services] a sus necesidades con ajustes útiles en la [!DNL Payment Services] Hogar.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Estas opciones de configuración solo se aplican al entorno que se establece en la variable _[!UICONTROL Payment mode]_en Configuración general.

Consulte la [[!UICONTROL General] sección de configuración](#general-settings) para obtener más información.

>[!IMPORTANT]
>
> Para la configuración heredada o de varios almacenes, consulte la [Configurar en el administrador](configure-admin.md) tema.

## Habilitar servicios de pago

Puede habilitar [!DNL Payment Services] para su sitio web y habilite pruebas de entorno limitado o pagos activos en la variable [!UICONTROL General] para obtener más información.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Haga clic **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Página principal](payments-home.md) para obtener más información.

   La variable _[!UICONTROL General]_incluye la configuración utilizada para habilitar [!DNL Payment Services] como método de pago.

1. Para habilitar [!DNL Payment Services] como método de pago para su tienda, cambie (**[!UICONTROL Enable Payment Services as payment method]**) a `Yes`.

1. Si sigue probando [!DNL Payment Services] para su tienda, establezca **Modo de pago** a `Sandbox`. Si está listo para activar los pagos, configúrelo en `Production`.

   >[!WARNING]
   >
   >Su _[!UICONTROL Sandbox Merchant ID]_y_[!UICONTROL Production Merchant ID]_ se generan automáticamente y están presentes en sus respetables campos al finalizar la incorporación para el entorno limitado o la producción. No elimine o cambie estos ID.

1. Seleccione la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un método de pago.
1. Para cambiar la configuración predeterminada de las funciones de pago y la visualización de tienda, configure las opciones adicionales según sea necesario:

   - [Campos de tarjeta de crédito](#credit-card-fields)
   - [Botones inteligentes PayPal](#paypal-smart-buttons)
   - [Estilo de botón](#button-style)

1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

### Campos de tarjeta de crédito

La variable _[!UICONTROL Credit Card Fields]_La configuración proporciona una opción de cierre de compra simple y segura para métodos de pago con tarjeta de crédito o tarjeta de débito.

Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

1. Para cambiar el nombre del método de pago mostrado durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Para habilitar el modo de depuración, cambie la **[!UICONTROL Debug Mode]** selector.
1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

### Botones inteligentes PayPal

La variable [!DNL PayPal Smart Buttons] las opciones de pago proporcionan un proceso de cierre de compra simple, rápido y seguro para su cliente. Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

Puede activar y configurar las opciones de pago de los botones inteligentes de PayPal:

1. Para cambiar el nombre del método de pago como se muestra durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout Title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Utilice los selectores de alternancia para habilitar o deshabilitar [!DNL PayPal smart button] funciones de visualización:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. Para cambiar el [Mensajería de pago posterior](payments-options.md#pay-later-button), active la casilla **[!UICONTROL Display Pay Later message]** .
1. Para habilitar el modo de depuración, cambie la **[!UICONTROL Debug Mode]** selector.
1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

#### Estilo de botón

También puede configurar la variable _[!UICONTROL Button style]_opciones de los botones inteligentes de PayPal:

1. Para cambiar el **[!UICONTROL Layout]**, seleccione `Vertical` o `Horizontal`.

   >[!NOTE]
   >
   > Si el estilo del botón está configurado como `Horizontal` y su tienda está configurada para mostrar varios botones inteligentes de PayPal, puede que solo vea dos botones en la página del producto, la página de cierre de compra y el minicarro, y un botón mostrado en el carrito.

1. Para habilitar la etiqueta en un diseño horizontal, cambie el **[!UICONTROL Show tagline]** selector.
1. Para modificar el **[!UICONTROL Color]**, seleccione la opción de color que desee.
1. Para modificar el **[!UICONTROL Shape]**, seleccione `Pill` o `Rect`.
1. Para habilitar el selector de altura del botón, active la opción **[!UICONTROL Responsive button height]** selector.
1. Para modificar el **[!UICONTROL Label]**, seleccione la opción de etiqueta que desee.
1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Puede configurar [!DNL PayPal Smart Buttons] estilo en el Administrador o [!DNL Payment Services Home]. Consulte [Guía de estilo de Botones de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obtener más información.
