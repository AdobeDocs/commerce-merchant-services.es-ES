---
title: '"[!DNL Quick Checkout] Notas de la versión"'
description: Revise las notas de la versión para obtener información sobre todas las [!DNL Quick Checkout] versiones.
source-git-commit: dc13c1e38c92341cfd3221a72e6568220b44690a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 2%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Quick Checkout] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Se ha corregido un problema](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Consulte [Próximas versiones](https://devdocs.magento.com/release/) para obtener más información sobre los programas de versiones y la asistencia técnica.

Consulte [Disponibilidad](https://devdocs.magento.com/release/availability.html) en la documentación para desarrolladores para obtener más información sobre la compatibilidad del producto.

## v1.0.0

![Nuevo](../assets/new.svg)<!-- Issue BOLT-341 --> Versión de disponibilidad general:[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) ahora es compatible con las versiones de Adobe Commerce 2.4.1 a 2.4.4.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-340 --> La variable [!DNL Quick Checkout] para Adobe Commerce puede instalarse para Adobe Commerce [en la infraestructura de nube](install.md#adobe-commerce-on-cloud-infrastructure) o [local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-1 --> La variable [!DNL Quick Checkout] para Adobe Commerce ofrece una tienda optimizada que permite un [experiencia de cierre de compra con un solo clic](overview.md) sin campos de relleno requeridos para los consumidores.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-1 --> La variable [!DNL Quick Checkout] para Adobe Commerce reconoce automáticamente a cada comprador en su red para [compras con un solo clic](checkout-flow.md) directamente en el sitio.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] para Adobe Commerce es compatible con un [cuenta de entorno limitado](testing.md#testing-in-sandbox) que permite a los comerciantes evaluar la extensión en el modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-780 --> Los compradores pueden realizar el check out a través de la [[!DNL Quick Checkout]](checkout-page.md) o a través de una [creación manual de pedidos](create-order-admin.md).

![Nuevo](../assets/new.svg)<!-- Issue BOLT-666 --> Los comerciantes pueden configurar la variable [!DNL Quick Checkout] con acciones de pago básicas, como [`Authorize and Capture` o `Authorize` ](onboarding.md#complete-admin-configuration)o cambiar entre entornos de entorno limitado y de producción.

![Problema conocido](../assets/bug.svg)<!-- Issue BOLT-342 --> Uso [claves de compositor incorrectas](https://support.magento.com/hc/en-us/articles/6909450342541) durante la instalación del [!DNL Quick Checkout] evita que el usuario [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) con el `MAGEID`.
