---
title: '"Tipos de sinónimos"'
description: '"De una y dos direcciones [!DNL Live Search] los sinónimos amplían la definición de palabras clave".'
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cd1b40ffb350a87ea1317be82789f702922881b9
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# Tipos de sinónimos

Los sinónimos unidireccionales y bidireccionales amplían la definición de palabras clave. Algunos pueden intercambiarse con la palabra clave, mientras que otros representan un subconjunto de la palabra clave.

## bidireccional

Los sinónimos bidireccionales tienen el mismo significado y devuelven los mismos resultados de búsqueda. En el siguiente ejemplo, la primera palabra que se muestra en negrita es la palabra clave que se usa en el catálogo, seguida de palabras que tienen el mismo significado que la palabra clave original. Puede crear un par simple de sinónimos bidireccionales o una cadena de varios sinónimos bidireccionales para la misma palabra clave.

**chaqueta** ![Selector bidireccional](assets/btn-two-way.png) abrigo
**pantalones** ![Selector bidireccional](assets/btn-two-way.png) barras ![Selector bidireccional](assets/btn-two-way.png) trolls

## Unidireccional

Un sinónimo unidireccional es un subconjunto de una palabra clave, pero con un significado más específico. Por ejemplo, los capris y los pantalones cortos son pantalones, pero no todos los pantalones son gorras o pantalones cortos. La búsqueda de pantalones incluye capris y pantalones cortos. Sin embargo, la búsqueda de pantalones cortos no devuelve capris.

**camisa** ![Selector unidireccional](assets/btn-one-way.png) hoodie
**pantalones** ![Selector unidireccional](assets/btn-one-way.png) capris ![Selector unidireccional múltiple](assets/btn-multiple-one-way.png) calf-length-pantalones ![Selector unidireccional múltiple](assets/btn-multiple-one-way.png) empujadores de pedales

## Prácticas recomendadas

Tenga en cuenta las siguientes prácticas recomendadas para sacar el máximo partido a los sinónimos de Live Search.

### Evitar &quot;parar palabras&quot;

La búsqueda activa filtra las &quot;palabras vacías&quot; comunes en inglés de los sinónimos, como:

a, un y, son, como, a, ser, pero, por, si, en, en, es, es, no, de, en, o tal, que, el, su, entonces, allí, estos, esto, para, fue, con

Las palabras &quot;Stop&quot; no hacen que los sinónimos sean más significativos, sino que aumentan la cantidad de datos que deben procesarse.

### Usar palabras únicas

Si un término sinónimo contiene varias palabras, el espacio en blanco entre las palabras hace que se traten como sinónimos separados. Por ejemplo, si define &quot;pieza temporal&quot; como sinónimo de &quot;reloj&quot;, las palabras &quot;tiempo&quot; y &quot;pieza&quot; se tratan como sinónimos separados.

### Uso del singular y plural

No es necesario definir las formas singular y plural de una palabra como sinónimo. Si tiene una mezcla de términos en singular y plural en su catálogo, Search encuentra el conjunto correcto de productos. Por ejemplo, si utiliza la palabra &quot;inclinación&quot; en el nombre del producto y un comprador busca &quot;pantalones&quot;, se devuelve el conjunto de productos correcto y se ofrece la palabra singular &quot;inclinación&quot; como sugerencia. El término singular &quot;hormiga&quot; se utiliza a menudo en la industria de la moda y a veces en la venta minorista, aunque la forma plural &quot;pantalones&quot; se utiliza más comúnmente en algunas áreas. (La palabra &quot;inclinar&quot; se refiere técnicamente a la parte de una prenda que cubre una pierna, por lo que se necesita un &quot;par de pantalones&quot; para cubrir ambas piernas.)

### Coherencia

Sea coherente con la forma en que se utiliza la terminología en su catálogo. Tenga en cuenta que puede haber diferencias regionales en el uso, y a veces diferencias dentro de un sector.

### Asignación de palabras clave

Esta técnica utiliza atributos de producto en los que se pueden buscar, en lugar de sinónimos, para crear asociaciones basadas en palabras clave entre productos. Como resultado, un producto asignado puede aparecer en los resultados de búsqueda de otro producto. Para obtener más información, consulte [Resultados de la búsqueda](https://docs.magento.com/user-guide/catalog/search-results.html).
