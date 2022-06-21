---
title: Tipos de recomendación
description: Obtenga información sobre las recomendaciones que puede implementar en varias páginas del sitio.
exl-id: c3b16307-479b-4736-968b-b6ab38233a48
source-git-commit: 42cb709f4699fcdd56df7ca02466ab416f01cab2
workflow-type: tm+mt
source-wordcount: '1575'
ht-degree: 0%

---

# Tipos de recomendación

Adobe Commerce proporciona un gran conjunto de recomendaciones que puede implementar en varias páginas del sitio. Todos los tipos de recomendación están basados en datos. Están basadas en datos de comportamiento, datos de atributos de producto y métricas. Para facilitar la referencia, los tipos de recomendación se agrupan de la siguiente manera:

- [Personalizado](#personalized)
- [Ventas cruzadas y ventas ascendentes](#crossup)
- [Popularidad](#popularity)
- [Alto rendimiento](#highperf)

Como práctica recomendada, Adobe recomienda las siguientes directrices al utilizar las recomendaciones:

- Diversifique los tipos de recomendación. Los clientes comienzan a ignorar las recomendaciones si sugieren los mismos productos una y otra vez.

- No implemente las mismas recomendaciones en la página del carro de compras y en la página de confirmación del pedido. Considere utilizar `Most Added to Cart` para la página del carro de compras y `Bought This, Bought That` para la página de confirmación del pedido.

- Mantenga el sitio ordenado. No implemente más de tres unidades de recomendación en la misma página.

- Si su tienda vende ropa, la variable `More like this` puede sugerir productos específicos de género que no coincidan con el sexo del producto que se está viendo. Considere utilizar este tipo de recomendación solo para categorías que no sean de ropa.

## Personalizado {#personalized}

Estos tipos de recomendaciones recomiendan los productos según el historial de comportamiento del comprador en el sitio.

| Tipo | Descripción |
|---|---|
| Recomendado para usted | Recomienda productos en función del comportamiento en el sitio actual y anterior de cada comprador. Muestra recomendaciones muy relevantes en función del historial de navegación y compras del comprador. Este tipo de recomendación es efectivo en la página principal donde la mayoría de los compradores inician su recorrido en un sitio. Para los compradores nuevos del sitio que no hayan generado ninguna señal para personalizar su experiencia, Adobe Commerce muestra los productos en función del tipo de recomendación Más visitados. Sin embargo, cuando el comprador empieza a interactuar con los productos del sitio, los productos recomendados se ajustan en tiempo real a su comportamiento.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría <br/><br/>**Etiquetas sugeridas:**<br/> - Sólo para ti<br/>- Recomendado para usted<br/>- Inspirado por las tendencias de compra |
| Vistos recientemente | Muestra los productos que el comprador ha visto más recientemente, según el historial del explorador. La unidad de recomendaciones elimina cualquier producto eliminado. La unidad de recomendación no se muestra si no hay historial del explorador o si no hay historial suficiente cuando se aplican las reglas de filtro. Si los resultados contienen menos productos de los que están configurados, la unidad de recomendación solo muestra los productos devueltos.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Vistos recientemente<br/>- Eche otro vistazo |

## Ventas cruzadas y ventas ascendentes {#crossup}

Estos tipos de recomendaciones son de prueba social y están dirigidos a ayudar a los compradores a encontrar lo que les gusta a otros o están basados en productos para ayudarles a encontrar otros productos similares

| Tipo | Descripción |
|---|---|
| Lo ha visto, ha visto que | Recomienda productos que los compradores ven con una frecuencia desproporcionada con mayor frecuencia con el producto visualizado actualmente.<br/><br/>**Donde se utiliza:**<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Los clientes que vieron este producto también vieron (PDP) |
| Visto esto, comprado que | Recomienda productos que los compradores tienden a comprar desproporcionadamente más a menudo después de ver el producto actual. Ayuda a guiar a los compradores a descubrir productos que de otra manera no habrían notado.<br/><br/>**Donde se utiliza:**<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Clientes que vieron esta última compra<br/>- Clientes comprados finalmente<br/>- ¿Qué compran otros después de ver este producto? |
| Compré esto, compré aquello | Recomienda productos que los compradores compran con una frecuencia desproporcionada con el producto visualizado actualmente. La mayoría de las veces se utiliza en la página de detalles del producto o del carro de compras para aumentar la exposición de los productos de venta cruzada relacionados y así aumentar el valor promedio de los pedidos. Muestra productos de gran relevancia que los compradores pueden añadir al carro agregando lo que otros compradores han comprado con el producto actual.<br/><br/>**Donde se utiliza:**<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Obtenga todo lo que necesite<br/>- No los olvide<br/>- Compradas más a menudo |
| Más parecido a esto | Recomienda productos basados en metadatos similares como nombre, descripción, asignación de categoría y atributos. Al evaluar los atributos de los productos que se están viendo, recomienda productos similares en la misma categoría. Por ejemplo, si un comprador está navegando por las alfombras de yoga, se recomiendan otros productos de la categoría equipamiento. Debido a que este tipo de recomendación no distingue entre géneros, no se recomienda para ropa, moda u otros verticales específicos de género.<br/><br/>**Donde se utiliza:**<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más productos como este<br/>- Similar a esto |
| [Similitud visual](#visualsim) | Recomienda productos de aspecto similar al producto visualizado. Este tipo de recomendación es más útil si las imágenes y los aspectos visuales de los productos son importantes para la experiencia de compra. |

## Popularidad {#popularity}

Estos tipos de recomendaciones recomiendan los productos más populares o de mayor tendencia en los últimos siete días.

| Tipo | Descripción |
|---|---|
| Más visitados | Recomienda productos que se vieron más contando el número de sesiones en las que se produjo una acción de visualización en los últimos siete días.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Más popular<br/>- Tendencias<br/>- Popular ahora<br/>: popular recientemente<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más compradas | Recomienda productos comprados con mayor frecuencia por compradores en los últimos siete días.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más popular<br/>- Tendencias<br/>- Popular ahora<br/>: popular recientemente<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más agregadas al carro de compras | Recomienda productos añadidos con mayor frecuencia al carro de compras por los compradores en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más popular<br/>- Tendencias<br/>- Popular ahora<br/>: popular recientemente<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Tendencias | Recomienda productos en función del impulso reciente de la popularidad de un producto en todo el sitio.<br/><br/>Adobe Sensei agrega datos de navegación y compras en el sitio para determinar y clasificar qué productos son los más populares entre los compradores. Debido a que Trending analiza el impulso del producto reciente, es un tipo de recomendación eficaz para los catálogos que tienen un alto volumen de negocios. Si el catálogo es más estático, puede que no sea tan útil a menos que los patrones de compra de la audiencia sean muy variables.<br/><br/>Cuando se usa en la página principal, Tendencia recomienda productos que son populares recientemente en todo el sitio. Las tendencias no muestran los productos que son populares de manera consistente, sino los que se han hecho populares recientemente. Por ejemplo, si tiene una campaña de marketing por correo electrónico que promociona ciertos productos, el aumento de popularidad generado por el correo electrónico aumenta la probabilidad de que los productos promocionados se clasifiquen como tendencias.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Tendencias<br/>- Tendencias ahora<br/>- Tendencias recientes<br/>- Productos calientes<br/>- Tendencias de productos relacionados (PDP) |

## Alto rendimiento {#highperf}

Estos tipos de recomendaciones recomiendan los productos de mayor rendimiento en función de criterios de éxito, como los complementos al carro o las tasas de conversión.

| Tipo | Descripción |
|---|---|
| Ver para comprar la conversión | Recomienda productos con la mayor tasa de conversión de vista a compra. De todas las sesiones del comprador que registraron una vista de producto, cuál es la proporción que eventualmente registró una compra por parte del comprador.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> -Principales vendedores<br/>- Productos populares<br/>- Puede estar interesado en |
| Ver conversión al carro de compras | Recomienda productos con la mayor tasa de conversión de vista al carro de compras. De todas las sesiones del comprador que registraron una vista de producto, ¿cuál es la proporción que eventualmente registró un anuncio al carro de compras por parte del comprador?<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Principales vendedores<br/>- Productos populares<br/>- Puede estar interesado en |
| Más compradas | A menudo denominados &quot;Principales vendedores&quot;, este tipo de recomendación cuenta el número de sesiones en las que se produjo una acción de pedido en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más popular<br/>- Tendencias<br/>- Popular ahora<br/>: popular recientemente<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más agregadas al carro de compras | Recomienda productos añadidos con mayor frecuencia al carro de compras por los compradores en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Donde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro de compras<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más popular<br/>- Tendencias<br/>- Popular ahora<br/>: popular recientemente<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |

## Similitud visual {#visualsim}

La variable _Similitud visual_ el tipo de recomendación recomienda productos de aspecto similar al producto que se está viendo. Este tipo de recomendación es más útil cuando las imágenes y los aspectos visuales de los productos son partes importantes de la experiencia de compra.

### Funcionamiento

La variable _Similitud visual_ el tipo de recomendación ofrece recomendaciones para otros productos del catálogo que tengan una similitud visual con las imágenes que se están viendo en ese momento. La similitud visual incluye aspectos como:

- Color
- Forma
- Tamaño
- Textura
- Material
- Estilo

Adobe Sensei utiliza la IA para procesar y analizar las imágenes del catálogo y crear atributos utilizados para determinar las similitudes visuales.

>[!NOTE]
>
> Si está probando este tipo de recomendación en un entorno que no sea de producción, asegúrese de que las URL de su imagen sean de acceso público.

>[!NOTE]
>
> Actualmente, las imágenes de producto deben tener un tamaño de 10 MB o menos.

Dado que este tipo de recomendación no es aplicable a la mayoría de los catálogos, no está habilitado de forma predeterminada. Debe habilitar explícitamente este tipo de recomendación.

### Habilitar Tipo de recomendación de similitud visual

>[!NOTE]
>
> La variable _Similitud visual_ el tipo de recomendación está disponible cuando [instalar](install-configure.md) como módulo opcional.

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Recommendations de producto** para mostrar el _Recommendations de producto_ tablero.

1. Haga clic en **Configuración** (icono de engranaje) para mostrar el _Configuración_ página.

1. En el _Visual Recommendations_ , seleccione **Habilitar Visual Recommendations**.

1. Haga clic en **Guardar cambios** cuando haya terminado.

   La variable [Crear nueva recomendación](create.md) ahora se muestra la página **Similitud visual** como tipo de recomendación seleccionable cuando el tipo de página es **Detalles del producto**.

Después de habilitar las recomendaciones visuales, Adobe Sensei inicia el procesamiento de imágenes. El tiempo que tarda depende del tamaño del catálogo.

### Donde se utiliza

- Detalles del producto

### Etiquetas de tienda sugeridas

- También puede gustarle
- Encontramos otros productos que usted podría necesitar
- Inspirado en este estilo

### Ejemplo

La siguiente imagen muestra la página de detalles del producto para la variable _Clamber Watch_:

![Clamber Watch](assets/visual-sim-pdp.png)

A continuación se muestra el _Similitud visual_ unidad de recomendaciones para _Clamber Watch_:

![Unidad de similitud visual](assets/visual-sim-unit.png)
