---
title: Configuración de servicios de pago
description: Después de la instalación, puede configurar [!DNL Payment Services] en la página de inicio.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 17ba23192fed6cd219411420c5d56b42c94af0f5
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 0%

---

# Configuración

Puede personalizar [!DNL Payment Services] a sus necesidades con ajustes útiles en la [!DNL Payment Services] Hogar.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Estas opciones de configuración solo se aplican al entorno que se establece en la variable _[!UICONTROL Payment mode]_del campo[_ General _opciones de configuración](#configure-general-settings).

Para obtener información sobre la configuración heredada o de varias tiendas, consulte [Configurar en el administrador](configure-admin.md).

## Configuración general

La variable [!UICONTROL General] La configuración proporciona la capacidad de habilitar o deshabilitar los servicios de pago como método de pago y agregar información a las transacciones de clientes para marcar o prefijar un sitio web o una vista de tienda con información personalizada.

### Habilitar servicios de pago

Puede habilitar [!DNL Payment Services] para su sitio web y habilite pruebas de entorno limitado o pagos activos.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Haga clic en **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Página principal](payments-home.md) para obtener más información.

   La variable _[!UICONTROL General]_incluye la configuración utilizada para habilitar [!DNL Payment Services] como método de pago.

1. Para habilitar [!DNL Payment Services] como método de pago para su tienda, en la _[!UICONTROL General]_sección, alternar **[!UICONTROL Enable Payment Services as payment method]**a `Yes`.

1. Si sigue probando [!DNL Payment Services] para su tienda, establezca **Modo de pago** a `Sandbox`. Si está listo para activar los pagos, configúrelo en `Production`.

   >[!NOTE]
   >
   >Su _[!UICONTROL Sandbox Merchant ID]_y_[!UICONTROL Production Merchant ID]_ se generan automáticamente y están presentes en sus respetables campos al finalizar la incorporación para el entorno limitado o la producción.

1. Haga clic en **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Ahora puede cambiar la configuración predeterminada de [opciones de pago](#configure-payment-options) funciones y visualización de tienda.

### Agregar descriptor de software

Puede añadir un [!UICONTROL Soft Descriptor] a la configuración de sus sitios web o vistas de tiendas individuales. Los descriptores de software muestran los estados bancarios de transacciones con clientes. Si tiene varias tiendas, marcas o catálogos, por ejemplo, puede definir fácilmente entre ellos añadiendo texto personalizado al [!UICONTROL Soft Descriptor] campo .

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Haga clic en **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Página principal](payments-home.md) para obtener más información.
1. Seleccione el sitio web o la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea crear un descriptor de software. Para la configuración inicial, deje esto como **[!UICONTROL Default]** para establecer el valor predeterminado.
1. Agregue el texto personalizado (hasta 22 caracteres) en el campo de texto y reemplace `Custom descriptor`.
1. Haga clic en **[!UICONTROL Save]**.
1. Para crear un descriptor de software que no sea el predeterminado configurado para un sitio web o una vista de tienda:
   1. Seleccione el sitio web o la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea crear un descriptor de software.
   1. Alternar _off_ **[!UICONTROL Use website]** (o **[!UICONTROL Use default]**, según el ámbito que haya seleccionado).
   1. Añada el texto personalizado en el campo de texto.
   1. Haga clic en **[!UICONTROL Save]**.
1. Para habilitar para un sitio web o almacenar, vea el descriptor de software predeterminado _o_ descriptor de software utilizado para el sitio web principal:
   1. Seleccione el sitio web o la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un descriptor de software existente.
   1. Alternar _en_ **[!UICONTROL Use website]** (o **[!UICONTROL Use default]**, según el ámbito seleccionado).
   1. Haga clic en **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Enable] | sitio web | Habilitar o deshabilitar [!DNL Payment Services] para su sitio web. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | vista de tienda | Defina el método o el entorno para su tienda. Opciones: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vista de tienda | El ID del comerciante del simulador de pruebas, que se genera automáticamente durante la incorporación al simulador de pruebas. |
| [!UICONTROL Production Merchant ID] | vista de tienda | El ID del comerciante de producción, que se genera automáticamente durante la incorporación al entorno limitado. |
| [!UICONTROL Soft Descriptor] | vista de sitio web o tienda | Agregue un descriptor de software a sus sitios web y vistas de tienda para agregar información a las transacciones de clientes que delimiten marcas, tiendas o líneas de productos. La variable [!UICONTROL Use website] se aplica cualquier descriptor de software añadido a nivel de sitio web. La variable [!UICONTROL Use default] la opción aplica cualquier descriptor de software agregado como predeterminado. |

## Configurar las opciones de pago

Ahora que ha activado [!UICONTROL Payment Services] para su sitio web, puede cambiar la configuración predeterminada para las funciones de pago y la visualización de tienda.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Haga clic en **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Página principal](payments-home.md) para obtener más información.
1. Configurar las opciones de pago para [tarjetas de crédito](#credit-card-fields), [botones de pago](#payment-buttons)y [estilo del botón](#button-style), según las secciones siguientes.

### Campos de tarjeta de crédito

La variable _[!UICONTROL Credit Card Fields]_La configuración proporciona una opción de cierre de compra simple y segura para métodos de pago con tarjeta de crédito o tarjeta de débito.

Consulte [Opciones de pago](payments-options.md#credit-card-fields) para obtener más información.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista de inicio](assets/payment-services-menu-small.png)

1. Seleccione la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un método de pago.
1. Para cambiar el nombre del método de pago mostrado durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Para habilitar [3DS Autenticación segura](security.md#3ds) (`Off` de forma predeterminada) active la opción **[!UICONTROL 3DS Secure authentication]** selector para `Always` o `When required`.
1. Para activar o desactivar los campos de tarjeta de crédito en la página de cierre de compra, active la opción **[!UICONTROL Show on checkout page]** selector.
1. Para habilitar o deshabilitar [bóveda de tarjetas](#card-vaulting), active la casilla **[!UICONTROL Vault enabled]** selector.
1. Para activar o desactivar el modo de depuración, active la opción **[!UICONTROL Debug Mode]** selector.
1. Haga clic en **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. [Vaciar la caché](#flush-the-cache).

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto para mostrarlo como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3DS Secure authentication] | sitio web | Habilitar o deshabilitar [3DS Autenticación segura](security.md#3ds). Opciones: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | sitio web | Habilite o deshabilite los campos de la tarjeta de crédito para que se muestren en la página de cierre de compra. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | sitio web | Habilitar o deshabilitar [bóveda de tarjetas de crédito](#card-vaulting). Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

### Botones de pago

La variable [!DNL PayPal Smart Buttons] las opciones de pago proporcionan un proceso de cierre de compra simple, rápido y seguro para su cliente. Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

Puede activar y configurar las opciones de pago de los botones inteligentes de PayPal:

1. Seleccione la vista de tienda, en la **[!UICONTROL Scope]** menú desplegable, para el cual desea habilitar un método de pago.
1. Para cambiar el nombre del método de pago como se muestra durante el cierre de compra, edite el valor en la variable **[!UICONTROL Checkout Title]** campo .
1. Hasta [configurar la acción de pago](production.md#set-payment-services-as-payment-method), alternancia **[!UICONTROL Payment action]** a `Authorize` o `Authorize and Capture`.
1. Utilice los selectores de alternancia para habilitar o deshabilitar [!DNL PayPal smart button] funciones de visualización:
   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Para usar Apple, pague [debe tener una cuenta de desarrollador de Apple](test-validate.md#test-in-sandbox-environment) (con información falsa de tarjeta de crédito y facturación) para probarla. Cuando esté listo para usar Apple Pay en el simulador de pruebas _o_ modo de producción, después de completar cualquier [pruebas y validación](test-validate.md), póngase en contacto con su representante de ventas para habilitarlo para sus tiendas activas.

      Al activar o desactivar la visibilidad de los botones de pago o del mensaje PayPal Pay Later, se muestra una vista previa de esa configuración en la parte inferior de la página Configuración .

1. Para habilitar el modo de depuración, cambie la **[!UICONTROL Debug Mode]** selector.
1. Haga clic en **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. [Vaciar la caché](#flush-the-cache).

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agregue el texto que se mostrará como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: campo de texto |
| [!UICONTROL Payment Action] | sitio web | La variable [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página de cierre de compra. Opciones: [!UICONTROL  Yes] / [!UICONTROL No] |
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
1. Para modificar el **[!UICONTROL Shape]**, seleccione `Pill` o `Rectangle`.
1. Para habilitar el selector de altura del botón, active la opción **[!UICONTROL Responsive button height]** selector.
1. Para modificar el **[!UICONTROL Label]**, seleccione la opción de etiqueta que desee.

   A medida que cambia las opciones de configuración para el diseño, el color, la forma, la altura y la etiqueta, se mostrará una vista previa de esa configuración en la parte inferior de la página Configuración.

1. Haga clic en **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, continúe editando o guarde los cambios.

1. [Vaciar la caché](#flush-the-cache).

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

## Vaciar la caché

Si cambia la configuración en _Configuración_, por ejemplo alternando los botones de pago, Venmo o PayPal PayLater de Apple, limpie manualmente la caché para que su tienda muestre las últimas configuraciones.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Si algún tipo de caché de la tabla Administración de caché tiene una `INVALIDATED` , es posible que la tienda no muestre la configuración más reciente para ese elemento. Vaciar la caché para actualizar la tienda y mostrar la configuración más reciente.

Para asegurarse de que su tienda muestre la configuración correcta, periódicamente [vaciar la caché](https://docs.magento.com/user-guide/system/cache-management.html).

## Bóveda de tarjetas

Puede activar la funcionalidad que permite a sus clientes almacenar (o &quot;guardar&quot;) la información de su tarjeta de crédito en su Mi cuenta para usarla en futuras compras.

Habilite o deshabilite el bóveda de tarjetas en el [Configuración del campo de la tarjeta de crédito](#credit-card-fields).

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información.

## 3DS

3DS protege a clientes y comerciantes de actividades fraudulentas en sus tiendas y permite el cumplimiento de las normas de la Unión Europea (UE).

Habilitar o deshabilitar 3DS en el [Configuración del campo de la tarjeta de crédito](#credit-card-fields).

Consulte [3DS en seguridad](security.md#3ds) para obtener más información.

## Usar varias cuentas de PayPal

En [!UICONTROL Payment Services], puede usar varias cuentas de PayPal en **one** cuenta de comerciante a nivel de sitio web. Por ejemplo, si está operando sus tiendas en varios países (que utilizan diferentes [currency](https://docs.magento.com/user-guide/stores/currency.html)) o quiere usar Adobe Commerce en algunas partes de su negocio, pero no _all_, puede configurar su cuenta de comerciante para utilizar varias cuentas de PayPal.

Consulte [Ámbito de sitio, tienda y vista](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) para obtener más información sobre la jerarquía de sitios web, tiendas y vistas de tiendas.

Su representante de ventas puede crear un [scope](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) para su cuenta de comerciante y a bordo del sitio adicional con PayPal para que cualquiera de los botones de PayPal que configure para aparecer se muestre en su sitio. Póngase en contacto con su representante de ventas para obtener ayuda sobre el uso de varias cuentas de PayPal para sus sitios web.

