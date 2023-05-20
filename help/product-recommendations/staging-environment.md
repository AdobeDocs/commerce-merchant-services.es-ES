---
title: Probar en el entorno de ensayo
description: Aprenda a utilizar [!DNL Product Recommendations] desde el entorno de producción en el entorno de ensayo con fines de prueba.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Probar en el entorno de ensayo

Antes de implementar las recomendaciones en el entorno de producción, debe probarlas en un entorno que no sea de producción para asegurarse de que todo funciona según lo esperado.

[!DNL Product Recommendations] productos de devolución basados en [datos de comportamiento del comprador](behavioral-data.md) recopilado de tu tienda. Sin embargo, en un entorno que no es de producción, es probable que no tenga datos de comportamiento de los compradores. El único tipo de recomendación que puede probar sin datos de comportamiento es `More like this`. Este tipo de recomendación no requiere datos de entrada, ya que utiliza una coincidencia de similitud de contenido directo.

Los siguientes tipos de recomendación requieren datos de comportamiento:

- Más visitados
- Vio esto, vio aquello.
- Compré esto, compré aquello.

¿Cómo puede probar las recomendaciones en un entorno que no es de producción utilizando datos de comportamiento? Hay un par de opciones.

## Obtener recomendaciones del entorno de producción (recomendado)

Adobe Commerce le permite recuperar recomendaciones del entorno de producción y previsualizarlas en el entorno que no sea de producción mediante [cambio](settings.md) el espacio de datos SaaS.

Para recuperar recomendaciones del entorno de producción, debe asegurarse de que:

- La recopilación de datos de la tienda es [configurado y habilitado](install-configure.md) sobre la producción.
- El catálogo de entornos de no producción es en gran medida el mismo que el que tiene en producción. El uso de catálogos similares garantiza que los productos devueltos en las unidades de recomendación imiten estrechamente los de la producción.

## Generar datos de comportamiento en un entorno que no sea de producción

1. Implementar el `magento/product-recommendations` a un entorno que no sea de producción en el que los datos del catálogo sean similares a los del catálogo de producción.

1. Utilice uno de los ID de espacio de datos de no producción para [configuración](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) en el Administrador.

1. Genere los datos usted mismo haciendo clic en su tienda para imitar el comportamiento de los compradores reales (o cree un script de automatización). Con las pruebas, se generan eventos de comportamiento en el entorno que no es de producción. Estos eventos se utilizan para producir las afinidades de productos que alimentan las recomendaciones. Para pruebas, [!DNL Commerce] sugiere que interactúe con los siguientes tipos de recomendaciones:

   - Más visitados: requiere datos de entrada mínimos. Los usuarios deben ver los productos.
   - Visto esto, visto aquello: requiere que varios usuarios vean varios productos.
   - Compró esto, compró aquello. Requiere que varios usuarios compren varios productos.

### Advertencias

- Los datos de comportamiento y catálogo del espacio de datos de SaaS que no es de producción identifican un entorno aislado en el que las recomendaciones de productos resultantes se basan totalmente en los datos de comportamiento generados en la tienda asociada.

- Como no tiene grandes cantidades de datos de comportamiento, los datos de entrada para calcular asociaciones de productos son escasos. Sin embargo, esos datos se siguen enviando a Sensei para calcular los modelos de aprendizaje automático y proporcionar recomendaciones basadas en los datos generados dentro de este entorno.
