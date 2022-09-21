---
title: consulta refineProduct
description: '''Una guía de referencia para la consulta `refineProduct` GraphQL para el servicio de catálogo de Adobe Commerce''.'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# consulta refineProduct

La variable `refineProduct` limita los resultados de una `products` consulta que se ejecutó con un producto complejo. Antes de ejecutar el `refineProduct` consulta, debe ejecutar el `products` consulta y construya la respuesta para que devuelva una lista de `options` dentro de un `ComplexProductView` fragmento en línea. Cuando un comprador seleccione una opción de producto (como tamaño o color) en la tienda, ejecute el `refineProduct` , especificando el SKU y los ID de valor de opción seleccionados como entrada. Según el número de opciones de producto que tenga el producto complejo, es posible que tenga que ejecutar la variable `refineProduct` consulta varias veces, hasta que el comprador haya seleccionado una variante específica.

Debe construir la respuesta de la consulta para que contenga ambas variables `ComplexProductView` y `SimpleProductView` fragmentos en línea. Si el comprador no ha seleccionado todas las opciones necesarias, la consulta devolverá los ID de opciones no seleccionadas y el precio mínimo y máximo del producto, en función de las opciones seleccionadas y las posibles opciones restantes. Si el comprador ha seleccionado todas las opciones necesarias, la consulta devuelve detalles sobre un producto simple, que incluye un precio establecido.

## Sintaxis

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
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

### Devolver detalles sobre un producto complejo parcialmente seleccionado

La siguiente consulta devuelve detalles sobre las opciones de color disponibles para una variante de producto de tamaño mediano `MH12`. El valor de la variable `optionIDs` el parámetro de entrada se toma de la variable `products` consulta [Devolver detalles sobre un producto complejo](products.md#complex-product-example) ejemplo.

**Solicitud:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Devolver detalles sobre un producto complejo completamente seleccionado

En la siguiente consulta, el comprador ha seleccionado opciones tanto para el tamaño como para el color. La respuesta contiene detalles sobre el producto simple correspondiente.

**Solicitud:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Campos de entrada

Debe especificar un valor de SKU y al menos un ID de opción como entrada.

| Campo | Tipo de datos | Descripción |
|--- | --- | ---|
| `optionIds` | [¡Cadena!]! | Una lista de ID asignados a las opciones de producto que el comprador ha seleccionado, como colores y tamaños específicos. |
| `sku` | ¡Cadena! | El SKU de un producto complejo. |

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
