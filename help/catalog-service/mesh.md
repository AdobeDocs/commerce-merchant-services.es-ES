---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] para Adobe Commerce proporciona una forma de integrar varias fuentes de datos a través de un punto final de GraphQL común."'
exl-id: cdda4a83-3c5f-4a69-8279-b90464e16c0e
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

El [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe I/O Runtime.

![Diagrama de arquitectura de catálogo](assets/catalog-service-architecture-mesh.png)

El primer paso para utilizar la API Mesh con el servicio de catálogo es conectar la API Mesh a su instancia. Consulte las instrucciones detalladas en [Crear una malla](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Para completar la instalación, instale el [Paquete de CLI de Adobe Developer](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Una vez configurada Mesh en Adobe I/O Runtime, ejecute el siguiente comando que agrega una `CommerceCatalogServiceGraph` fuente a su malla.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

Donde `variables.json` es un archivo independiente que almacena los valores que se utilizan con más frecuencia para Adobe I/O Runtime.
Por ejemplo, la clave de API se puede guardar en el archivo:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Después de ejecutar este comando, el servicio de catálogo debe ejecutarse a través de la API Mesh. Puede ejecutar el `aio api-mesh:get` para ver la configuración de la malla actualizada.

## Ejemplos de API Mesh

La malla de API permite a los usuarios consumir fuentes de datos externas para mejorar la instancia de Adobe Commerce. También se puede utilizar para configurar los datos de Commerce existentes para habilitar la nueva funcionalidad.

### Habilitar precios de nivel

En este ejemplo, la API Mesh se utiliza para habilitar los precios de nivel en Adobe Commerce.
Reemplace el `name `, `endpoint`, y `x-api-key` valores.

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

Una vez configurada, consulte la malla para ver los precios por niveles:

```graphql
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

### Obtener un ID de entidad

Esta malla adjunta el `entityId` a la interfaz ProductView. Reemplace el `name `, `endpoint`, y `x-api-key` valores.

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
              "endpoint": "https://catalog-service.adobe.io/graphql",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend interface ProductView {\n  entityId: String\n}\n extend type SimpleProductView {\n  entityId: String\n}\n extend type ComplexProductView {\n  entityId: String\n}\n",
      "additionalResolvers": [
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n    items {\n  sku\n uid\n  }\n    }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          },
          {
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n items {\n  sku\n uid\n }}",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          }
      ]
    }
  }
```

`entityId` ahora se puede consultar:

```graphql
query {
  products(skus: ["MH07"]){
    sku
    name
    id
    entityId
  }
}
```
