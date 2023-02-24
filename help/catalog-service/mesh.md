---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] para Adobe Commerce proporciona una forma de integrar varias fuentes de datos a través de un extremo común de GraphQL."'
source-git-commit: bdceeeeb1ed58c4ffbc87bee24c1eb3754b1cde9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

La variable [Mesh de API para Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe I/O Runtime.

![Diagrama de arquitectura del catálogo](assets/catalog-service-architecture-mesh.png)

El primer paso para utilizar la red de API con el servicio de catálogo es conectar la red de API a su instancia. Consulte las instrucciones detalladas en [Crear una red](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Para completar la configuración, instale la variable [Paquete CLI de Adobe Developer](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Una vez que Mesh está configurado en Adobe I/O Runtime, ejecute el siguiente comando que agrega una `CommerceCatalogServiceGraph` fuente de su red.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

Donde `variables.json` es un archivo independiente que almacena los valores más utilizados para Adobe I/O Runtime.
Por ejemplo, la clave de API se puede guardar en el archivo :

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Después de ejecutar este comando, el servicio de catálogo debe ejecutarse a través de la red de API. Puede ejecutar el `aio api-mesh:get` para ver la configuración de la red actualizada.

## Uso de la red de API

La red de API permite a los usuarios consumir fuentes de datos externas para mejorar su instancia de Adobe Commerce. También se puede utilizar para configurar los datos de comercio existentes a fin de habilitar nuevas funciones.

En este ejemplo, la red de API se utiliza para habilitar los precios de nivel en Adobe Commerce.
Sustituya el `name `, `endpoint`y `x-api-key` valores.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Una vez configurada, consulte la red para obtener precios por niveles:

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
