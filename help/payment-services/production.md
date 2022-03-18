---
title: Habilitar [!DNL Payment Services] para producción
description: Complete el proceso de incorporación habilitando [!DNL Payment Services] para producción.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Habilitar [!DNL Payment Services] para producción

Después de que la extensión Servicios de pagos esté [instalado](install.md), su instancia es [configurado y conectado](connect.md)y [configuración del simulador para pruebas](sandbox.md) y probado, puede continuar poniendo el servicio en producción y completar la [proceso de incorporación](onboard.md).

## Establezca [!DNL Payment Services] como método de pago

Tras [configurar los servicios de comercio](connect.md#configure-commerce-services) y habilite [prueba de entorno limitado](sandbox.md#enable-sandbox-testing) o [pagos en directo](#enable-live-payments), debe establecer [!DNL Payment Services] como método de pago.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Haga clic **[!UICONTROL Enable Payment Services]**.

   Esta opción está visible si aún no se ha configurado [!DNL Payment Services] como método de pago para uno o más de sus sitios web Magento.

   Se le redirige al área de configuración en Administración con las opciones relevantes expandidas (**[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** > _[!UICONTROL Recommended Solutions]_>_[!UICONTROL Payment Services]_), donde puede habilitar la variable [!DNL Payment Services] como [método de pago](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}.

1. En _[!UICONTROL General Configuration]_, conjunto **[!UICONTROL Enable]**a `Yes`.
1. Establezca **[!UICONTROL Payment Action]**, para ambas _[!UICONTROL Credit Card Fields]_y_[!UICONTROL PayPal Smart Buttons]_, a una de las siguientes opciones:

   | Configuración | Descripción |
   |---|---|
   | `Authorize` | Aprueba la compra y suspende los fondos. La cantidad no se retira hasta que el comerciante la &quot;captura&quot;. |
   | `Authorize and Capture` | Aprueba la compra y el comerciante &quot;captura&quot; los fondos. |

1. Haga clic **[!UICONTROL Save Config]**.
1. Haga clic en **[!UICONTROL Go to Payment Services]** para que se le devuelva al [!DNL Payment Services] home.
1. [Borre la caché](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}.

   El borrado debe realizarse después de cada cambio de configuración.

Consulte [Configurar servicios de pago](configure-admin.md) para obtener más información sobre la configuración de los campos de tarjeta de crédito y los botones inteligentes PayPal.

## Integración completa del comerciante

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Haga clic **[!UICONTROL Live onboarding]**.

   Esta opción está visible si aún no ha completado la integración activa para [!DNL Payment Services].

   Se te presenta una ventana de PayPal.

1. Continúe con el flujo de PayPal, con sus credenciales de cuenta de PayPal (no sus credenciales de cuenta de simulación de pruebas) o regístrese en una nueva cuenta de PayPal.
1. En la barra lateral de administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   La variable _[!UICONTROL Live onboarding]_ya no está visible y se ve un &quot;[!UICONTROL Live payments pending]&quot;.

   En ese cuadro de texto, también se le puede pedir que confirme su dirección de correo electrónico con PayPal para completar la incorporación.

1. Si se le solicita que confirme su dirección de correo electrónico, compruebe el mensaje de confirmación enviado desde PayPal y haga clic en para confirmar su dirección de correo electrónico.
1. En la barra lateral de administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Actualice la ventana del explorador.

   Cuando se aprueba la incorporación de su comerciante de PayPal, debería ver una notificación que indica que su sistema de pago está en modo de caja fuerte y que no está procesando pagos en vivo.

   >[!IMPORTANT]
   >
   >Si revoca el consentimiento a [!DNL Payment Services] para Adobe Commerce y el Magento Open Source para procesar sus pagos (en la configuración de su cuenta de PayPal), los pedidos de su tienda no pueden ser procesados por [!DNL Payment Services].

## Solicitar el derecho de pago del Adobe

Para habilitar la incorporación activa, debe solicitar el derecho de pago de [Adobe](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Incorporación en directo** no es accesible hasta que se haya aprobado el derecho de pago.

## Configuración del nivel de precios

Para obtener su [!DNL Payment Services] _ID del comerciante_:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Payment Methods]**.
1. Expanda el _[!UICONTROL Recommended Solutions]_para obtener más información.
1. En el _[!UICONTROL Payment Services]_, expanda la sección_[!UICONTROL General Configuration]_ para obtener más información.
1. Seleccione el _ID del comerciante_ y envíelo a su representante de ventas, que configurará el nivel de precios correcto.

## Habilitar los pagos en vivo

A _ID del comerciante de producción_ se genera automáticamente y se rellena en la variable [configuración](configure-admin.md). No cambie ni modifique este ID.

Para habilitar los pagos en vivo:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Sales]** y elija **[!UICONTROL Payment Methods]**.
1. Expanda el _[!UICONTROL Recommended Solutions]_para obtener más información.
1. En el _[!UICONTROL Payment Services]_, expanda la sección_[!UICONTROL General Configuration]_ para obtener más información.
1. Establezca **[!UICONTROL Method]** a `Production`.
1. Haga clic **[!UICONTROL Save Config]**.
1. [Borre la caché](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}.

   >[!IMPORTANT]
   >
   >Si no borra la caché, los clientes no podrán ver las opciones de pago de PayPal durante el cierre de compra.

Si vuelve a la [!DNL Payment Services] En el inicio, el mensaje del modo de pago de espacio aislado ya no aparece porque ahora está procesando pagos activos.

Consulte [Configurar en el administrador](configure-admin.md) para obtener más opciones de configuración.

>[!IMPORTANT]
>
>Si revoca el consentimiento a [!DNL Payment Services] para procesar sus pagos (en la configuración de su cuenta de PayPal), los pedidos de su tienda no pueden ser procesados por [!DNL Payment Services]. Si desea volver a habilitar el procesamiento de pagos, debe volver a completar la incorporación.

## Prueba en producción

Es muy recomendable probar Pagos en producción, con tarjetas de crédito y bancos reales, antes de exponer esta funcionalidad a compradores.

Consulte [Prueba y validación](test-validate.md) para obtener más información.
