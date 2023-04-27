---
title: Conexión de datos de comercio a Adobe Experience Platform
description: Obtenga información sobre cómo conectar los datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Conexión de datos de Commerce a Adobe Experience Platform

Al instalar el conector del Experience Platform, aparecen dos páginas de configuración nuevas en la **Sistema** menú bajo **Servicios** en el comercio _Administrador_.

- Conector de Commerce Services
- Conector del Experience Platform

Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, debe configurar ambos conectores, empezando por el conector de Commerce Services y terminando con el conector del Experience Platform.

## Actualizar el conector de Commerce Services

Si ha instalado anteriormente un servicio de Adobe Commerce, probablemente ya haya configurado el conector de Commerce Services. Si no es así, debe completar las siguientes tareas en la [Conector de Commerce Services](../landing/saas.md) página:

1. Inicie sesión en su cuenta de comercio para [recupere las claves de la API de producción y del simulador de pruebas](../landing/saas.md#credentials).
1. Seleccione un [Espacio de datos SaaS](../landing/saas.md#saas-configuration).
1. Inicie sesión en su cuenta de Adobe para [recuperar el ID de organización](../landing/saas.md#ims-organization-optional).

Después de configurar el conector de Commerce Services, debe configurar el conector del Experience Platform.

## Actualización del conector del Experience Platform

En esta sección, debe conectar la instancia de Adobe Commerce a Adobe Experience Platform mediante el ID de su organización. A continuación, puede especificar el tipo de datos (tienda o back office) que se enviarán al perímetro del Experience Platform.

![Configuración del conector del Experience Platform](assets/epc-config-dc.png)

## General

1. Inicie sesión en su cuenta de Adobe en [Conector de Commerce Services](../landing/saas.md#organizationid) y seleccione su ID de organización.

   >[!NOTE]
   >
   >Si ha configurado anteriormente el conector de Commerce Services, puede omitir este paso, ya que su ID de organización ya se ha seleccionado.

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Ámbito** menú desplegable, establezca el contexto en **Sitio web**.

1. En el **ID de organización** , compruebe el ID asociado a su cuenta de Adobe Experience Platform, tal como se configura en la variable [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. (Opcional) Si ya tiene un [SDK web de AEP (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) implementado en su sitio, active la casilla de verificación y añada el nombre del SDK web de AEP. De lo contrario, deje estos campos en blanco y el conector del Experience Platform se implementará por usted.

   >[!NOTE]
   >
   >Si especifica su propio SDK web de AEP, el conector del Experience Platform utiliza el ID del conjunto de datos asociado a dicho SDK y no el ID del conjunto de datos especificado en esta página (si existe).

## Recopilación de datos

En el **Recopilación de datos** , seleccione los datos de tienda o back office para enviarlos al perímetro del Experience Platform. Para asegurarse de que la instancia de Adobe Commerce pueda empezar a recopilar datos, revise la [requisitos previos](overview.md#prerequisites).

Consulte el tema de eventos para obtener más información sobre [storefront](events.md#storefront-events) y [back office](events.md#back-office-events) eventos.

>[!NOTE]
>
>Todos los campos de la **Recopilación de datos** se aplican a la sección **Sitio web** o superior.

1. Select **Eventos de tienda** si desea enviar datos de comportamiento de tienda.

   >[!NOTE]
   >
   >La variable **Eventos de tienda** se activa automáticamente si el SDK web de AEP y el ID de organización son válidos.

1. Select **Eventos de back office** si desea enviar la información de estado del pedido, por ejemplo, si se ha realizado, cancelado, reembolsado o enviado un pedido.

   >[!NOTE]
   >
   >Si selecciona **Eventos de back office**, todos los datos de back office se envían al perímetro del Experience Platform. Si un comprador decide excluirse de la recopilación de datos, debe establecer explícitamente la preferencia de privacidad del comprador en el Experience Platform. Esto es diferente de los eventos de tienda en los que el recolector ya gestiona el consentimiento en función de las preferencias del comprador. [Más información](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) acerca de la configuración de la preferencia de privacidad de un comprador en el Experience Platform.

1. Para garantizar actualizaciones de datos de eventos de back-office basadas en una programación de acuerdo con un [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) trabajo, debe cambiar la `Sales Orders Feed` index to `Update by Schedule`.

   1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Seleccione la casilla de verificación para la variable `Sales Orders Feed` indexador.

   1. Establezca **[!UICONTROL Actions]** a `Update by Schedule`.

   1. Si está habilitando datos de back office por primera vez, ejecute los siguientes comandos para reindexar y déclencheur una resincronización. Las resincronizaciones posteriores se producen automáticamente siempre que la variable [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) el trabajo está configurado correctamente.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (Omita este paso si utiliza su propio SDK web de AEP). [Crear](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) un conjunto de datos en Adobe Experience Platform o seleccione un conjunto de datos existente que desee utilizar para la recopilación.

1. (Omita este paso si utiliza su propio SDK web de AEP). En el **ID de almacén de datos** , pegue el ID de ese conjunto de datos nuevo o existente.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Sitio web específico al que desea aplicar la configuración. |
| ID de organización (global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula la instancia de Adobe Commerce con Adobe Experience Platform. |
| ¿El SDK web de AEP ya está implementado en su sitio? | Seleccione esta casilla de verificación si ha implementado su propio SDK web de AEP en su sitio |
| Nombre del SDK web de AEP (global) | Si ya tiene un SDK web Experience Platform implementado en su sitio, especifique el nombre de ese SDK en este campo. Esto permite que el recopilador de eventos de tienda y el SDK de evento de tienda utilicen su SDK web de Experience Platform en lugar de la versión implementada por el conector del Experience Platform. Si no tiene un SDK web de Experience Platform implementado en su sitio, deje este campo en blanco y el conector de Experience Platform implemente uno por usted. |
| Eventos de tienda | Se selecciona de forma predeterminada siempre que el ID de organización y el ID de flujo de datos sean válidos. Los eventos de tienda recopilan datos de comportamiento anónimos de sus compradores a medida que navegan por el sitio. |
| Eventos de Back Office | Si se selecciona, la carga útil de evento contiene información de estado de pedido anónima, como si se ha realizado, cancelado, reembolsado o enviado un pedido. |
| ID de almacén de datos (sitio web) | ID que permite el flujo de datos de Adobe Experience Platform a otros productos DX de Adobe. Este ID debe estar asociado a un sitio web específico de la instancia de Adobe Commerce específica. Si especifica su propio SDK web de Experience Platform, no especifique un ID de conjunto de datos en este campo. El conector del Experience Platform utiliza el ID del almacén de datos asociado a dicho SDK e ignora cualquier ID del almacén de datos especificado en este campo (si existe). |

## Comprobar que se están enviando datos al Experience Platform

Después de la incorporación, los datos de tienda empiezan a fluir hasta el límite del Experience Platform. Los datos de back office tardan unos 5 minutos después de la incorporación para que aparezcan al final. Las actualizaciones posteriores son visibles en el perímetro en función de la programación cron.

Cuando los datos de comercio se envían al Experience Platform, puede crear informes como los siguientes:

![Datos de comercio en Adobe Experience Platform](assets/aem-data-1.png)
_Datos de comercio en Adobe Experience Platform_
