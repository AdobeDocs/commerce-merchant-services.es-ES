---
title: Conector de Commerce Services
description: Obtenga información sobre cómo integrar la instancia de Adobe Commerce o Magento Open Source en servicios mediante claves de API de producción y simulación de pruebas.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 89be4b0aa7b311db10cffe7abf9c16a2becbd3a4
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Algunas funciones de Adobe Commerce y Magento Open Source utilizan la tecnología [!DNL Commerce Services]  e implementada como SaaS (software como servicio). Para utilizar estos servicios, debe conectar su [!DNL Commerce] con las claves de la API de producción y simulación de pruebas, y especifique el espacio de datos en la variable [configuración](https://docs.magento.com/user-guide/configuration/services/saas.html). Solo es necesario configurarlo una vez.

## Servicios disponibles {#availableservices}

A continuación se enumeran las [!DNL Commerce] funciones a las que puede acceder a través de la [!DNL Commerce Services Connector]:

| Servicio | Disponibilidad |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) equipado con Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) equipado con Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce y Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.corp.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce y Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.corp.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |

## Arquitectura

En un nivel superior, la variable [!DNL Commerce Services Connector] se compone de los siguientes elementos principales:

![Arquitectura del conector de Commerce Services](assets/saas-config-sync-workflow.png)

En las secciones siguientes se examina cada uno de estos elementos con más detalle.

## Credenciales {#apikey}

Las claves de la API de producción y del simulador de pruebas se generan a partir de la variable [!DNL Commerce] la cuenta del titular de la licencia, identificada por un [!DNL Commerce] ID (MageID). Para pasar la validación de autorizaciones para servicios como [!DNL Product Recommendations] o [!DNL Live Search], el titular de la licencia de la organización del comerciante puede generar el conjunto de claves de API siempre y cuando la cuenta esté en buen estado. Las claves se pueden compartir según la &quot;necesidad de saber&quot; con el integrador de sistemas o el equipo de desarrollo que administra proyectos y entornos en nombre del titular de la licencia. Además, los integradores de soluciones también están autorizados a usar [!DNL Commerce Services]. Si es integrador de soluciones, la firma de la función [!DNL Commerce] el contrato de socio debe generar las claves de API.

### Generar las claves de la API de producción y del simulador de pruebas {#genapikey}

1. Inicie sesión en su [!DNL Commerce] cuenta en [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. En el **Magento** , seleccione **Portal de API** en la barra lateral.

1. En el _Entorno_ seleccione **Producción** o **Sandbox**.

1. Escriba un nombre en la _Claves de API_ y haga clic en **Agregar nuevo**.

   Se abrirá un cuadro de diálogo para descargar la nueva clave.

   ![Descargar clave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Esta es la única oportunidad que tiene para copiar o descargar sus claves.

1. Haga clic en **Descargar** a continuación, haga clic en **Cancelar**.

1. Repita los pasos anteriores para cada entorno (producción y entorno limitado).

   La variable **Claves de API** ahora muestra sus claves de API. Necesita las claves de producción y de simulación de pruebas cuando [seleccionar o crear un proyecto SaaS](#createsaasenv).

## Configuración de SaaS {#saasenv}

[!DNL Commerce] las instancias deben configurarse con un proyecto SaaS y un espacio de datos SaaS para que [!DNL Commerce Services] puede enviar datos a la ubicación correcta. Un proyecto SaaS agrupa todos los espacios de datos SaaS. Los espacios de datos SaaS se utilizan para recopilar y almacenar datos que permitan [!DNL Commerce Services] para trabajar. Algunos de estos datos se pueden exportar desde el [!DNL Commerce] instancia y algunos se pueden recopilar del comportamiento del comprador en la tienda. Estos datos se mantienen para proteger el almacenamiento en la nube.

Para [!DNL Product Recommendations], el espacio de datos SaaS contiene datos de catálogo y comportamiento. Puede señalar una [!DNL Commerce] instancia a un espacio de datos SaaS mediante [seleccionarlo](https://docs.magento.com/user-guide/configuration/services/saas.html) en el [!DNL Commerce] configuración.

>[!WARNING]
>
> Utilice su espacio de datos SaaS de producción solo en su producción [!DNL Commerce] para evitar conflictos de datos. De lo contrario, se corre el riesgo de contaminar los datos del sitio de producción con datos de prueba, lo que provoca retrasos en la implementación. Por ejemplo, los datos del producto de producción se pueden sobrescribir erróneamente de los datos de ensayo, como las direcciones URL de ensayo.

### Seleccionar o crear un proyecto SaaS {#createsaasenv}

>[!NOTE]
>
> Si no ve la variable **[!UICONTROL Commerce Services Connector]** en la sección [!DNL Commerce] debe instalar el [!DNL Commerce] módulos para el [[!DNL Commerce] service](#availableservices).

Para seleccionar o crear un proyecto SaaS, solicite la variable [!DNL Commerce] Clave de API de [!DNL Commerce] titular de licencia para su tienda.

1. En el _Administrador_ barra lateral, vaya a **Sistema** > Servicios > **Conector de Commerce Services**.

1. En el _Claves de API de Sandbox_ y _Claves de API de producción_ , pegue los valores clave.

   Las claves privadas deben incluir `----BEGIN PRIVATE KEY---` al principio de la clave y `----END PRIVATE KEY----` al final de la clave privada.

1. Haga clic en **Guardar**.

Cualquier proyecto SaaS asociado con sus claves aparece en la **Proyecto** en el campo **Identificador SaaS** para obtener más información.

1. Si no existen proyectos SaaS, haga clic en **Crear proyecto**. A continuación, en el **Proyecto** , introduzca un nombre para el proyecto SaaS.

   Al crear un proyecto SaaS, [!DNL Commerce] genera uno o más espacios de datos SaaS en función de su [!DNL Commerce] licencia:
   - Adobe Commerce: Un espacio de datos de producción; dos espacios de datos de prueba
   - Magento Open Source - Un espacio de datos de producción; sin espacios de datos de prueba

1. Seleccione el **Espacio de datos** para usar en la configuración actual de su [!DNL Commerce] tienda.

>[!WARNING]
>
> Si genera nuevas claves en la sección Portal de API de Mi cuenta, actualice inmediatamente las claves de API en la configuración de Administración. Si genera nuevas claves y no las actualiza en el Administrador, las extensiones SaaS ya no funcionan y se pierden datos valiosos.

Para cambiar los nombres del proyecto SaaS o del espacio de datos, haga clic en **Cambiar nombre**.

## Organización IMS (opcional) {#organizationid}

(Esta función está diseñada para una futura integración con Adobe Experience Platform). Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, inicie sesión en la cuenta de Adobe con su Adobe ID. Después de iniciar sesión, la organización de IMS asociada a su cuenta de Adobe se muestra en esta sección.

## Sincronización del catálogo

Cuando [!DNL Commerce] se conecta correctamente con [!DNL Commerce Services], el proceso de sincronización de catálogos exporta los datos del producto desde el [!DNL Commerce] servidor a [!DNL Commerce Services]. [Más información](catalog-sync.md) acerca del proceso de sincronización del catálogo.
