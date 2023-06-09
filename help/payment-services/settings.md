---
title: Configuración de servicios de pago
description: Después de la instalación, puede configurar [!DNL Payment Services] en el Inicio.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: c28b86f3a0ff0aae06a4ee8a60b2b9f304295ff8
workflow-type: tm+mt
source-wordcount: '2036'
ht-degree: 0%

---

# Configuración

Puede personalizar [!DNL Payment Services] para satisfacer sus necesidades con ajustes útiles en la [!DNL Payment Services] Hogar.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Estas opciones de configuración solo se aplican al entorno configurado en la variable _[!UICONTROL Payment mode]_del campo[_ General _opciones de configuración](#configure-general-settings).

Para ver la configuración heredada o de varias tiendas, consulte [Configurar en el administrador](configure-admin.md).

## Configuración general

El [!UICONTROL General] La configuración de permite activar o desactivar Servicios de pago como método de pago y añadir información a las transacciones de los clientes para marcar o codificar un sitio web o una vista de tienda con información personalizada.

### Habilitar servicios de pago

Puede activar [!DNL Payment Services] para su sitio web y habilite las pruebas de zona protegida o los pagos activos.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista Inicio](assets/payment-services-menu-small.png)

1. Clic **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Inicio](payments-home.md) para obtener más información.

   El _[!UICONTROL General]_Esta sección incluye la configuración utilizada para habilitar [!DNL Payment Services] como forma de pago.

1. Para habilitar [!DNL Payment Services] como forma de pago para su tienda, en la _[!UICONTROL General]_sección, alternar **[!UICONTROL Enable Payment Services as payment method]**hasta `Yes`.

1. Si todavía está realizando la prueba [!DNL Payment Services] para su tienda, establezca **Modo de pago** hasta `Sandbox`. Si está listo para habilitar los pagos activos, establézcalo en `Production`.

   >[!NOTE]
   >
   >Su _[!UICONTROL Sandbox Merchant ID]_y_[!UICONTROL Production Merchant ID]_ se generan automáticamente y están presentes en sus campos respetables cuando termine la incorporación para la zona protegida o la producción.

1. Clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, que siga editándolos o que los guarde.

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Ahora puede cambiar la configuración predeterminada de [opciones de pago](#configure-payment-options) funciones y visualización de tienda.

### Añadir descriptor temporal

Puede añadir un [!UICONTROL Soft Descriptor] a su sitio web o configuración de vistas de tienda individuales. Los descriptores leves se muestran en los extractos bancarios de transacciones de clientes. Si, por ejemplo, tiene varias tiendas, marcas o catálogos, puede delimitar fácilmente entre ellos añadiendo texto personalizado a la [!UICONTROL Soft Descriptor] field.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista Inicio](assets/payment-services-menu-small.png)

1. Clic **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Inicio](payments-home.md) para obtener más información.
1. Seleccione el sitio web o la vista de la tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea crear un descriptor temporal. Para la configuración inicial, deje esto como **[!UICONTROL Default]** para establecer el valor predeterminado.
1. Añada el texto personalizado (hasta 22 caracteres) en el campo de texto y reemplace `Custom descriptor`.
1. Clic **[!UICONTROL Save]**.
1. Para crear un descriptor temporal distinto del predeterminado configurado para una vista de sitio web o tienda:
   1. Seleccione el sitio web o la vista de la tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea crear un descriptor temporal.
   1. Alternar _desactivado_ **[!UICONTROL Use website]** (o **[!UICONTROL Use default]**, en función del ámbito seleccionado).
   1. Añada el texto personalizado en el campo de texto.
   1. Clic **[!UICONTROL Save]**.
1. Para habilitar para un sitio web o tienda, consulte el descriptor temporal predeterminado _o_ el descriptor temporal utilizado para el sitio web principal:
   1. Seleccione el sitio web o la vista de la tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea activar un descriptor temporal existente.
   1. Alternar _el_ **[!UICONTROL Use website]** (o **[!UICONTROL Use default]**, según el ámbito seleccionado).
   1. Clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, que siga editándolos o que los guarde.

### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Enable] | sitio web | Habilitar o deshabilitar [!DNL Payment Services] para su sitio web. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | vista de tienda | Defina el método o el entorno para su tienda. Opciones: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | vista de tienda | El ID de comerciante de la zona protegida, que se genera automáticamente durante la incorporación a la zona protegida. |
| [!UICONTROL Production Merchant ID] | vista de tienda | Su ID de comerciante de producción, que se genera automáticamente durante la incorporación a la zona protegida. |
| [!UICONTROL Soft Descriptor] | sitio web o vista de tienda | Añada un descriptor temporal a sus sitios web y vistas de tiendas para añadir información a las transacciones de clientes que delimitan marcas, tiendas o líneas de productos. El [!UICONTROL Use website] Esta opción aplica cualquier descriptor temporal agregado en el nivel de sitio web. El [!UICONTROL Use default] La opción aplica cualquier descriptor temporal agregado como predeterminado. |

## Configurar opciones de pago

Ahora que ha habilitado [!UICONTROL Payment Services] para su sitio web, puede cambiar la configuración predeterminada de las funciones de pago y la visualización de la tienda.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista Inicio](assets/payment-services-menu-small.png)

1. Clic **[!UICONTROL Settings]**. Consulte [Introducción a [!DNL Payment Services] Inicio](payments-home.md) para obtener más información.
1. Configurar opciones de pago para [tarjetas de crédito](#credit-card-fields), [botones de pago](#payment-buttons), y [estilo de botón](#button-style), en las secciones siguientes.

### Campos de tarjeta de crédito

El _[!UICONTROL Credit Card Fields]_La configuración de proporciona una opción de pago simple y segura para los métodos de pago con tarjeta de crédito o débito.

Consulte [Opciones de pago](payments-options.md#credit-card-fields) para obtener más información.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Vista Inicio](assets/payment-services-menu-small.png)

1. Seleccione la vista de la tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea activar una forma de pago.
1. Para cambiar el nombre del método de pago mostrado durante el cierre de compra, edite el valor en la **[!UICONTROL Checkout title]** field.
1. Hasta [establecer la acción de pago](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** hasta `Authorize` o `Authorize and Capture`.
1. Para habilitar [Autenticación segura en 3DS](security.md#3ds) (`Off` de forma predeterminada) alternar **[!UICONTROL 3DS Secure authentication]** selector a `Always` o `When required`.
1. Para habilitar o deshabilitar los campos de tarjeta de crédito en la página de pago, active la casilla de verificación **[!UICONTROL Show on checkout page]** selector.
1. Para habilitar o deshabilitar [bóveda de tarjetas](#card-vaulting), cambie el **[!UICONTROL Vault enabled]** selector.
1. Para habilitar o deshabilitar [Métodos de pago abovedados en el administrador](#card-vaulting) (para que los comerciantes completen los pedidos de los clientes en Admin mediante su método de pago abovedado), active la opción **[!UICONTROL Show vaulted methods in Admin]** selector.
1. Para habilitar o deshabilitar el modo de depuración, cambie el **[!UICONTROL Debug Mode]** selector.
1. Clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, que siga editándolos o que los guarde.

1. [Vaciar la caché](#flush-the-cache).

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Añade el texto que se mostrará como el título de esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | sitio web | El [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3DS Secure authentication] | sitio web | Habilitar o deshabilitar [Autenticación segura en 3DS](security.md#3ds). Opciones: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | sitio web | Habilitar o deshabilitar los campos de tarjeta de crédito para mostrar en la página de cierre de compra. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | vista de tienda | Habilitar o deshabilitar [depósito de tarjetas de crédito](vaulting.md). Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show vaulted payment methods in Admin] | vista de tienda | Habilite o deshabilite la capacidad para que el comerciante complete pedidos de clientes en Admin [uso de un método de pago abovedado](vaulting.md). Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

### Botones de pago

El [!DNL PayPal Smart Buttons] las opciones de pago ofrecen un proceso de pago simple, rápido y seguro para tu cliente. Consulte [Opciones de pago](payments-options.md#paypal-smart-buttons) para obtener más información.

Puedes activar y configurar las opciones de pago de los botones inteligentes de PayPal:

1. Seleccione la vista de la tienda, en la **[!UICONTROL Scope]** menú desplegable, para el que desea activar una forma de pago.
1. Para cambiar el nombre de la forma de pago como se muestra durante el cierre de compra, edite el valor en la **[!UICONTROL Checkout Title]** field.
1. Hasta [establecer la acción de pago](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** hasta `Authorize` o `Authorize and Capture`.
1. Utilice los selectores de alternancia para activar o desactivar [!DNL PayPal smart button] funciones de visualización:

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Para usar Apple Pay [debe tener una cuenta de Apple sandbox tester](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (con tarjeta de crédito falsa e información de facturación) para probarlo. Cuando esté listo para usar Apple Pay en una zona protegida _o_ modo de producción, después de completar cualquier [pruebas y validación](test-validate.md#test-in-sandbox-environment), completado [registro automático con [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registre su dominio activo_ solo la sección ) y [configúrelo para sus tiendas en [!DNL Payment Services]](settings.md#payment-buttons).

     Al activar o desactivar la visibilidad de los botones de pago o del mensaje PayPal Más tarde, se muestra una vista previa visual de esa configuración en la parte inferior de la página Configuración.

1. Para habilitar el modo de depuración, cambie el **[!UICONTROL Debug Mode]** selector.
1. Clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, que siga editándolos o que los guarde.

1. [Vaciar la caché](#flush-the-cache).

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|---|---|---|
| [!UICONTROL Title] | vista de tienda | Agrega el texto que se mostrará como título para esta opción de pago en la vista Método de pago durante el cierre de compra. Opciones: campo de texto |
| [!UICONTROL Payment Action] | sitio web | El [acción de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para el método de pago especificado. Opciones: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página de cierre de compra. Opciones: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página de detalles del producto. Opciones: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la vista previa del minicarrito. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | vista de tienda | Habilitar o deshabilitar [!DNL PayPal Smart Buttons] en la página del carro de compras. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | vista de tienda | Activar o desactivar la aparición de la opción de pago posterior en la que se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | sitio web | Habilite o deshabilite la mensajería Pagar más tarde en el carro de compras, la página del producto, el minicarrito y durante el flujo de cierre de compra. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | vista de tienda | Activa o desactiva la opción de pago Venmo donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | vista de tienda | Activa o desactiva la opción de pago de Apple Pay donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Credit and Debit card button] | vista de tienda | Activa o desactiva la opción de pago con tarjeta de crédito y débito donde se muestran los botones de pago. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | sitio web | Habilite o deshabilite el modo de depuración. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |

### Estilo de botón

También puede configurar la variable _[!UICONTROL Button style]_opciones de los botones inteligentes de PayPal:

1. Para cambiar el **[!UICONTROL Layout]**, seleccione `Vertical` o `Horizontal`.

   >[!NOTE]
   >
   > Si el estilo del botón está configurado como `Horizontal` Si la tienda está configurada para mostrar varios botones inteligentes de PayPal, es posible que solo veas dos botones en la página del producto, la página de pago y el minicarrito, y un botón en el carrito.

1. Para habilitar el eslogan en un diseño horizontal, alterne la **[!UICONTROL Show tagline]** selector.
1. Para modificar **[!UICONTROL Color]**, seleccione la opción de color que desee.
1. Para modificar **[!UICONTROL Shape]**, seleccione `Pill` o `Rectangle`.
1. Para habilitar el selector de altura del botón, alterne la opción **[!UICONTROL Responsive button height]** selector.
1. Para modificar **[!UICONTROL Label]**, seleccione la opción de etiqueta que desee.

   A medida que cambia las opciones de configuración de diseño, color, forma, altura y etiqueta, aparece una vista previa visual de esa configuración en la parte inferior de la página Configuración.

   ![[!DNL PayPal Smart Buttons] opciones](assets/payment-buttons.png){width="500"}

1. Clic **[!UICONTROL Save]**.

   Si intenta salir de esta vista sin guardar los cambios, aparecerá un modal que le pedirá que descarte los cambios, que siga editándolos o que los guarde.

1. [Vaciar la caché](#flush-the-cache).

Puede configurar [!DNL PayPal Smart Buttons] estilo [en la configuración heredada en el Administrador](configure-admin.md#configure-paypal-smart-buttons) o aquí en [!DNL Payment Services Home]. Consulte [Guía de estilo de los botones de PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obtener más información sobre las opciones.

#### Opciones de configuración

| Campo | Ámbito | Descripción |
|--- |--- |--- |
| [!UICONTROL Layout] | Vista de tienda | Definir el estilo del diseño de los botones de pago. Opciones: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Vista de tienda | Habilitar/deshabilitar el lema. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Vista de tienda | Defina el color de los botones de pago. Opciones: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Vista de tienda | Definir la forma de los botones de pago. Opciones: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Vista de tienda | Define si los botones de pago utilizan una altura predeterminada. Opciones: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Vista de tienda | Definir la altura de los botones de pago. Valor predeterminado: ninguno |
| [!UICONTROL Label] | Vista de tienda | Definir la etiqueta que aparece en los botones de pago. Opciones: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Configurar funciones

Para asegurarse de que los usuarios administradores puedan crear y administrar pedidos en la administración de Commerce, habilite [!DNL Payment Services]Recursos específicos de a las funciones de usuario.

Consulte [Funciones de usuario](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) para obtener información sobre cómo administrar las funciones.

Al asignar recursos a la función, debe seleccionar:

- **Pagar con[!DNL Payment Services]**: este recurso garantiza que, al crear un pedido en el administrador, [!DNL Payment Services] las tarjetas de crédito están disponibles como forma de pago. Si selecciona la opción **Acciones** recurso principal, este recurso también se selecciona.
- **[!DNL Payment Services]**: este recurso incluye el **Tablero** y **Proxy de servicios SaaS** recursos, que también deben seleccionarse. Garantizan que [!DNL Payment Services] aparece en la _Ventas_ menú.

  ![Recursos de servicios de pago](assets/roles-payments.png)

## Vaciar la caché

Si cambia la configuración en _Configuración_, por ejemplo, cambiando los botones Apple Pay, Venmo o PayPal Paylater, vacíe manualmente la caché para que la tienda muestre las configuraciones más recientes.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Clic **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

Si algún tipo de caché de la tabla Administración de caché tiene un `INVALIDATED` estado, es posible que la tienda no muestre la configuración más reciente de ese elemento. Vacíe la caché para actualizar el almacén y mostrar la configuración más reciente.

Para asegurarse de que su tienda muestra la configuración correcta, haga lo siguiente periódicamente [vaciar la caché](https://docs.magento.com/user-guide/system/cache-management.html).

## Bóveda de tarjetas

Puede habilitar una funcionalidad que permita a los clientes almacenar (o &quot;guardar&quot;) la información de su tarjeta de crédito en Mi cuenta para usarla en futuras compras.

También puede utilizar el depósito de tarjetas en el Administrador para completar pedidos posteriores para clientes existentes.

Habilite o deshabilite el almacenamiento de tarjetas en [Configuración del campo de tarjeta de crédito](#credit-card-fields).

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información.

## 3DS

3DS protege a clientes y comerciantes de actividades fraudulentas en sus tiendas y permite el cumplimiento de las normas de la Unión Europea (UE).

Activar o desactivar 3DS en [Configuración del campo de tarjeta de crédito](#credit-card-fields).

Consulte [3DS en seguridad](security.md#3ds) para obtener más información.

## Usar varias cuentas de PayPal

Entrada [!UICONTROL Payment Services], puedes usar varias cuentas de PayPal dentro de **uno** cuenta de comerciante en el nivel de sitio web. Por ejemplo, si tiene tiendas en varios países (que usan diferentes [divisas](https://docs.magento.com/user-guide/stores/currency.html)) o desea utilizar Adobe Commerce para algunas partes de su negocio, pero no para _todo_, puede configurar su cuenta de comerciante para que utilice varias cuentas de PayPal.

Consulte [Sitio, tienda y vista de ámbito](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) para obtener más información sobre la jerarquía de sitios web, tiendas y vistas de tiendas.

El representante de ventas puede crear un nuevo [ámbito](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) para tu cuenta de comerciante e incorpora el sitio adicional con PayPal para que cualquier botón de PayPal que configures aparezca en tu sitio. Póngase en contacto con su representante de ventas para obtener ayuda con el uso de varias cuentas de PayPal para sus sitios web.
