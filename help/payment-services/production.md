---
title: Activar [!DNL Payment Services] para producción
description: Complete el proceso de incorporación habilitando [!DNL Payment Services] para producción.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Activar [!DNL Payment Services] para producción

Puede poner el servicio en producción y completar la [proceso de incorporación](onboard.md), para seguir los pasos de este tema, después de hacer lo siguiente:

* [Instalar](install.md) la extensión Servicios de pago
* [Configuración y conexión](connect.md) su instancia
* [Configuración de](sandbox.md) y [prueba](test-validate.md) su zona protegida

## Establecer [!DNL Payment Services] como forma de pago

Después de usted [configuración de los servicios de Commerce](connect.md#configure-commerce-services) y habilite [pruebas de zona protegida](sandbox.md#enable-sandbox-testing) o [pagos pendientes](#enable-live-payments), debe establecer [!DNL Payment Services] como forma de pago.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clic **[!UICONTROL Enable Payment Services]**.

   Esta opción está visible si aún no ha configurado [!DNL Payment Services] como forma de pago para uno o más de sus sitios web.

   Se le dirigirá al área de configuración de la vista Inicio con las opciones relevantes expandidas (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), donde puede activar la variable [!DNL Payment Services] opciones como [forma de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. Entrada _[!UICONTROL General Configuration]_, configurado **[!UICONTROL Enable]**hasta `Yes`.
1. Establecer **[!UICONTROL Payment Action]**, para ambos _[!UICONTROL Credit Card Fields]_y_[!UICONTROL PayPal payment buttons]_, a uno de los siguientes:

   | Configuración | Descripción |
   |---|---|
   | `Authorize` | Aprueba la compra y retiene los fondos. La cantidad no se retira hasta que sea &quot;capturada&quot; por el comerciante. |
   | `Authorize and Capture` | Aprueba la compra y el comerciante &quot;captura&quot; los fondos. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] admite capturas parciales. Un comerciante puede capturar parcialmente (facturar) partes de un pedido. Por ejemplo, puede capturar cada elemento de forma individual, o un elemento ahora y el resto más tarde.

1. Clic **[!UICONTROL Save]**.
1. Clic **[!UICONTROL Go to Payment Services]** para que se le dirija de nuevo a [!DNL Payment Services] Hogar.
1. [Borre la caché](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   La limpieza debe realizarse después de cada cambio de configuración.

Consulte [Configurar servicios de pago](settings.md) para obtener más información sobre la configuración de los campos de tarjeta de crédito y los botones de pago de PayPal.

## Incorporación completa del comerciante

El siguiente paso para permitir que sus tiendas entren en funcionamiento con los servicios de pago es completar la incorporación activa.

Payment Services proporciona [**Avanzadas** (totalmente compatible) y **Standard** Opciones de pago (Pago y envío exprés)](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) y flujos de incorporación, según el país en el que opere y su experiencia de pago preferida.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clic **[!UICONTROL Live onboarding]**.

   Esta opción está visible si aún no ha completado la incorporación en directo para [!DNL Payment Services].

1. En el _Seleccione su país_ modal, seleccione el país desde el que opera.

   Payment Services ofrece soporte completo para todas las opciones de pago de [cinco países](../payment-services/overview.md#availability) actualmente. Payment Services proporciona la capacidad de Pago y envío exprés (un subconjunto de opciones de pago) para todos los demás países representados en la lista de países.

   El país que elija en la lista determinará las opciones de pago y el flujo de incorporación:[Avanzadas](#advanced-onboarding) (totalmente compatible) o [Standard](#standard-onboarding) (Pago y envío rápido): disponible para usted.

>[!TIP]
>
> Una vez que elija y continúe con una opción de incorporación (Estándar o Avanzada), debe volver a completar la incorporación para actualizar o reducir la categoría desde la selección inicial.

### Incorporación avanzada

Este flujo de incorporación está disponible para los comerciantes de [países con pleno apoyo](../payment-services/overview.md#availability).

Una vez seleccionado el país:

1. En el modal que aparece, seleccione **Avanzadas**.

   Para el **Standard** , continúe con la [Flujo de incorporación estándar](#standard-onboarding).

1. Clic **Continuar**.
1. Continúe con el flujo de PayPal para la incorporación avanzada totalmente compatible, usando las credenciales de su cuenta de PayPal (no las credenciales de su cuenta de zona protegida) _o_ regístrate en una nueva cuenta PayPal.

>[!IMPORTANT]
>
>**Incorporación avanzada** requiere que los comerciantes [solicitar derechos de pagos](#request-payments-entitlement-from-adobe) para habilitar la incorporación en directo.

### Incorporación estándar

Este flujo de incorporación estándar está disponible para comerciantes de países disponibles para los que [solo admite el cierre de compra exprés](../payment-services/overview.md#availability) se proporciona.

Una vez seleccionado el país:

1. En el _Acuerdo de servicios de pago_ modal que aparece, haga clic en el **Acuerdo de servicios de pago** para ver el acuerdo de Adobe Commerce Payment Services.
1. En el _Acuerdo de servicios de pago_ modal, haga clic en **Acepto.**.
1. Continúa con el flujo de PayPal para la incorporación de Pago y envío exprés, usando tus credenciales de cuenta de PayPal (no tus credenciales de cuenta de zona protegida) o regístrate en una nueva cuenta de PayPal.

>[!IMPORTANT]
>
>[Campos de Apple Pay y de tarjeta de crédito](../payment-services/payments-options.md) no están disponibles para **Incorporación estándar**.

## Confirmar correo electrónico

1. En la barra lateral de Administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   El _[!UICONTROL Live onboarding]_ya no está visible y ve un &quot;&quot;.[!UICONTROL Live payments pending]Cuadro de texto &quot;.

   En ese cuadro de texto, también se le puede pedir que confirme su dirección de correo electrónico con PayPal para completar la incorporación.

1. Si se te pide que confirmes tu dirección de correo electrónico, comprueba en tu correo electrónico el mensaje de confirmación enviado desde PayPal y pulsa para confirmar tu dirección de correo electrónico.
1. En la barra lateral de Administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Actualice la ventana del explorador.

   Cuando se apruebe la incorporación de tu comerciante PayPal, deberías ver una notificación que indique que tu sistema de pago está en modo de zona protegida y no está procesando pagos en vivo.

   >[!IMPORTANT]
   >
   >Si revoca el consentimiento a [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] para procesar tus pagos (en la configuración de tu cuenta PayPal), los pedidos de tu tienda no pueden ser procesados por [!DNL Payment Services]. En su página de inicio de servicios de pago, aparece una alerta sobre el consentimiento revocado.

## Solicitar derecho de pagos del Adobe

Para activar tus tiendas, solicita el derecho de pago desde el Adobe (para [Solo incorporación avanzada](#advanced-onboarding)):

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clic **[!UICONTROL Get Live Payments]** en su [!DNL Payment Services] Hogar.

   ![Solicitar derechos](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Complete el formulario.
1. Un miembro del equipo de ventas se pondrá en contacto con usted.

También puede solicitar el derecho de pagos desde el Adobe en [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Incorporación en directo** no es accesible hasta que se aprueba el derecho de pagos.

## Configurar nivel de precios

Obtenga su [!DNL Payment Services] _ID de comerciante_:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. En la vista Inicio, haga clic en **[!UICONTROL Settings]**. Consulte [Inicio](payments-home.md) para obtener más información.
1. Seleccione el requerido _ID de comerciante_ y enviarlo a su representante de ventas, que configurará el nivel de precios correcto.

Consulte [Procesamiento de los niveles 2 y 3](levels-card-payment-transactions.md) para obtener más información sobre las transacciones de pago.

## Habilitar pagos activos

A _ID de comerciante de producción_ se genera automáticamente y se rellena en [configuración](configure-admin.md). No cambie ni modifique este ID.

Activar pagos activos:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. En Inicio, haga clic en **[!UICONTROL Settings]** en la parte superior derecha de la página. Consulte [Inicio](payments-home.md) para obtener más información.
1. En el _[!UICONTROL General Configuration]_conjunto de secciones **[!UICONTROL Payment mode]**hasta `Production`.
1. Clic **[!UICONTROL Save]**.
1. [Borre la caché](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >Si no borras la caché, los clientes no podrán ver las opciones de pago de PayPal durante el proceso de pago y envío.

Si vuelve a navegar a [!DNL Payment Services] En Inicio, el mensaje del modo de pago de zona protegida ya no aparece porque está procesando pagos activos.

Consulte [Configurar en el administrador](configure-admin.md) para las opciones de configuración heredadas.

>[!IMPORTANT]
>
>Si revoca el consentimiento a [!DNL Payment Services] para procesar tus pagos (en la configuración de tu cuenta PayPal), los pedidos de tu tienda no pueden ser procesados por [!DNL Payment Services]. Si deseas volver a habilitar el procesamiento de pagos, debes completar de nuevo la incorporación. En su página de inicio de servicios de pago, aparece una alerta sobre el consentimiento revocado.

## Prueba en producción

Es muy recomendable probar Payments in production, con tarjetas de crédito y bancos reales, antes de exponer esta funcionalidad a los compradores.

Consulte [Prueba y validación](test-validate.md) para obtener más información.
