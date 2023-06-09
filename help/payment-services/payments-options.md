---
title: Opciones de pago
description: Configura las opciones de pago para personalizar los métodos disponibles para los clientes de tu tienda.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 44d36c530ba95f38c264ac40123ea12ec98c32b3
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 0%

---

# Opciones de pago

Con [!DNL Adobe Commerce] y [!DNL Magento Open Source] [!DNL Payment Services], tienes varias opciones de pago disponibles. Puede configurar estas opciones de pago mediante:

* [Configuración de inicio](payments-home.md)
* [Configuración de tienda](configure-admin.md) (recomendado para opciones de pago heredadas o una configuración de varias tiendas)

Hay diferentes comportamientos para cada método de pago según dónde se encuentre en el proceso de pago:

* Página de producto: la página de producto de un elemento.
* Minicarrito: disponible al hacer clic en el icono del carrito cuando se agrega un producto al carrito
* Carro de compras: disponible al hacer clic en _Ver y editar el carro_ desde el minicarrito
* Vista de extracción: disponible al hacer clic en _Continuar con el cierre_ desde un minicarrito o carro de compras

>[!IMPORTANT]
>
>La incorporación a Payment Services debe completarse antes de que se puedan procesar los pagos.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] proporciona un pago simple y seguro para los métodos de pago con tarjeta de crédito o débito. Cuando un comprador cierra la compra utilizando campos de tarjeta de crédito, introduce su nombre, dirección de facturación e información de la tarjeta de crédito o débito para realizar el pedido. La información de sus clientes se utiliza de forma segura durante la sesión de compra para guiarlos sin problemas a través del flujo de cierre de compra.

Activar [depósito de tarjetas de crédito](#vaulting) para que tus tiendas permitan a los compradores almacenar (guardar) la información de su tarjeta de crédito para un pago rápido más tarde.

Puede configurar [!UICONTROL Credit Card Fields] en la configuración de la tienda o en la página de inicio de Payment Services. Consulte [Configuración](settings.md#credit-card-fields) para obtener más información.

También puede cambiar el diseño, la anchura, la altura y el estilo exterior de los campos de tarjeta de crédito. Consulte [Documentación de PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) para obtener más información.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], que utilizan PayPal para completar una compra, almacena la dirección de envío del comprador, las direcciones de facturación y los datos de pago para su uso posterior. Los compradores pueden utilizar cualquier forma de pago previamente almacenada u ofrecida por PayPal.

![[!DNL PayPal Smart Buttons] opciones](assets/payment-buttons.png){width="500"}

Puede configurar [!UICONTROL PayPal Smart Buttons] en la configuración de la tienda o en la página de inicio de Payment Services.  Consulte [Configuración](settings.md#payment-buttons) para obtener más información.

### [!DNL PayPal] botón

Los clientes pueden pagar con facilidad y confianza usando el botón PayPal.

El [!DNL PayPal] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

### [!DNL Venmo] botón

Los clientes pueden realizar el registro de salida utilizando [Venmo](https://venmo.com/) botón.

El [!DNL Venmo] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

### [!DNL Apple Pay] botón

Los clientes pueden usar Touch ID en sus dispositivos para usar [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), que utiliza credenciales de pago de tarjetas de crédito y débito almacenadas en su dispositivo iOS o macOS.

El [!DNL Apple Pay] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

>[!NOTE]
>
> Para usar [!DNL Apple Pay] para sus tiendas, complete [registro automático con [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registre su dominio activo_ solo la sección ) y [configúrelo para sus tiendas en [!DNL Payment Services]](settings.md#payment-buttons).

### Botón de débito o tarjeta de crédito de PayPal

Los clientes pueden pagar con el botón de débito o tarjeta de crédito de PayPal.

El botón de débito o tarjeta de crédito de PayPal está visible desde la página de pago.

Esta opción se puede utilizar para presentar una opción de pago mediante tarjeta de crédito o débito de PayPal a sus compradores cuando no tenga un proveedor de tarjeta de crédito alternativo.

### [!DNL Pay Later] botón

Ofrezca a sus clientes pagos a corto plazo sin intereses y otras opciones de financiación para que puedan comprar ahora y pagar más tarde con el [!DNL Pay Later] botón.

El [!DNL Pay Later] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra:

* **Cuando un cliente selecciona un producto entre 30 y 600 dólares**, mensajes en PayPal y [!DNL Pay Later] proporciona al cliente más información sobre el [!DNL Pay in 4] opción de pago. Los clientes pueden hacer clic **Más información** para obtener más información sobre &quot;[!DNL Pay in 4]&quot; opción _o_ Pulsa el texto &quot;O consulta la financiación especial de 6 meses&quot; en la ventana emergente para obtener más información sobre la opción Crédito PayPal y solicitarla.
* **Cuando un cliente selecciona un producto o productos que superan los 98,99 $**, mensajes en PayPal y [!DNL Pay Later] ofrece a los clientes más información sobre la opción de pago de crédito de PayPal. Los clientes pueden hacer clic **Más información** para obtener más información y solicitar la opción de crédito de PayPal, _o_ Haga clic en el texto &quot;O consulte Pagar en 4&quot; en la ventana emergente para obtener más información sobre la variable [!DNL Pay in 4] opción.

  >[!NOTE]
  >
  >Las cantidades enumeradas anteriormente están sujetas a cambios.

Consulte [Configuración](settings.md#payment-buttons) para obtener información sobre cómo deshabilitar/habilitar el [!DNL Pay Later] mensajería.

Hay dos opciones de pago con el [!DNL Pay Later] botón:

* **Pagar en 4**—Los clientes pueden pagar el saldo de su pedido en cuatro pagos sin intereses (cada dos semanas) después de un pago inicial inicial. Consulte la [Pagar en 4 documentos](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) para obtener más información.
* **Crédito de PayPal**: los clientes pueden pagar el saldo de su pedido en su totalidad durante seis meses, sin intereses. Consulte la [Documentación de crédito de PayPal](https://www.paypal.com/us/webapps/mpp/paypal-credit) para obtener más información.

### [!DNL Pay Now] botón

El [!DNL Pay Now] El botón está visible en la ventana emergente de PayPal cuando un cliente hace clic en un botón de pago de la pantalla de pagos.

Si el importe final del pedido aún no se conoce (por ejemplo, cuando aún no tiene información de la dirección de envío) y el cliente está en proceso de cierre de compra desde la página del producto, el minicarrito o el carro de compras, un _Continuar_ está disponible en su lugar. Cuando un cliente hace clic en _Continuar_ Sin embargo, después de confirmar su forma de pago, se le redirige a una página de revisión de pedidos para recopilar los detalles necesarios antes de completar el pago.

## Usar sólo botones de pago de PayPal

Para poner rápidamente su tienda en modo de producción, puede configurar _solamente_ Botones de pago de PayPal (Venmo, PayPal, etc.)—en lugar de utilizar también la opción de pago con tarjeta de crédito PayPal.

Esto le permite:

* Proporcione una variedad de opciones de pago para sus clientes sin solicitar la aprobación de su tarjeta de crédito a través de PayPal.
* Utiliza tu proveedor de tarjetas de crédito existente para realizar pagos con tarjeta de crédito, mientras también usas otras opciones de pago de PayPal.
* Utiliza los botones de pago de PayPal en una región donde PayPal no admite tarjetas de crédito como opción de pago.

Hasta **capturar pagos con _solamente_ Botones de pago PayPal (_no_ la opción de pago con tarjeta de crédito PayPal)**:

1. Asegúrese de que la tienda esté [en modo de producción](settings.md#enable-payment-services).
1. [Configura los botones de pago de PayPal que desees](settings.md#payment-buttons) en Configuración.
1. Turno _Desactivado_ el **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** en la opción _[!UICONTROL Payment buttons]_sección.

Hasta **capturar pagos con su proveedor de tarjetas de crédito existente _y_ Botones de pago de PayPal**:

1. Asegúrese de que la tienda esté [en modo de producción](settings.md#enable-payment-services).
1. [Configura los botones de pago de PayPal que desees](settings.md#payment-buttons).
1. Turno _Desactivado_ el **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** en la opción _[!UICONTROL Payment buttons]_sección.
1. Turno _Desactivado_ el **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** en la opción _[!UICONTROL Credit card fields]_y utilice su [cuenta de proveedor de tarjetas de crédito existente](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Recalculación de pedidos

Cuando un cliente introduce el flujo de cierre de compra desde el minicarrito, el carro de compras o la página de producto, se le dirige a una página de revisión de pedidos donde puede ver la dirección de envío seleccionada en una ventana emergente de PayPal. Una vez que el cliente selecciona el método de envío, el importe del pedido se vuelve a calcular correctamente y el cliente puede ver los costes e impuestos de envío.

Cuando un cliente introduce el flujo de cierre de compra desde la página de cierre de compra, el sistema ya tiene conocimiento de la dirección de envío y de la cantidad calculada final, y los totales se representan correctamente.

Las vacaciones fiscales, los gastos de envío y los impuestos sobre las ventas pueden variar considerablemente de una ubicación a otra. Después [!DNL Payment Services] recibe la dirección de envío y la tarifa, vuelve a calcular rápidamente todos los costes aplicables y los muestra correctamente durante las últimas etapas del cierre de compra.

## Bóveda de tarjetas de crédito

Los compradores pueden guardar la información de su tarjeta de crédito para futuras compras en el sitio web (cualquier tienda dentro de la cuenta del mismo comerciante).

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información.

## Seguridad

Consulte [Conformidad con PCI](security.md#pci-compliance) para obtener más información.
