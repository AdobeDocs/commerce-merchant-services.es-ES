---
title: Configuración de servicios de pago
description: Después de la instalación, puede configurar [!DNL Payment Services] en la página de inicio.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 0bd6137ec7cd5da04ae6a48f06cd5aec254b46ef
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 0%

---

# Configuración

Puede personalizar [!DNL Payment Services] a sus necesidades con ajustes útiles en la [!DNL Payment Services] Hogar.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Estas opciones de configuración solo se aplican al entorno que se establece en la variable _[!UICONTROL Payment mode]_en_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> Para la configuración heredada o de varios almacenes, consulte la [Configurar en el administrador](configure-admin.md) tema.

## Habilitar servicios de pago

Puede habilitar [!DNL Payment Services] para su sitio web y habilite pruebas de entorno limitado o pagos activos en la variable [!UICONTROL General] para obtener más información.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Haga clic **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Página principal](payments-home.md) para obtener más información.

   La variable _[!UICONTROL General]_incluye la configuración utilizada para habilitar [!DNL Payment Services] como método de pago.

1. Para habilitar [!DNL Payment Services] como método de pago para su tienda, en la _[!UICONTROL General]_sección, alternar (**[!UICONTROL Enable Payment Services as payment method]**) a `Yes`.

1. Si sigue probando [!DNL Payment Services] para su tienda, establezca **Modo de pago** a `Sandbox`. Si está listo para activar los pagos, configúrelo en `Production`.

   >[!NOTE]
   >
   >Su _[!UICONTROL Sandbox Merchant ID]_y_[!UICONTROL Production Merchant ID]_ se generan automáticamente y están presentes en sus respetables campos al finalizar la incorporación para el entorno limitado o la producción.

1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Ahora puede cambiar la configuración predeterminada de [opciones de pago](#configure-payment-options) funciones y visualización de tienda.

### Opciones de configuración generales

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Enable] | sitio web | Habilitar o deshabilitar [!DNL Payment Services] para su sitio web. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | vista de tienda | Defina el método o el entorno para su tienda. Opciones: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vista de tienda | El ID del comerciante del simulador de pruebas, que se genera automáticamente durante la incorporación al simulador de pruebas. |
| [!UICONTROL Production Merchant ID] | vista de tienda | El ID del comerciante de producción, que se genera automáticamente durante la incorporación al entorno limitado. |

## Configurar las opciones de pago

Ahora que ha habilitado los servicios de pago para su sitio web, puede cambiar la configuración predeterminada para las funciones de pago y la visualización de tienda.

### Campos de tarjeta de crédito

La variable _[!UICONTROL Credit Card Fields]_La configuración proporciona una opción de cierre de compra simple y segura para métodos de pago con tarjeta de crédito o tarjeta de débito.

Consulte [Opciones de pago](payments-options.md#credit-card-fields) para obtener más información.

1. Seleccione la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un método de pago.
1. Para cambiar el nombre del método de pago mostrado durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Para habilitar el modo de depuración, cambie la **[!UICONTROL Debug Mode]** selector.
1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto para mostrarlo como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

### Botones de pago

La variable [!DNL PayPal Smart Buttons] las opciones de pago proporcionan un proceso de cierre de compra simple, rápido y seguro para su cliente. Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

Puede activar y configurar las opciones de pago de los botones inteligentes de PayPal:

1. Seleccione la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un método de pago.
1. Para cambiar el nombre del método de pago como se muestra durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout Title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Utilice los selectores de alternancia para habilitar o deshabilitar [!DNL PayPal smart button] funciones de visualización:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Para usar Apple, pague [debe tener una cuenta de desarrollador de Apple](test-validate.md#test-in-sandbox-environment) (con información falsa de tarjeta de crédito y facturación) para probarla. Cuando esté listo para usar Apple Pay en el simulador de pruebas *o* modo de producción, después de completar cualquier [pruebas y validación](test-validate.md), póngase en contacto con su representante de ventas para habilitarlo para sus tiendas activas.

      Al activar o desactivar la visibilidad de los botones de pago o del mensaje PayPal Pay Later, se muestra una vista previa de esa configuración en la parte inferior de la página Configuración .

1. Para habilitar el modo de depuración, cambie la **[!UICONTROL Debug Mode]** selector.
1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto que se mostrará como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: campo de texto |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página de detalles del producto. Opciones: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la vista previa del minicarro. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página del carro de compras. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | vista de tienda | Active o desactive el aspecto de la opción de pago posterior donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | sitio web | Habilite o deshabilite el mensaje Pagar después en el carro de compras, la página del producto, el minicarro y durante el flujo de cierre de compra. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | vista de tienda | Active o desactive la opción de pago Venmo donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | vista de tienda | Active o desactive la opción de pago Apple Pay donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

### Estilo de botón

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

   A medida que cambia las opciones de configuración para el diseño, el color, la forma, la altura y la etiqueta, se mostrará una vista previa de esa configuración en la parte inferior de la página Configuración.

1. Haga clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Puede configurar [!DNL PayPal Smart Buttons] estilo [en la configuración heredada en la](configure-admin.md#configure-paypal-smart-buttons) o aquí dentro [!DNL Payment Services Home]. Consulte [Guía de estilo de Botones de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obtener más información sobre las opciones.

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|--- |--- |--- |
| [!UICONTROL Layout] | Vista de la tienda | Defina el estilo de diseño de los botones de pago. Opciones: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Vista de la tienda | Habilite o deshabilite el tagline. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Vista de la tienda | Defina el color de los botones de pago. Opciones: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Vista de la tienda | Defina la forma de los botones de pago. Opciones: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Vista de la tienda | Define si los botones de pago utilizan una altura predeterminada. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Vista de la tienda | Defina la altura de los botones de pago. Valor predeterminado: ninguno |
| [!UICONTROL Label] | Vista de la tienda | Defina la etiqueta que aparece en los botones de pago. Opciones: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Usar varias cuentas de PayPal

En Servicios de pago, puede utilizar varias cuentas de PayPal en **one** cuenta de comerciante a nivel de sitio web. Por ejemplo, si está operando sus tiendas en varios países (que utilizan diferentes [currency](https://docs.magento.com/user-guide/stores/currency.html)) o quiere usar Adobe Commerce en algunas partes de su negocio, pero no *all*, puede configurar su cuenta de comerciante para utilizar varias cuentas de PayPal.

Consulte [Ámbito de sitio, tienda y vista](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) para obtener más información sobre la jerarquía de sitios web, tiendas y vistas de tiendas.

Su representante de ventas puede crear un [scope](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) para su cuenta de comerciante y a bordo del sitio adicional con PayPal para que cualquiera de los botones de PayPal que configure para aparecer se muestre en su sitio. Póngase en contacto con su representante de ventas para obtener ayuda sobre el uso de varias cuentas de PayPal para sus sitios web.
