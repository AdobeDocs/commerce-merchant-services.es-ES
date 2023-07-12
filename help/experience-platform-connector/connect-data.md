---
title: Conexión de datos de Commerce con Adobe Experience Platform
description: Aprenda a conectar sus datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1484a465f3ce5b5578a7c5cf3f5f3b7d68d69c41
workflow-type: tm+mt
source-wordcount: '1952'
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

En esta sección, puede conectar la instancia de Adobe Commerce a Adobe Experience Platform mediante el ID de la organización. A continuación, puede especificar el tipo de datos (tienda y back office) que se enviarán al perímetro del Experience Platform.

![Configuración del conector del Experience Platform](assets/epc-config-dc.png)

## General

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. En el **Configuración** pestaña debajo de **General**, compruebe el ID asociado con su cuenta de Adobe Experience Platform, tal como se ha configurado en la [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. En el **Ámbito** desplegable, establezca el contexto en **Sitio web**.

1. (Opcional) Si ya tiene un [SDK web de AEP (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) Al implementarlo en el sitio, active la casilla de verificación y añada el nombre del SDK web de AEP. De lo contrario, deje estos campos en blanco y el conector del Experience Platform implementará uno por usted.

   >[!NOTE]
   >
   >Si especifica su propio SDK web de AEP, el conector del Experience Platform utiliza el ID de conjunto de datos asociado a ese SDK y no el ID de conjunto de datos especificado en esta página (si lo hay).

## Recopilación de datos

En esta sección, se especifica el tipo de datos que se desea enviar al perímetro del Experience Platform. Existen dos tipos de datos: del lado del cliente y del lado del servidor.

Los datos del lado del cliente son datos capturados en la tienda. Esto incluye las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, y [lista de solicitudes](events.md#b2b-events) información (para comerciantes B2B). Los datos del lado del servidor, o datos del back office, son datos capturados en los servidores de Commerce. Esto incluye información sobre el estado de un pedido, como si se ha realizado, cancelado, reembolsado, enviado o completado.

Para asegurarse de que la instancia de Adobe Commerce puede comenzar la recopilación de datos, revise la [requisitos previos](overview.md#prerequisites).

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
>Después de la incorporación, los datos de la tienda comienzan a fluir al perímetro del Experience Platform. Los datos del back office tardan unos cinco minutos en aparecer en el perímetro. Las actualizaciones posteriores son visibles en el perímetro en función de la programación de cron.

## (Beta) Enviar datos de pedidos históricos

>[!NOTE]
>
>Esta función solo está disponible para usuarios beta. Puede unirse a la versión beta enviando un correo electrónico a la siguiente dirección: [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Adobe Commerce recopila hasta cinco años de datos y estado de pedidos históricos. Puede utilizar el conector del Experience Platform para enviar esos datos históricos al Experience Platform y enriquecer los perfiles de cliente en función de esos pedidos anteriores. Los datos se almacenan en un conjunto de datos dentro de Experience Platform.

Aunque Commerce ya recopila los datos del pedido histórico, hay varias tareas que debe completar para enviar esos datos a Experience Platform. Las siguientes secciones le guían a través del proceso.

### Instalar pedido beta histórico

Para habilitar la recopilación de datos de pedidos históricos para la versión beta, debe actualizar la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Abra la raíz `composer.json` archivo y buscar `magento/experience-platform-connector`.

1. En el `require` , actualice el número de versión como se indica a continuación:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0.0-beta1",
      ...
    }
   ```

1. Para los comerciantes B2B, actualice el `.json` como se indica a continuación:

   ```json
   "require": {
     ...
     "magento/experience-platform-connector-b2b": "^2.0.0-beta1"
     ...
   }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   o, para los comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

### Configuración del pedido beta histórico

Para asegurarse de que el historial de pedidos de los clientes se puede enviar al Experience Platform, debe especificar las credenciales que vinculan la instancia de Commerce al Experience Platform. Si ya ha instalado y habilitado el [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) extensión, ya ha especificado las credenciales necesarias y puede omitir este paso. Si aún no ha instalado y habilitado la extensión de Audience Activation, complete los siguientes pasos:

>[!NOTE]
>
>En esta sección, introduzca las credenciales de la consola de desarrollador. Asegúrese de que el proyecto de la consola del desarrollador tenga el [funciones y permisos configurados](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.

1. Expandir **[!UICONTROL Services]** y seleccione **[!UICONTROL Experience Platform Connector]**.

1. Introduzca las credenciales de configuración que se encuentran en la [consola para desarrolladores](https://developer.adobe.com/console/home).

   ![Configuración de administración del conector del Experience Platform](./assets/epc-admin-config.png){width="700" zoomable="yes"}

   >[!NOTE]
   >
   >Para la versión beta, Commerce utiliza credenciales de tokens web JSON (JWT) en Developer Console. Después de la versión beta, Commerce utilizará OAuth 2.0 en Developer Console.

1. Clic **Guardar configuración**.

### Configuración del servicio de sincronización de pedidos

Después de introducir las credenciales del desarrollador, puede configurar el servicio de sincronización de pedidos. El servicio de sincronización de pedidos utiliza el [Marco de cola de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/) y RabbitMQ. Después de completar estos pasos, los datos de estado de los pedidos se pueden sincronizar con SaaS, que es necesario antes de enviarlos al Experience Platform.

1. [Activar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >RabbitMQ ya está configurado para las versiones de Commerce 2.4.7 y posteriores, pero debe habilitar a los consumidores.

1. Habilitar consumidores de cola de mensajes mediante el trabajo cron en `.magento.env.yaml` usando `CRON_CONSUMERS_RUNNER` variable de entorno.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Consulte la [documentación de implementación de variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) para obtener más información sobre todas las opciones de configuración disponibles.

Con el servicio de sincronización de pedidos habilitado, puede especificar el intervalo de fechas de pedidos histórico en la página de conector del Experience Platform.

### Especificar intervalo de fechas del historial de pedidos

En esta sección, especifique el intervalo de fechas para los pedidos históricos que desea enviar al Experience Platform.

![Historial de pedidos de sincronización](./assets/order-history.png){width="700" zoomable="yes"}

1. En el Administrador, vaya a **Sistema** > Servicios > **Conector del Experience Platform**.

1. Seleccione el **Historial de pedidos** pestaña.

1. En **Sincronización del historial de pedidos**, introduzca la variable **ID de conjunto de datos**. Debe ser el mismo conjunto de datos asociado al conjunto de datos especificado en la variable [recopilación de datos](#data-collection) sección anterior.

   1. Para acceder al ID del conjunto de datos, abra la interfaz de usuario del Experience Platform y seleccione **Conjuntos de datos** en el panel de navegación izquierdo para abrir **Conjuntos de datos** panel. El panel enumera todos los conjuntos de datos disponibles para su organización. Se muestran los detalles de cada conjunto de datos enumerado, incluido su nombre, el esquema al que se adhiere y el estado de la ejecución de la ingesta más reciente.
   1. Abra el conjunto de datos asociado al conjunto de datos.
   1. En el panel derecho, verá detalles sobre el conjunto de datos. Copie el ID del conjunto de datos.

   ![Copiar ID de conjunto de datos](./assets/retrieve-dataset-id.png){width="700" zoomable="yes"}

1. En el **Desde** y **Hasta** Los campos especifican el rango de datos para los datos de pedidos históricos que desea enviar. No puede seleccionar un intervalo de fecha que exceda de cinco años.

1. Seleccionar [!UICONTROL Start Sync] para almacenar en déclencheur la sincronización para comenzar. Los datos históricos de pedidos son datos por lotes, a diferencia de los datos de la tienda y el back office que transmiten los datos. Los datos por lotes tardan unos 45 minutos en llegar a Experience Platform.

   >[!NOTE]
   >
   >En la versión beta, si almacena en déclencheur una sincronización varias veces en el mismo intervalo de tiempo o en un intervalo de tiempo superpuesto, verá eventos duplicados en el conjunto de datos.

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
