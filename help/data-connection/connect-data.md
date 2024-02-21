---
title: Conexión de datos de Commerce con Adobe Experience Platform
description: Aprenda a conectar sus datos de Commerce a Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 655b5d18a4fb77232523c9c18a9fb362de93c70a
workflow-type: tm+mt
source-wordcount: '2501'
ht-degree: 0%

---

# Conexión de datos de Commerce con Adobe Experience Platform

Al instalar el [!DNL Data Connection] extensión, aparecen dos nuevas páginas de configuración en la **Sistema** menú debajo de **Servicios** en el Commerce _Administrador_.

- Conector de Commerce Services
- [!DNL Data Connection]

Para conectar la instancia de Adobe Commerce a Adobe Experience Platform, debe configurar ambos conectores, empezando por el conector de Commerce Services y terminando por el [!DNL Data Connection] extensión.

## Configuración del conector de Commerce Services

Si ya ha instalado un servicio de Adobe Commerce, probablemente ya haya configurado el conector de Commerce Services. Si no es así, debe completar las siguientes tareas en la [Conector de Commerce Services](../landing/saas.md) página:

1. Inicie sesión en su cuenta de Commerce para [Recuperación de las claves API de producción y zona protegida](../landing/saas.md#credentials).
1. Seleccione una [Espacio de datos SaaS](../landing/saas.md#saas-configuration).
1. Inicie sesión en su cuenta de Adobe para [Recuperación del ID de organización](../landing/saas.md#ims-organization-optional).

Después de configurar el conector de Commerce Services, configure las variables [!DNL Data Connection] extensión.

## Configure las variables [!DNL Data Connection] extensión

En esta sección, aprenderá a configurar el [!DNL Data Connection] extensión.

### Agregar detalles de cuenta de servicio y credenciales

Si planea recopilar y enviar [datos de pedidos históricos](#send-historical-order-data) o [Datos de perfil del cliente (Beta)](#send-customer-profile-data), debe agregar los detalles de cuenta de servicio y credenciales. Además, si está configurando la variable [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) extensión, debe completar estos pasos.

Si solo recopila y envía datos de tienda o de back office, puede ir al [general](#general) sección.

#### Paso 1: Crear un proyecto en la consola de Adobe Developer

Cree un proyecto en la consola de Adobe Developer que autentique Commerce para poder realizar llamadas a la API de Experience Platform.

Para crear el proyecto, siga los pasos descritos en la sección [Autenticación y acceso a las API de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) tutorial.

A medida que avance en el tutorial, asegúrese de que su proyecto tenga lo siguiente:

- Acceso a lo siguiente [perfiles de producto](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **Acceso a todo de producción predeterminado** y **Acceso completo predeterminado de AEP**.
- La correcta [funciones y permisos están configurados](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- Si ha decidido utilizar JSON Web Tokens (JWT) como método de autenticación de servidor a servidor, también debe cargar una clave privada.

El resultado de este paso crea un archivo de configuración que se utiliza en el siguiente paso.

#### Paso 2: Descargar archivo de configuración

Descargue la [archivo de configuración de workspace](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Copie y pegue el contenido de este archivo en **Detalles de cuenta de servicio/credencial** de la administración de Commerce.

1. En el Administrador de comercio, navegue hasta **Tiendas** > Configuración > **Configuración** > **Servicios** > **[!DNL Data Connection]**.

1. Seleccione el método de autorización de servidor a servidor que implementó desde el **Tipo de autorización de Adobe Developer** menú. Adobe recomienda utilizar OAuth. JWT se ha desaprobado. [Más información](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (Solo JWT) Copie y pegue el contenido de su `private.key` en el archivo **Secreto del cliente** field. Utilice el siguiente comando para copiar el contenido.

   ```bash
   cat config/private.key | pbcopy
   ```

   Consulte [Autenticación de cuenta de servicio (JWT)](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) para obtener más información sobre `private.key` archivo.

1. Copie el contenido del `<workspace-name>.json` en el archivo **Detalles de cuenta de servicio/credencial** field.

   ![[!DNL Data Connection] Configuración de administración](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Clic **Guardar configuración**.

### General

1. En el Administrador, vaya a **Sistema** > Servicios > **[!DNL Data Connection]**.

1. En el **Configuración** pestaña debajo de **General**, compruebe el ID asociado con su cuenta de Adobe Experience Platform, tal como se ha configurado en la [Conector de Commerce Services](../landing/saas.md#organizationid). El ID de organización es global. Solo se puede asociar un ID de organización por cada instancia de Adobe Commerce.

1. En el **Ámbito** desplegable, establezca el contexto en **Sitio web**.

1. (Opcional) Si ya tiene un [SDK web de AEP (alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) Al implementarlo en el sitio, active la casilla de verificación y añada el nombre del SDK web de AEP. De lo contrario, deje estos campos en blanco y la variable [!DNL Data Connection] La extensión de implementa una para usted.

   >[!NOTE]
   >
   >Si especifica su propio SDK web de AEP, la variable [!DNL Data Connection] La extensión de utiliza el ID de flujo de datos asociado con ese SDK y no el ID de flujo de datos especificado en esta página (si lo hay).

### Recopilación de datos

En esta sección, especifique el tipo de datos que desea recopilar y enviar al perímetro del Experience Platform. Existen tres tipos de datos:

- **Comportamiento** (datos del lado del cliente) son datos capturados en la tienda. Esto incluye las interacciones del comprador, como `View Page`, `View Product`, `Add to Cart`, y [lista de solicitudes](events.md#b2b-events) información (para comerciantes B2B).

- **Back office** (datos del lado del servidor) son datos capturados en los servidores de Commerce. Esto incluye información sobre el estado de un pedido, como si se ha realizado, cancelado, reembolsado, enviado o completado. También incluye [datos de pedidos históricos](#send-historical-order-data).

- (**Beta**) **Perfil** son datos relacionados con la información de perfil del comprador. Aprender [más](#send-customer-profile-data).

Para asegurarse de que la instancia de Adobe Commerce puede comenzar la recopilación de datos, revise la [requisitos previos](overview.md#prerequisites).

Consulte el tema de eventos para obtener más información sobre [escaparate](events.md#storefront-events), [back office](events-backoffice.md), y [perfil](events-backoffice.md#customer-profile-events-server-side) eventos.

>[!NOTE]
>
>Todos los campos del **Recopilación de datos** se aplican a la **Sitio web** ámbito o superior.

1. Seleccionar **Eventos de tienda** si desea enviar datos de comportamiento de la tienda.

1. Seleccionar **Eventos de back office** si desea enviar información sobre el estado del pedido, por ejemplo, si se ha realizado, cancelado, reembolsado o enviado un pedido.

   >[!NOTE]
   >
   >Si selecciona **Eventos de back office**, todos los datos de back office se envían al perímetro del Experience Platform. Si un comprador decide excluirse de la recopilación de datos, debe establecer explícitamente la preferencia de privacidad del comprador en el Experience Platform. Esto es diferente a los eventos de tienda en los que el coleccionista ya gestiona el consentimiento en función de las preferencias del comprador. Aprender [más](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) acerca de la configuración de la preferencia de privacidad de un comprador en el Experience Platform.

1. (Omita este paso si utiliza su propio SDK web de AEP). [Crear](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) Cree una secuencia de datos en Adobe Experience Platform o seleccione una secuencia de datos existente que desee utilizar para la recopilación. Introduzca el ID de la secuencia de datos en **ID de flujo de datos** field.

1. Introduzca el **ID de conjunto de datos** que desea que contenga los datos de Commerce. Para encontrar la ID del conjunto de datos:

   1. Abra la interfaz de usuario del Experience Platform y seleccione **Conjuntos de datos** en el panel de navegación izquierdo para abrir **Conjuntos de datos** panel. El panel enumera todos los conjuntos de datos disponibles para su organización. Se muestran los detalles de cada conjunto de datos enumerado, incluido su nombre, el esquema al que se adhiere y el estado de la ejecución de la ingesta más reciente.
   1. Abra el conjunto de datos asociado al conjunto de datos.
   1. En el panel derecho, vea los detalles sobre el conjunto de datos. Copie el ID del conjunto de datos.

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

#### Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Ámbito | Sitio web específico donde desea aplicar los ajustes de configuración. |
| ID de organización (global) | ID que pertenece a la organización que compró el producto Adobe DX. Este ID vincula su instancia de Adobe Commerce con Adobe Experience Platform. |
| ¿El SDK web de AEP ya está implementado en el sitio? | Seleccione esta casilla de verificación si ha implementado su propio SDK web de AEP en el sitio |
| Nombre del SDK web de AEP (global) | Si ya tiene un SDK web de Experience Platform implementado en el sitio, especifique el nombre de ese SDK en este campo. Esto permite que el Recopilador de eventos de tienda y el SDK de eventos de tienda utilicen el SDK web de Experience Platform en lugar de la versión implementada por el [!DNL Data Connection] extensión. Si no tiene un SDK web de Experience Platform implementado en el sitio, deje este campo vacío y la variable [!DNL Data Connection] La extensión de implementa una para usted. |
| Eventos de tienda | Está activada de forma predeterminada siempre que el ID de organización y el ID de flujo de datos sean válidos. Los eventos de tienda recopilan datos de comportamiento anónimos de sus compradores a medida que navegan por el sitio. |
| Eventos de back office | Si se selecciona, la carga útil de evento contiene información anónima del estado del pedido, como si se ha realizado, cancelado, reembolsado o enviado un pedido. |
| ID de flujo de datos (sitio web) | ID que permite que los datos fluyan desde Adobe Experience Platform a otros productos DX de Adobe. Este ID debe estar asociado a un sitio web específico dentro de la instancia de Adobe Commerce específica. Si especifica su propio SDK web de Experience Platform, no especifique ningún ID de flujo de datos en este campo. El [!DNL Data Connection] La extensión de utiliza el ID de flujo de datos asociado con ese SDK e ignora cualquier ID de flujo de datos especificado en este campo (si lo hay). |
| ID del conjunto de datos (sitio web) | ID del conjunto de datos que contiene los datos de Commerce. Este campo es obligatorio a menos que haya anulado la selección del campo **Eventos de tienda** o **Eventos de back office** casillas de verificación. Además, si utiliza su propio SDK web de Experience Platform y, por lo tanto, no especificó un ID de conjunto de datos, debe agregar el ID del conjunto de datos asociado a su conjunto de datos. De lo contrario, no podrá guardar este formulario. |

Después de la incorporación, los datos de la tienda comienzan a fluir al perímetro del Experience Platform. Los datos del back office tardan unos cinco minutos en aparecer en el perímetro. Las actualizaciones posteriores son visibles en el perímetro en función de la programación de cron.

### Envío de datos de perfil de cliente

>[!IMPORTANT]
>
>Esta función está en versión beta. Si desea unirse al programa beta, envíe una solicitud a [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Existen dos tipos de datos de perfil que puede enviar al Experience Platform: registros de perfil y eventos de perfil de series temporales.

Un registro de perfil contiene datos que se guardan cuando un comprador crea un perfil en su instancia de Commerce, como el nombre del comprador. Cuando el esquema y el conjunto de datos estén [configurado correctamente](profile-data.md), se envía un registro de perfil al Experience Platform y se reenvía al servicio de segmentación y administración de perfiles de Adobe: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

Los eventos de perfil de series temporales contienen datos sobre la información de perfil del comprador; por ejemplo, si crean, editan o eliminan una cuenta del sitio. Cuando los datos de evento de perfil se envían al Experience Platform, residen en un conjunto de datos donde otros productos DX pueden utilizarlos.

1. Asegúrese de que tiene [proporcionado](#add-service-account-and-credential-details) cuenta de servicio y detalles de credenciales.

1. Asegúrese de tener un esquema y un conjunto de datos especificados para [ingesta de datos de registro de perfil](profile-data.md) y [ingesta de datos de eventos de perfil de series temporales](update-xdm.md#time-series-profile-event-data).

1. Coloque una marca de verificación en **Perfiles de cliente** casilla de verificación si desea enviar datos de perfil al Experience Platform.

1. Introduzca el **ID de conjunto de datos de perfil**.

   Los datos del registro de perfil deben utilizar un conjunto de datos diferente al que utiliza actualmente para los datos de evento de comportamiento y de back office.

1. Si no desea transmitir eventos de perfil a través del mismo ID de flujo de datos que utiliza para los datos de comportamiento y de back office, quite la marca de la etiqueta **Transmitir perfiles de clientes a través del mismo ID de flujo de datos** e introduzca el ID de la secuencia de datos que desee utilizar en su lugar.

Un registro de perfil puede tardar unos 10 minutos en estar disponible en Real-Time CDP. Los eventos de perfil comienzan a transmitirse inmediatamente.

#### Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Perfiles de cliente | Seleccione esta casilla de verificación si desea recopilar y enviar registros de perfil de cliente. |
| ID de conjunto de datos de perfil | Un registro de perfil debe utilizar un conjunto de datos diferente al conjunto de datos utilizado para los eventos de comportamiento y back office. |
| Transmitir perfiles de clientes a través del mismo ID de flujo de datos | Decida si desea utilizar el mismo conjunto de datos que se utiliza actualmente para sus eventos de comportamiento y de back office o no. |
| Flujo de datos para perfiles de clientes | Especifique el conjunto de datos específico del registro de perfil del cliente. |

### Enviar datos de pedidos históricos

Adobe Commerce recoge hasta cinco años de [datos y estado de pedidos históricos](events-backoffice.md#back-office-events). Puede usar el complemento [!DNL Data Connection] para enviar esos datos históricos al Experience Platform y enriquecer los perfiles de clientes y personalizar las experiencias de los clientes en función de esos pedidos anteriores. Los datos se almacenan en un conjunto de datos dentro de Experience Platform.

Aunque Commerce ya recopila los datos de pedidos históricos, hay que completar varios pasos para enviar esos datos a Experience Platform.

Vea este vídeo para obtener más información sobre los pedidos históricos y, a continuación, complete los siguientes pasos para implementar la recopilación de pedidos históricos.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### Configuración del servicio de sincronización de pedidos

El servicio de sincronización de pedidos utiliza el [Marco de cola de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/) y RabbitMQ. Después de completar estos pasos, los datos de estado de los pedidos se pueden sincronizar con SaaS, que es necesario antes de enviarlos al Experience Platform.

1. Asegúrese de que tiene [proporcionado](#add-service-account-and-credential-details) cuenta de servicio y detalles de credenciales.

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

Con el servicio de sincronización de pedidos habilitado, puede especificar el intervalo de fechas de pedidos histórico en la variable **[!UICONTROL [!DNL Data Connection]]** página.

#### Especificar intervalo de fechas del historial de pedidos

Especifique el intervalo de fechas para los pedidos históricos que desea enviar al Experience Platform.

1. En el Administrador, vaya a **Sistema** > Servicios > **[!DNL Data Connection]**.

1. Seleccione el **Historial de pedidos** pestaña.

1. En **Sincronización del historial de pedidos**, el **Copiar ID de conjunto de datos de configuración** La casilla de verificación ya está activada. Esto garantiza que utilice el mismo conjunto de datos especificado en la variable **Configuración** pestaña.

1. En el **Desde** y **Hasta** , especifique el intervalo de fechas para los datos de pedidos históricos que desea enviar. No puede seleccionar un intervalo de fecha que exceda de cinco años.

1. Seleccionar **[!UICONTROL Start Sync]** para almacenar en déclencheur la sincronización para comenzar. Los datos históricos de pedidos son datos por lotes, a diferencia de los datos de la tienda y el back office que transmiten los datos. Los datos por lotes tardan unos 45 minutos en llegar a Experience Platform.

##### Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Copiar ID de conjunto de datos de configuración | Copia el ID del conjunto de datos introducido en el **Configuración** pestaña. |
| ID del conjunto de datos (sitio web) | ID del conjunto de datos que contiene los datos de Commerce. Este campo es obligatorio a menos que haya anulado la selección del campo **Eventos de tienda** o **Eventos de back office** casillas de verificación. Además, si utiliza su propio SDK web de Experience Platform y, por lo tanto, no especificó un ID de conjunto de datos, debe agregar el ID del conjunto de datos asociado a su conjunto de datos. De lo contrario, no podrá guardar este formulario. |
| Desde | Fecha a partir de la cual desea empezar a recopilar datos del historial de pedidos. |
| Hasta | Fecha a partir de la cual desea finalizar la recopilación de datos del historial de pedidos. |
| Iniciar sincronización | Inicia el proceso de sincronización de los datos del historial de pedidos con el perímetro del Experience Platform. Este botón está desactivado si la variable **[!UICONTROL Dataset ID]** El campo está en blanco o la ID del conjunto de datos no es válida. |

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

## Pasos siguientes

Cuando los datos de Commerce se envían al perímetro de Experience Platform, otros productos de Adobe Experience Cloud, como Adobe Journey Optimizer, pueden utilizar esos datos. Por ejemplo, puede configurar Journey Optimizer para que escuche ciertos eventos y, en función de esos datos de evento, almacenar en déclencheur un correo electrónico para un usuario primerizo o si hay un carro de compras abandonado. Descubra cómo puede ampliar su plataforma de Commerce mediante [creación de recorridos de cliente](using-ajo.md) en Journey Optimizer.
