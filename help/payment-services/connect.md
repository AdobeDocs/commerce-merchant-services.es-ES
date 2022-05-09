---
title: Conecte la instancia
description: Conecte la instancia de Commerce con una clave de API y una clave privada, y especifique el espacio de datos en la configuración.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# Conecte la instancia

[!DNL Payment Services] cuenta con la tecnología Commerce Services e implementada como SaaS (software como servicio). La instancia de comercio se conecta con una clave de API y una clave privada, y especifica el espacio de datos en la configuración. Esta conexión solo se configura una vez.

Consulte [Conector de Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} en la guía del usuario principal para obtener información detallada sobre este servicio.

## Obtener credenciales de API

Para consumir un servicio Commerce SaaS, debe utilizar las claves de API de su instancia, que se crean y administran en su [Mi tablero de cuenta](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. Se pueden crear dos pares de claves API diferentes para una cuenta de Commerce (una para entornos limitados y otra para producción (pagos activos)), aunque solo se puede utilizar activamente un par a la vez.

>[!NOTE]
>
>Necesita ayuda para acceder a su [!UICONTROL My Account] tablero? Consulte [Crear una cuenta de comercio](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;} en la guía de usuario principal.

Un par de claves de API dado es válido para todos los servicios de comercio de un entorno, por lo que si ya tiene los servicios de comercio configurados para su instancia de comercio, el par de claves de API ya está presente en el administrador. Si se pierde la clave de API privada, debe generarse un nuevo par de claves de API y aplicarse a la configuración de Commerce Services en Admin.

Para obtener información sobre cómo generar una clave de API para entornos de entorno limitado o de producción, consulte [Conector de Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} en la guía de usuario principal.

>[!IMPORTANT]
>
>Si regenera un par de claves de API y cambia el Identificador SaaS, todos los servicios de comercio utilizados por esta instancia se conectarán a un almacén de datos diferente y se perderá el acceso (incluidos los datos almacenados anteriormente). Se recomienda no volver a generar un par de claves API y cambiar el identificador SaaS en una instancia de producción activa.

### Clave de API de comercio y clave privada

Algunas [!DNL Adobe Commerce] y [!DNL Magento Open Source] las funciones se implementan como SaaS (software como servicio), conocidos como Commerce Services. Para utilizar estos servicios, debe conectar la instancia de Commerce a estos servicios mediante una clave de API y una clave privada, y especificar el espacio de datos deseado en la variable [configuración](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

Cuando crea una cuenta de comercio, identificada por un MageID, puede generar una clave de API de comercio y una clave privada. Para usar los servicios de comercio, como [!DNL Payment Services], [!DNL Product Recommendations]o [!DNL Live Search], el titular de la licencia debe generar estas claves para pasar la validación de derechos. Estas claves se pueden pasar al integrador de sistemas o al equipo de desarrollo que administra los proyectos y entornos en nombre del titular de la licencia. Si es integrador de soluciones, también puede utilizar estos servicios para sus propias necesidades. En ese caso, el firmante del contrato de socio comercial debe generar las claves.

### Generación de una clave de API y una clave privada

1. Inicie sesión en su cuenta de comercio en [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. En el **[!UICONTROL Magento]** , seleccione **[!UICONTROL API Portal]** en la barra lateral.
1. En el _[!UICONTROL Environment]_seleccione **[!UICONTROL Sandbox]**, luego **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >Las claves de API son necesarias para ambos entornos.

1. Escriba un nombre en la _[!UICONTROL API Keys]_y haga clic en **[!UICONTROL Add New]**.

   Esta acción abre un cuadro de diálogo para descargar la nueva clave.

   >[!IMPORTANT]
   >
   >Este cuadro de diálogo es la única oportunidad que tiene para copiar o descargar su clave.

1. Haga clic en **[!UICONTROL Download]** a continuación, haga clic en **[!UICONTROL Cancel]**.

   La variable _[!UICONTROL API Keys]_ahora muestra su clave de API.

1. Copie la clave de API y la clave privada al seleccionar o crear un proyecto SaaS.

   Consulte [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} en la guía del usuario principal para obtener información más detallada.

La misma clave de API se puede usar en todas las instancias, pero cada instancia debe tener su propio espacio de datos SaaS.

Al crear un proyecto SaaS, Commerce genera uno o más espacios de datos SaaS en función de la licencia de Commerce:

* [!DNL Adobe Commerce] - Un espacio de datos de producción; dos espacios de datos de prueba
* [!DNL Magento Open Source] - Un espacio de datos de producción; sin espacios de datos de prueba

### Configuración del proyecto SaaS

>[!NOTE]
>
>Si no ve la variable _[!UICONTROL Commerce Services Connector]_en la configuración de Commerce, debe instalar los módulos de Commerce para el servicio de Commerce que desee, como [[!DNL Payment Services]](install.md).

Para seleccionar o crear un proyecto SaaS, solicite la clave de la API de comercio del titular de licencia de comercio para su tienda.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. En el panel izquierdo, expanda **[!UICONTROL Services]** y elija **[!UICONTROL Commerce Services Connector]**.
1. En el _[!UICONTROL API Keys]_pegue los valores de clave.

   >[!IMPORTANT]
   >
   >Añadir valores clave para ambas **[!UICONTROL sandbox]** y **[!UICONTROL production]** entornos.

1. Haga clic **[!UICONTROL Save Config]**.

   Al guardar, si hay algún proyecto SaaS asociado a su clave de API, esos proyectos aparecerán en el _[!UICONTROL SaaS Project]_en el campo_[!UICONTROL SaaS Identifier]_ para obtener más información.

1. Si no existen proyectos SaaS, haga clic en **[!UICONTROL Create Project]**. A continuación, introduzca un nombre para su proyecto SaaS en la **[!UICONTROL Project Name]** campo .
1. Para utilizar la configuración actual de su tienda de comercio, seleccione la opción **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>Si vuelve a generar las claves en la sección Portal de API de Mi cuenta, actualice inmediatamente las claves de API en la configuración de Administración. Si genera nuevas claves y no las actualiza en el administrador, sus extensiones SaaS ya no funcionarán y perderá datos valiosos.

Para cambiar los nombres, haga clic en el botón **[!UICONTROL Rename this Project]** o **[!UICONTROL Rename Data Space]** botones respectivamente.

## Configurar Commerce Services

El primer paso para la incorporación [!DNL Payment Services] es configurar los servicios de comercio en el Administrador.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Haga clic **[!UICONTROL Configure Commerce Services]**.

   Esta opción está visible si todavía no ha configurado los servicios de comercio para su cuenta.

   Se le redirige al área de configuración en el Administrador, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar Commerce Services Connector.

1. Para configurar los servicios de comercio, siga los pasos descritos en [Servicios de comercio](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
