---
title: Información general de guía
description: El conector de Adobe Experience Platform para Adobe Commerce conecta la instancia de Commerce con otros productos de Adobe Experience Cloud.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2fb44e73a76ad4e1433b2abd88be1304e7e10596
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Información general sobre el conector del Experience Platform

La extensión del conector del Experience Platform permite a los comerciantes de Adobe Commerce enviar datos al perímetro de Adobe Experience Platform para que otros productos de Adobe Experience Cloud, como Adobe Analytics y Adobe Target, puedan utilizar esos datos de comercio. Al conectar los datos de comercio con otros productos de Adobe Experience Cloud, puede realizar tareas como analizar el comportamiento de los usuarios en el sitio, realizar pruebas A/B y crear campañas personalizadas.

Los eventos de tienda capturan las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, etc. Los datos capturados no incluyen información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html). Consulte la lista completa de [eventos de tienda](events.md).

El conector del Experience Platform aparece en el administrador de comercio, en **Sistema** > Servicios > **Conector del Experience Platform**.

![Extensión del conector del Experience Platform Vista de administración](assets/epc-adminui.png)

## Requisitos previos para utilizar el conector del Experience Platform {#prereqs}

Para utilizar el conector del Experience Platform, primero debe:

- Complete lo siguiente [formulario](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) y Adobe le proporcionarán acceso a Datastreams y Adobe Experience Platform (si es necesario).

Cuando se concede el acceso:

1. [Iniciar sesión](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) a su cuenta de Adobe.
1. Mira tu [organización](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). El ID de organización es el ID asociado a la empresa Experience Cloud aprovisionada. Este ID es una cadena alfanumérica de 24 caracteres seguida de (que debe incluir) `@AdobeOrg`.
1. Cree o actualice su [Esquema XDM](update-xdm.md) con grupos de campos específicos de comercio.
1. [Crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) y seleccione el esquema XDM que contiene el específico de comercio **Grupos de campos**.

>[!NOTE]
>
> El ID de organización y el conjunto de datos se utilizan para conectar la instancia de Adobe Commerce a Adobe Experience Platform.

## Pasos siguientes

- Instale el [Extensión de conector del Experience Platform](install.md).

   La extensión del conector del Experience Platform se instala desde la línea de comandos del servidor y se conecta a la instalación de Adobe Commerce como un [service](../landing/saas.md). Cuando se completa el proceso, aparece el conector del Experience Platform en la variable **Sistema** menú bajo **Servicios** en el comercio _Administrador_.
- [Cargar perfiles del comprador](profile.md) a Adobe Experience Platform, de modo que los datos de tienda se puedan atribuir a compradores específicos para mejorar su experiencia de compra.

## Audiencia

Esta guía está diseñada para el comerciante de Adobe Commerce que debe conectar sus datos de tienda de Adobe Commerce con otros productos DX de Adobe.

### asistencia al PWA Studio

Consulte la [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentación para obtener información sobre cómo utilizar el conector de Experience Platform en una tienda de PWA Studio.

## Problemas conocidos

Actualmente, el conector del Experience Platform tiene los siguientes problemas conocidos:

- Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.
- Los datos de tienda tardan aproximadamente una hora en llegar de Adobe Commerce a los distintos destinos después de conectarse al perímetro de Adobe Experience Platform.

Si necesita información o tiene preguntas que no están incluidas en esta guía, utilice los siguientes recursos:

- [Centro de ayuda](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [Entradas de soporte](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;}: envíe un ticket para recibir ayuda adicional.
