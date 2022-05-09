---
title: '"[!DNL Payment Services] Notas de la versión"'
description: Revise las notas de la versión para obtener información sobre todas las [!DNL Payment Services] versiones.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 1%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Payment Services] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Se ha corregido un problema](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

## Versión 1.1.0

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.4.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2682 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] está disponible para comerciantes canadienses. Los comerciantes pueden ver la configuración de pagos en [Francés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) o [Inglés](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![Nuevo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] support [Dólares canadienses (CAD)](overview.md#accepted-credit-cards-and-currencies) con tarjeta de crédito y Paypal. Los compradores pueden tener una experiencia de compra en su idioma preferido, dependiendo de la configuración regional de la tienda en la que estén comprando.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2680 --> Los comerciantes pueden [tablero [!DNL Payment Services]](onboard.md) extensión en su idioma preferido.

![Nuevo](../assets/new.svg)<!-- Issue PAY-2678 --> Los comerciantes ahora pueden ver [informes financieros](order-payment-status.md) en dólares canadienses (CAD).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] ahora es compatible con [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3035 --> Se ha mejorado el cierre de compra del administrador para la variable [!DNL Payment Services] extensión.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-3017 --> Se ha mejorado la alerta de modo Simulador para pruebas para mostrar alertas adecuadas con varias tiendas.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] permite habilitar/deshabilitar métodos de pago disponibles como Venmo en el nivel de vista previa.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2277 --> Se ha mejorado la capacidad del comerciante en el administrador para deshabilitar/habilitar selectivamente los botones inteligentes de PayPal.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2561 --> Los productos que se han eliminado anteriormente no aparecen en el carro de la compra _Revisar orden_ página.

![Se ha corregido un problema](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] mejora las etiquetas de método de pago en el Administrador.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso [claves de compositor incorrectas](https://support.magento.com/hc/en-us/articles/4406603542541) durante la instalación de la extensión impide que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con correcto `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [informes](https://support.magento.com/hc/en-us/articles/4406114741517) para el estado de pago de pago de pago y pedido no se sincroniza inmediatamente.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> [Cuenta de espacio aislado de PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] no se puede comprobar si la cuenta se crea durante la incorporación.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2842 --> [Error en la tarjeta de crédito de prueba](https://support.magento.com/hc/en-us/articles/5201041963917) con PayPal al procesar pagos en un entorno de espacio aislado.

## v1.0.0

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general. [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con [!DNL Adobe Commerce] y [!DNL Magento Open Source] versiones 2.4.0 a 2.4.3-p1.

![Nuevo](../assets/new.svg)<!-- Issue PAY-124 --> La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] puede instalarse para [[!DNL Adobe Commerce] en la infraestructura de nube](install.md#magento-commerce-cloud) o [Local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] admite un [cuenta de entorno limitado](onboard.md#enable-sandbox-testing) que permite a los comerciantes evaluar la extensión en el modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue PAY-666 --> Los comerciantes pueden [configurar servicios de pago](settings.md) con comportamientos de pago básicos (como la captura automática y el cambio entre entornos de entorno limitado o de producción).

![Nuevo](../assets/new.svg)<!-- Issue PAY-780 --> Los compradores pueden consultar con [!DNL Payment Services] o puede tomar el pedido por teléfono y [crear un pedido completo](create-order.md) en Admin para ellos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] ofrece a los comerciantes informes completos para que pueda obtener una visión clara de sus pedidos y pagos de tienda.

![Nuevo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] admite precios en niveles (basados en TPV) adaptados a cualquier comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1443 --> Es posible personalizar el aspecto de los botones PayPal y los campos CC para el [Servicios de pago](payments-options.md) extensión.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso [claves de compositor incorrectas](https://support.magento.com/hc/en-us/articles/4406603542541) durante la instalación de la extensión impide que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con correcto `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [informes](https://support.magento.com/hc/en-us/articles/4406114741517) para el estado de pago de pago de pago y pedido no se sincroniza inmediatamente.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> [Cuenta de espacio aislado de PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] no se puede comprobar.
