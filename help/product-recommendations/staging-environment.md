---
title: Prueba en entorno de ensayo
description: Aprenda a utilizar [!DNL Product Recommendations] del entorno de producción en el entorno de ensayo para realizar pruebas.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Prueba en entorno de ensayo

Antes de implementar recomendaciones en el entorno de producción, debe realizar pruebas en un entorno que no sea de producción para asegurarse de que todo funciona según lo esperado.

[!DNL Product Recommendations] devolución de productos en función de [datos de comportamiento del comprador](behavioral-data.md) recopilado de tu tienda. Sin embargo, en un entorno que no es de producción, es probable que no tenga datos de comportamiento de compradores. El único tipo de recomendación que puede probar sin datos de comportamiento es `More like this`. Este tipo de recomendación no requiere datos de entrada, ya que utiliza una coincidencia de similitud de contenido directo.

Los siguientes tipos de recomendación requieren datos de comportamiento:

- Más visitados
- Lo ha visto, ha visto que
- Compré esto, compré aquello

¿Cómo se pueden probar las recomendaciones en un entorno que no sea de producción utilizando datos de comportamiento? Hay un par de opciones.

## Recuperar recomendaciones del entorno de producción (recomendado)

Adobe Commerce le permite recuperar recomendaciones de su entorno de producción y previsualizarlas en un entorno que no sea de producción mediante [conmutación](settings.md) el espacio de datos SaaS.

Para recuperar recomendaciones del entorno de producción, debe asegurarse de que:

- La recopilación de datos de tienda es [configurado y habilitado](install-configure.md) en producción.
- El catálogo de entornos que no son de producción es en gran medida el mismo que el que tiene en producción. El uso de catálogos similares garantiza que los productos devueltos en las unidades de recomendación se parezcan mucho a los de producción.

## Generar datos de comportamiento en entornos que no sean de producción

1. Implemente el `magento/product-recommendations` a un entorno que no sea de producción donde los datos del catálogo sean similares al catálogo de producción.

1. Utilice uno de los ID de espacio de datos que no sean de producción para [configuración](https://docs.magento.com/user-guide/configuration/services/saas.html) en el menú

1. Genere los datos usted mismo haciendo clic alrededor de su tienda para imitar el comportamiento de los compradores reales (o crear un script de automatización). A través de las pruebas, se generan eventos de comportamiento en un entorno que no es de producción. Estos eventos se utilizan para producir las afinidades de producto que impulsan las recomendaciones. Para pruebas, [!DNL Commerce] sugiere que interactúe con los siguientes tipos de recomendaciones:

   - Más visitados: requiere datos de entrada mínimos. Los usuarios deben ver los productos.
   - Visto esto, visto eso: requiere que varios usuarios vean varios productos.
   - Comprado esto, comprado eso: requiere que varios usuarios compren varios productos.

### Advertencias

- Los datos de comportamiento y catálogo del espacio de datos SaaS sin producción identifican un entorno aislado en el que las recomendaciones de productos resultantes se basan completamente en los datos de comportamiento generados en el almacén asociado.

- Debido a que no tiene grandes cantidades de datos de comportamiento, los datos de entrada para calcular asociaciones de productos son escasos. Sin embargo, esos datos se siguen enviando a Sensei para calcular los modelos de aprendizaje automático y ofrecer recomendaciones basadas en los datos que haya generado en este entorno.
