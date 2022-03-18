---
title: Prueba de la variable [!DNL Express Checkout] para la extensión de Adobe Commerce
description: La prueba y validación garantizan que la variable [!DNL Express Checkout] funciona según lo esperado.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Prueba de la variable [!DNL Express Checkout] para la extensión de Adobe Commerce

>[!IMPORTANT]
>
> Esta función es para usuarios del Programa de Adoptadores Anticipados (EAP, por sus siglas en inglés) y aún no es accesible para todos los clientes. Actualmente está limitado a los clientes de EE. UU. Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.

Antes de exponer la variable [!DNL Express Checkout] para la extensión de Adobe Commerce a los compradores, se recomienda realizar pruebas en un entorno de entorno limitado y en el entorno de producción. Las pruebas y la validación ayudan a garantizar que la variable [!DNL Express Checkout] funciona según lo esperado y proporciona una experiencia de cierre de compra perfecta para su tienda y sus clientes.

Antes de configurar la variable [!DNL Express Checkout] en el administrador de Adobe Commerce, es necesario crear un [producción](https://merchant.bolt.com/register){target=&quot;_blank&quot;} y [entorno limitado](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} cuenta de comerciante en Bolt.

## Pruebas en el simulador de pruebas

Prueba de la variable [!DNL Express Checkout] en un entorno sandbox es un paso de validación muy importante, aunque es un entorno simulado conectado únicamente a la cuenta de entorno limitado de Bolt, no a bancos reales o comerciantes.

### Uso de una cuenta de entorno limitado

Al probar y validar el simulador de pruebas, debe utilizar un número de tarjeta de crédito falso y un [entorno limitado](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} cuenta de comerciante en Bolt, para que no esté creando cargos reales en una cuenta de tarjeta de crédito existente.

## Pruebas en producción

>[!NOTE]
>
> Es muy recomendable probar la variable [!DNL Express Checkout] en un entorno de producción, con tarjetas de crédito y bancos reales, antes de exponer la extensión a compradores. Aunque las pruebas en entornos limitados son importantes, las pruebas en producción son el método más infalible para asegurarse de que funciona según lo esperado.

Se recomienda realizar pruebas en producción de una de las dos maneras siguientes:

- Elija una hora en la que sepa que los compradores no realizarán ningún pedido.
- Utilice una tienda web a la que los compradores no puedan acceder temporalmente, pero que esté accesible para realizar pruebas.

Complete sus pruebas de producción con tarjetas de crédito reales y cuentas de producción de Bolt, probando todo el ciclo de vida de un cierre de compra. Cuando completa el flujo de cierre de compra durante las pruebas, obtiene una idea clara de cómo funciona la funcionalidad cuando la utilizan los compradores activos.

También debe verificar que la información que aparece en los extractos bancarios para los métodos de pago que utiliza en las pruebas de producción sea correcta y esperada (incluida la descripción de su negocio).

## Cómo probar el [!DNL Express Checkout] Extensión

Complete un cierre de compra correcto desde la tienda siguiendo estos pasos:

1. Vaya a su tienda y coloque los artículos deseados en su carro de compras.
1. Continúe con el cierre de compra.
1. Introduzca una dirección de correo electrónico asociada a una cuenta de Bolt cuando se le solicite.
1. Introduzca la contraseña única (OTP) enviada a la dirección de correo electrónico de la cuenta.
1. Seleccione el tablero de entorno:

   - Sandbox
   - Producción

1. Realizar pedido.

Una vez realizado el pedido, puede ver los detalles de sus pedidos en su _Cuadrícula de pedidos_ vista:

1. Vaya a _Ventas_ > _Pedidos_.
1. Consulte la lista de todos los pedidos colocados.

Consulte la [pedidos](https://docs.magento.com/user-guide/sales/orders.html) para obtener más información sobre su _Cuadrícula de pedidos_ vista.
