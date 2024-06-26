---
title: "[!DNL Payment Services] Notas de la versión"
description: Revise las notas de la versión para obtener información acerca de todos los [!DNL Payment Services] versiones.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 9b4ce379728b126390177d64c10d57b2c587619c
workflow-type: tm+mt
source-wordcount: '2502'
ht-degree: 0%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Payment Services] e incluir:

![Nuevo](../assets/new.svg) Nuevas funciones
![Problema corregido](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Para ver los cambios y correcciones de funciones publicados fuera de la versión de la función normal, consulte la _Actualizaciones de servicios alojados_ secciones.

Obtenga más información acerca de las próximas versiones, la compatibilidad del producto y las versiones de Adobe Commerce que admiten el [!DNL Payment Services] extensión, consulte Adobe Commerce [Programación de versiones](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) y [Disponibilidad del producto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) temas.

## Actualizaciones de servicios alojados

Estas notas de la versión describen los cambios y correcciones de características que se produjeron y que se lanzaron fuera de las versiones de funciones normales para el servicio alojado.

+++Actualizaciones de servicios alojados

_5 de marzo de 2024_

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-5252 --> Ahora, los comerciantes pueden copiar datos de las cuadrículas del panel seleccionando el contenido de una sola celda.

_10 de octubre de 2023_

![Nuevo problema](../assets/fix.svg)<!-- Issue PAY-4888 --> Ahora, los comerciantes pueden filtrar las transacciones con tarjetas de crédito y débito por los últimos cuatro dígitos del número de tarjeta en el [Informe Transacciones](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_12 de julio de 2023_

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4587 --> Un problema introducido en la [!DNL Payment Services] Ya se ha resuelto la versión 2.1.0 que impedía que las versiones de extensión anteriores anularan la autorización. Comerciantes que utilicen cualquier versión de [!DNL Payment Services] puede anular las autorizaciones.

_9 de junio de 2023_

![Nuevo](../assets/new.svg)<!-- Issue PAY-4288 --> Ahora, los comerciantes pueden [configurar _solamente_ Botones de pago de PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—y _no_ utiliza la opción de pago con tarjeta de crédito PayPal. Esto permite a los comerciantes proporcionar varias opciones de pago, incluidos los botones de pago Venmo y PayPal, y utilizar un proveedor de tarjetas de crédito existente en lugar de la opción de pago con tarjeta de crédito PayPal.

![Nuevo](../assets/new.svg)<!-- Issue PAY-4050 --> Se ha añadido un [vista de visualización de datos](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), que aparece en la página de inicio de Payment Service, para el informe Estado de pago del pedido.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4486--> Anteriormente, el botón PayPal Paylater no aparecía en el proceso de pago y envío de los comerciantes del Reino Unido. Ese problema está resuelto.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4485--> Las vistas de visualización de datos de informes ahora aparecen en [!DNL Payment Services] Inicio cuando[!DNL Payment Services] está deshabilitada.

_25 de enero de 2023_

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-4102 --> Nuevas instalaciones de [!DNL Payment Services] no pueden configurar los servicios de Commerce, procesamiento [!DNL Payment Services] inoperable. Para solucionar este problema, actualice su [!DNL Payment Services] extensión a la versión 1.5.3.

_12 de septiembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3705 --> El `increment_id` ya está disponible para su uso en la reconciliación de pagos en sistemas ERP externos. Se propaga al [`custom_id` _y_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visible tanto en el webhook de PayPal como en el detalle de actividad del comerciante para un pago.

_31 de agosto de 2022_

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3629 --> Cuando un nuevo comerciante accede a la [!DNL Payment Services] Inicio por primera vez, la página ahora se carga inmediatamente para mostrar el contenido en lugar de requerir una actualización de la página.

_9 de agosto de 2021_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay ya está disponible como un botón inteligente de PayPal. Esta [opción de pago](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permite a los clientes utilizar la función Touch ID en su dispositivo iOS o macOS para seleccionar Apple Pay. Apple Pay procesa el pago mediante las credenciales de pago de la tarjeta de crédito y débito almacenadas en el dispositivo.

_28 de junio de 2021_

![Nuevo](../assets/new.svg)<!-- Issue PAY-1720 --> Las disputas por pedidos de tienda ya están disponibles en [el informe Estado del pago del pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Para solucionar las disputas, accede directamente al Centro de resolución de PayPal desde [!DNL Payment Services].

![Nuevo](../assets/new.svg)<!-- Issue PAY-2854 --> Mejoras en la experiencia del usuario de [!DNL Payment Services] Inicio incluye la capacidad de modificar una configuración en el nivel de herencia actual y mejoras en la visualización del encabezado y la navegación.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2854 --> Ahora puede ver advertencias cuando cambia del modo de zona protegida al modo de producción y cuando intenta salir de una vista con actualizaciones que no se han guardado.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2761 --> Ahora puede personalizar los datos que se muestran en la variable [Informe de estado de pago del pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) y el [Informe de pagos](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) mostrando u ocultando columnas mediante el control Configuración de columna.

+++

## Versión 2.6.0

_4 de junio de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-4877 --> Ahora, [!DNL Payment Services] admite [Funciones de precios de L2/L3](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). Esta función solo está disponible para [!DNL Payment Services] clientes con precios de IC++ habilitados. Si desea utilizar datos de procesamiento L2/L3 para [!DNL Payment Services], póngase en contacto con su [!DNL Payment Services] administrador de cuentas.

![Fix](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] le permite activar Apple Pay directamente desde la extensión sin descargar y alojar el [archivo de asociación de dominio](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## Versión 2.5.0

_23 de abril de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] ahora admite [Directrices de Adobe Commerce para `--db-prefix` parámetro](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) para las versiones de Adobe Commerce 2.4.7 y posteriores.

## Versión 2.4.3

_16 de abril de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- Issue PAY-5106 --> Se ha corregido un problema que indicaba de forma incorrecta los totales del importe del pedido durante el cierre de compra entre PayPal y Adobe Commerce. Ahora, los comerciantes pueden asegurarse de que los totales de la cantidad del pedido son correctos al realizar un pedido.

## Versión 2.4.2

_11 de abril de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue xxx --> Se ha añadido compatibilidad con Adobe Commerce 2.4.7.

## Versión 2.4.1

_4 de abril de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- PAY-5322 --> Se ha corregido un problema de compatibilidad de PCI con las versiones más recientes de Adobe Commerce. Ahora, [!DNL Payment Services] se adapta a los requisitos de cierre de compra en Adobe Commerce como opción de pago.

![Fix](../assets/fix.svg)<!-- PAY-5323 --> PayAfter y Venmo se muestran correctamente en Adobe Commerce. Se ha corregido un error que impedía que el administrador mostrara las opciones de alternancia PayAfter y Venmo.

## Versión 2.4.0

_20 de marzo de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-4868 --> Los comerciantes pueden [Configuración de Google Pay durante toda la experiencia de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html), similar a otros botones de pago de[!DNL Payment Services] a través de Admin.

![Nuevo](../assets/new.svg)<!-- PAY-4381 --> [Payment Services admite Google Pay a través de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) que permite a los comerciantes tener una experiencia Commerce sin encabezado con el método de pago Google Pay.

![Nuevo](../assets/new.svg)<!-- PAY-4878 --> Ahora, la [!DNL Payment Services] la función de cierre de compra básica está integrada para Adobe Commerce y los comerciantes Magento Open Source.[!DNL Payment Services] Ahora puede dar soporte a comerciantes con negocios en cualquiera de las 200 regiones geográficas de todo el mundo.[!DNL Payment Services] El proceso de pago y envío básico proporciona opciones de débito/crédito, PayPal, Venmo (cuando esté disponible) y PayAfter (cuando esté disponible) en una incorporación de autoservicio.

![Fix](../assets/fix.svg)<!-- PAY-5291 --> La recepción de la confirmación de pago para algunas transacciones puede retrasarse. En ese caso, ahora los comerciantes pueden obtener un estado de pago actualizado para un pedido. [Payment services detecta el estado pendiente de una transacción de pago](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) en un pedido, detectando las transacciones pendientes, monitorizándolas de forma proactiva y actualizándolas cuando se haya capturado el estado pendiente.

## Versión 2.3.4

_1 de marzo de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-5244 --> Se ha corregido la compatibilidad de cierre de compra asincrónico.

![Fix](../assets/fix.svg)<!-- PAY-5253 --> Se ha corregido un error por el que un token de Vault no pertenecía a [!DNL Payment Services] no se ha podido eliminar.

## Versión 2.3.3

_14 de febrero de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-5048 --> Se ha agregado compatibilidad con PHP 8.3

![Fix](../assets/fix.svg)<!-- PAY-5048 --> Se ha corregido un error con `is_deleted` Indicador. Ahora, los pedidos no fallan debido a la `Rejected` estado enviado desde la extensión.

## Versión 2.3.2

_26 de enero de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- PAY-5183 --> Se corrigieron problemas de rendimiento de REST/GraphQL. Ahora, el botón de tarjeta de crédito se procesa cuando se obtiene a través de la API.

## Versión 2.3.1

_7 de diciembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-5047 --> El tipo de método de pago o marca de tarjeta de crédito/débito ya está disponible en las siguientes ubicaciones:
- la página pedido del cliente en la tienda
- el correo electrónico de confirmación del pedido enviado al comprador
- desde el [vista de detalles del pedido](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) en el Administrador de Commerce.

## Versión 2.3.0

_1 de diciembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-4381 --> [Payment Services ahora admite la integración con GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Con la compatibilidad de GraphQL para los botones de pago de PayPal, los campos alojados y Apple Pay,[!DNL Payment Services] ahora es compatible con una configuración de Commerce sin encabezado.

## Versión 2.2.1

_27 de septiembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4870 --> Se ha corregido un problema que llenaba incorrectamente el nuevo atributo de encabezado en Storefront al enviar la versión de extensión con la última versión. Anteriormente, con la variable `1.3.0` versión del conector de Commerce Services, no se pudo ampliar el `User-Agent header` desde el [!DNL Payment Services] extensión.

## Versión 2.2.0

_30 de agosto de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- PAY-4638 --> Se ha añadido un [integración con Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html), que proporciona servicios automatizados de protección contra el fraude.

![Nuevo](../assets/new.svg)<!-- PAY-3981 --> [Apple Pay promocionado a una opción de pago independiente](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button), fuera de los botones de pago de PayPal, para aumentar la visibilidad del comprador de la opción de pago y para permitir a los comerciantes controlar la colocación y el estilo de Apple Pay.

![Nuevo](../assets/new.svg)<!-- PAY-4002 --> Se ha mejorado la experiencia del usuario con el cierre de compra de los campos de tarjeta de crédito, incluidas mejoras de estilo como la adición de iconos de pago, para reducir la carga cognitiva del comprador y aumentar las conversiones.

![Nuevo](../assets/new.svg)<!-- PAY-4002 --> Funcionalidad agregada para permitir a los comerciantes [ordenar el orden de sus opciones de pago](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) para priorizar ciertas opciones de pago. Esta funcionalidad promueve una mayor tasa de conversación de cierre de compra.

![Nuevo](../assets/new.svg)<!-- PAY-4035 --> Ahora, los comerciantes pueden supervisar de forma eficaz el estado de sus tiendas e identificar cualquier problema de transacción con el nuevo [Informe Transacciones](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) disponible en el[!DNL Payment Services] Página de inicio del administrador. El informe también presenta datos sobre las tasas de autorización de transacciones y las tendencias negativas de las transacciones.

## Versión 2.1.0

_9 de junio de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue xxx --> Se ha agregado compatibilidad con Adobe Commerce 2.4.7-beta1.

![Nuevo](../assets/new.svg)<!-- Issue xxx --> Añadido [disponibilidad en los siguientes países y monedas asociadas](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australia, Francia, Reino Unido.

![Nuevo](../assets/new.svg)<!-- Issue PAY-4296 --> Añadido [recursos ampliados para funciones de administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) para garantizar que los usuarios administradores puedan crear y administrar pedidos para clientes y puedan ver[!DNL Payment Services] en el menú Ventas.

![Nuevo](../assets/new.svg)<!-- Issue PAY-4236 --> Añadido [anulación automática para pedidos que incurren en errores durante el cierre de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Nuevo](../assets/new.svg)<!-- Issue PAY-4183 --> Funcionalidad creada para [mostrar el botón de opción de pago con tarjeta de crédito/débito](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) en la página de cierre de compra.

## Versión 2.0.0

_10 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-4152 --> Se ha agregado compatibilidad con PHP 8.2 y Adobe Commerce 2.4.6. No compatible con PHP 7.x.

## Versión 1.6.1

_10 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- Issue PAY-4226 --> Se ha corregido un problema que impedía nuevas [!DNL Payment Services] que los comerciantes utilicen el cierre de compra en Admin.[!DNL Payment Services] utilizaba anteriormente el ID de cliente de Commerce, que no existe para nuevos clientes.

![Fix](../assets/fix.svg)<!-- Issue PAY-4205 --> Se ha corregido un problema que provocaba que el estado de la dirección de envío especificada se reemplazara por el estado en la configuración de impuestos predeterminada durante la desprotección con [Opción PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Ahora, los clientes pueden enviar sus pedidos a un estado distinto del configurado como predeterminado en la configuración de impuestos del comerciante.

![Fix](../assets/fix.svg)<!-- Issue PAY-4202 --> Se ha corregido un problema que impedía que los clientes usaran el depósito de tarjetas para completar una compra o eliminar un método de pago abovedado para una tienda [uso del `Authorize and Capture` acción de pago](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Anteriormente, aparecía el error &quot;No se encontró el ID de Provider Vault&quot; cuando el cliente intentaba utilizar o modificar sus tarjetas de crédito abovedadas.

## Versión 1.6.0

_17 de febrero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-3540 --> Añadido [Función de cumplimiento PCI 3DS para comerciantes que realizan transacciones en la Unión Europea (UE) y Gran Bretaña](security.md#3ds). Este nivel adicional de seguridad, que requiere que los compradores se autentiquen con el emisor de su tarjeta de crédito, ayuda a evitar el fraude en línea y es necesario como parte de las regulaciones de cumplimiento de la Unión Europea (UE).

![Nuevo](../assets/new.svg)<!-- Issue PAY-3609 --> Se ha añadido la capacidad de [habilitar el almacenamiento de tarjetas en Admin](vaulting.md#use-vaulting-in-the-admin). Esto permite a los comerciantes crear un pedido para los clientes en Admin mediante sus métodos de pago abovedados.

## Versión 1.5.4

_29 de enero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4110 --> Se ha corregido un problema que impedía a los compradores realizar un pedido mediante botones de pago en la página del producto, el minicarrito y el carrito. Los compradores ahora pueden completar los pedidos correctamente.

## Versión 1.5.3

_25 de enero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-4102 --> Se ha publicado una corrección de un problema conocido incompatible con versiones anteriores. Esta versión bloquea la versión de la extensión de ID de servicio a la última versión estable, que vuelve a habilitar la nueva [!DNL Payment Services] para configurar los servicios de Commerce.

## Versión 1.5.2

_22 de diciembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3992 --> Facturación mejorada en [!DNL Payment Services] cuando se rechaza una forma de pago.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] ahora muestra correctamente los botones de pago de PayPal para los comerciantes que utilizan [Desactivar cierre de compra](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} plantilla personalizada para la página de cierre de compra. Anteriormente, la minicart mostraba los botones de forma intermitente.

## Versión 1.5.1

_23 de noviembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] ahora incluye el número de versión en el encabezado del agente de usuario para que las solicitudes puedan realizar el seguimiento, filtrar o eliminar los extremos no utilizados.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] ahora muestra correctamente los datos del pedido cuando se realiza un pedido desde la página del producto mediante botones de pago.

## Versión 1.5.0

_18 de noviembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-3880 --> Un comprador ahora puede [guardar la información de su tarjeta de crédito durante el cierre de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) para usarlo en una compra posterior para la misma tienda u otra dentro de la misma cuenta de comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3950 --> Los comerciantes ahora pueden activar la [Función compra instantánea de Commerce](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) para sus tiendas, de modo que los compradores puedan (use [información de tarjeta de crédito](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) para acelerar el cierre de compra.

## Versión 1.4.1

_14 de octubre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg)<!-- Issue PAY-3766 --> Cuando se rechaza la forma de pago de un cliente, el mensaje de error visible es más descriptivo. Aconseja al cliente que vuelva a introducir la información de pago y vuelva a intentarlo, pruebe otra forma de pago o que se ponga en contacto con su banco para informarle de la transacción rechazada.

## Versión 1.4.0

_30 de septiembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] ahora incluye la capacidad de configurar una cuenta de comerciante para [usar varias cuentas comerciales de PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Esto permite al comerciante operar sus tiendas en varios países utilizando diferentes monedas, o usar Adobe Commerce para una parte de su negocio.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3231 --> Los comerciantes pueden [añada un [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) a sitios web o a configuraciones de vistas de tiendas individuales que se muestran en los extractos bancarios de las transacciones de los clientes para delimitar marcas, tiendas o líneas de productos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3707 --> [Activar o desactivar los campos de tarjeta de crédito y los botones de pago de PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) para pago y envío en[!DNL Payment Services] configuración.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3546 --> Cuando un cliente hace clic en **[!UICONTROL Edit cart]**, la página redirige a la página del carro de compras y muestra los elementos actualizados en lugar de mostrar un carro de compras vacío.

## Versión 1.3.1

_6 de septiembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3663 --> Ahora, cuando el almacén de un comerciante está capturando un pedido autorizado con una moneda no global, el proceso de captura se completa y no se muestra ningún error.

## Versión 1.3.0

_9 de agosto de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-XX --> Versión de disponibilidad general—[!DNL Payment Services] es ahora [compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ahora es compatible con el navegador Safari v15.5 en dispositivos móviles y de escritorio.

## Versión 1.2.0

_29 de junio de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay no es compatible con el navegador Safari v15.5 en dispositivos móviles y de escritorio. Al utilizar la versión 15.5 de Safari, no puedes completar el proceso de pago y envío con Apple Pay.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3264 --> Anteriormente, cuando un usuario que iniciaba sesión seleccionaba una dirección de facturación/envío distinta de la predeterminada para su cuenta, se producía un error de cierre de compra. Ahora, se envía la dirección de facturación/envío seleccionada (en lugar de la dirección guardada predeterminada) y el cierre de compra se completa correctamente.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3314 --> Si desactiva los botones de pago de PayPal para el pago y envío, no se muestran errores.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3330 --> Los pagos ya no fallan durante el pago y envío cuando un usuario invitado introduce un número de teléfono que incluye guiones.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Cuando las credenciales de los servicios de Commerce no son válidas,[!DNL Payment Services] ahora le alerta mostrando un error de credenciales de la [!DNL Payment Services] Inicio en la Admin.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] es incompatible con `commerce-data-export` v101.20 y posterior, lo que la hace incompatible con la versión [[!DNL Channel manager] extensión](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## Versión 1.1.0

_31 de marzo de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general—[!DNL Payment Services] es ahora [compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2682 --> El [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] ya está disponible para comerciantes canadienses. Los comerciantes pueden ver la configuración de pagos en [francés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) o [Inglés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] admite [Dólar canadiense (CAD)](overview.md#accepted-credit-cards-and-currencies) para tarjetas de crédito y transacciones con PayPal.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2680 --> Los comerciantes pueden [a bordo [!DNL Payment Services]](onboard.md) extensión en inglés o francés.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2678 --> Los comerciantes ahora pueden ver los informes financieros, tanto los [Estado de pago del pedido](order-payment-status.md) y [Informes de pagos](payouts.md), en dólares canadienses (CAD).

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] ahora es compatible con [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-3017 --> Se ha mejorado la alerta del modo de espacio aislado para mostrar alertas adecuadas con varias tiendas.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-2742 --> Ahora puedes activar y desactivar los métodos de pago disponibles, como Venmo, en el nivel de vista de tienda. Anteriormente, solo se podían configurar métodos de pago por sitio web.

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-2277 --> Ahora puede seleccionar [activar o desactivar botones de pago individuales de PayPal](settings.md#payment-buttons).

![Problema corregido](../assets/fix.svg)<!-- Issue PAY-2561 --> Los productos eliminados anteriormente no aparecen en el carro de compras de la _Revisar pedido_ página.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2842 --> Probar transacciones de tarjeta de crédito [puede fallar con PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) al procesar pagos en un entorno de zona protegida.

## Versión 1.0.0

_29 de noviembre de 2021_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) ahora es compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.3-p1.

![Nuevo](../assets/new.svg)<!-- Issue PAY-124 --> El [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] se puede instalar para [[!DNL Adobe Commerce] en la infraestructura en la nube](install.md#adobe-commerce-on-cloud-infrastructure) o [On-Premise](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] admite un [cuenta de zona protegida](sandbox.md) que permite a los comerciantes evaluar la extensión en modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue PAY-666 --> Los comerciantes pueden [configurar Payment Services](settings.md) extensión con comportamientos de pago básicos, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) cambiar entre entornos de zona protegida o de producción.

![Nuevo](../assets/new.svg)<!-- Issue PAY-780 --> Sus compradores pueden pagar con [!DNL Payment Services] o mediante [creación manual de pedidos](create-order.md).

![Nuevo](../assets/new.svg)<!-- Issue PAY-1856 --> Creación de informes completos mediante [Estado de pago del pedido](order-payment-status.md) y [Informes de pagos](payouts.md), están disponibles para [!DNL Payment Services] para darle una visión clara de los pedidos de su tienda y los pagos relacionados.

![Nuevo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] admite precios por niveles flexibles, basados en el volumen total de procesamiento, adaptados a cualquier comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1443 --> Puede hacerlo fácilmente [personalizar la apariencia](payments-options.md) de botones de pago de PayPal y campos de tarjeta de crédito para [!DNL Payment Services] extensión.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso de [claves de composición incorrectas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) durante la instalación de la extensión evita que el usuario [autentificación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con el correcto `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] informes [puede que no se sincronice inmediatamente](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> Su [Cuenta de zona protegida de PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) para [!DNL Payment Services] no se puede comprobar si crea esa cuenta durante la incorporación.
