---
title: '[!DNL Quick Checkout] Notas de la versión'
description: Revise las notas de la versión para obtener información acerca de todos los [!DNL Quick Checkout] versiones.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
feature: Release Notes, Services, Checkout
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Quick Checkout] e incluir:

![Nuevo](../assets/new.svg) Nuevas funciones
![Problema corregido](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Consulte [Próximas versiones](https://devdocs.magento.com/release/) para obtener más información sobre las programaciones de versiones y la compatibilidad.

Consulte [Disponibilidad](https://devdocs.magento.com/release/availability.html) en la documentación para desarrolladores para obtener más información sobre la compatibilidad del producto.

## Actualizaciones del panel de administración

Estas notas de la versión describen los cambios y correcciones de características que se produjeron y se lanzaron fuera de las versiones de funciones habituales para el Panel de administración.

+++Actualizaciones del panel de administración

23 de mayo de 2023_

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-489 --> Ahora, la **Nuevas cuentas** componente en la [!DNL Quick Checkout] La página de informes incluye Spectrum [Iconos de flujo de trabajo](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_25 de abril de 2023_

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-452 --> El [!DNL Quick Checkout] **Realizar un recorrido** ahora muestra un cursor de mano en el que se puede hacer clic al pasar el ratón por encima.

_19 de abril de 2023_

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-596 --> El [!DNL Quick Checkout] La página Informes ahora muestra correctamente el gráfico Nuevas cuentas al analizar fechas en formato ISO 8601.

_14 de diciembre de 2022_

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-524 --> El [!DNL Quick Checkout] El panel de administración ahora muestra los pedidos totales correctos y la información actualizada del sistema de informes.

_30 de noviembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue BOLT-502 --> Ahora, la [informe](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tiene un nuevo ajuste preestablecido &quot;Último año&quot;.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-471 --> Mejoras en la experiencia del usuario en [!DNL Quick Checkout] El panel de administración muestra más información en [Tooltips](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-514 --> Mejoras en la experiencia del usuario en [!DNL Quick Checkout] El panel de administración muestra los números de pedidos totales correctos, la coherencia en los colores y las leyendas correctas para todos los gráficos.

_2 de noviembre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue BOLT-293 --> Ahora, la [informe](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) en la pestaña [!DNL Quick Checkout] El panel Administrador muestra gráficos e información de informes sobre las estadísticas de la experiencia de cierre de compra de la tienda.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-422 --> El [_Información general_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) Esta sección de la sección del tema Informes muestra información detallada sobre el rendimiento de cierre de compra de su tienda, incluido el tiempo promedio de cierre de compra, las nuevas cuentas creadas durante el cierre de compra y el abandono de este.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-423 --> El [_Tendencias_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) de la pestaña Informes muestra las tendencias de la experiencia de cierre de compra filtradas por tipo de cuenta y las nuevas cuentas creadas durante el cierre de compra.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-439 --> El **Informes** visualizaciones de pestañas [ajustes preestablecidos de filtro predeterminados](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) que se puede utilizar para mostrar intervalos de datos específicos.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-433 --> Ahora puede ver una _No hay datos disponibles_ advertencia para un gráfico cuando una solicitud no devuelve datos.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-473 --> Mejoras en la experiencia del usuario de [!DNL Quick Checkout] El panel de administración incluye la capacidad de habilitar un [seguimiento de pago y envío](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) que permite a Adobe Commerce compartir información de informes con Bolt.

_5 de octubre de 2022_

![Nuevo](../assets/new.svg)<!-- Issue BOLT-379 --> Ahora, cuando un nuevo comerciante accede a la [!DNL Quick Checkout] Panel de administración por primera vez en [tour de funciones con tecnología Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) aparece.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-377 --> El **Informes** en la pestaña [!DNL Quick Checkout] El panel Administración muestra gráficos y análisis de informes.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-377 --> El **Informes** en la pestaña [!DNL Quick Checkout] El panel Administración muestra los ajustes preestablecidos de intervalo de fechas y filtro para gráficos e informes de Analytics.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-369 --> Ahora, la [[!DNL Quick Checkout] Panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) muestra la versión de la aplicación en el pie.

+++

## v1.8.0

_24 de febrero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-520 --> Versión de disponibilidad general—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) ahora está preinstalado en las versiones 2.4.6 y posteriores de Adobe Commerce Cloud.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-592 --> Mejoras en la experiencia del usuario al realizar un pedido en [Panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) usando [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) como forma de pago. Esta funcionalidad permite a los clientes realizar un pedido con el Braintree como forma de pago durante el cierre de compra cuando [!DNL Quick Checkout] está activada.

## v1.7.0

_22 de febrero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Problema corregido](../assets/fix.svg)<!-- Issue AC-8002 --> Mejoras en la experiencia del usuario al realizar un pedido con una [Envío Múltiple](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) método. Esta funcionalidad habilita la visualización de los métodos de pago durante el cierre de compra cuando [!DNL Quick Checkout] está activada.

## v1.6.0

_9 de febrero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-567 --> Mejoras en la experiencia del usuario al [realización de un pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) uso del [Envío en tienda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) con el método [!DNL Quick Checkout] desactivado.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-569 --> Mejoras en la funcionalidad de cierre de sesión que permite a los compradores [cierre de sesión de la red de pernos](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_18 de enero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-522 --> Se puede habilitar/deshabilitar una nueva configuración para detectar si [compradores](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) se puede iniciar sesión automáticamente en Bolt.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-523 --> Se puede habilitar/deshabilitar una nueva configuración que permita a los comerciantes especificar si los compradores pueden iniciar sesión automáticamente en ambas redes o solo en la red de Bolt.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-542 --> Mejoras en la experiencia del usuario al [guardar tarjeta o dirección en una cuenta de Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) cuando un comprador proporciona correo electrónico.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-550 --> Mejoras en la experiencia del usuario en [inicio de sesión automático](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) cuando un usuario de perno proporciona correo electrónico.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-544 --> Mejoras de compatibilidad para [URL de devolución](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) con [de varios sitios](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) en Bolt.

## v1.4.0

_30 de noviembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-513 --> Ahora, cuando un cliente de Adobe Commerce ha iniciado sesión en la tienda durante el proceso de cierre de compra y tiene una cuenta de Bolt, se muestra una opción para iniciar sesión en la cuenta de Bolt del comprador.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-512 --> Una nueva configuración detecta automáticamente si los compradores que iniciaron sesión también pueden hacerlo en Bolt.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-480 --> Una nueva configuración en [!DNL Quick Checkout] El panel de administración le permite cambiar el flujo de navegación predeterminado a **Envío** una vez que un cliente de Bolt inicia sesión. De forma predeterminada, se configura en **Pagos** página.

## v1.3.0

_2 de noviembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-293 --> Ahora, [!DNL Quick Checkout] incluye la capacidad de habilitar un [seguimiento de pago y envío](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) que permite a Adobe Commerce compartir información de informes con Bolt.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-461 --> Ahora puede ver un mensaje de advertencia en su [!DNL Quick Checkout] Panel de administración si [seguimiento de pago y envío](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) La configuración de está deshabilitada.

## v1.2.0

_8 de septiembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-341 --> Versión de disponibilidad general—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) ahora es compatible con las versiones 2.4.5 de Adobe Commerce.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] para Adobe Commerce y Magento Open Source proporciona un [Vista del panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) con toda la información necesaria para configurar y utilizar la extensión de.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-364 --> Un usuario administrador [Puede configurar roles de usuario y permisos](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) para permitir que otros usuarios vean [!DNL Quick Checkout] Panel de administración.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] El panel de administración ahora contiene un encabezado de página que incluye secciones específicas como **Información general**, **Informes**, y **Configuración**.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-379 --> Cuando un nuevo comerciante accede a la [!DNL Quick Checkout] El panel de administración aparece por primera vez con un widget de bienvenida que proporciona un recorrido por las características.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Vista del panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora un **Configuración** paso que aparece cuando no se proporcionan la API y las claves publicables en la [Configuración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) vista.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Vista del panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora un **Recursos** que cambia según la fase de incorporación.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Vista del panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incluye un **Ayuda y asistencia** sección.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-369 --> El [[!DNL Quick Checkout] Panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) ahora muestra la versión de la extensión en el pie de página.

## v1.1.0

_12 de agosto de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-375 --> Mejoras en la experiencia del usuario en [[!DNL Quick Checkout] Panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) ahora incluya solo los parámetros visibles y validados cuando la extensión esté habilitada.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-349 --> Mejoras de compatibilidad para las direcciones de envío existentes con la cartera Bolt.

## v1.0.0

_9 de agosto de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg)<!-- Issue BOLT-341 --> Versión de disponibilidad general—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) ahora es compatible con las versiones de Adobe Commerce 2.4.1 a 2.4.4.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-340 --> El [!DNL Quick Checkout] para Adobe Commerce se puede instalar para Adobe Commerce [en la infraestructura en la nube](install.md#adobe-commerce-on-cloud-infrastructure) o [local](install.md#on-premises) instancias. Estos métodos requieren el uso de una interfaz de línea de comandos.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-1 --> El [!DNL Quick Checkout] para Adobe Commerce ofrece una tienda optimizada que permite un [experiencia de cierre de compra con un solo clic](overview.md) sin rellenar los campos requeridos para los consumidores.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-1 --> El [!DNL Quick Checkout] para Adobe Commerce reconoce automáticamente cada comprador en su red para [compras con un solo clic](checkout-flow.md) directamente en el sitio.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-1 --> El [!DNL Quick Checkout] para Adobe Commerce permite que un comprador esté [ha iniciado sesión en las redes Adobe Commerce y Bolt](checkout-flow.md/#quick-checkout-use-cases) para proporcionar un mejor `one-click checkout` experiencia.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] para Adobe Commerce admite un [cuenta de zona protegida](testing.md#testing-in-sandbox) que permite a los comerciantes evaluar la extensión en modo de prueba.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-780 --> Los compradores pueden realizar el registro de salida a través del [[!DNL Quick Checkout]](checkout-page.md) o a través de una [creación manual de pedidos](create-order-admin.md).

![Nuevo](../assets/new.svg)<!-- Issue BOLT-666 --> Los comerciantes pueden configurar las [!DNL Quick Checkout] con acciones de pago básicas, como [`Authorize and Capture` o `Authorize`](onboarding.md#complete-admin-configuration)o cambiar entre entornos de zona protegida y entornos de producción.

![Nuevo](../assets/new.svg)<!-- Issue BOLT-288 --> Personalizado [duración de sesión de usuario](user-session-lifetime.md) para [!DNL Quick Checkout] para Adobe Commerce.

![Problema corregido](../assets/fix.svg)<!-- Issue BOLT-375 --> Mejoras en la experiencia del usuario en [[!DNL Quick Checkout] Panel de administración](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) permite guardar la configuración cuando se proporcionan todos los parámetros necesarios.

![Problema conocido](../assets/bug.svg)<!-- Issue BOLT-342 --> Común [solución de problemas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) problemas durante la instalación de [!DNL Quick Checkout].
