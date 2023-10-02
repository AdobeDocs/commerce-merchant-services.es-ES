---
title: Indexación de precios de SaaS
description: Uso de la indexación de precios SaaS para mejorar el rendimiento
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Indexación de precios de SaaS

La indexación de precios SaaS acelera el tiempo que tardan los cambios de precios en reflejarse [Servicios de Commerce](../landing/saas.md) después de enviarlos. Esto permite a los comerciantes con catálogos grandes y complejos, o con varios sitios web o grupos de clientes, procesar continuamente los cambios de precios.
Si tiene una tienda sin encabezado o usa el [catalog-adapter](./catalog-adapter.md) extensión, los clientes pueden desactivar el indexador de precios principal de Adobe Commerce.

Los procesos computacionales pesados, como la indexación y el cálculo de precios, se han trasladado del núcleo de Commerce a la infraestructura en la nube de Adobe. Esto permite a los comerciantes ampliar rápidamente los recursos para aumentar los tiempos de indexación de precios y reflejar esos cambios más rápido.

El flujo de datos de indexación principal a los servicios SaaS tiene este aspecto:

![Flujo de datos predeterminado](assets/old_way.png)

Con la indexación de precios SaaS, el flujo es:

![Flujo de datos de indexación de precios SaaS](assets/new_way.png)

Todos los comerciantes pueden beneficiarse de estas mejoras, pero los que verán las mayores ganancias son los clientes con:

* Cambios constantes en los precios: los comerciantes que necesitan cambios repetidos en sus precios para cumplir objetivos estratégicos como promociones frecuentes, descuentos estacionales o reducciones de existencias.
* Varios sitios web o grupos de clientes: comerciantes con catálogos de productos compartidos en varios sitios web (dominios/marcas) o grupos de clientes.
* Gran cantidad de precios únicos en sitios web o grupos de clientes: comerciantes con catálogos de productos compartidos extensos que contienen precios únicos en sitios web o grupos de clientes, como comerciantes B2B con precios negociados previamente, marcas con diferentes estrategias de precios.

La indexación de precios SaaS está disponible de forma gratuita para los clientes que utilizan los servicios de Adobe Commerce y admite el cálculo de precios para todos los tipos de productos Adobe Commerce integrados.

Esta miniguía describe cómo funciona la indexación de precios SaaS y cómo habilitarla.

## Requisitos

* Adobe Commerce 2.4.4+
* Al menos uno de los siguientes servicios de Commerce con la última versión de la extensión de Adobe Commerce:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Product Recommendations](../product-recommendations/guide-overview.md)

Los usuarios de Luma y Adobe Commerce Core GraphQL pueden instalar el [`catalog-adapter`](catalog-adapter.md) que proporciona compatibilidad con Luma y Core GraphQl y deshabilita el indexador de precios de productos de Adobe Commerce.

## Uso

Después de actualizar la instancia de Adobe Commerce con la compatibilidad con la indexación de precios SaaS, sincronice las nuevas fuentes:

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-bundle-product-override-data-exporter
magento/module-gift-card-product-data-exporter
```

## Precios para tipos de productos personalizados

Los cálculos de precios son compatibles con tipos de productos personalizados, como precio base, precio especial, precio de grupo, precio de regla de catálogo, etc.

Si tiene un tipo de producto personalizado que utiliza una fórmula específica para calcular el precio final, puede ampliar el comportamiento de la fuente de precios del producto.

## Uso

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

Las nuevas fuentes deben sincronizarse manualmente con `resync` [comando CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). De lo contrario, los datos se actualizan en el proceso de sincronización estándar. Obtenga más información acerca de [Sincronización de catálogo](../landing/catalog-sync.md) proceso.

## Escenarios de uso

### Luma sin dependencias de extensión

* Un comerciante de Luma o Adobe Commerce Core GraphQL que tiene instalado un servicio requerido (Live Search, Product Recommendations, Servicio de catálogo)
* No hay extensiones de terceros que dependan del indexador de precios principal de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar nuevas fuentes.
1. Instale el adaptador del catálogo.

### GraphQl principal de Luma y Adobe Commerce con dependencias de indexador de precios principal de PHP

* Un comerciante de Luma o Adobe Commerce Core GraphQL que tiene instalado un servicio compatible (Live Search, Product Recommendations, Servicio de catálogo)
* Con una extensión de terceros que depende del indexador de precios principal de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar las nuevas fuentes
1. Instale el adaptador del catálogo.
1. Vuelva a habilitar el indexador de precios principal de PHP.
1. Utilice nuevas fuentes y el código de compatibilidad de Luma en la `catalog-adapter` módulo.

### Comerciante sin encabezado

* Un comerciante sin encabezado que tiene instalado un servicio compatible (Live Search, Product Recommendations, Servicio de catálogo)
* Sin dependencia en el indexador de precios PHP Core
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar nuevas fuentes
1. Instale el adaptador de catálogo, que desactiva el indexador de precios principal de PHP.

## Precios personalizados

El indexador de precios SaaS admite funciones de precio de tipo de producto personalizadas que están disponibles en Adobe Commerce, como precio especial, precio de grupo y precio de regla de catálogo.

Por ejemplo: hay un tipo de producto personalizado  `custom_type` y un producto con el SKU &quot;Custom Type Product&quot;.

De forma predeterminada, la extensión de exportación de datos de Commerce envía la siguiente fuente de precios al indexador de precios:

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

Si &quot;Tipo de producto personalizado&quot; utiliza una fórmula única para calcular el precio del producto, los integradores de sistemas pueden anular los campos precio y descuento al ampliar la extensión de exportación de datos comerciales.

1. Cree un complemento en la `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` clase.

`di.xml` archivo:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. Cree un método con la fórmula personalizada:

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
