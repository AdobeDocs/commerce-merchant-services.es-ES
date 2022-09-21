---
title: consulta productSearch
description: '''Una guía de referencia para la consulta GraphQL de productSearch para el servicio de catálogo de Adobe Commerce''.'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 2%

---


# consulta productSearch

El servicio de catálogo para Adobe Commerce `productSearch` puede utilizar LiveSearch para devolver detalles sobre los SKU especificados como entrada. Aunque esta consulta es la misma que la [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html), LiveSearch devuelve un valor `productView` objeto. Consulte la [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html) tema para información de referencia.

## Sintaxis

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## Encabezados requeridos

Debe especificar los siguientes encabezados HTTP para ejecutar esta consulta.

| Encabezado | Descripción |
|--- | ---|
| `Magento-Customer-Group` | Para los clientes de tienda, este valor estará disponible en la tienda en la `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Este valor se muestra en **Sistema** > **Conector de Commerce Services** > **Identificador SaaS** > **ID del espacio de datos** o se puede obtener ejecutando el `bin/magento config:show services_connector/services_id/environment_id` comando. |
| `Magento-Store-Code` | El código asignado al almacén asociado con la vista del almacén activo. Por ejemplo, `main_website_store`. |
| `Magento-Store-View-Code` | El código asignado a la vista de tienda activa. Por ejemplo, `default`. |
| `Magento-Website-Code` | Código asignado al sitio web asociado con la vista de tienda activa. Por ejemplo, `base`. |
| `X-Api-Key` | Clave única que se genera durante el proceso de incorporación. |

## Uso de ejemplo

En el ejemplo siguiente, la consulta devuelve información sobre los mismos productos que el ejemplo anterior. Sin embargo, se ha construido para devolver información de artículos dentro del servicio de catálogo `productView` en lugar del núcleo `product` objeto. Tenga en cuenta que la información de precios varía según el tipo de producto. En aras de la brevedad, no se muestra la información de facetas.

**Solicitud:**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**Respuesta:**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
