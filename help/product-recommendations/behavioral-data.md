---
title: Datos de comportamiento
description: Obtenga información sobre los datos de comportamiento y cuándo puede empezar a utilizarlos.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Datos de comportamiento

Algunos tipos de recomendación utilizan datos de comportamiento de los compradores para entrenar modelos de aprendizaje automático y crear recomendaciones personalizadas. Otros tipos de recomendación solo utilizan datos de catálogo y no utilizan datos de comportamiento. Si desea comenzar rápidamente, puede utilizar los siguientes tipos de recomendaciones solo de catálogo:

- `More like this`
- `Visual similarity`

Por lo tanto, ¿cuándo puede empezar a utilizar tipos de recomendación que utilicen datos de comportamiento? Depende de ti. Este problema se conoce como _Inicio en frío_.

El problema de _inicio en frío_ es una medida de cuánto tiempo necesita un modelo para entrenarse antes de que pueda considerarse de alta calidad. En las recomendaciones de productos, se traduce en esperar a que Adobe Sensei entrene sus modelos de aprendizaje automático antes de implementar unidades de recomendaciones en el sitio. Cuantos más datos tengan estos modelos, más precisas y útiles serán las recomendaciones. La recopilación de estos datos lleva tiempo y varía en función del volumen de tráfico. Como estos datos solo se pueden recopilar en un sitio de producción, lo mejor es implementar la recopilación de datos allí lo antes posible. Puede hacerlo [instalando y configurando](install-configure.md) el módulo `magento/production-recommendations`.

La siguiente tabla proporciona algunas directrices generales sobre la cantidad de tiempo que se tarda en recopilar suficientes datos para cada tipo de recomendación:

| Tipo de recomendación | Tiempo de formación | Notas |
|---|---|---|
| Basado en popularidad (`Most viewed`, `Most purchased`, `Most added to cart`) | Varía | Depende del volumen de eventos: las vistas son los más comunes y, por lo tanto, aprende más rápido; luego agrega al carro de compras y, por último, compra |
| `Viewed this, viewed that` | Requiere más formación | El volumen de las vistas de productos es decentemente alto |
| `Viewed this, bought that`, `Bought this, bought that` | Requiere la mayor cantidad de formación | Los eventos de compra son los eventos más raros en el sitio de comercio, especialmente en comparación con las vistas de productos |
| `Trending` | Se necesitan tres días de datos para establecer una línea de base de popularidad | La tendencia es una medida del impulso reciente en la popularidad de un producto en comparación con su propia línea de base de popularidad. La puntuación de tendencia de un producto se calcula mediante un conjunto en primer plano (popularidad reciente en 24 horas) y un conjunto de fondo (línea de base de popularidad en 72 horas). Si un artículo se ha vuelto mucho más popular en las últimas 24 horas en comparación con su popularidad de línea de base, entonces recibe una puntuación de tendencia alta. Cada producto tiene esta puntuación, y los más altos en cualquier momento comprenden el conjunto de los productos de tendencia superior. |

Otras variables que pueden afectar al tiempo necesario para entrenar:

- Un mayor volumen de tráfico contribuye a un aprendizaje más rápido
- Algunos tipos de recomendación se entrenan más rápido que otros
- Adobe Commerce vuelve a calcular los datos de comportamiento cada cuatro horas. Recommendations será más preciso cuanto más tiempo se utilice en el sitio.

Para ayudarle a visualizar el progreso de formación de cada tipo de recomendación, la página [crear recomendación](create.md) muestra indicadores de preparación.

Mientras se recopilan los datos en producción y se entrenan los modelos de aprendizaje automático, puede implementar las [tareas restantes](implementation-workflow.md) necesarias para implementar recomendaciones en su tienda. En el momento en que haya terminado de probar y configurar las recomendaciones, los modelos de aprendizaje automático han recopilado y calculado suficientes datos para crear recomendaciones relevantes, lo que le permite implementar las recomendaciones en su tienda.

Si no hay tráfico suficiente (vistas, productos comprados, tendencias) para la mayoría de las SKU, es posible que no haya suficientes datos para completar el proceso de aprendizaje. Esto puede hacer que el indicador de disponibilidad del administrador parezca atascado.
Los indicadores de preparación están pensados para proporcionar a los comerciantes otro punto de datos a la hora de elegir qué tipo de recomendaciones es mejor para su tienda. Los números son una guía y es posible que nunca alcancen el 100%.

## Recomendaciones de copia de seguridad {#backuprecs}

Si no hay datos de entrada suficientes para proporcionar todos los elementos de recomendación solicitados en una unidad, Adobe Commerce proporciona recomendaciones de copia de seguridad para rellenar las unidades de recomendación. Por ejemplo, si implementa el tipo de recomendación `Recommended for you` en su página de inicio, un comprador que visita por primera vez su sitio no ha generado suficientes datos de comportamiento para recomendar con precisión productos personalizados. En este caso, Adobe Commerce muestra artículos basados en el tipo de recomendación `Most viewed` a este comprador.

Los siguientes tipos de recomendación vuelven a `Most viewed` tipo de recomendación si no se recopilan suficientes datos de entrada:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
