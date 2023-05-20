---
title: Tipos de recomendación
description: Obtenga información acerca de las recomendaciones que puede implementar en varias páginas del sitio.
exl-id: c3b16307-479b-4736-968b-b6ab38233a48
source-git-commit: 42cb709f4699fcdd56df7ca02466ab416f01cab2
workflow-type: tm+mt
source-wordcount: '1575'
ht-degree: 0%

---

# Tipos de recomendación

Adobe Commerce proporciona un gran conjunto de recomendaciones que puede implementar en varias páginas del sitio. Todos los tipos de recomendación están basados en datos. Se basan en datos de comportamiento, datos de atributos de productos y métricas. Para facilitar la referencia, los tipos de recomendación se agrupan de la siguiente manera:

- [Personalizado](#personalized)
- [Venta cruzada y mejora de ventas](#crossup)
- [Popularidad](#popularity)
- [De alto rendimiento](#highperf)

Como práctica recomendada, Adobe recomienda las siguientes directrices al utilizar Recommendations:

- Diversifique los tipos de recomendaciones. Los clientes empiezan a ignorar las recomendaciones si sugieren los mismos productos una y otra vez.

- No implemente las mismas recomendaciones en la página del carro de compras y en la página de confirmación de pedidos. Considere utilizar `Most Added to Cart` para la página del carro de compras y `Bought This, Bought That` para la página de confirmación del pedido.

- Mantenga su sitio ordenado. No implemente más de tres unidades de recomendación en la misma página.

- Si su tienda vende ropa, la `More like this` La recomendación puede sugerir productos específicos del sexo que no coinciden con el sexo del producto que se está viendo. Considere utilizar este tipo de recomendación solo para categorías que no sean de ropa.

## Personalizado {#personalized}

Estos tipos de recomendación recomiendan productos basados en el historial de comportamiento del comprador específico en el sitio.

| Tipo | Descripción |
|---|---|
| Recomendado para usted | Recomienda productos en función del comportamiento actual y anterior de cada comprador en el sitio. Muestra recomendaciones muy relevantes basadas en el historial de navegación y compra del comprador. Este tipo de recomendación es efectivo en la página de inicio donde la mayoría de los compradores comienzan su recorrido en un sitio. Para los compradores nuevos del sitio que no hayan generado ninguna señal para personalizar su experiencia, Adobe Commerce muestra los productos en función del tipo de recomendación Más visitado. Sin embargo, cuando el comprador comienza a interactuar con los productos en el sitio, los productos recomendados se ajustan en tiempo real a su comportamiento.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría <br/><br/>**Etiquetas sugeridas:**<br/> - Solo para ti<br/>- Recomendado para usted<br/>- Inspirado en sus tendencias de compra |
| Vistos recientemente | Muestra los productos que el comprador ha visto más recientemente en función del historial del explorador. La unidad de recomendación elimina todos los productos eliminados. La unidad de recomendación no se muestra si no hay historial de explorador o no hay suficiente historial cuando se aplican reglas de filtro. Si los resultados contienen menos productos que los configurados, la unidad de recomendación solo muestra los productos devueltos.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Vistos recientemente<br/>- Eche otro vistazo |

## Venta cruzada y mejora de ventas {#crossup}

Estos tipos de recomendación están orientados a la prueba social para ayudar a los compradores a encontrar lo que les gustó a otros o están impulsados por productos para ayudarles a encontrar otros productos similares

| Tipo | Descripción |
|---|---|
| Vio esto, vio aquello. | Recomienda productos que los compradores ven con mayor frecuencia y de forma desproporcionada con el producto visualizado actualmente.<br/><br/>**Dónde se utiliza:**<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Los clientes que vieron este producto también vieron (PDP) |
| Vio esto, compró aquello. | Recomienda productos que los compradores tienden a comprar con desproporción con mayor frecuencia después de ver el producto actual. Ayuda a guiar a los compradores para descubrir productos que de otra manera no habrían notado.<br/><br/>**Dónde se utiliza:**<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Los clientes que vieron este Ultimate compraron<br/>- Clientes que finalmente compraron<br/>- ¿Qué compran los demás después de ver este producto? |
| Compré esto, compré aquello. | Recomienda productos que los compradores compran con una frecuencia desproporcionada mayor con el producto visualizado actualmente. Se suele utilizar en el carro de compras o en la página de detalles del producto para aumentar la exposición del producto de venta cruzada relacionado y aumentar el valor promedio de pedido. Muestra productos de gran relevancia que los compradores pueden añadir al carro de compras sumando lo que otros compradores han comprado con el producto actual.<br/><br/>**Dónde se utiliza:**<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Consigue todo lo que necesites<br/>- No te olvides de estos<br/>- Comprados frecuentemente juntos |
| Más parecido a esto | Recomienda productos basados en metadatos similares como nombre, descripción, asignación de categorías y atributos. Al evaluar los atributos de los productos que se están viendo, recomienda productos similares en la misma categoría. Por ejemplo, si un comprador está explorando alfombras de yoga, se recomiendan otros productos en la categoría de equipamiento. Dado que este tipo de recomendación no distingue entre géneros, no se recomienda para prendas de vestir, moda u otros verticales específicos de género.<br/><br/>**Dónde se utiliza:**<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Más productos como este<br/>- Similar a esto |
| [Similitud visual](#visualsim) | Recomienda productos de aspecto similar al producto que se está viendo. Este tipo de recomendación es más útil si las imágenes y los aspectos visuales de los productos son importantes para la experiencia de compra. |

## Popularidad {#popularity}

Estos tipos de recomendación recomiendan productos que son los más populares o los que han sido tendencia en los últimos siete días.

| Tipo | Descripción |
|---|---|
| Más visitados | Recomienda los productos que más se vieron contando la cantidad de sesiones en las que se produjo una acción de visualización en los últimos siete días.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- El más popular<br/>- Tendencia<br/>- Popular en este momento<br/>- Recientemente popular<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más comprados | Recomienda los productos comprados con mayor frecuencia por los compradores en los últimos siete días.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - El más popular<br/>- Tendencia<br/>- Popular en este momento<br/>- Recientemente popular<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más añadidos al carro | Recomienda los productos que los compradores añaden con mayor frecuencia a los carros de compras en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - El más popular<br/>- Tendencia<br/>- Popular en este momento<br/>- Recientemente popular<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Tendencia | Recomienda productos en función del impulso reciente de la popularidad de un producto en todo el sitio.<br/><br/>Adobe Sensei agrega datos de compra y navegación a todo el sitio para determinar y clasificar qué productos son los más populares entre los compradores. Dado que Trending analiza el impulso reciente del producto, es un tipo de recomendación eficaz para los catálogos que tienen una alta rotación. Si el catálogo es más estático, puede que no sea tan útil a menos que los patrones de compra de la audiencia sean muy variables.<br/><br/>Cuando se utiliza en la página de inicio, Tendencia recomienda productos que son populares recientemente en todo el sitio. Las tendencias no muestran productos que son populares de manera consistente, sino más bien aquellos que se han vuelto populares recientemente. Por ejemplo, si tiene una campaña de marketing por correo electrónico que promociona determinados productos, el aumento de popularidad generado por el correo electrónico aumenta la probabilidad de que los productos promocionados se clasifiquen como tendencias.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/>- Tendencia<br/>- Tendencia ahora<br/>- Tendencias recientes<br/>- Productos calientes<br/>- Productos relacionados con las tendencias (PDP) |

## Alto rendimiento {#highperf}

Estos tipos de recomendación recomiendan productos de mayor rendimiento según criterios de éxito como las tasas de conversión o de complementos al carro de compras.

| Tipo | Descripción |
|---|---|
| Ver para adquirir la conversión | Recomienda productos con la tasa de conversión de vista a compra más alta. De todas las sesiones de compradores que registraron una vista de producto, ¿cuál es la proporción que finalmente registró una compra por parte del comprador?<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> -Principales vendedores<br/>- Productos populares<br/>- Podría estar interesado en |
| Ver conversión al carro de compras | Recomienda productos con la mayor tasa de conversión de vista a carro. De todas las sesiones de compradores que registraron una vista de producto, ¿cuál es la proporción que finalmente registró un anuncio al carro de compras del comprador?<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - Principales vendedores<br/>- Productos populares<br/>- Podría estar interesado en |
| Más comprados | A menudo denominado &quot;Principales vendedores&quot;, este tipo de recomendación cuenta el número de sesiones en las que se produjo una acción de pedido en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - El más popular<br/>- Tendencia<br/>- Popular en este momento<br/>- Recientemente popular<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |
| Más añadidos al carro | Recomienda los productos que los compradores añaden con mayor frecuencia a los carros de compras en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br/><br/>**Dónde se utiliza:**<br/>- Página de inicio<br/>- Categoría<br/>- Detalles del producto<br/>- Carro<br/>- Confirmación <br/><br/>**Etiquetas sugeridas:**<br/> - El más popular<br/>- Tendencia<br/>- Popular en este momento<br/>- Recientemente popular<br/>- Productos populares inspirados en este producto (PDP)<br/>- Principales vendedores |

## Similitud visual {#visualsim}

El _Similitud visual_ el tipo de recomendación recomienda productos de aspecto similar al producto que se está viendo. Este tipo de recomendación es más útil cuando las imágenes y los aspectos visuales de los productos son partes importantes de la experiencia de compra.

### Cómo funciona

El _Similitud visual_ recommendations ofrece recomendaciones para otros productos del catálogo que tienen una similitud visual con las imágenes que se están viendo en ese momento. La similitud visual incluye aspectos como:

- Color
- Forma
- Tamaño
- Textura
- Material
- Estilo

Adobe Sensei utiliza IA para procesar y analizar las imágenes del catálogo y crear atributos utilizados para determinar similitudes visuales.

>[!NOTE]
>
> Si está probando este tipo de recomendación en un entorno que no es de producción, asegúrese de que las URL de la imagen sean accesibles públicamente.

>[!NOTE]
>
> Actualmente, las imágenes de producto deben tener un tamaño de 10 MB o menos.

Debido a que este tipo de recomendación no es aplicable a la mayoría de los catálogos, no está habilitado de forma predeterminada. Debe habilitar explícitamente este tipo de recomendación.

### Habilitar tipo de recomendación de similitud visual

>[!NOTE]
>
> El _Similitud visual_ el tipo de recomendación está disponible cuando [instalar](install-configure.md) como módulo opcional.

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Product Recommendations** para mostrar el _Product Recommendations_ panel.

1. Clic **Configuración** (icono del engranaje) para mostrar el _Configuración_ página.

1. En el _Visual Recommendations_ , seleccione para **Habilitar Visual Recommendations**.

1. Clic **Guardar cambios** cuando haya terminado.

   El [Crear nueva recomendación](create.md) ahora muestra la página **Similitud visual** como un tipo de recomendación seleccionable cuando el tipo de página es **Detalles del producto**.

Después de habilitar las recomendaciones visuales, Adobe Sensei inicia el procesamiento de imágenes. El tiempo que tarda depende del tamaño del catálogo.

### Dónde se utiliza

- Detalles del producto

### Etiquetas de tienda sugeridas

- También le puede gustar
- Encontramos otros productos que te pueden gustar
- Inspirado en este estilo

### Ejemplo

La siguiente imagen muestra la página de detalles del producto para _Reloj Clamber_:

![Reloj Clamber](assets/visual-sim-pdp.png)

A continuación se muestra el _Similitud visual_ unidad de recomendación para _Reloj Clamber_:

![Unidad de similitud visual](assets/visual-sim-unit.png)
