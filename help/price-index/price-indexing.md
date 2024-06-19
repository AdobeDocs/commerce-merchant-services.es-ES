---
title: Indexación de precios de SaaS
description: Uso de la indexación de precios SaaS para mejorar el rendimiento
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Indexación de precios de SaaS

La indexación de precios SaaS mejora el rendimiento del sitio al mover procesos de computación pesados como la indexación y el cálculo de precios de la aplicación Commerce a la infraestructura en la nube de Adobe. Este enfoque permite a los comerciantes ampliar sus recursos rápidamente para aumentar los tiempos de indexación de precios y reflejar los cambios de precios más rápido al enviar datos a la tienda y a los servicios conectados de Commerce.

El diagrama siguiente muestra el flujo de datos de indexación a los servicios SaaS cuando Commerce utiliza el [indexación de precios](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) proceso incluido en la aplicación de Commerce:

![Flujo de datos predeterminado](assets/old_way.png)

Con la indexación de precios SaaS habilitada, el flujo de datos cambia. La indexación de precios se realiza utilizando [Exportación de datos de SaaS de Commerce](../data-export/data-synchronization.md).

![Flujo de datos de indexación de precios SaaS](assets/new_way.png)

Todos los comerciantes pueden beneficiarse del uso de la indexación de precios SaaS, pero los comerciantes que tienen proyectos con las siguientes características pueden obtener las mayores ganancias:

* **Cambios constantes en los precios**-Comerciantes que requieren cambios repetidos en sus precios para cumplir con objetivos estratégicos como promociones frecuentes, descuentos estacionales o reducciones de existencias.
* **Varios sitios web o grupos de clientes**-Comerciantes con catálogos de productos compartidos en varios sitios web (dominios/marcas) o grupos de clientes.
* **Muchos precios únicos en sitios web o grupos de clientes**-Comerciantes con extensos catálogos de productos compartidos que contienen precios únicos en sitios web o grupos de clientes. Algunos ejemplos son los comerciantes B2B que han negociado previamente precios o marcas con diferentes estrategias de precios.

## Usar indexación de precios SaaS

La indexación de precios SaaS se activa automáticamente al instalar Adobe Commerce Services. Admite el cálculo de precios para todos los tipos de productos integrados de Adobe Commerce.

### Requisitos

* Adobe Commerce 2.4.4+

### Requisitos previos

* Uno de los siguientes servicios de Commerce debe instalarse con la última versión de la extensión de Commerce:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)
   * [Product Recommendations](../product-recommendations/guide-overview.md)


>[!NOTE]
>
>Si es necesario, el indexador de precios predeterminado en la aplicación de Commerce se puede desactivar utilizando [Adaptador de catálogo](catalog-adapter.md).

## Sincronizar precios con la indexación de precios SaaS

Después de habilitar la indexación de precios SaaS para Adobe Commerce, actualice los precios en la tienda y en los servicios de Commerce sincronizando las nuevas fuentes:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Precios para tipos de productos personalizados

Los cálculos de precios se admiten para tipos de productos personalizados, como precio base, precio especial, precio de grupo, precio de regla de catálogo, etc.

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

