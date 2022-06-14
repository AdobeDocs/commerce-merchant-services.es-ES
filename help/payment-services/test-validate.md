---
title: Prueba y validación
description: Las pruebas y la validación ayudan a garantizar que [!DNL Payment Services] funciona según lo esperado y proporciona las mejores opciones de pago para sus clientes
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 599405b908cc8b770c917a18ad488a1f69be222b
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Prueba y validación

Antes de exponer [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] para los compradores, es aconsejable realizar pruebas en el entorno de entorno limitado _y_ en producción. Las pruebas y la validación ayudan a garantizar que [!DNL Payment Services] funciona según lo esperado y proporciona las mejores opciones de pago para su tienda y sus clientes.

## Prueba en el entorno de entorno limitado

Pruebas [!DNL Payment Services] en un entorno sandbox es un paso importante para la validación, aunque es un entorno simulado conectado únicamente al simulador de pruebas de PayPal, no a bancos y comerciantes reales.

1. Complete correctamente el cierre de compra desde la tienda, ya sea con [Campos de tarjeta de crédito](payments-options.md#credit-card-fields) o [Botones inteligentes PayPal](payments-options.md#paypal-smart-buttons). Consulte [Uso del modo de entorno limitado](#use-sandbox-mode) para obtener más información sobre el uso de tarjetas de crédito falsas en las pruebas.
1. Captura (cuando se produce la acción de pago) [configure como `Authorize and Capture`](production.md#set-payment-services-as-payment-method), [reembolso](refunds.md)o [void](voids.md) el pedido que acaba de completarse. También puede [crear una factura](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;} para un pedido, si la acción de pago está establecida en `Authorize` en lugar de `Authorize and Capture`.
1. En un plazo de 24 a 48 horas, consulte la transacción y otra información en la [Informe de rutas](payouts.md).
1. Consulte los detalles del pedido en la [Informe del estado del pago del pedido](order-payment-status.md).

### Uso del modo de entorno limitado

Al probar y validar el simulador de pruebas, debe usar números de tarjeta de crédito falsos para no crear cargos reales en una cuenta de tarjeta de crédito existente.

Use el Generador de tarjetas de crédito de PayPal para [generar información de tarjeta de crédito aleatoria](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) para pruebas.

>[!NOTE]
>
>El procesamiento de pago del espacio aislado de PayPal a veces es lento y el servicio puede a veces caer. Esta situación no es indicativa de la velocidad y la eficacia del procesamiento de pagos de productos vivos.

## Prueba en producción

Es muy recomendable que pruebe [!DNL Payment Services] en producción, con tarjetas de crédito y bancos reales, antes de exponer esta funcionalidad a compradores. Aunque la prueba [!DNL Payment Services] en sandbox es importante, probar en producción es el método más sencillo para garantizar [!DNL Payment Services] funciona según lo esperado.

Puede probar [!DNL Payment Services] en producción de una de las dos maneras siguientes:

* Elija una hora en la que sepa que los compradores no realizarán ningún pedido.
* Utilice una tienda web a la que los compradores no puedan acceder temporalmente, pero que esté accesible para realizar pruebas.

Complete sus pruebas de producción con tarjetas de crédito reales y cuentas PayPal, probando todo el ciclo de vida de un pago, incluyendo la captura y el reembolso. Completar todo el proceso de cierre de compra y pago durante las pruebas le ofrece la imagen más clara de cómo su [!DNL Payment Services] funcionará cuando los compradores en directo lo utilicen.

También debe verificar que la información que aparece en los extractos bancarios para los métodos de pago que utiliza en las pruebas de producción sea correcta y esperada (incluida la descripción de su negocio).
