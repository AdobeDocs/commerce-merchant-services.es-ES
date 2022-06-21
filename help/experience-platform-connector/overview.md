---
title: Información general de guía
description: El conector de Adobe Experience Platform para Adobe Commerce conecta su [!DNL Commerce] a otros productos de Adobe Experience Cloud.
source-git-commit: dc4bb1ea7d2ffc953cca31637bf5aefba6266241
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Información general sobre el conector del Experience Platform

La extensión del conector del Experience Platform permite a los comerciantes de Adobe Commerce enviar datos al perímetro de Adobe Experience Platform para que otros productos de Adobe Experience Cloud, como Adobe Analytics y Adobe Target, puedan utilizarlos [!DNL Commerce] datos. Al conectar el [!DNL Commerce] con otros productos de Adobe Experience Cloud, puede realizar tareas como analizar el comportamiento del usuario en el sitio, realizar pruebas A/B y crear campañas personalizadas.

Los eventos de tienda capturan las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, etc. Los datos capturados no incluyen información de identificación personal (PII). Todos los identificadores de usuario, como los ID de cookie y las direcciones IP, se anonimizan estrictamente. [Más información](https://www.adobe.com/privacy/experience-cloud.html). Consulte la lista completa de [eventos de tienda](events.md).

## Requisitos previos para utilizar el conector del Experience Platform {#prereqs}

Para utilizar el conector del Experience Platform, primero debe:

- Complete lo siguiente [formulario](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) y Adobe le proporcionarán acceso a Datastreams y Adobe Experience Platform (si es necesario).

Cuando se concede el acceso:

1. [Iniciar sesión](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) a su cuenta de Adobe.
1. Mira tu [organización](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). El ID de organización es el ID asociado a la empresa Experience Cloud aprovisionada. Este ID es una cadena alfanumérica de 24 caracteres seguida de @AdobeOrg (que debe incluirse).
1. Acceda al espacio de trabajo del conjunto de datos y [crear un conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en).

El ID de organización y el conjunto de datos se utilizan al conectar la instancia de Adobe Commerce a Adobe Experience Platform.

## Pasos siguientes

- Instale el [Extensión de conector del Experience Platform](install.md).

   La extensión del conector del Experience Platform se instala desde la línea de comandos del servidor y se conecta a la instalación de Adobe Commerce como un [service](../landing/saas.md). Cuando se completa el proceso, aparece el conector del Experience Platform en la variable **Sistema** menú bajo **Servicios** en el [!DNL Commerce] _Administrador_.

## Audiencia

Esta guía está diseñada para el comerciante de Adobe Commerce que debe conectar sus datos de tienda de Adobe Commerce con otros productos DX de Adobe.

## Problemas conocidos

Actualmente, el conector del Experience Platform tiene los siguientes problemas conocidos:

- Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.
- Los datos de tienda tardan aproximadamente una hora en llegar de Adobe Commerce a los distintos destinos después de conectarse al perímetro de Adobe Experience Platform.

## Asistencia

Si necesita información o tiene preguntas que no están incluidas en esta guía, publique en el siguiente canal de Slack:

- `#beacon-ama`
