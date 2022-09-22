---
title: consulta de productos
description: '''Una guía de referencia para la consulta de GraphQL para el servicio de catálogo de Adobe Commerce''.'
source-git-commit: d9b8c89f6d04aa9d569b450af2893b92938119ad
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# consulta de productos

El servicio de catálogo para Adobe Commerce `products` la consulta devuelve detalles sobre los SKU especificados como entrada. Aunque esta consulta tiene el mismo nombre que la [`products` query](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) que se proporciona con Adobe Commerce y Magento Open Source principales, hay algunas diferencias.

La consulta del servicio de catálogo requiere uno o más valores de SKU como entrada. La consulta está diseñada principalmente para recuperar información y procesar los siguientes tipos de contenido:

* Páginas de detalles del producto : puede proporcionar detalles completos sobre el producto identificado por el SKU especificado.

* Páginas de comparación de productos : puede recuperar información seleccionada sobre varios productos, como el nombre, el precio y la imagen.

La variable `ProductView` el objeto de salida es considerablemente diferente al objeto principal `products` query `Products` objeto de salida. Las principales diferencias incluyen:

* Los productos son sencillos o complejos. Los productos de tarjetas de regalo, simples, virtuales y descargables se asignan a `SimpleProductView`. El resto de tipos de productos se asignan a `ComplexProductView`. Los productos simples tienen precios definidos. Los productos complejos tienen rangos de precios. Dado que los productos complejos están compuestos por varios productos simples, tienen acceso a precios de producto sencillos.

* Los atributos definidos por el comerciante se exponen en un contenedor de nivel superior e indican sus funciones de tienda. Las funciones incluyen Mostrar en PDP, Mostrar en PLP y Mostrar en resultados de búsqueda.

* También se puede acceder a las imágenes como un contenedor de nivel superior y su función puede filtrarlas. Una imagen puede tener una función base, pequeña o en miniatura.

## Sintaxis

```graphql
products (skus [String]) [ProductView]
```

## Encabezados requeridos

Debe especificar los siguientes encabezados HTTP para ejecutar esta consulta.

| Encabezado | Descripción |
| --- | --- |
| `Magento-Customer-Group` | Para los clientes de tienda, este valor estará disponible en la tienda en la `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Este valor se muestra en **Sistema** > **Conector de Commerce Services** > **Identificador SaaS** > **ID del espacio de datos** o se puede obtener ejecutando el `bin/magento config:show services_connector/services_id/environment_id` comando. |
| `Magento-Store-Code` | El código asignado al almacén asociado con la vista del almacén activo. Por ejemplo, `main_website_store`. |
| `Magento-Store-View-Code` | El código asignado a la vista de tienda activa. Por ejemplo, `default`. |
| `Magento-Website-Code` | Código asignado al sitio web asociado con la vista de tienda activa. Por ejemplo, `base`. |
| `X-Api-Key` | Clave única que se genera durante el proceso de incorporación. |

## Uso de ejemplo

### Devolver detalles sobre un producto simple

La siguiente consulta devuelve detalles sobre un producto simple.

**Solicitud:**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**Respuesta:**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### Devolver detalles sobre un producto complejo {#complex-product-example}

La siguiente consulta devuelve detalles sobre un producto configurable.

**Solicitud:**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## Campos de salida

La variable `ProductView` El objeto return es una interfaz que puede contener los siguientes campos. La implementa el [`SimpleProductView`](#SimpleProductView-type) y [`ComplexProductView`](#ComplexProductView-type) tipos.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Lista de atributos definidos por el comerciante designados para la tienda. |
| `description` | Cadena | Descripción detallada del producto. |
| `id` | ¡ID! | El ID del producto, generado como clave compuesta, único por configuración regional. |
| `images(roles: [String])` | [ProductViewImage] | Una lista de imágenes definidas para el producto. |
| `metaDescription` | Cadena | Breve descripción del producto para listas de resultados de búsqueda. |
| `metaKeyword` | Cadena | Lista de palabras clave separadas por coma que solo son visibles para los motores de búsqueda. |
| `metaTitle` | Cadena | Cadena que se muestra en la barra de título y en la ficha del explorador y en las listas de resultados de búsqueda. |
| `name` | Cadena | Nombre del producto. |
| `shortDescription` | Cadena | Resumen del producto. |
| `sku` | Cadena | SKU de producto. |
| `url` | Cadena | URL canónica del producto. |

### Tipo ComplexProductView {#ComplexProductView-type}

La variable `ComplexProductView` representa los productos de paquetes, configurables y de grupo. Los precios de productos complejos se devuelven como un rango de precios, ya que los valores de precios pueden variar en función de las opciones seleccionadas. El tipo implementa `ProductView`.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Lista de atributos definidos por el comerciante designados para la tienda. |
| `description` | Cadena | Descripción detallada del producto. |
| `id` | ¡ID! | El ID del producto, generado como clave compuesta, único por configuración regional. |
| `images(roles: [String])` | [ProductViewImage] | Una lista de imágenes definidas para el producto. |
| `metaDescription` | Cadena | Breve descripción del producto para listas de resultados de búsqueda. |
| `metaKeyword` | Cadena | Lista de palabras clave separadas por coma que solo son visibles para los motores de búsqueda. |
| `metaTitle` | Cadena | Cadena que se muestra en la barra de título y en la ficha del explorador y en las listas de resultados de búsqueda. |
| `name` | Cadena | Nombre del producto. |
| `options` | [ProductViewOption] | Lista de opciones seleccionables. |
| `priceRange` | ProductViewPriceRange | Una gama de precios posibles para un producto complejo. |
| `shortDescription` | Cadena | Resumen del producto. |

### Tipo de precio

La variable `Price type` define el precio de un producto simple o una parte de un rango de precios para un producto complejo. Puede incluir una lista de ajustes de precios.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `amount` | ProductViewMoney | Contiene el valor monetario y el código de moneda de un producto. |

### Tipo PriceAjuste

La variable `PriceAdjustment` especifica la cantidad y el tipo de un ajuste de precio. Un valor de código de ejemplo es `weee`.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `amount` | Flotante | El importe del ajuste de precio. |
| `code` | Cadena | Identifica el tipo de ajuste de precio. |

### Tipo ProductViewAttribute

La variable `ProductViewAttribute` es un contenedor para atributos definidos por el cliente que se muestran en la tienda.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `label` | Cadena | Etiqueta del atributo. |
| `name` | ¡Cadena! | Nombre de un código de atributo. |
| `roles` | [Cadena] | Funciones designadas para un atributo en la tienda, como &quot;Mostrar en PLP&quot;, &quot;Mostrar en PDP&quot; o &quot;Mostrar en la búsqueda&quot;. |
| `value` | JSON | Valor de atributo, arbitrario de tipo . |

### Tipo ProductViewImage

La variable `ProductViewImage` contiene detalles sobre una imagen de producto.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `label` | Cadena | Etiqueta de visualización de la imagen del producto. |
| `roles` | [Cadena] | Lista que describe cómo se utiliza la imagen. Puede `image`, `small_image`o `thumbnail`. |
| `url` | ¡Cadena! | Dirección URL de la imagen del producto. |

### Tipo ProductViewMoney

La variable `ProductViewMoney` define un valor monetario, que incluye un valor numérico y un código de moneda.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `currency` | ProductViewCurrency | Código de moneda de tres letras, como USD o EUR. |
| `value` | Flotante | Un número que expresa un valor monetario. |

### Tipo ProductViewOption

Las opciones de producto proporcionan una forma de configurar los productos mediante la realización de selecciones de valores de opción específicos. Al seleccionar una o varias opciones, se señalará un producto simple específico.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `id` | ID | El ID de la opción . |
| `multi` | Booleano | Indica si la opción permite varias opciones. |
| `required` | Booleano | Indica si la opción debe estar seleccionada. |
| `title` | Cadena | Nombre para mostrar de la opción. |
| `values` | [ProductViewOptionValue!] | Lista de valores de opciones disponibles. |

### Interfaz ProductViewOptionValue

La variable `ProductViewOptionValue` La interfaz define los campos de producto disponibles para el `ProductViewOptionValueProduct` y `ProductViewOptionValueConfiguration` tipos.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `id` | ID | El ID de un valor de opción. |
| `title` | Cadena | Nombre para mostrar del valor de la opción. |

### Tipo ProductViewOptionValueConfiguration

La variable `ProductViewOptionValueConfiguration` es una implementación de `ProductViewOptionValue` para valores de configuración.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `id` | ID | El ID de un valor de opción. |
| `title` | Cadena | Nombre para mostrar del valor de la opción. |

### Tipo ProductViewOptionValueProduct

La variable `ProductViewOptionValueProduct` es una implementación de `ProductViewOptionValue` que añade detalles sobre un producto simple.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `id` | ID | El ID de un valor de opción. |
| `title` | Cadena | Nombre para mostrar del valor de la opción. |
| `product` | SimpleProductView | Detalles sobre un producto simple. |

### Tipo ProductViewPrice

La variable `ProductViewPrice` proporciona la vista de precios del producto base, inherente a los productos simples.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `final` | Precio | Valor de precio después de descuentos, excluidas las promociones personalizadas. |
| `regular` | Precio | Precio base del producto especificado por el comerciante. |
| `roles` | [Cadena] | Determina si el precio debe ser visible u oculto. |

### Tipo ProductViewPriceRange

La variable `ProductViewPriceRange` type enumera el precio mínimo y máximo de un producto complejo.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `maximum` | ProductViewPrice | Precio máximo. |
| `minimum` | ProductViewPrice | Precio mínimo. |

### Tipo SimpleProductView {#SimpleProductView-type}

La variable `SimpleProductView` representa todos los tipos de producto, excepto paquete, configurable y grupo. Los precios simples de los productos no contienen intervalos de precios. `SimpleProductView` implementaciones `ProductView`.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Lista de atributos definidos por el comerciante designados para la tienda. |
| `description` | Cadena | Descripción detallada del producto. |
| `id` | ¡ID! | El ID del producto, generado como clave compuesta, único por configuración regional. |
| `images(roles: [String])` | [ProductViewImage] | Una lista de imágenes definidas para el producto. |
| `metaDescription` | Cadena | Breve descripción del producto para listas de resultados de búsqueda. |
| `metaKeyword` | Cadena | Lista de palabras clave separadas por coma que solo son visibles para los motores de búsqueda. |
| `metaTitle` | Cadena | Cadena que se muestra en la barra de título y en la ficha del explorador y en las listas de resultados de búsqueda. |
| `name` | Cadena | Nombre del producto. |
| `price` | ProductViewPrice | Vista del precio base del producto. |
| `shortDescription` | Cadena | Resumen del producto. |
| `sku` | Cadena | SKU de producto. |
| `url` | Cadena | URL canónica del producto. |
