---
title: Conexión de datos de Commerce con Adobe Experience Platform
description: Aprenda a conectar sus datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Conexión de datos de Commerce con Adobe Experience Platform

Al instalar el conector del Experience Platform, aparecen dos nuevas páginas de configuración en la **Sistema** menú debajo de **Servicios** en el Commerce _Administrador_.

- Conector de Commerce Services
- Conector del Experience Platform

Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, debe configurar ambos conectores, empezando por el conector de Commerce Services y terminando por el conector de Experience Platform.

## Actualizar el conector de Commerce Services

Si ya ha instalado un servicio de Adobe Commerce, probablemente ya haya configurado el conector de Commerce Services. Si no es así, debe completar las siguientes tareas en la [Conector de Commerce Services](../landing/saas.md) página:

1. Inicie sesión en su cuenta de Commerce para [Recuperación de las claves API de producción y zona protegida](../landing/saas.md#credentials).
1. Seleccione una [Espacio de datos SaaS](../landing/saas.md#saas-configuration).
1. Inicie sesión en su cuenta de Adobe para [Recuperación del ID de organización](../landing/saas.md#ims-organization-optional).

Después de configurar el conector de Commerce Services, configure el conector del Experience Platform.

## Actualización del conector del Experience Platform

En esta sección, puede conectar la instancia de Adobe Commerce a Adobe Experience Platform mediante el ID de la organización. A continuación, puede especificar el tipo de datos (tienda o back office) que se enviarán al perímetro del Experience Platform.

![Configuración del conector del Experience Platform](assets/epc-config-dc.png)

## General

1. Inicie sesión en su cuenta de Adobe en [Conector de Commerce Services](../landing/saas.md#organizationid) y seleccione su ID de organización.

   >[!NOTE]
   >
   >Si ha configurado anteriormente el conector de Commerce Services, puede omitir este paso, ya que el ID de su organización ya se ha seleccionado.

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Ámbito** desplegable, establezca el contexto en **Sitio web**.

1. En el **ID de organización** , compruebe el ID asociado con su cuenta de Adobe Experience Platform, tal como se configura en la [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. (Opcional) Si ya tiene un [SDK web de AEP (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) Al implementarlo en el sitio, active la casilla de verificación y añada el nombre del SDK web de AEP. De lo contrario, deje estos campos en blanco y el conector del Experience Platform implementará uno por usted.

   >[!NOTE]
   >
   >Si especifica su propio SDK web de AEP, el conector del Experience Platform utiliza el ID de conjunto de datos asociado a ese SDK y no el ID de conjunto de datos especificado en esta página (si lo hay).

## Recopilación de datos

En esta sección, se especifica el tipo de datos que se desea enviar al perímetro del Experience Platform. Existen dos tipos de datos: del lado del cliente y del lado del servidor.

Los datos del lado del cliente son datos capturados en la tienda. Esto incluye las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, y [lista de solicitudes](events.md#b2b-events) información (para comerciantes B2B). Los datos del lado del servidor, o datos del back office, son datos capturados en los servidores de Commerce. Esto incluye información sobre el estado de un pedido, como si se ha realizado, cancelado, reembolsado, enviado o completado.

En el **Recopilación de datos** , seleccione el tipo de datos que desea enviar al perímetro del Experience Platform. Para asegurarse de que la instancia de Adobe Commerce puede comenzar la recopilación de datos, revise la [requisitos previos](overview.md#prerequisites).

Consulte el tema de eventos para obtener más información sobre [escaparate](events.md#storefront-events) y [back office](events.md#back-office-events) eventos.

>[!NOTE]
>
>Todos los campos del **Recopilación de datos** se aplican a la **Sitio web** ámbito o superior.

1. Seleccionar **Eventos de tienda** si desea enviar datos de comportamiento de la tienda.

   >[!NOTE]
   >
   >El **Eventos de tienda** La casilla de verificación se activa automáticamente si el SDK web de AEP y el ID de organización son válidos.

1. Seleccionar **Eventos de back office** si desea enviar información sobre el estado del pedido, por ejemplo, si se ha realizado, cancelado, reembolsado o enviado un pedido.

   >[!NOTE]
   >
   >Si selecciona **Eventos de back office**, todos los datos de back office se envían al perímetro del Experience Platform. Si un comprador decide excluirse de la recopilación de datos, debe establecer explícitamente la preferencia de privacidad del comprador en el Experience Platform. Esto es diferente a los eventos de tienda en los que el coleccionista ya gestiona el consentimiento en función de las preferencias del comprador. [Más información](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) acerca de la configuración de la preferencia de privacidad de un comprador en el Experience Platform.

1. Para garantizar que las actualizaciones de datos de eventos de back office se basen en una programación según un [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) trabajo, debe cambiar el `Sales Orders Feed` index a `Update by Schedule`.

   1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Seleccione la casilla de verificación del `Sales Orders Feed` indexador.

   1. Establecer **[!UICONTROL Actions]** hasta `Update by Schedule`.

   1. Si está habilitando los datos del back office por primera vez, ejecute los siguientes comandos para reindexar y almacenar en déclencheur una resincronización. Las resincronizaciones posteriores se producen automáticamente siempre que la variable [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) el trabajo está configurado correctamente.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (Omita este paso si utiliza su propio SDK web de AEP). [Crear](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Cree una secuencia de datos en Adobe Experience Platform o seleccione una secuencia de datos existente que desee utilizar para la recopilación.

1. (Omita este paso si utiliza su propio SDK web de AEP). En el **ID de flujo de datos** , pegue el ID de ese conjunto de datos nuevo o existente.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Sitio web específico donde desea aplicar los ajustes de configuración. |
| ID de organización (global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula su instancia de Adobe Commerce con Adobe Experience Platform. |
| ¿El SDK web de AEP ya está implementado en el sitio? | Seleccione esta casilla de verificación si ha implementado su propio SDK web de AEP en el sitio |
| Nombre del SDK web de AEP (global) | Si ya tiene un SDK web de Experience Platform implementado en el sitio, especifique el nombre de ese SDK en este campo. Esto permite que el Recopilador de eventos de tienda y el SDK de eventos de tienda utilicen el SDK web de Experience Platform en lugar de la versión implementada por el conector de Experience Platform. Si no tiene un SDK web de Experience Platform implementado en el sitio, deje este campo en blanco y el conector de Experience Platform lo implementa por usted. |
| Eventos de tienda | Está activada de forma predeterminada siempre que el ID de organización y el ID de flujo de datos sean válidos. Los eventos de tienda recopilan datos de comportamiento anónimos de sus compradores a medida que navegan por el sitio. |
| Eventos de Back Office | Si se selecciona, la carga útil de evento contiene información anónima del estado del pedido, como si se ha realizado, cancelado, reembolsado o enviado un pedido. |
| ID de flujo de datos (sitio web) | ID que permite que los datos fluyan desde Adobe Experience Platform a otros productos DX de Adobe. Este ID debe estar asociado a un sitio web específico dentro de la instancia de Adobe Commerce específica. Si especifica su propio SDK web de Experience Platform, no especifique ningún ID de flujo de datos en este campo. El conector del Experience Platform utiliza el ID de conjunto de datos asociado con ese SDK e ignora cualquier ID de conjunto de datos especificado en este campo (si lo hay). |

>[!NOTE]
>
>Después de la incorporación, los datos de la tienda comienzan a fluir al perímetro del Experience Platform. Los datos del back office tardan unos 5 minutos en aparecer en el perímetro. Las actualizaciones posteriores son visibles en el perímetro en función de la programación de cron.

## Confirmar que se recopilan los datos del evento

Para confirmar que se están recopilando datos de su tienda de Commerce, utilice el [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) para examinar su sitio de Commerce. Después de confirmar que se están recopilando datos, puede comprobar que los datos de evento de la tienda y del back office aparecen en el perímetro ejecutando una consulta que devuelva datos del [conjunto de datos creado](overview.md#prerequisites).

1. Seleccionar **Consultas** en la navegación izquierda del Experience Platform y haga clic en [!UICONTROL Create Query].

   ![Editor de consultas](assets/query-editor.png)

1. Cuando se abra el Editor de consultas, escriba una consulta que seleccione datos del conjunto de datos.

   ![Crear consulta](assets/create-query.png)

   Por ejemplo, la consulta podría tener el aspecto siguiente:

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Una vez ejecutada la consulta, los resultados se muestran en la variable **Resultados** , junto a la pestaña **Consola** pestaña. Esta vista muestra el resultado tabular de la consulta.

   ![Editor de consultas](assets/query-results.png)

En este ejemplo, se ven datos de evento de la variable [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview), etc. Esta vista le permite verificar que los datos de Commerce llegaron al límite.

Si los resultados no son los esperados, abra el conjunto de datos y busque las importaciones de lotes fallidas. Más información sobre [resolución de problemas de importaciones por lotes](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
