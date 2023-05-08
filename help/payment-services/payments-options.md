---
title: Opciones de pago
description: Configure las opciones de pago para personalizar los métodos disponibles para los clientes de la tienda.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 9bc392f2ae12269ded6174b830562444d6827f5f
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

---

# Opciones de pago

con [!DNL Adobe Commerce] y [!DNL Magento Open Source] [!DNL Payment Services], tiene a su disposición varias opciones de pago. Puede configurar estas opciones de pago mediante:

* [Configuración de inicio](payments-home.md)
* [Configuración del almacén](configure-admin.md) (recomendado para opciones de pago preexistentes o configuración de varias tiendas)

Existen diferentes comportamientos para cada método de pago según la ubicación en el proceso de cierre de compra:

* Página de producto: la página de producto de un elemento
* Minicarro: disponible al hacer clic en el icono del carro de compras cuando se agrega un producto al carro de compras
* Carro de compras: disponible al hacer clic en _Ver y editar el carro_ del minicarro
* Vista de cierre de compra: disponible al hacer clic en _Continuar con el cierre de compra_ desde minicarrito o carro de compras

>[!IMPORTANT]
>
>La incorporación de Servicios de Pago debe completarse antes de que se puedan procesar los pagos.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] proporcionar un cierre de compra simple y seguro para métodos de pago con tarjeta de crédito o tarjeta de débito. Cuando un comprador cierra la compra utilizando campos de tarjeta de crédito, introduce su nombre, dirección de facturación e información de tarjeta de crédito o débito para realizar el pedido. La información de sus clientes se utiliza de forma segura durante la sesión de compra para guiarlos sin problemas a través del flujo de cierre de compra.

Habilitar [bóveda de tarjetas de crédito](#vaulting) para que sus tiendas permitan a los compradores almacenar (guardar) la información de su tarjeta de crédito para realizar una compra rápida más tarde.

Puede configurar [!UICONTROL Credit Card Fields] en la configuración de la tienda o en la página de inicio de los servicios de pago. Consulte [Configuración](settings.md#credit-card-fields) para obtener más información.

También puede cambiar el diseño, la anchura, la altura y el estilo exterior de los campos de la tarjeta de crédito. Consulte [Documentación de PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) para obtener más información.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], que utilizan PayPal para completar una compra, almacena la dirección de envío, las direcciones de facturación y los detalles de pago del comprador para su uso posterior. Los compradores pueden utilizar cualquier método de pago previamente almacenado u ofrecido por PayPal.

![[!DNL PayPal Smart Buttons] opciones](assets/buttons-md.png)

Puede configurar [!UICONTROL PayPal Smart Buttons] en la configuración de la tienda o en la página de inicio de los servicios de pago.  Consulte [Configuración](settings.md#payment-buttons) para obtener más información.

### [!DNL PayPal] botón

Los clientes pueden realizar el check out con facilidad y confianza mediante el botón PayPal.

La variable [!DNL PayPal] se puede ver en la página del producto, el minicarro, el carro de compras y las vistas de cierre de compra.

### [!DNL Venmo] botón

Los clientes pueden realizar la comprobación utilizando la variable [Venmo](https://venmo.com/) botón.

La variable [!DNL Venmo] se puede ver en la página del producto, el minicarro, el carro de compras y las vistas de cierre de compra.

### [!DNL Apple Pay] botón

Los clientes pueden utilizar el ID táctil en sus dispositivos para utilizar [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), que utiliza credenciales de pago de tarjeta de crédito y débito almacenadas en su dispositivo iOS o macOS.

La variable [!DNL Apple Pay] se puede ver en la página del producto, el minicarro, el carro de compras y las vistas de cierre de compra.

>[!NOTE]
>
> Para usar [!DNL Apple Pay] para sus tiendas, complete [registro propio con [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registrar el dominio de lanzamiento_ solo sección) y [configúrelo para sus tiendas en [!DNL Payment Services]](settings.md#payment-buttons).

### [!DNL Pay Later] botón

Ofrezca a sus clientes pagos a corto plazo, sin intereses y otras opciones de financiación para que puedan comprar ahora y pagar más tarde con el [!DNL Pay Later] botón.

La variable [!DNL Pay Later] se puede ver en la página del producto, el minicarro, el carro de compras y las vistas de cierre de compra:

* **Cuando un cliente selecciona un producto entre 30 y 600 dólares**, mensajería en PayPal y [!DNL Pay Later] proporciona al cliente más información sobre los [!DNL Pay in 4] opción de pago. Los clientes pueden hacer clic en **Más información** para obtener más información sobre &quot;[!DNL Pay in 4]&quot;, opción _o_ haga clic en el texto &quot;O ver 6 meses de financiación especial&quot; en la ventana emergente para conocer y solicitar la opción Crédito de PayPal.
* **Cuando un cliente selecciona un producto o productos que exceden los 98,99 dólares**, mensajería en PayPal y [!DNL Pay Later] Los botones proporcionan a los clientes más información acerca de la opción de pago PayPal Credit . Los clientes pueden hacer clic en **Más información** para conocer y solicitar la opción Crédito PayPal, _o_ haga clic en el texto &quot;O consulte Pagar en 4&quot; en la ventana emergente para obtener más información sobre la [!DNL Pay in 4] .

   >[!NOTE]
   >
   >Las cantidades enumeradas arriba están sujetas a cambios.

Consulte [Configuración](settings.md#payment-buttons) para aprender a desactivar o habilitar el [!DNL Pay Later] mensajería.

Hay dos opciones de pago con la variable [!DNL Pay Later] botón:

* **Pago en 4**—Los clientes pueden pagar su saldo en cuatro pagos sin intereses (cada dos semanas) después de un pago inicial. Consulte la [Pagar en 4 documentación](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) para obtener más información.
* **Crédito PayPal**: los clientes pueden pagar su saldo total en seis meses, sin intereses. Consulte la [Documentación de crédito de PayPal](https://www.paypal.com/us/webapps/mpp/paypal-credit) para obtener más información.

### [!DNL Pay Now] botón

La variable [!DNL Pay Now] está visible en la ventana emergente de PayPal cuando un cliente hace clic en un botón de pago en la pantalla de pagos.

Si todavía no se conoce la cantidad del pedido final (por ejemplo, cuando todavía no tiene información de la dirección de envío) y el cliente está en proceso de retirar de la página del producto, el minicarro o el carro de compras, una _Continuar_ en su lugar. Cuando un cliente hace clic en _Continuar_, una vez que confirman su método de pago, se les dirige a una página de revisión de pedidos para reunir los detalles necesarios antes de completar el cierre de compra.

## Recalculación de pedidos

Cuando un cliente entra en el flujo de cierre de compra desde el minicarro, el carro de compras o la página de producto, se le dirige a una página de revisión de pedidos donde puede ver la dirección de envío seleccionada en una ventana emergente de PayPal. Una vez que el cliente selecciona el método de envío, el importe del pedido se vuelve a calcular correctamente y el cliente puede ver los costes de envío y los impuestos.

Cuando un cliente introduce el flujo de cierre de compra desde la página de cierre de compra, el sistema ya conoce la dirección de envío y la cantidad calculada final, y los totales se representan correctamente.

Las vacaciones fiscales, los costes de envío y los impuestos sobre las ventas pueden variar mucho de una ubicación a otra. Después [!DNL Payment Services] recibe la dirección de envío y la tarifa, vuelve a calcular rápidamente todos los costes aplicables y los muestra correctamente durante las últimas etapas del cierre de compra.

## Cierre de compra desde la página de producto

Cuando un cliente cierra la compra directamente desde la página del producto, mediante PayPal o [!DNL Pay Later] , solo se compra el elemento representado en la página de producto actual. Los artículos que ya residen en el carro de compras del cliente no se agregan al flujo de cierre de compra y no se compran.

Si el cliente cancela el pedido, el artículo de la página de producto actual se agrega al carro de compras del cliente, uniéndose a cualquier otro artículo presente en el carro de compras. Esta función permite al cliente adquirir rápidamente el artículo que está viendo, al mismo tiempo que mantiene cualquier otro artículo que agregó al carro de compras anteriormente al examinar productos.

Cuando un cliente introduce el flujo de cierre de compra desde la página del producto, la página de cierre de compra se simplifica (la vista solo muestra los datos y las opciones relacionados con el pedido).

## Bóveda de tarjetas de crédito

Los compradores pueden almacenar (o &quot;guardar&quot;) la información de sus tarjetas de crédito para futuras compras a nivel de sitio web (cualquier tienda dentro de la cuenta del mismo comerciante).

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información.

## Seguridad

Consulte [Cumplimiento de PCI](security.md#pci-compliance) para obtener más información.
