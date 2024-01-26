---
title: Probar y validar
description: Las pruebas y la validación ayudan a garantizar que [!DNL Payment Services] Las funciones de funcionan según lo esperado y proporcionan las mejores opciones de pago para sus clientes
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Probar y validar

Antes de exponer [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] Para los compradores, es aconsejable realizar pruebas en el entorno de zona protegida _y_ en producción. Las pruebas y la validación ayudan a garantizar que [!DNL Payment Services] Las funciones de funcionan según lo esperado y proporcionan las mejores opciones de pago para su tienda y clientes.

## Realizar pruebas en un entorno limitado

Pruebas [!DNL Payment Services] en un entorno de zona protegida es un paso de validación importante, aunque sea un entorno simulado conectado únicamente a la zona protegida de PayPal, no a bancos y comerciantes reales.

1. Completa un pago y envío correcto desde tu tienda, ya sea con [Campos de tarjeta de crédito](payments-options.md#credit-card-fields) o cualquiera de los [Botones de pago de PayPal](payments-options.md#paypal-smart-buttons). Consulte [Credenciales de prueba](#testing-credentials) para obtener más información sobre el uso de tarjetas de crédito falsas para realizar pruebas.
1. Capturar (cuando su acción de pago sea [establezca en `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [reembolsar](refunds.md), o [anular](voids.md) el pedido que acaba de completar. También puede hacer lo siguiente [crear una factura](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} para un pedido, si la acción de pago está configurada en `Authorize` en lugar de `Authorize and Capture`.
1. En un plazo de 24 a 48 horas, consulte la transacción y otra información en la [Informe de pagos](payouts.md).
1. Consulte los detalles del pedido en la [Informe de estado de pago del pedido](order-payment-status.md).

### Credenciales de prueba

Al probar y validar su zona protegida debe utilizar números de tarjeta de crédito falsos, para que no esté creando cargos reales en una cuenta de tarjeta de crédito existente.

Utilice el generador de tarjetas de crédito de PayPal para [generar información de tarjeta de crédito aleatoria](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) para pruebas.

Para probar Apple Pay en modo de zona protegida:

* Crear un [Cuenta del comprobador de zona protegida Apple](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), con tarjeta de crédito falsa e información de facturación.
* [Registro de dominios de zona protegida](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>El procesamiento del pago en la zona protegida de PayPal a veces es lento y el servicio puede caerse ocasionalmente. Esta situación no es una indicación de la velocidad y la eficiencia del procesamiento de pagos de productos en vivo.

## Prueba en producción

Se recomienda encarecidamente que realice pruebas [!DNL Payment Services] en producción, con tarjetas de crédito reales y bancos, antes de exponer esta funcionalidad a los compradores. Aunque las pruebas [!DNL Payment Services] en la zona protegida es importante, la prueba en la producción es el método más infalible para garantizar [!DNL Payment Services] funciona según lo esperado.

Puede probar [!DNL Payment Services] en producción de una de las dos maneras siguientes:

* Elija un momento en el que sepa que los compradores no realizarán ningún pedido.
* Utilice una tienda web a la que los compradores no puedan acceder temporalmente, pero a la que usted pueda acceder para realizar pruebas.

Complete sus pruebas de producción con tarjetas de crédito reales y cuentas de PayPal, probando todo el ciclo de vida de un pago, incluyendo la captura y el reembolso. Completar todo el proceso de pago y envío durante las pruebas te ofrece una visión más clara de cómo [!DNL Payment Services] La funcionalidad de funcionará cuando la usen compradores activos.

También debe verificar que la información que aparece en los extractos bancarios para los métodos de pago que utiliza en las pruebas de producción es correcta y esperada (incluida la descripción de su negocio).

Para probar Apple Pay en el modo de producción, debe [registro de los dominios de producción](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
