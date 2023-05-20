---
title: "Probando el [!DNL Quick Checkout] para la extensión de Adobe Commerce"
description: '"Las pruebas y la validación garantizan que la [!DNL Quick Checkout] la extensión funciona según lo esperado".'
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Pruebe el [!DNL Quick Checkout] extensión

Antes de exponer el [!DNL Quick Checkout] para la extensión de Adobe Commerce a sus compradores, se recomienda realizar pruebas en un entorno de zona protegida y en el entorno de producción. Las pruebas y la validación ayudan a garantizar que la [!DNL Quick Checkout] funciona según lo esperado y ofrece una experiencia de cierre de compra perfecta para su tienda y clientes.

Antes de configurar el [!DNL Quick Checkout] en el administrador de Adobe Commerce es necesario crear  [producción](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} cuentas de comerciante en [!DNL Bolt].

## Pruebas en espacios aislados

Prueba de la [!DNL Quick Checkout] en un entorno de zona protegida es un paso de validación muy importante, aunque sea un entorno simulado conectado únicamente a la [!DNL Bolt] cuenta de zona protegida, no a bancos reales o comerciantes.

### Uso de cuentas de zona protegida

Al probar y validar la zona protegida, debe utilizar un número de tarjeta de crédito falso y un [espacio aislado](https://merchant-sandbox.bolt.com/register){target="_blank"} cuenta de comerciante en [!DNL Bolt], para que no cree cargos reales en una cuenta de tarjeta de crédito existente.

## Pruebas en producción

>[!NOTE]
>
> Se recomienda encarecidamente que pruebe el [!DNL Quick Checkout] en un entorno de producción, con tarjetas de crédito reales y bancos, antes de exponer la extensión a los compradores. A pesar de que las pruebas en entornos limitados son importantes, las pruebas en producción son el método más seguro para garantizar que funcione según lo esperado.

Pruebe el entorno de producción de una de las dos formas recomendadas:

- Elija un momento en el que sepa que los compradores no realizarán ningún pedido.
- Utilice una tienda web a la que los compradores no puedan acceder temporalmente, pero a la que usted pueda acceder para realizar pruebas.

Complete sus pruebas de producción con tarjetas de crédito reales y [!DNL Bolt] cuentas de producción, probar todo el ciclo de vida de un cierre de compra. Cuando completa todo el flujo de cierre de compra durante las pruebas, le ofrece una imagen clara de cómo funciona su funcionalidad cuando los compradores en vivo la utilizan.

También debe verificar que la información que aparece en los extractos bancarios para los métodos de pago que utiliza en las pruebas de producción es correcta y esperada (incluida la descripción de su negocio).

## Cómo probar el [!DNL Quick Checkout] extensión

Completa un pago y envío correcto desde tu tienda:

1. Ve a la tienda y coloca los artículos que desees en el carro de compras.
1. Continúe con el cierre de compra.
1. Introduzca una dirección de correo electrónico asociada a un [!DNL Bolt] cuenta cuando se le solicite.
1. Introduzca la contraseña de un solo uso (OTP) enviada a la dirección de correo electrónico de la cuenta.
1. Seleccione el tablero de entorno:

   - Sandbox
   - Producción

1. Realice el pedido.

Una vez realizado un pedido, puede ver los detalles de sus pedidos en su _cuadrícula de pedidos_ ver:

1. Vaya a _Ventas_ > _Pedidos_.
1. Consulte la lista de todos los pedidos realizados.

Consulte la [Pedidos](https://docs.magento.com/user-guide/sales/orders.html) para obtener más información acerca de su _cuadrícula de pedidos_ vista.
