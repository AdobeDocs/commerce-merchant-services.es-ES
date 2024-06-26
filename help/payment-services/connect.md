---
title: Conectar su instancia
description: Conecte la instancia de Commerce con una clave de API y una clave privada, y especifique el espacio de datos en la configuración.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 5d3a89b2ef06b2c67ec715ce4f31f22249b336e0
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Conectar su instancia

[!DNL Payment Services] cuenta con la tecnología de Commerce Services y se implementa como SaaS (software como servicio). La instancia de Commerce se conecta mediante una clave de API y una clave privada, y se especifica el espacio de datos en la configuración mediante [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Esta conexión solo se configura una vez.**

>[!INFO]
>
> Consulte nuestra [[!DNL Adobe Commerce] Conector de servicios](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) para obtener más información.

* Si tiene *ya está conectada su instancia*, obteniendo y utilizando sus credenciales de API y configurando los servicios de Commerce, puede continuar con [configuración de la zona protegida de pruebas](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Si todavía *necesita conectar su instancia*, vea la información de este tema acerca de [obtención de credenciales de API](#obtain-api-credentials) y [configurar los servicios de Commerce](#configure-commerce-services).
* Si es usted *no está seguro de si la instancia está conectada*, vaya a **Sistema** > Servicios > **Conector de Commerce Services** y vea los valores de clave de API pública y privada en la [!UICONTROL Sandbox Keys] y [!UICONTROL Production Keys] , y las secciones *Proyecto* y *Espacio de datos* campos en la [!UICONTROL SaaS Identifier] sección. Si esos valores están presentes, la instancia está conectada.

>[!NOTE]
>
>Todos los comerciantes con derecho a servicios de pago pueden utilizar un espacio de datos de producción y dos espacios de datos de prueba.

## Obtener credenciales de API

Para consumir un servicio SaaS de Commerce, debe utilizar las claves de API de la instancia (clave de API pública de Commerce y clave privada) tanto para la zona protegida como para la producción, que se crean y administran en su [Mi tablero de cuenta](https://account.magento.com/customer/account/login). [El par de claves](https://docs.magento.com/user-guide/configuration/services/saas.html) se pueden crear para una cuenta de Commerce (una para la zona protegida y otra para la producción), aunque solo se puede utilizar activamente un par a la vez.

>[!NOTE]
>
>Necesita ayuda para acceder a su [!UICONTROL My Account] ¿tablero? Consulte [Crear una cuenta de Commerce](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Una vez creada, siempre encontrará una clave de API pública en el panel de Mi cuenta. Se puede copiar o eliminar según sea necesario. La clave de API privada se vuelve visible al crear una clave de API pública para simulación de pruebas o producción; solo está disponible para copiarla o guardarla en el cuadro de diálogo siguiente y no se puede acceder a ella posteriormente.

Un par de claves API determinado es válido para todos los servicios de Commerce en un entorno, por lo que si ya tiene los servicios de Commerce configurados para su instancia, su par de claves API ya estará presente en el conector de servicios de Commerce.

Si se pierde la clave de API, se debe configurar un nuevo par de claves de API [generado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) y [aplicado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) Vaya a la configuración de Commerce Services Connector en Admin. Si se configuran claves incorrectas o no existe ninguna en la configuración, aparecerá un cuadro de diálogo de error de verificación de cuenta en Payment Services que le notificará que la cuenta no se ha verificado.

Consulte un [lista de servicios de Commerce disponibles que utilizan la API](https://docs.magento.com/user-guide/system/saas.html#available-services).

Para obtener información sobre cómo generar una clave de API para entornos de zona protegida o de producción, consulte [Credenciales](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Se recomienda no regenerar un par de claves de API *y* cambiar el identificador de SaaS o el espacio de datos en una instancia de producción activa. Perderá datos de su instancia si se modifican.

## Configuración de servicios de Commerce

La misma clave de API se puede utilizar en todas las instancias, pero cada instancia debe tener su propia [Espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Los comerciantes deben utilizar las mismas claves generadas para el MageID para sus derechos de pago.

Ahora que ha obtenido sus credenciales, puede configurar su proyecto SaaS y el espacio de datos Saas.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Clic **[!UICONTROL Configure Commerce Services]**.

   Esta opción está visible si aún no ha configurado los servicios de Commerce para su cuenta.

   Se le dirigirá al área de configuración en el Administrador de, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar el conector de servicios de Commerce.

1. Para configurar los servicios de Commerce, siga los pasos descritos en [Configuración de SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).

   >[!INFO]
   >
   > Consulte nuestra [[!DNL Adobe Commerce] Conector de servicios](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) para obtener más información.

## Extremo

[!DNL Payment Services] utiliza el [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) para conectarse a Commerce Services e implementarlo como SaaS. Esta [!DNL Commerce Services Connector] se comunica a través del punto final en:

* `commerce-beta.adobe.io` para entornos de zona protegida.
* `commerce.adobe.io for` para entornos en directo.
