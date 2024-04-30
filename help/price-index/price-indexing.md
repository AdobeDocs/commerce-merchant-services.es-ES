---
title: Indexación de precios de SaaS
description: Uso de la indexación de precios SaaS para mejorar el rendimiento
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '409'
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

Esta guía describe cómo funciona la indexación de precios SaaS y cómo habilitarla.

## Requisitos

* Adobe Commerce 2.4.4+
* Al menos uno de los siguientes servicios de Commerce con la última versión de la extensión de Adobe Commerce:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)
   * [Product Recommendations](../product-recommendations/guide-overview.md)

Los usuarios de Luma y Adobe Commerce Core GraphQL pueden instalar el [`catalog-adapter`](catalog-adapter.md) que proporciona compatibilidad con Luma y Core GraphQl y deshabilita el indexador de precios de productos de Adobe Commerce.

## Uso

Después de actualizar la instancia de Adobe Commerce con la compatibilidad con la indexación de precios SaaS, sincronice las nuevas fuentes:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Precios para tipos de productos personalizados

Los cálculos de precios son compatibles con tipos de productos personalizados, como precio base, precio especial, precio de grupo, precio de regla de catálogo, etc.

Si tiene un tipo de producto personalizado que utiliza una fórmula específica para calcular el precio final, puede ampliar el comportamiento de la fuente de precios del producto.

1. Cree un complemento en la `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` clase.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
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
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
