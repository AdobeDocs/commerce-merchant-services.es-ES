---
title: Conector de Commerce Services
description: Obtenga información sobre cómo integrar la instancia de Adobe Commerce o Magento Open Source en servicios mediante claves de API de producción y de zona protegida.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Algunas funciones de Adobe Commerce y Magento Open Source utilizan [!DNL Commerce Services]  e implementado como SaaS (software como servicio). Para utilizar estos servicios, debe conectar su [!DNL Commerce] usando las claves de API de producción y de entorno limitado, y especifique el espacio de datos en la variable [configuración](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Solo debe configurar esto una vez.

## Servicios disponibles {#availableservices}

A continuación se enumeran los [!DNL Commerce] funciones a las que puede acceder a través de [!DNL Commerce Services Connector]:

| Servicio | Disponibilidad |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) equipado con Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) equipado con Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | ADOBE COMMERCE y MAGENTO OPEN SOURCE |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | ADOBE COMMERCE y MAGENTO OPEN SOURCE |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Arquitectura

En un nivel superior, la [!DNL Commerce Services Connector] se compone de los siguientes elementos principales:

![Arquitectura del conector de Commerce Services](assets/saas-config-sync-workflow.png)

En las secciones siguientes se analiza cada uno de estos elementos con más detalle.

## Credenciales {#apikey}

Las claves de API de producción y de zona protegida se generan a partir de la variable [!DNL Commerce] cuenta del titular de la licencia, que se identifica mediante una [!DNL Commerce] ID (MageID). Para pasar la validación de derechos para servicios como [!DNL Product Recommendations] o [!DNL Live Search], el titular de la licencia de la organización del comerciante puede generar el conjunto de claves API siempre y cuando la cuenta esté al día. Las claves se pueden compartir, según sea necesario, con el integrador de sistemas o el equipo de desarrollo que gestiona los proyectos y entornos en nombre del titular de la licencia. Además, los integradores de soluciones también pueden utilizar [!DNL Commerce Services]. Si es un integrador de soluciones, el firmante de la variable [!DNL Commerce] el contrato de socio debe generar las claves API.

### Generar las claves API de producción y de zona protegida {#genapikey}

1. Inicie sesión en su [!DNL Commerce] cuenta en [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. En el **Magento** pestaña, seleccione **Portal de API** en la barra lateral.

1. Desde el _Entorno_ menú, seleccione **Producción** o **Sandbox**.

1. Introduzca un nombre en la _Claves de API_ y haga clic en **Añadir nuevo**.

   Esto abre un cuadro de diálogo para descargar la nueva clave.

   ![Descargar clave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Esta es la única oportunidad que tiene para copiar o descargar sus claves.

1. Clic **Descargar** luego haga clic en **Cancelar**.

1. Repita los pasos anteriores para cada entorno (producción y zona protegida).

   El **Claves de API** ahora muestra sus claves API. Necesita las claves de producción y de la zona protegida al [seleccionar o crear un proyecto SaaS](#createsaasenv).

## Configuración de SaaS {#saasenv}

[!DNL Commerce] Las instancias de deben configurarse con un proyecto SaaS y un espacio de datos SaaS para que [!DNL Commerce Services] puede enviar datos a la ubicación correcta. Un proyecto SaaS agrupa todos los espacios de datos SaaS. Los espacios de datos SaaS se utilizan para recopilar y almacenar datos que habilitan [!DNL Commerce Services] para trabajar. Algunos de estos datos pueden exportarse desde el [!DNL Commerce] y algunos se pueden recopilar del comportamiento del comprador en la tienda. Estos datos se conservan para proteger el almacenamiento en la nube.

Para [!DNL Product Recommendations], el espacio de datos SaaS contiene datos de catálogo y de comportamiento. Puede señalar a [!DNL Commerce] a un espacio de datos SaaS por [seleccionándolo](https://docs.magento.com/user-guide/configuration/services/saas.html) en el [!DNL Commerce] configuración.

>[!WARNING]
>
> Utilice su espacio de datos SaaS de producción solo en su producción [!DNL Commerce] para evitar conflictos de datos. De lo contrario, se corre el riesgo de contaminar los datos del sitio de producción con datos de prueba, lo que provoca retrasos en la implementación. Por ejemplo, los datos del producto de producción se podrían sobrescribir por error a partir de los datos de ensayo, como las direcciones URL de ensayo.

### Seleccionar o crear un proyecto SaaS {#createsaasenv}

>[!NOTE]
>
> Si no ve el **[!UICONTROL Commerce Services Connector]** de la sección [!DNL Commerce] , debe instalar la variable [!DNL Commerce] módulos para el que desee [[!DNL Commerce] servicio](#availableservices).

Para seleccionar o crear un proyecto de SaaS, solicite lo siguiente [!DNL Commerce] Clave de API de [!DNL Commerce] titular de la licencia de su tienda.

1. En el _Administrador_ barra lateral, vaya a **Sistema** > Servicios > **Conector de Commerce Services**.

1. En el _Claves de API de zona protegida_ y _Claves de API de producción_ , pegue los valores clave.

   Las claves privadas deben incluir `----BEGIN PRIVATE KEY---` al principio de la clave y `----END PRIVATE KEY----` al final de la clave privada.

1. Clic **Guardar**.

Todos los proyectos SaaS asociados a sus claves aparecen en la **Proyecto** en el campo **Identificador de SaaS** sección.

1. Si no existen proyectos SaaS, haga clic en **Crear proyecto**. A continuación, en la **Proyecto** , introduzca un nombre para el proyecto SaaS.

   Cuando crea un proyecto SaaS, [!DNL Commerce] genera uno o más espacios de datos SaaS en función de su [!DNL Commerce] licencia:
   - Adobe Commerce: un espacio de datos de producción, dos espacios de datos de prueba
   - Magento Open Source: un espacio de datos de producción, sin espacios de datos de prueba

1. Seleccione el **Espacio de datos** para usar en la configuración actual de [!DNL Commerce] tienda.

>[!WARNING]
>
> Si genera claves nuevas en la sección del portal de API de Mi cuenta, actualice inmediatamente las claves de API en la configuración de la administración. Si genera claves nuevas y no las actualiza en el Administrador, las extensiones SaaS dejarán de funcionar y perderá datos valiosos.

Para cambiar los nombres del proyecto SaaS o del espacio de datos, haga clic en **Cambiar nombre**.

## Organización de IMS (opcional) {#organizationid}

Para conectar la instancia de Adobe Commerce al Adobe Experience Platform, inicie sesión en la cuenta de Adobe con el Adobe ID. Después de iniciar sesión, la organización de IMS asociada a su cuenta de Adobe se muestra en esta sección.

## Sincronización de catálogo

Cuando su [!DNL Commerce] la instancia se conecta correctamente a [!DNL Commerce Services], el proceso de sincronización de catálogos exporta datos de productos de su [!DNL Commerce] servidor a [!DNL Commerce Services]. Actualmente, solo Product Recommendations utiliza el servicio de sincronización de catálogos. [Más información](catalog-sync.md) sobre el proceso de sincronización del catálogo.
