---
title: Integración del SDK de Adobe Experience Platform Mobile con Commerce
description: Aprenda a utilizar el SDK de Adobe Experience Platform Mobile con su tienda de comercio personalizada o sin encabezado.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 2afe6d36ada662500f5a4a08779664d6591271e8
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Integración del SDK de Adobe Experience Platform Mobile con Commerce

>[!IMPORTANT]
>
>El SDK de Adobe Experience Platform Mobile para iOS es compatible con iOS 11 o posterior.

Integración de [SDK de Adobe Experience Platform Mobile](https://developer.adobe.com/client-sdks/home/) con la aplicación móvil de Commerce permite a los comerciantes enviar contenido comercial  [datos de evento](events.md) hasta el borde Experience Platform.

Cuando los datos de evento de Commerce están disponibles en el perímetro, otras aplicaciones de Adobe Experience Cloud pueden acceder a ellos. Por ejemplo, puede utilizar los datos para crear audiencias en Real-Time CDP y luego [usar esas audiencias](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) para personalizar su aplicación móvil de Commerce.

## Configuración

Para empezar a utilizar el SDK de Adobe Experience Platform Mobile con Commerce, instale y configure el SDK en el Experience Platform. A continuación, finalice la configuración en Commerce.

### Experience Platform

1. Obtenga información acerca de las funcionalidades de la aplicación móvil revisando la [Tutorial de Adobe Experience Cloud en aplicaciones móviles](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Instalación y configuración](https://developer.adobe.com/client-sdks/documentation/getting-started/) el SDK en el Experience Platform.

   >[!NOTE]
   >
   >El esquema que cree y configure en el Experience Platform es el mismo esquema que utiliza en el código de la aplicación en la aplicación móvil de Commerce.

### Comercio

Una vez completada la configuración del SDK para Experience Platform, añada la configuración del SDK a Commerce.

1. Para enviar datos de evento de comercio al Experience Platform mediante el SDK, debe proporcionar un esquema XDM en el código de la aplicación. Este esquema debe coincidir con el esquema [configurado](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) para el SDK en el Experience Platform.

   El siguiente ejemplo muestra cómo realizar un seguimiento de la variable `web.webpagedetails.pageViews` y configure el `identityMap` uso del campo de correo electrónico.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Conéctese al entorno de Commerce Cloud.

   En la configuración de compilación del proyecto, agregue la URL al extremo de Commerce GraphQL. Por ejemplo:

   - Depurar: http://_depurar_.commerce.cloud/graphql/
   - Versión: http://_versión_.commerce.cloud/graphql/

1. Para recuperar datos de los extremos de Commerce GraphQL, genere primero los archivos y directorios necesarios en el proyecto utilizando [Generador de códigos Apollo](https://www.apollographql.com/docs/ios/).

   1. Desde el directorio del proyecto, [instalar](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apolo iOS.

   1. [Inicializar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) la CLI de Apollo Codegen.

      Esto crea un `apollo-codegen-configuration.json` archivo.

   1. Genere los archivos y directorios GraphQL necesarios en su proyecto reemplazando el contenido del `apollo-codegen-configuration.json` archivo con lo siguiente:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Buscar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) el esquema de Commerce GraphQL.

      Asegúrese de que la ruta es a `./apollo-codegen-config.json` , que contiene la referencia al esquema de Commerce GraphQL.

   1. [Generar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) el código fuente.

      Asegúrese de que la ruta es a `./apollo-codegen-config.json` , que contiene la información de configuración para generar los archivos y directorios necesarios.

   1. Dentro del recién creado **GraphQLGenerated** , agregue o edite tipos de GraphQL. Por ejemplo, puede agregar un `DynamicBlocks.graphql` escriba con el siguiente contenido:

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Ahora ha integrado el SDK móvil de Adobe Experience Platform con su aplicación móvil de Commerce. Los datos de eventos fluyen desde la aplicación al perímetro del Experience Platform.

Para obtener información sobre cómo recuperar audiencias de Real-Time CDP desde la aplicación de comercio móvil e informar sobre reglas de precios del carro de compras y bloques dinámicos, consulte [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
