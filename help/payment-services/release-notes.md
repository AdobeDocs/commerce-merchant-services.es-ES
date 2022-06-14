---
title: '"[!DNL Payment Services] Notas de la versión"'
description: Revise las notas de la versión para obtener información sobre todas las [!DNL Payment Services] versiones.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Payment Services] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Se ha corregido un problema](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Consulte [Próximas versiones](https://devdocs.magento.com/release/) para obtener más información sobre los programas de versiones y la asistencia técnica.

Consulte [Disponibilidad](https://devdocs.magento.com/release/availability.html) en la documentación para desarrolladores para obtener más información sobre la compatibilidad del producto.

## Versión 1.1.0

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general:[!DNL Payment Services] ahora es [compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2682 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] ya está disponible para los comerciantes canadienses. Los comerciantes pueden ver la configuración de pagos en [Francés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) o [Inglés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] support [Dólares canadienses (CAD)](overview.md#accepted-credit-cards-and-currencies) para tarjetas de crédito y transacciones PayPal.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2680 --> Los comerciantes pueden [tablero [!DNL Payment Services]](onboard.md) extensión en inglés o francés.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2678 --> Los comerciantes ahora pueden ver los informes financieros, tanto la variable [Estado del pago del pedido](order-payment-status.md) y [Informes de rutas](payouts.md), en dólares canadienses (CAD).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ahora es compatible con [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3017 --> Se ha mejorado la alerta de modo Simulador para pruebas para mostrar alertas adecuadas con varias tiendas.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2742 --> Ahora puede habilitar y deshabilitar los métodos de pago disponibles, como Venmo, en el nivel de vista de tienda. Anteriormente, solo se podían configurar los métodos de pago por sitio web.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2277 --> Ahora puede [activar o desactivar botones inteligentes individuales de PayPal](settings.md#paypal-smart-buttons).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2561 --> Los productos que se han eliminado anteriormente no aparecen en el carro de la compra _Revisar orden_ página.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2842 --> Probar transacciones con tarjetas de crédito [puede fallar con PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) al procesar pagos en un entorno de espacio aislado.

## v1.0.0

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general:[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.3-p1.

![Nuevo](../assets/new.svg)<!-- Issue PAY-124 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] puede instalarse para [[!DNL Adobe Commerce] en la infraestructura de nube](install.md#adobe-commerce-on-cloud-infrastructure) o [Local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] admite un [cuenta de entorno limitado](sandbox.md) que permite a los comerciantes evaluar la extensión en el modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue PAY-666 --> Los comerciantes pueden [configurar los servicios de pago](settings.md) extensión con comportamientos de pago básicos, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) cambio entre entornos de simulación de pruebas o de producción.

![Nuevo](../assets/new.svg)<!-- Issue PAY-780 --> Sus compradores pueden consultar [!DNL Payment Services] o mediante [creación manual de pedidos](create-order.md).

![Nuevo](../assets/new.svg)<!-- Issue PAY-1856 --> Informes completos mediante [Estado del pago del pedido](order-payment-status.md) y [Informes de rutas](payouts.md), están disponibles para [!DNL Payment Services] para ofrecerle una visión clara de los pedidos de su tienda y los pagos relacionados.

![Nuevo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] admite precios en niveles flexibles, basados en el volumen total de procesamiento, adaptados a cualquier comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1443 --> Puede [personalizar el aspecto](payments-options.md) de botones inteligentes de PayPal y campos de tarjeta de crédito para la extensión Servicios de pago.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso [claves de compositor incorrectas](https://support.magento.com/hc/en-us/articles/4406603542541) durante la instalación de la extensión impide que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con el `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] informes [no se puede sincronizar inmediatamente](https://support.magento.com/hc/en-us/articles/4406114741517).

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> Su [Cuenta de espacio aislado de PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] no se puede comprobar si crea esa cuenta durante la incorporación.
