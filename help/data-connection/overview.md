---
title: Información general de la guía
description: Obtenga información sobre cómo integrar datos de Adobe Commerce con Adobe Experience Platform mediante el [!DNL Data Connection] extensión.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# [!DNL Data Connection] descripción general

>[!IMPORTANT]
>
>Se ha cambiado el nombre del conector del Experience Platform a [!DNL Data Connection].

El [!DNL Data Connection] Esta extensión permite a los comerciantes de Adobe Commerce enviar [escaparate](events.md#storefront-events) y [back office](events.md#back-office-events) a Adobe Experience Platform Edge para que otros productos de Adobe Experience Cloud, como Adobe Analytics y Adobe Journey Optimizer, puedan utilizar esos datos de Commerce. Al conectar los datos de Commerce a otros productos de Adobe Experience Cloud, puede realizar tareas como analizar el comportamiento del usuario en el sitio, realizar pruebas AB y crear campañas personalizadas.

[Eventos de tienda](events.md#storefront-events) capturar las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, y [lista de solicitudes](events.md#b2b-events) información (para comerciantes B2B). [Back Office](events.md#back-office-events) los eventos capturan información sobre el estado de un pedido como, por ejemplo, si se ha realizado, cancelado, reembolsado, enviado o completado. Los datos capturados no incluyen información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

El [!DNL Data Connection] La extensión de aparece en el Administrador de comercio en **Sistema** > Servicios > **[!DNL Data Connection]**.

![[!DNL Data Connection] vista de administración de extensiones](assets/epc-adminui.png)

## Requisitos previos {#prereqs}

Para usar la variable [!DNL Data Connection] Extensión, debe tener lo siguiente:

- Adobe Commerce 2.4.3 o posterior
- Adobe ID e ID de organización
- [Capa de datos del cliente de Adobe (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). La ACDL es necesaria para recopilar datos de evento de tienda.
- Derechos a otros productos DX de Adobe

## Pasos de incorporación

1. [Instalar](install.md) el [!DNL Data Connection] extensión.
1. [Iniciar sesión](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) a su cuenta de Adobe y [ver para confirmar](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) su ID de organización. El ID de organización es el ID asociado con la empresa de Experience Cloud aprovisionada. Se trata de una cadena alfanumérica de 24 caracteres seguida de (que debe incluirse) `@AdobeOrg`.
1. [Crear o actualizar](update-xdm.md) Cree su esquema XDM con grupos de campos específicos de Commerce.
1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) en función del esquema que haya creado o actualizado. Este conjunto de datos contiene los datos de Commerce que envía.
1. [Creación de una secuencia de datos](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de Commerce.
1. [Conectar con Commerce Services](../landing/saas.md).
1. [Conectar con Adobe Experience Platform](connect-data.md).

## Público

Esta guía está diseñada para el comerciante de Adobe Commerce que desea conectar sus datos de Adobe Commerce a otros productos DX de Adobe.

### soporte de PWA Studio

Consulte la [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) para obtener información acerca de cómo utilizar el [!DNL Data Connection] en una tienda de PWA Studio.

### AEM soporte de la {#aem-support}

Consulte la [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) AEM para obtener información sobre cómo enviar datos de evento de tienda desde una página de producto procesada por el usuario en el que el usuario es el Experience Platform CIF mediante el uso de la documentación de: [!DNL Data Connection] extensión.

Si necesita información o tiene preguntas que no se tratan en esta guía, utilice los siguientes recursos:

- [Centro de ayuda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Tickets de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Envíe un ticket para recibir ayuda adicional.