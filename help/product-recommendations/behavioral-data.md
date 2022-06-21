---
title: Datos de comportamiento
description: Obtenga información sobre los datos de comportamiento y cuándo puede empezar a utilizarlos.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 371ae21c97021912279381b5e32f953fe3b4f0dd
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# Datos de comportamiento

Algunos tipos de recomendaciones utilizan datos de comportamiento de sus compradores para entrenar modelos de aprendizaje automático y crear recomendaciones personalizadas. Otros tipos de recomendaciones utilizan solo datos de catálogo y no utilizan datos de comportamiento. Si desea empezar rápidamente, puede utilizar los siguientes tipos de recomendaciones de solo catálogo:

- `More like this`
- `Visual similarity`

Entonces, ¿cuándo puede empezar a usar tipos de recomendaciones que utilizan datos de comportamiento? Depende. Esto se denomina _Inicio en frío_ problema.

La variable _Inicio en frío_ El problema es una medida del tiempo que un modelo necesita entrenar antes de que pueda considerarse de alta calidad. En las recomendaciones de productos, significa esperar a que Adobe Sensei forme sus modelos de aprendizaje automático antes de implementar unidades de recomendación en el sitio. Cuantos más datos tengan estos modelos, más precisas y útiles serán las recomendaciones. La recopilación de estos datos lleva tiempo y varía en función del volumen de tráfico. Dado que estos datos solo se pueden recopilar en un sitio de producción, lo más recomendable es implementar allí la recopilación de datos lo antes posible. Puede hacerlo de [instalación y configuración](install-configure.md) el `magento/production-recommendations` módulo.

En la tabla siguiente se proporcionan algunas directrices generales sobre la cantidad de tiempo que se tarda en recopilar datos suficientes para cada tipo de recomendación:

| Tipo de recomendación | Tiempo de prueba | Notas |
|---|---|---|
| Basado en popularidad (`Most viewed`, `Most purchased`, `Most added to cart`) | Varía | Depende del volumen de eventos: las vistas son más comunes y, por lo tanto, aprenden más rápido; luego agrega al carro de compras y luego compra |
| `Viewed this, viewed that` | Requiere más formación | El volumen de las vistas de productos es bastante alto |
| `Viewed this, bought that`, `Bought this, bought that` | Requiere la mayor formación | Los eventos de compra son los eventos más raros del sitio de comercio, especialmente en comparación con las vistas de productos |
| `Trending` | Requiere tres días de datos para establecer una línea de base de popularidad | La tendencia es una medida del impulso reciente en la popularidad de un producto comparada con su propio punto de referencia de popularidad. La puntuación de tendencia de un producto se calcula utilizando un conjunto en primer plano (popularidad reciente de más de 24 horas) y un conjunto de antecedentes (línea de base de popularidad de más de 72 horas). Si un elemento se ha vuelto mucho más popular en las últimas 24 horas en comparación con su popularidad de línea base, entonces recibe una puntuación de tendencia alta. Cada producto tiene esta puntuación, y los más altos en cualquier momento comprenden el conjunto de productos de mayor tendencia. |

Otras variables que pueden afectar al tiempo necesario para la formación:

- Un mayor volumen de tráfico contribuye a un aprendizaje más rápido
- Algunos tipos de recomendaciones se entrenan más rápido que otros
- Adobe Commerce vuelve a calcular los datos de comportamiento cada cuatro horas. Aunque técnicamente puede implementar las unidades de recomendación en ese momento, sepa que las recomendaciones son más precisas cuanto más tiempo se usen en el sitio.

Para ayudarle a visualizar el progreso de formación de cada tipo de recomendación, la variable [crear recomendación](create.md) muestra los indicadores de disponibilidad.

Mientras que los datos se recopilan en los modelos de producción y aprendizaje automático están formados, puede implementar la variable [tareas restantes](implementation-workflow.md) necesario para implementar recomendaciones en su tienda. Para cuando haya terminado de probar y configurar las recomendaciones, los modelos de aprendizaje automático han recopilado y calculado datos suficientes para crear recomendaciones relevantes, lo que le permite implementar las recomendaciones en su tienda.

## Recomendaciones de copia de seguridad {#backuprecs}

Si no hay datos de entrada suficientes para proporcionar todos los artículos de recomendación solicitados en una unidad, Adobe Commerce proporciona recomendaciones de copia de seguridad para rellenar las unidades de recomendación. Por ejemplo, si implementa el `Recommended for you` tipo de recomendación para su página principal, un comprador nuevo en su sitio no ha generado suficientes datos de comportamiento para productos personalizados recomendados con precisión. En este caso, Adobe Commerce muestra elementos basados en la variable `Most viewed` tipo de recomendación a este comprador.

Los siguientes tipos de recomendación se devuelven a `Most viewed` tipo de recomendación si no se recopilan suficientes datos de entrada:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
