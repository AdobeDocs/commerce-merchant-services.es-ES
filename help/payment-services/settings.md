---
title: Configuración de servicios de pago
description: Después de la instalación, puede configurar [!DNL Payment Services] en la página de inicio.
role: Admin, User
level: Intermediate
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Configurar en la vista Inicio

Puede personalizar [!DNL Payment Services] a sus necesidades con ajustes útiles en la vista Inicio.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Estas opciones de configuración solo se aplican al entorno que se establece en la variable _[!UICONTROL Payment mode]_en General settings.

Consulte la [[!UICONTROL General] sección de configuración](#general-settings) para obtener más información.

>[!IMPORTANT]
>
> Para la configuración heredada o de varios almacenes, consulte la [Configurar en el administrador](configure-admin.md) tema.

## Configurar servicios de pago

Puede habilitar [!DNL Payment Services] para su sitio web y habilite pruebas de entorno limitado o pagos activos en la variable [!UICONTROL General] configuración.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. En la vista Inicio, haga clic en **[!UICONTROL Settings]**. Consulte [Página principal](payments-home.md) para obtener más información.

   La variable _[!UICONTROL General]_incluye las opciones de configuración utilizadas para establecer [!DNL Payment Services] como método de pago.

1. Para la opción de alternancia en la parte superior (**[!UICONTROL Enable Payment Services as payment method]**), configúrelo en `Yes` para habilitar [!DNL Payment Services] para su sitio web.

1. Para **Modo de pago**, configúrelo en `Sandbox` si todavía está probando [!DNL Payment Services] para su tienda o `Production` si está listo para activar los pagos en directo.

   >[!WARNING]
   >
   >Su _[!UICONTROL Sandbox Merchant ID]_y_[!UICONTROL Production Merchant ID]_ se generan automáticamente y están presentes en sus respetables campos cuando haya terminado la incorporación para el entorno limitado o la producción. No elimine o cambie estos ID.

1. Para cambiar la configuración predeterminada de las funciones de pago y la visualización de tienda, configure las opciones adicionales según sea necesario:

   - [Campos de tarjeta de crédito](#credit-card-fields)
   - [Botones inteligentes PayPal](#paypal-smart-buttons)
   - [Estilo de botón](#button-style)

1. Para guardar los cambios, haga clic en **[!UICONTROL Save]** en la parte superior derecha de la página.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

### Campos de tarjeta de crédito

La variable _[!UICONTROL Credit Card Fields]_las opciones de pago proporcionan un cierre de compra simple y seguro para los métodos de pago con tarjeta de crédito o tarjeta de débito.

Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

1. Para **[!UICONTROL Checkout title]**, escriba el texto (si es necesario) para cambiar el nombre del método de pago que se muestra durante el cierre de compra.
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), conjunto **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Para **[!UICONTROL Debug Mode]**, active el selector para habilitar el modo de depuración.
1. Para guardar los cambios, haga clic en **[!UICONTROL Save]** en la parte superior derecha de la página.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

### Botones inteligentes PayPal

La variable [!DNL PayPal Smart Buttons] las opciones de pago proporcionan un proceso de cierre de compra simple, rápido y seguro para su cliente. Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

Puede activar las opciones de pago de los botones inteligentes de PayPal en Inicio:

1. Para cambiar el nombre del método de pago como se muestra durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout Title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), conjunto **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Utilice los selectores de alternancia para habilitar o deshabilitar [!DNL PayPal smart button] funciones de visualización:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** para activar la opción para mostrar el botón durante el cierre de compra.

1. Para cambiar el [Mensajería de pago posterior](payments-options.md#pay-later-button) (si lo desea), cambie la **[!UICONTROL Display Pay Later message]** .
1. Para habilitar el modo de depuración, haga clic en **[!UICONTROL Debug Mode]**,
1. Para guardar los cambios, haga clic en **[!UICONTROL Save]** en la parte superior derecha de la página.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

### Estilo de botón

También puede configurar la variable _[!UICONTROL Button style]_opciones de los botones inteligentes de PayPal en Inicio:

1. Para cambiar el **[!UICONTROL Layout]**, seleccione `Vertical` o `Horizontal`.
1. Para habilitar el etiquetado en una presentación horizontal, haga clic en **[!UICONTROL Show tagline]**.
1. Para modificar el **[!UICONTROL Color]**, seleccione la opción de color que desee.
1. Para cambiar el **[!UICONTROL Shape]**, seleccione `Pill` o `Rect`.
1. Para habilitar el selector de altura del botón, haga clic en **[!UICONTROL Responsive button height]**.
1. Para modificar el **[!UICONTROL Label]**, seleccione la opción de etiqueta que desee.
1. Para guardar los cambios, haga clic en **[!UICONTROL Save]** en la parte superior derecha de la página.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Puede configurar [!DNL PayPal Smart Buttons] estilo en Admin o Home. Consulte [Guía de estilo de Botones de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obtener más información.
