---
title: Información general de guía
description: Obtenga información sobre cómo integrar datos de Adobe Commerce con Adobe Experience Platform mediante el conector del Experience Platform.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: c9b1d7e34632f7a54544bc6944144b1833ecc5a5
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Información general sobre el conector del Experience Platform

La extensión del conector del Experience Platform permite a los comerciantes de Adobe Commerce enviar datos al perímetro de Adobe Experience Platform para que otros productos de Adobe Experience Cloud, como Adobe Analytics y Adobe Target, puedan utilizar esos datos de comercio. Al conectar los datos de comercio con otros productos de Adobe Experience Cloud, puede realizar tareas como analizar el comportamiento de los usuarios en el sitio, realizar pruebas A/B y crear campañas personalizadas.

[Eventos de tienda](events.md) capturar interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, etc. Los datos capturados no incluyen información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html).

El conector del Experience Platform aparece en el administrador de comercio, en **Sistema** > Servicios > **Conector del Experience Platform**.

![Extensión del conector del Experience Platform Vista de administración](assets/epc-adminui.png)

## Requisitos previos {#prereqs}

Para utilizar el conector del Experience Platform, debe tener lo siguiente:

- Adobe Commerce 2.4.3 o posterior
- Adobe ID e ID de organización
- Derechos a otros productos DX de Adobe

## Pasos de incorporación

1. [Instalar](install.md) la extensión del conector del Experience Platform.
1. [Iniciar sesión](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) a su cuenta de Adobe y [ver](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) su ID de organización. El ID de organización es el ID asociado a la empresa Experience Cloud aprovisionada. Este ID es una cadena alfanumérica de 24 caracteres seguida de (que debe incluir) `@AdobeOrg`.
1. [Connect](connect-data.md) la instancia de Adobe Commerce en Adobe Experience Platform.
1. [Crear o actualizar](update-xdm.md) el esquema XDM con grupos de campos específicos de comercio.
1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basado en el esquema creado o actualizado.
1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) y seleccione el esquema XDM que contiene los grupos de campos específicos de comercio.
1. (Opcional) [Cargar perfiles del comprador](profile.md) a Adobe Experience Platform, de modo que los datos de tienda se puedan atribuir a compradores específicos para mejorar su experiencia de compra.

## Audiencia

Esta guía está diseñada para el comerciante de Adobe Commerce que desea conectar sus datos de Adobe Commerce a otros productos DX de Adobe.

### asistencia al PWA Studio

Consulte la [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentación para obtener información sobre cómo utilizar el conector de Experience Platform en una tienda de PWA Studio.

### AEM {#aem-support}

Consulte la [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentación para aprender a enviar datos de evento de tienda desde una página de producto procesada AEM al Experience Platform mediante el conector CIF - Experience Platform.

Si necesita información o tiene preguntas que no están incluidas en esta guía, utilice los siguientes recursos:

- [Centro de ayuda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Entradas de soporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}: envíe un ticket para recibir ayuda adicional.
