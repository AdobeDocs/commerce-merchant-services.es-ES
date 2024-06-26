---
title: Opciones de pago
description: Configura las opciones de pago para personalizar los métodos disponibles para los clientes de tu tienda.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# Opciones de pago

Con [!DNL Adobe Commerce] y [!DNL Magento Open Source] [!DNL Payment Services], tienes varias opciones de pago disponibles.

Puede configurar estas opciones de pago en [Configuración de inicio](payments-home.md) o [Configuración de tienda](configure-admin.md) (recomendado para opciones de pago heredadas o una configuración de varias tiendas).

Hay diferentes comportamientos para cada método de pago según dónde se encuentre en el proceso de pago:

* Página de producto: la página de producto de un elemento.
* Minicarrito: disponible al hacer clic en el icono del carro de compras cuando se agrega un producto al carro de compras
* Carro de compras: disponible al hacer clic en _Ver y editar el carro_ desde el minicarrito
* Vista de extracción: disponible al hacer clic en _Continuar con el cierre_ desde un minicarrito o carro de compras

>[!IMPORTANT]
>
>[!DNL Payment Services] la incorporación debe completarse antes de que se puedan procesar los pagos.

## Experiencia de pagos estándar y avanzados

[!DNL Payment Services] proporciona **Avanzadas** (totalmente compatible) y **Standard** (Pago y envío exprés) opciones de pago y flujos de incorporación, según el país en el que opere.

* **Avanzadas** - Todo disponible [opciones de pagos](../payment-services/payments-options.md) están disponibles para el [países con pleno apoyo](../payment-services/overview.md#availability). Durante la incorporación para habilitar los pagos activos, seleccione la [Opción de incorporación avanzada](../payment-services/production.md#advanced-onboarding).
* **Standard** - Un subconjunto de opciones de pagos (Pago y envío exprés) —tarjetas de crédito y débito de PayPal— está disponible para otros países compatibles. [Campos de tarjeta de crédito](#credit-card-fields) y [Apple Pay](#apple-pay-button) no están disponibles para esta opción de incorporación. Durante la incorporación para habilitar los pagos activos, seleccione la [Opción de incorporación estándar](../payment-services/production.md#standard-onboarding).

Consulte [Activar [!DNL Payment Services] para producción](../payment-services/production.md#complete-merchant-onboarding) para obtener información sobre cómo completar la incorporación avanzada y estándar.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] proporciona un pago simple y seguro para los métodos de pago con tarjeta de crédito o débito. Cuando un comprador cierra la compra utilizando campos de tarjeta de crédito, introduce su nombre, dirección de facturación e información de la tarjeta de crédito o débito para realizar el pedido. La información de sus clientes se utiliza de forma segura durante la sesión de compra para guiarlos sin problemas a través del flujo de cierre de compra.

![Campos de tarjeta de crédito en cierre de compra](assets/credit-card-fields.png){width="500" zoomable="yes"}

Activar [depósito de tarjetas de crédito](#vaulting) para que tus tiendas permitan a los compradores almacenar (guardar) la información de su tarjeta de crédito para un pago rápido más tarde.

Puede configurar [!UICONTROL Credit Card Fields] en la configuración de la tienda o en [!DNL Payment Services] Hogar. Consulte [Configuración](settings.md#credit-card-fields) para obtener más información.

También puede cambiar el diseño, la anchura, la altura y el estilo exterior de los campos de tarjeta de crédito. Consulte [Documentación de PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) para obtener más información.

## [!DNL Apple Pay] botón

Los clientes pueden utilizar [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), que utiliza las credenciales de pago de las tarjetas de crédito y débito almacenadas en un dispositivo iOS o macOS para realizar compras.

[!DNL Apple Pay] solo está disponible en el explorador Safari. Los comerciantes pueden añadir hasta 99 dominios por cuenta de comerciante.

![Botón Apple Pay en la minicart](assets/applepay-button.png){width="500" zoomable="yes"}

El [!DNL Apple Pay] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

>[!NOTE]
>
> Para usar [!DNL Apple Pay] para sus tiendas, complete [registro automático con [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registre su dominio activo_ solo la sección ) y [configúrelo para sus tiendas en [!DNL Payment Services]](settings.md#payment-buttons).

Puede configurar [!UICONTROL Apple Pay] en la configuración de la tienda o en la página de inicio de Payment Services. Consulte [Configuración](settings.md#apple-pay) para obtener más información.

## [!DNL Google Pay] botón

Los clientes pueden utilizar [[!DNL Google Pay]](https://pay.google.com/about/) al añadir los datos de pago a su cuenta de Google, donde se almacenan de forma segura para una experiencia de pago sin problemas.

[!DNL Google Pay] solo está disponible en determinados países o regiones y en determinados dispositivos. Consulte [[!DNL Google Pay] documentación](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration) para obtener más información.

![Botón Google Pay en el pago y envío](assets/google-pay-button.png){width="500" zoomable="yes"}

El [!DNL Google Pay] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

Puede configurar [!UICONTROL Google Pay] en la configuración de la tienda o en la página de inicio de Payment Services. Consulte [Configuración](configure-admin.md) para obtener más información.

>[!NOTE]
>
> El [!DNL Google Pay] La API solo se puede utilizar en sitios web en un contexto seguro. Consulte [Solución de problemas](https://developers.google.com/pay/api/web/support/troubleshooting) para obtener más información.

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], que utilizan PayPal para completar una compra, almacena la dirección de envío del comprador, las direcciones de facturación y los datos de pago para su uso posterior. Los compradores pueden utilizar cualquier forma de pago previamente almacenada u ofrecida por PayPal.

![Botón PayPal](assets/paypal-button.png){width="350" zoomable="yes"}

Puede configurar [!UICONTROL PayPal payment buttons] en la configuración de la tienda o en [!DNL Payment Services] Hogar. Consulte [Configuración](settings.md#payment-buttons) para obtener más información.

Conoce la disponibilidad de formas de pago por país en PayPal [Documentación de métodos de pago](https://developer.paypal.com/docs/checkout/payment-methods/).

### [!DNL PayPal] botón

Los clientes pueden pagar con facilidad y confianza usando el botón PayPal.

El [!DNL PayPal] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

### [!DNL Venmo] botón

Los clientes pueden realizar el registro de salida utilizando [Venmo](https://venmo.com/) botón.

El [!DNL Venmo] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

### Botón de débito o tarjeta de crédito de PayPal

Los clientes pueden pagar con el botón de débito o tarjeta de crédito de PayPal.

El botón de débito o tarjeta de crédito de PayPal está visible desde la página de pago.

Esta opción se puede utilizar para presentar una opción de pago con tarjeta de crédito o débito a sus compradores con un botón alojado en PayPal como alternativa a una integración con tarjeta de crédito.

### [!DNL Pay Later] botón

Ofrezca a sus clientes pagos a corto plazo sin intereses y otras opciones de financiación para que puedan comprar ahora y pagar más tarde con el [!DNL Pay Later] botón.

El [!DNL Pay Later] El botón está visible desde la página de producto, el minicarrito, el carro de compras y las vistas de cierre de compra.

Ver información sobre las ofertas de Pago posterior en [Documentación de ofertas de PayPal más tarde](https://developer.paypal.com/docs/checkout/pay-later/us/). Utilice el **País o región** para seleccionar una región de interés.

Obtenga información sobre cómo deshabilitar o habilitar el [!DNL Pay Later] mensajería actualizando el [Configuración](settings.md#payment-buttons) configuración.

## Usar sólo botones de pago de PayPal

Para poner rápidamente su tienda en modo de producción, puede configurar _solamente_ Botones de pago de PayPal (Venmo, PayPal, etc.)—en lugar de utilizar también la opción de pago con tarjeta de crédito PayPal.

Esto le permite:

* Proporcione varias opciones de pago para sus clientes, incluidos los botones de pago Venmo y PayPal, con la opción de desactivar los campos de tarjeta alojados en PayPal y utilizar un proveedor de tarjeta de crédito existente.
* Utiliza tu proveedor de tarjetas de crédito existente para realizar pagos con tarjeta de crédito, al mismo tiempo que utilizas otras opciones de pago de PayPal.
* Utiliza los botones de pago de PayPal en las regiones donde PayPal no admite tarjetas de crédito como opción de pago.

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
