---
title: '"[!DNL Payment Services] Notas de la versión"'
description: Revise las notas de la versión para obtener información sobre todas las [!DNL Payment Services] versiones.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Payment Services] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Se ha corregido un problema](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

## v1.0.0

![Nuevo](../assets/new.svg)<!-- Issue PAY-2127 --> Versión de disponibilidad general. [Servicios de pago](https://marketplace.magento.com/magento-payment-services.html) ahora es compatible con las versiones 2.4.0 a 2.4.3-p1 de Adobe Commerce y Magento Open Source.

![Nuevo](../assets/new.svg)<!-- Issue PAY-124 --> La variable [!DNL Payment Services] extensión para Adobe Commerce y Magento Open Source se pueden instalar para [Adobe Commerce en infraestructura en la nube](install.md#magento-commerce-cloud) o [Local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] admite un [cuenta de entorno limitado](onboard.md#enable-sandbox-testing) que permite a los comerciantes evaluar la extensión en el modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue PAY-666 --> Los comerciantes pueden [configurar servicios de pago](configure-admin.md) con comportamientos de pago básicos (como la captura automática y el cambio entre entornos de entorno limitado o de producción).

![Nuevo](../assets/new.svg)<!-- Issue PAY-780 --> Los compradores pueden consultar con [!DNL Payment Services] o puede tomar el pedido por teléfono y [crear un pedido completo](create-order.md) en Admin para ellos.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] ofrece a los comerciantes informes completos para que pueda obtener una visión clara de sus pedidos y pagos de tienda.

![Nuevo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] admite precios en niveles (basados en TPV) adaptados a cualquier comerciante.

![Nuevo](../assets/new.svg)<!-- Issue PAY-1443 --> Es posible personalizar el aspecto de los botones PayPal y los campos CC para el [Servicios de pago](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) extensión.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2473 --> Uso [claves de compositor incorrectas](https://support.magento.com/hc/en-us/articles/4406603542541) durante la instalación de la extensión impide que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con correcto `MAGEID`.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [informes](https://support.magento.com/hc/en-us/articles/4406114741517) para el estado de pago de pago de pago y pedido no se sincroniza inmediatamente.

![Problema conocido](../assets/bug.svg)<!-- Issue PAY-2475 --> [Cuenta de espacio aislado de PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] no se puede comprobar.
