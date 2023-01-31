---
title: "[!DNL Payment Services] Notas de la versión"
description: Revise las notas de la versión para obtener información sobre todas las [!DNL Payment Services] versiones.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: a9970d8ac1400a63ef60b289150556b70e71ef22
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 0%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Payment Services] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Se ha corregido un problema](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Para ver los cambios y correcciones de funciones publicados fuera de la versión normal de las funciones, consulte las secciones Actualizaciones del servicio alojado .

Consulte [Próximas versiones](https://devdocs.magento.com/release/) para obtener más información sobre los programas de versiones y la asistencia técnica.

Consulte [Disponibilidad](https://devdocs.magento.com/release/availability.html) en la documentación para desarrolladores para obtener más información sobre la compatibilidad del producto.

## Actualizaciones de servicio alojadas

Estas notas de la versión describen los cambios y correcciones que se produjeron y se publicaron fuera de las versiones de funciones habituales para el servicio alojado.

+++Actualizaciones de servicio alojadas

_25 de enero de 2023_

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-4102 --> Las nuevas instalaciones de Servicios de Pago no pueden configurar Commerce Services, lo que hace que los Servicios de Pago no sean operativos. Para solucionar este problema, actualice la extensión de los servicios de pago a la versión 1.5.3.

_12 de septiembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3705 --> La variable `increment_id` ya está disponible para su uso en la conciliación de pagos en sistemas ERP externos. Se propaga a la variable [`custom_id` _y_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visible tanto en el enlace web de PayPal como en el detalle de actividad del comerciante para un pago.

_31 de agosto de 2022_

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3629 --> Cuando un nuevo comerciante accede al Inicio de Servicios de Pago por primera vez, la página ahora se carga inmediatamente para mostrar el contenido en lugar de requerir una actualización de la página.

_9 de agosto de 2021_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay ya está disponible como un botón inteligente de PayPal. Esta [opción de pago](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permite a los clientes utilizar la función Touch ID en su dispositivo iOS o macOS para seleccionar Apple Pay. Apple Pay procesa el pago utilizando las credenciales de pago de tarjeta de crédito y débito almacenadas en el dispositivo.

_28 de junio de 2021_

![Nuevo](../assets/new.svg)<!-- Issue PAY-1720 --> Las disputas por pedidos de tienda ya están disponibles en [informe de estado de pago de pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Puede tomar medidas en disputas navegando directamente al Centro de Resolución de PayPal desde [!DNL Payment Services].

![Nuevo](../assets/new.svg)<!-- Issue PAY-2854 --> Mejoras en la experiencia del usuario [!DNL Payment Services] Inicio incluye la capacidad de modificar una configuración en el nivel de herencia actual y mejoras en la visualización del encabezado y la navegación.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2854 --> Ahora puede ver advertencias cuando cambia del modo de entorno limitado al modo de producción y cuando intenta abandonar una vista con actualizaciones que no se han guardado.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2761 --> Ahora puede personalizar los datos que aparecen en la [Informe del estado del pago del pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) y [Informe de rutas](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) mostrando u ocultando columnas con el control de configuración de columna.

+++

## v1.5.4

_29 de enero de 2023_

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-4110 --> Se ha corregido un problema que impedía que los compradores realizaran un pedido utilizando botones inteligentes en la página del producto, el minicarro y el carro de compras. Los compradores ahora pueden completar los pedidos correctamente.

## v1.5.3

_25 de enero de 2023_

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-4102 --> Se ha publicado una corrección en un problema conocido incompatible con versiones anteriores. Esta versión bloquea la versión de la extensión de ID de servicio a la última versión estable, lo que permite que las nuevas instalaciones de Servicios de pago configuren Commerce Services.

## v1.5.2

_22 de diciembre de 2022_

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3992 --> Se ha mejorado la facturación en Servicios de Pago cuando se rechaza un método de pago.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3999 --> Los servicios de pago ahora muestran correctamente los botones inteligentes de PayPal para los comerciantes mediante [Cierre de compra de incendios](https://marketplace.magento.com/swissup-firecheckout.html){target=_blank} plantilla personalizada para la página de cierre de compra. Anteriormente, el minigráfico mostraba los botones de forma intermitente.

## v1.5.1

_23 de noviembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3923 --> Los servicios de pago ahora incluyen el número de versión en el encabezado del agente de usuario para que las solicitudes puedan rastrear, filtrar o eliminar puntos finales no utilizados.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3968 --> Los servicios de pago ahora muestran correctamente los datos de pedidos cuando se realiza un pedido desde la página del producto mediante botones inteligentes.

## v1.5.0

_18 de noviembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-3880 --> Ahora un comprador puede [vault (guardar) la información de su tarjeta de crédito durante el cierre de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) para usar en una compra posterior para la misma tienda o para otra tienda dentro de la misma cuenta de comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3950 --> Los comerciantes ahora pueden habilitar la variable [Función de comercio de compra instantánea](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) para sus tiendas, de modo que los compradores puedan (usar [información de tarjetas de crédito abovedada](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) para acelerar el cierre de compra.

## v1.4.1

_14 de octubre de 2022_

![Corrección](../assets/fix.svg)<!-- Issue PAY-3766 --> Cuando se rechaza el método de pago de un cliente, el mensaje de error visible es más descriptivo. Recomienda al cliente que vuelva a introducir la información de pago y vuelva a intentarlo, pruebe otro método de pago o que se ponga en contacto con su banco en cuanto a la transacción rechazada.

## v1.4.0

_30 de septiembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-784 --> Los servicios de pago ahora incluyen la capacidad de configurar una cuenta de comerciante para [usar varias cuentas comerciales de PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Esto permite al comerciante operar sus tiendas en varios países utilizando distintas divisas, o usar Adobe Commerce para una parte de su negocio.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3231 --> Los comerciantes pueden [añadir un [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) a sitios web o configuraciones de vistas de almacén individuales que se muestran en los estados bancarios de transacciones de clientes para delinear marcas, tiendas o líneas de producto.

![Nuevo](../assets/new.svg)<!-- Issue PAY-3707 --> [Habilitar o deshabilitar campos de tarjeta de crédito y botones inteligentes de PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) para el cierre de compra en la configuración de Servicios de pago.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3546 --> Cuando un cliente hace clic en **[!UICONTROL Edit cart]**, la página redirige a la página del carro de compras y muestra los elementos actualizados en lugar de mostrar un carro vacío.

## v1.3.1

_6 de septiembre de 2022_

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3663 --> Ahora, cuando la tienda de un comerciante está capturando un pedido autorizado con una moneda no global, el proceso de captura se completa y no se muestra ningún error.

## v1.3.0

_9 de agosto de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-XX --> Versión de disponibilidad general:[!DNL Payment Services] ahora es [compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay ahora es compatible con el explorador Safari v15.5 en dispositivos móviles y de escritorio.

## v1.2.0

_29 de junio de 2022_

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay es incompatible con el explorador Safari v15.5 en dispositivos móviles y de escritorio. Al utilizar Safari versión 15.5, no se puede completar el cierre de compra con Apple Pay.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3264 --> Anteriormente, cuando un usuario que iniciaba sesión seleccionaba una dirección de facturación/envío diferente que la dirección predeterminada de su cuenta, se producía un error de cierre de compra. Hemos corregido este problema y ahora se envía la dirección de facturación/envío seleccionada (en lugar de la dirección guardada predeterminada) y el cierre de compra se completa correctamente.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3314 --> Si deshabilita los botones inteligentes de PayPal para el cierre de compra, no se mostrarán errores.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3330 --> Los pagos ya no fallan durante el cierre de compra cuando un usuario invitado introduce un número de teléfono que incluye guiones.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Cuando las credenciales de Commerce Services no son válidas, la variable [!DNL Payment Services] La página principal ahora aparecerá en el Administrador. Aparece un error de credenciales para avisarle de que sus credenciales no son válidas.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] actualmente es incompatible con `commerce-data-export` v101.20 y posteriores, lo que hace que sea incompatible con el [[!DNL Channel manager] Extensión](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 de marzo de 2022_

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general:[!DNL Payment Services] ahora es [compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2682 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] ya está disponible para los comerciantes canadienses. Los comerciantes pueden ver la configuración de pagos en [Francés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) o [Inglés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] support [Dólares canadienses (CAD)](overview.md#accepted-credit-cards-and-currencies) para tarjetas de crédito y transacciones PayPal.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2680 --> Los comerciantes pueden [tablero [!DNL Payment Services]](onboard.md) extensión en inglés o francés.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2678 --> Los comerciantes ahora pueden ver los informes financieros, tanto la variable [Estado del pago del pedido](order-payment-status.md) y [Informes de rutas](payouts.md), en dólares canadienses (CAD).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ahora es compatible con [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3017 --> Se ha mejorado la alerta de modo Simulador para pruebas para mostrar alertas adecuadas con varias tiendas.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2742 --> Ahora puede habilitar y deshabilitar los métodos de pago disponibles, como Venmo, en el nivel de vista de tienda. Anteriormente, solo se podían configurar los métodos de pago por sitio web.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2277 --> Ahora puede [activar o desactivar botones inteligentes individuales de PayPal](settings.md#payment-buttons).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2561 --> Los productos que se han eliminado anteriormente no aparecen en el carro de la compra _Revisar orden_ página.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2842 --> Probar transacciones con tarjetas de crédito [puede fallar con PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) al procesar pagos en un entorno de espacio aislado.

## v1.0.0

_29 de noviembre de 2021_

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general:[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.3-p1.

![Nuevo](../assets/new.svg)<!-- Issue PAY-124 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] puede instalarse para [[!DNL Adobe Commerce] en la infraestructura de nube](install.md#adobe-commerce-on-cloud-infrastructure) o [Local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] admite un [cuenta de entorno limitado](sandbox.md) que permite a los comerciantes evaluar la extensión en el modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue PAY-666 --> Los comerciantes pueden [configurar los servicios de pago](settings.md) extensión con comportamientos de pago básicos, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) cambio entre entornos de simulación de pruebas o de producción.

![Nuevo](../assets/new.svg)<!-- Issue PAY-780 --> Sus compradores pueden consultar [!DNL Payment Services] o mediante [creación manual de pedidos](create-order.md).

![Nuevo](../assets/new.svg)<!-- Issue PAY-1856 --> Informes completos mediante [Estado del pago del pedido](order-payment-status.md) y [Informes de rutas](payouts.md), están disponibles para [!DNL Payment Services] para ofrecerle una visión clara de los pedidos de su tienda y los pagos relacionados.

![Nuevo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] admite precios en niveles flexibles, basados en el volumen total de procesamiento, adaptados a cualquier comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1443 --> Puede [personalizar el aspecto](payments-options.md) de botones inteligentes de PayPal y campos de tarjeta de crédito para la variable [!DNL Payment Services] extensión.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso [claves de compositor incorrectas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) durante la instalación de la extensión impide que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con el `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] informes [no se puede sincronizar inmediatamente](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> Su [Cuenta de espacio aislado de PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) para [!DNL Payment Services] no se puede comprobar si crea esa cuenta durante la incorporación.
