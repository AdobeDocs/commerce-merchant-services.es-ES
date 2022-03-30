---
title: Flujo de trabajo de implementación
description: Learn the steps to successfully implement [!DNL Product Recommendations] on your storefront.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Flujo de trabajo de implementación

[!DNL Product Recommendations] utiliza datos de comportamiento y de catálogo:

- Comportamiento : datos de la participación de un comprador en su sitio, como vistas de productos, artículos agregados a un carro de compras y compras. Adobe Commerce y Adobe Sensei no recopilan información de identificación personal.

- Catalog - Product metadata, such as name, price, and availability.

Al instalar el `magento/product-recommendations module`, Adobe Sensei agrega los datos de comportamiento y catálogo y crea [!DNL Product Recommendations] para cada tipo de recomendación. The [!DNL Product Recommendations] service then deploys those recommendations to your storefront. Para ayudarle a implementar recomendaciones de productos en su tienda, utilice el siguiente flujo de trabajo:

>[!NOTE]
>
> If your storefront is implemented using PWA Studio, refer to the [PWA documentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si utiliza una tecnología de front-end personalizada, como React o Vue JS, aprenda a [integrar](headless.md) [!DNL Product Recommendations] en tu tienda sin cabeza.

## Workflow

1. **Implementar la recopilación de datos en producción**

   Implementación [!DNL Product Recommendations] requiere dos principales [fuentes de datos](type.md): catálogo y comportamiento. Dado que la producción es el único entorno en el que se capturan y analizan las acciones de los compradores, le conviene empezar a recopilar datos en la producción lo antes posible. [Más información](behavioral-data.md) cómo Adobe Sensei forma los modelos de aprendizaje automático que resultan en recomendaciones de mayor calidad. As an added benefit, when you start collecting behavioral data on production, you can [fetch recommendations](verify.md) based on this production data while operating in non-production environments. You can then test and experiment with different recommendations that are computed based on real shopper data collected in production.

   Para implementar la recopilación de datos en la producción, debe [instalar y configurar](install-configure.md) el [!DNL Product Recommendations] al proporcionar un [Clave de API](https://docs.magento.com/user-guide/system/saas.html#apikey).

   >[!TIP]
   >
   > La implementación de la recopilación de datos no cambia el aspecto de su tienda ni la experiencia de sus compradores. Solo la creación e implementación de unidades de recomendación altera la experiencia del cliente en su tienda. Asegúrese de realizar pruebas en el entorno que no sea de producción antes de implementarlas en producción. Además, no cree unidades de recomendación hasta que no personalice la plantilla. Consulte el paso siguiente.

1. **Personalice la plantilla para que coincida con su estilo**

   La tienda representa la marca, por lo que asegúrese de modificar la plantilla de recomendaciones de productos para que coincida con el tema del sitio.

   >[!TIP]
   >
   > By customizing the template, you can specify your stylesheet, overwrite where a recommendation unit appears on a page, and so on.

   See [Customize](https://devdocs.magento.com/recommendations/customize.html) in the developer documentation to learn how to complete this step.

1. **Probar recomendaciones en un entorno que no sea de producción**

   Siempre es recomendable probar una nueva tecnología en un entorno que no sea de producción antes de implementarla en producción. La prueba de recomendaciones en un entorno que no es de producción le permite jugar con diferentes tipos de unidades de recomendación, posición y páginas. Puede extraer recomendaciones basadas en datos de comportamiento ya recopilados en la producción mientras realiza pruebas en un entorno que no sea de producción, de modo que los resultados de las recomendaciones se basen en el comportamiento de compra de los clientes reales.

   >[!TIP]
   >
   > Asegúrese de que el catálogo de entornos que no son de producción sea en gran medida el mismo que el que tiene en producción. El uso de catálogos similares garantiza que los productos devueltos en las unidades de recomendación imiten de cerca los productos en producción.

   See [Fetch](staging-environment.md) behavioral data from your production environment to learn how to complete this step.

1. **Create and deploy recommendations to your production storefront**

   Ahora que ha implementado la recopilación de datos de comportamiento en producción, ha modificado la plantilla de recomendaciones de productos y ha probado las recomendaciones utilizando el comportamiento real del comprador, está listo para promocionar todo el código a producción y [crear](create.md) recomendaciones de productos en directo.
