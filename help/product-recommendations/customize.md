---
title: Personalizar
description: Aprenda a personalizar las recomendaciones de productos.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Personalizar

Al instalar el módulo Product Recommendations, Adobe Commerce crea el `ProductRecommendationsLayout` directorio. Este directorio contiene archivos de plantilla que puede personalizar para cambiar la forma en que aparecen las recomendaciones en la tienda. En concreto, puede modificar o anular la siguiente plantilla:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Para obtener más información sobre la modificación de archivos de plantilla, consulte [Personalización de plantilla](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) en la Guía para desarrolladores de Frontend.

Si modifica la variable `recommendations.html` debe conservar las siguientes etiquetas en el archivo para asegurarse de que Adobe Commerce pueda recopilar métricas de recomendaciones de su tienda:

| Etiqueta | Uso |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Recopila eventos de vista. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Recopila eventos de clic. <br/>**Nota:** Si añade etiquetas de anclaje, debe incluir estos atributos. |

Además de las `recommendations.html` , el archivo `ProductRecommendationsLayout` El directorio contiene los siguientes subdirectorios:

| Directorio | Finalidad |
|---|---|
| `layout` | Contains `*.xml` archivos para cada tipo de página |
| `templates` | Contiene archivos que llaman a los scripts de recuperación y procesamiento |
| `web/js` | Contiene los archivos JavaScript que recuperan y representan recomendaciones para su tienda |
| `web/template` | Contiene la plantilla para `magento/product-recommendations` módulo |

## Posición de unidad de recomendación

Cuando usted [crear](create.md) una recomendación, especifique el [ubicación](placement.md) donde aparece en la página. Se puede colocar una unidad de recomendación en la parte superior o inferior del contenedor de contenido principal. Sin embargo, puede personalizar esta ubicación. Si crea un tipo de contenido de recomendación de Page Builder, utilice las herramientas de Page Builder para colocar la unidad de recomendación en la página. Para el resto de tipos de página, edite la variable `*.xml` archivos que se generan al crear la recomendación.

1. Cambie a la `layout` directorio:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   En la tabla siguiente se enumeran los archivos XML presentes en este directorio:

   | Nombre de archivo | Página |
   |---|---|
   | `catalog_category_view.xml` | Categoría |
   | `catalog_product_view.xml` | Detalles del producto |
   | `checkout_cart_index.xml` | Carrito |
   | `checkout_onepage_success.xml` | Finalizar compra |
   | `cms_index_index.xml` | Inicio |

   >[!NOTE]
   >
   >Los nombres de archivo en la `layout` Este directorio puede ser diferente si su tienda utiliza extensiones de terceros.

1. Modifique la `catalog_product_view.xml` archivo para que la unidad de recomendación aparezca después de la imagen del producto en la página de detalles del producto. Antes de personalizar este archivo XML, consulte el archivo y las secciones que debe modificar:

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

   En el fragmento anterior, la variable `main.content` el bloque de referencia indica que la unidad de recomendación se colocará en algún lugar relativo a ese elemento. Su `block` contiene el elemento `after="-"` , que especifica que la unidad de recomendación se mostrará en la página después del bloque de contenido principal.

1. Vamos a modificar este archivo especificando un bloque de contenido diferente.

   Cambio del bloque de referencia `name` de `main.content` hasta `product.info.media`.

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

   Este cambio hace que la unidad de recomendación aparezca después de la imagen del producto en la página de detalles del producto. Si desea que la unidad de recomendación aparezca antes de `product.info.media`, cambie la `after="-"` atribuir a `before="-"`. El `pagePlacement` es un argumento interno que no debe modificarse.

Consulte [descripción general del diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) para obtener más información sobre los tipos de bloques de la página.

## Atributos de producto personalizados

Los desarrolladores suelen necesitar acceso a los valores de atributos de productos personalizados en las unidades de recomendaciones de las tiendas para que puedan añadir tratamientos visuales a los productos basados en esos atributos.

Por ejemplo, si su tienda vende algunos productos orgánicos, puede que tenga un atributo personalizado en esos productos que los designe como `Organic = Yes`. Es posible que necesite acceso a este valor de atributo en la tienda para que pueda dar a estos productos un tratamiento visual especial cuando aparezcan en Recommendations. Del mismo modo, el acceso a estos valores de atributos de producto personalizados le permite crear insignias de productos o controlar la lógica personalizada en la capa de presentación del sitio.

![Añadir insignia](assets/unit-custom.png)

Para asegurarse de que haya un atributo de producto personalizado disponible cuando procese la unidad de recomendación en la página, establezca el `Used in Product Listing` propiedad a `Yes` en el [Atributos del producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) en la página de administración.

Cuando se establece esta propiedad, la carga útil JSON incluye un `attributes` que contiene una matriz de códigos y valores de atributo. A continuación, puede aplicar un estilo de tienda personalizado basado en estos valores de atributo, como agregar tratamientos visuales especiales o insignias, como se mencionó anteriormente.

>[!NOTE]
>
>Los cambios de atributos del producto pueden tardar hasta una hora en aparecer en la carga útil JSON.
