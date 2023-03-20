---
title: Personalizar
description: Obtenga información sobre cómo personalizar las recomendaciones de productos.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Personalizar

Al instalar el módulo Product Recommendations, Adobe Commerce crea la variable `ProductRecommendationsLayout` directorio. Este directorio contiene archivos de plantilla que puede personalizar para cambiar la forma en que aparecen las recomendaciones en la tienda. Específicamente, puede modificar o anular la siguiente plantilla:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Para obtener más información sobre la modificación de archivos de plantilla, consulte [Personalización de plantillas](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) en la Guía para desarrolladores de Frontend.

Si modifica la variable `recommendations.html` , debe conservar las siguientes etiquetas en el archivo para asegurarse de que Adobe Commerce pueda recopilar métricas de recomendación de su tienda:

| Etiqueta | Uso |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Recopila eventos de vista. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Recopila eventos de clic. <br/>**Nota:** Si agrega etiquetas de anclaje, debe incluir estos atributos. |

Además del `recommendations.html` archivo, la variable `ProductRecommendationsLayout` contiene los siguientes subdirectorios:

| Directorio | Objetivo |
|---|---|
| `layout` | Contiene `*.xml` archivos para cada tipo de página |
| `templates` | Contiene archivos que llaman a las secuencias de comandos de recuperación y procesamiento |
| `web/js` | Contiene los archivos JavaScript que recuperan y procesan recomendaciones para su tienda |
| `web/template` | Contiene la plantilla para la variable `magento/product-recommendations` módulo |

## Posicionamiento de la unidad de recomendación

Cuando [crear](create.md) una recomendación, debe especificar la variable [ubicación](placement.md) donde aparece en la página. Una unidad de recomendación se puede colocar en la parte superior o inferior del contenedor de contenido principal. Sin embargo, puede personalizar esta ubicación. Si crea un tipo de contenido de recomendación de Page Builder , utilice las herramientas de Page Builder para colocar la unidad de recomendación en la página. Para el resto de tipos de página, edite la variable `*.xml` archivos que se generan cuando se crea la recomendación.

1. Cambie a la función `layout` directorio:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   La tabla siguiente muestra los archivos XML presentes en este directorio:

   | Nombre de archivo | Página |
   |---|---|
   | `catalog_category_view.xml` | Categoría |
   | `catalog_product_view.xml` | Detalles del producto |
   | `checkout_cart_index.xml` | Carro de compras |
   | `checkout_onepage_success.xml` | Cierre de compra |
   | `cms_index_index.xml` | Página principal |

   >[!NOTE]
   >
   >Los nombres de archivo de la variable `layout` puede ser diferente si su tienda utiliza extensiones de terceros.

1. Modifique el `catalog_product_view.xml` para que la unidad de recomendación aparezca después de la imagen del producto en la página de detalles del producto. Antes de personalizar este archivo XML, eche un vistazo al archivo y comprenda las secciones que debe modificar:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   En el fragmento anterior, la variable `main.content` el bloque de referencia indica que la unidad de recomendación se colocará en algún lugar en relación con ese elemento. Su `block` contiene el `after="-"` , que especifica que la unidad de recomendación se mostrará en la página después del bloque de contenido principal.

1. Vamos a modificar este archivo especificando un bloque de contenido diferente.

   Cambiar el bloque de referencia `name` from `main.content` a `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Este cambio hace que la unidad de recomendación aparezca después de la imagen del producto en la página de detalles del producto. Si desea que la unidad de recomendación aparezca antes del `product.info.media`, cambie la variable `after="-"` atributo a `before="-"`. La variable `pagePlacement` es un argumento interno que no debe modificarse.

Consulte [información general del diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) para obtener más información sobre los tipos de bloques de la página.

## Atributos de producto personalizados

Los desarrolladores suelen necesitar acceso a los valores de atributos de producto personalizados en unidades de recomendaciones en tiendas, de modo que puedan añadir tratamientos visuales a los productos en función de esos atributos.

Por ejemplo, si la tienda vende algunos productos orgánicos, es posible que tenga un atributo personalizado en esos productos que los designe como `Organic = Yes`. Es posible que necesite acceder a este valor de atributo en la tienda para poder dar a estos productos un tratamiento visual especial cuando aparezcan en Recommendations. Del mismo modo, el acceso a estos valores de atributos de producto personalizados le permite asignar un distintivo a productos o dirigir la lógica personalizada en la capa de presentación del sitio.

![Agregar distintivo](assets/unit-custom.png)

Para asegurarse de que un atributo de producto personalizado esté disponible cuando procese la unidad de recomendación en la página, establezca la variable `Used in Product Listing` propiedad a `Yes` en el [Atributos del producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) en la página Administración.

Cuando se establece esta propiedad, la carga útil JSON incluye un `attributes` que contiene una matriz de códigos y valores de atributo. A continuación, puede aplicar estilos de tienda personalizados basados en estos valores de atributo, como la adición de tratamientos visuales especiales o distintivos como se mencionó anteriormente.

>[!NOTE]
>
>Los cambios en los atributos del producto pueden tardar hasta una hora en aparecer en la carga útil JSON.
