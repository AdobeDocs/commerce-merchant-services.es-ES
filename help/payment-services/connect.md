---
title: Conectar su instancia
description: Conecte la instancia de Commerce con una clave de API y una clave privada, y especifique el espacio de datos en la configuración.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Conectar su instancia

[!DNL Payment Services] cuenta con la tecnología Commerce Services e implementada como SaaS (software como servicio). La instancia de comercio se conecta con una clave de API y una clave privada, y se especifica el espacio de datos en la configuración mediante la variable [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Esta conexión solo se configura una vez.**

* Si tiene *ya ha conectado la instancia*, al obtener y usar sus credenciales de API y configurar Commerce Services, puede continuar con [configuración del entorno limitado de pruebas](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Si *necesita conectar su instancia*, consulte la información de este tema acerca de [obtención de credenciales de API](#obtain-api-credentials) y [configuración de Commerce Services](#configure-commerce-services).
* Si *no está seguro de si la instancia está conectada*, vaya a **Sistema** > Servicios > **Conector de Commerce Services** y vea los valores de clave de API pública y privada en la variable [!UICONTROL Sandbox Keys] y [!UICONTROL Production Keys] y *Proyecto* y *Espacio de datos* campos de la variable [!UICONTROL SaaS Identifier] para obtener más información. Si esos valores están presentes, la instancia está conectada.

## Obtener credenciales de API

Para consumir un servicio Commerce SaaS, debe utilizar las claves de API de su instancia (clave de API pública de comercio y clave privada) tanto para el simulador para pruebas como para la producción, que se crean y administran en su [Mi tablero de cuenta](https://account.magento.com/customer/account/login). [El par de teclas](https://docs.magento.com/user-guide/configuration/services/saas.html) se puede crear para una cuenta de comercio (una para entornos limitados y otra para producción), aunque solo se puede utilizar de forma activa un par a la vez.

>[!NOTE]
>
>Necesita ayuda para acceder a su [!UICONTROL My Account] tablero? Consulte [Crear una cuenta de comercio](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Una vez creada, siempre hay disponible una clave de API pública en el panel de Mi cuenta. Se puede copiar o eliminar según sea necesario. La clave de API privada se hace visible al crear una clave de API pública para entornos limitados o de producción; solo está disponible para copiarlo o guardarlo desde el cuadro de diálogo siguiente y no se puede acceder a él más adelante.

Un par de claves de API dado es válido para todos los servicios de comercio de un entorno, por lo que si ya tiene los servicios de comercio configurados para su instancia, el par de claves de API ya está presente en el conector de servicios de comercio.

Si se pierde la clave de API, debe establecerse un nuevo par de claves de API [generado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) y [aplicado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) a la configuración del conector de Commerce Services en Admin. Si se configuran las claves incorrectas o no existe ninguna en la configuración, aparece un cuadro de diálogo de error de verificación de la cuenta en los servicios de pago que le notifica que la cuenta no se ha verificado.

Consulte una [lista de servicios de comercio disponibles que utilizan la API](https://docs.magento.com/user-guide/system/saas.html#available-services).

Para obtener información sobre cómo generar una clave de API para entornos de entorno limitado o de producción, consulte [Credenciales](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>Se recomienda no volver a generar un par de claves de API *y* cambie el identificador de SaaS o el espacio de datos en una instancia de producción activa. Perderá datos para su instancia si se modifican.

## Configurar Commerce Services

La misma clave de API se puede usar en todas las instancias, pero cada instancia debe tener su propia [Espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

Ahora que ha obtenido sus credenciales, puede configurar su proyecto SaaS y el espacio de datos Saas.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Haga clic en **[!UICONTROL Configure Commerce Services]**.

   Esta opción está visible si todavía no ha configurado los servicios de comercio para su cuenta.

   Se le redirige al área de configuración en el Administrador, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar Commerce Services Connector.

1. Para configurar los servicios de comercio, siga los pasos descritos en [Configuración de SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
