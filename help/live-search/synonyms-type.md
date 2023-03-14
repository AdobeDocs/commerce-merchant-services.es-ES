---
title: "Tipos de sinónimos"
description: '"Uno y dos vías [!DNL Live Search] los sinónimos amplían la definición de palabras clave".'
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Tipos de sinónimos

Los sinónimos unidireccionales y bidireccionales amplían la definición de palabras clave. Algunos son intercambiables con la palabra clave, mientras que otros representan un subconjunto de la palabra clave.

## Bidireccional

Los sinónimos bidireccionales tienen el mismo significado y devuelven los mismos resultados de búsqueda. En el ejemplo siguiente, la primera palabra que aparece en negrita es la palabra clave que se utiliza en el catálogo, seguida de palabras que tienen el mismo significado que la palabra clave original. Puede crear un par simple de sinónimos bidireccionales o una cadena de varios sinónimos bidireccionales para la misma palabra clave.

**chaqueta** ![Selector bidireccional](assets/btn-two-way.png) abrigo
**pantalones** ![Selector bidireccional](assets/btn-two-way.png) pantalones ![Selector bidireccional](assets/btn-two-way.png) pantalones

## Unidireccional

Un sinónimo unidireccional es un subconjunto de una palabra clave, pero con un significado más específico. Por ejemplo, los capris y los shorts son pantalones, pero no todos son capris o shorts. Una búsqueda de pantalones incluye capris y pantalones cortos. Sin embargo, la búsqueda de pantalones cortos no devuelve capris.

**sudadera** ![Selector unidireccional](assets/btn-one-way.png) sudadera con capucha
**pantalones** ![Selector unidireccional](assets/btn-one-way.png) capris ![Selector múltiple unidireccional](assets/btn-multiple-one-way.png) pantalones largos de pantorrilla ![Selector múltiple unidireccional](assets/btn-multiple-one-way.png) traficantes

## Prácticas recomendadas

Tenga en cuenta las siguientes prácticas recomendadas para sacar el máximo partido a [!DNL Live Search] sinónimos.

### Evite las palabras &quot;stop&quot;

[!DNL Live Search] elimina las &quot;palabras de detención&quot; comunes del inglés de los sinónimos, como:

a, y, son, como, en, ser, pero, por, porque, si, en, en, es, no, no, de, en, o, tal, que, el, su, entonces, allí, estos, ellos, esto, a, era, voluntad, con

Las palabras de detención no hacen que los sinónimos sean más significativos, sino que aumentan la cantidad de datos que deben procesarse.

### Usar palabras únicas

Si un término de sinónimo contiene varias palabras, el espacio en blanco entre las palabras hace que se traten como sinónimos independientes. Por ejemplo, si define &quot;reloj&quot; como sinónimo de &quot;reloj&quot;, las palabras &quot;tiempo&quot; y &quot;reloj&quot; se tratan como sinónimos independientes.

### Uso del singular y el plural

No es necesario definir las formas singular y plural de una palabra como sinónimo. Si en el catálogo existe una mezcla de términos en singular y en plural, Search busca el conjunto de productos correcto. Por ejemplo, si utiliza la palabra &quot;pantalón&quot; en el nombre del producto y un comprador busca &quot;pantalones&quot;, se devuelve el conjunto correcto de productos y la palabra singular &quot;pantalón&quot; se ofrece como sugerencia. El término singular &quot;pantalón&quot; se utiliza a menudo en la industria de la moda y a veces en el comercio minorista, aunque la forma plural &quot;pantalones&quot; se utiliza más comúnmente en algunas áreas. (La palabra &quot;pantalón&quot; se refiere técnicamente a la parte de una prenda que cubre una pierna, por lo que se necesita un &quot;par de pantalones&quot; para cubrir ambas piernas).

### Coherencia

Sea coherente con la forma en que se utiliza la terminología en su catálogo. Tenga en cuenta que puede haber diferencias regionales en el uso y, a veces, diferencias dentro de una industria.

### Asignación de palabras clave

Esta técnica utiliza atributos de producto en los que se pueden buscar, en lugar de sinónimos, para crear asociaciones basadas en palabras clave entre productos. Como resultado, un producto asignado puede aparecer en los resultados de búsqueda de otro producto. Para obtener más información, consulte [Resultados de búsqueda](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html).
