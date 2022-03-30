---
title: Tipos de recomendación
description: Obtenga información sobre las recomendaciones que puede implementar en varias páginas del sitio.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 0%

---

# Tipos de recomendación

Adobe Commerce proporciona un gran conjunto de recomendaciones que puede implementar en varias páginas del sitio. Para facilitar la referencia, los tipos de recomendación se agrupan de la siguiente manera:

- [Personalizado](#personalized)
- [Ventas cruzadas y ventas ascendentes](#crossup)
- [Popularidad](#popularity)
- [Alto rendimiento](#highperf)

Como práctica recomendada, Adobe recomienda las siguientes directrices al utilizar las recomendaciones:

- Diversifique los tipos de recomendación. Los clientes comienzan a ignorar las recomendaciones si sugieren los mismos productos una y otra vez.

- No implemente las mismas recomendaciones en la página del carro de compras y en la página de confirmación del pedido. Considere utilizar `Most Added to Cart` para la página del carro de compras y `Bought This, Bought That` para la página de confirmación del pedido.

- Mantenga el sitio ordenado. No implemente más de tres unidades de recomendación en la misma página.

- Si su tienda vende ropa, la variable `More like this` puede sugerir artículos específicos de género que no coincidan con el sexo del producto que se está viendo. Considere utilizar solo este tipo de recomendación para categorías que no sean ropa.

## Personalizado {#personalized}

| Tipo | Descripción |
|---|---|
| Recomendado para usted | Recomienda artículos en función del comportamiento en el sitio actual y anterior de cada comprador. Muestra recomendaciones muy relevantes en función del historial de navegación y compras del comprador. Este tipo de recomendación es efectivo en la página principal donde la mayoría de los compradores inician su recorrido en un sitio. Para los compradores nuevos del sitio que no hayan generado ninguna señal para personalizar su experiencia, Adobe Commerce muestra los artículos en función del tipo de recomendación Más visitados. Sin embargo, cuando el comprador empieza a interactuar con los productos del sitio, los productos recomendados se ajustan en tiempo real a su comportamiento.<br /><br />Se utilizaban:<br /><br />- Página de inicio<br />- Categoría<br /><br />Etiquetas sugeridas:<br /><br /> - Sólo para ti<br />- Recomendado para usted<br />- Inspirado por las tendencias de compra |
| Vistos recientemente | Muestra los productos que el comprador ha visto más recientemente, según el historial del explorador. La unidad de recomendaciones elimina cualquier producto eliminado. La unidad de recomendación no se muestra si no hay historial del explorador o si no hay historial suficiente cuando se aplican las reglas de filtro. Si los resultados contienen menos productos de los que están configurados, la unidad de recomendación solo muestra los productos devueltos.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br />- Vistos recientemente<br />- Eche otro vistazo |

## Ventas cruzadas y ventas ascendentes {#crossup}

| Tipo | Descripción |
|---|---|
| Lo ha visto, ha visto que | Recomienda artículos vistos con mayor frecuencia por otros compradores que vieron el mismo artículo. A menudo se denomina recomendación de prueba social que ayuda a los compradores a encontrar productos como otros compradores.<br /><br />Donde se utiliza:<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br ><br />- Los clientes que vieron este artículo también vieron (PDP) |
| Visto esto, comprado que | Recommends items most often purchased by shoppers who viewed the specified item. Ayuda a guiar a los compradores a descubrir productos que de otra manera no habrían notado.<br /><br />Donde se utiliza:<br /><br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br />- Clientes que vieron esta última compra<br />- Clientes comprados finalmente<br />- ¿Qué compran otros después de ver este artículo? |
| Compré esto, compré aquello | Recomienda artículos comprados con mayor frecuencia por compradores que compraron el artículo especificado. La mayoría de las veces se utiliza en la página de detalles del producto o del carro de compras para aumentar la exposición de los productos de venta cruzada relacionados y así aumentar el valor promedio de los pedidos. Muestra productos de gran relevancia que los compradores pueden añadir al carro agregando lo que otros compradores han comprado con el producto actual.<br /><br />Donde se utiliza:<br /><br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br />- Obtenga todo lo que necesite<br />- No los olvide<br />- Compradas más a menudo |
| Más parecido a esto | Recomienda artículos basados en contenido y atributos similares. Al evaluar los atributos de los productos que se están viendo, recomienda productos similares en la misma categoría. Por ejemplo, si un comprador está navegando por las alfombras de yoga, se recomiendan otros productos de la categoría equipamiento. Because this recommendation type does not distinguish genders, it is not recommended for apparel, fashion, or other gender-specific verticals.<br /><br />Donde se utiliza:<br /><br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br /> - Más elementos como este<br />- Similar a esto |
| [Similitud visual](#visualsim) | Recomienda productos de aspecto similar al producto visualizado. This recommendation type is most useful if images and the visual aspects of products are important to the shopping experience. |

## Popularidad {#popularity}

| Tipo | Descripción |
|---|---|
| Más visitados | Recomienda productos que se vieron más contando el número de sesiones en las que se produjo una acción de visualización en los últimos siete días.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br />- Más popular<br />- Tendencias<br />- Popular ahora<br />: popular recientemente<br />- Elementos populares inspirados en este elemento (PDP)<br />- Principales vendedores |
| Tendencias | Recomienda artículos en función del impulso reciente de la popularidad de un producto en todo el sitio.<br /><br />Adobe Sensei agrega datos de navegación y compras en el sitio para determinar y clasificar qué productos son los más populares entre los compradores. Debido a que Trending analiza el impulso del producto reciente, es un tipo de recomendación eficaz para los catálogos que tienen un alto volumen de negocios. Si el catálogo es más estático, puede que no sea tan útil a menos que los patrones de compra de la audiencia sean muy variables.<br /><br />Cuando se usa en la página principal, Tendencia recomienda artículos que son populares recientemente en todo el sitio. Las tendencias no muestran los productos que son populares de manera consistente, sino los que se han hecho populares recientemente. Por ejemplo, si tiene una campaña de marketing por correo electrónico que promociona ciertos productos, el aumento de popularidad generado por el correo electrónico aumenta la probabilidad de que los productos promocionados se clasifiquen como tendencias.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br />- Tendencias<br />- Tendencias ahora<br />- Tendencias recientes<br />- Elementos activos<br />- Tendencias de productos relacionados (PDP) |

## Alto rendimiento {#highperf}

| Tipo | Description |
|---|---|
| Ver para comprar la conversión | Recomienda productos con la mayor tasa de conversión de vista a compra. De todas las sesiones del comprador que vieron el producto, el porcentaje que compró el producto.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br /> -Principales vendedores<br />- Elementos populares<br />- Puede estar interesado en |
| View to cart conversion | Recomienda productos con la mayor tasa de conversión de vista al carro de compras. De todas las sesiones de compradores que vieron el producto, el porcentaje que agregó el producto al carro de compras.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br /> - Principales vendedores<br />- Elementos populares<br />- Puede estar interesado en |
| Más compradas | A menudo denominados &quot;Principales vendedores&quot;, este tipo de recomendación cuenta el número de sesiones en las que se produjo una acción de pedido en los últimos siete días. Este tipo de recomendación se puede utilizar en todas las páginas.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br /> - Más popular<br />- Tendencias<br />- Popular ahora<br />: popular recientemente<br />- Elementos populares inspirados en este elemento (PDP)<br />- Principales vendedores |
| Most added to cart | Recommends items most frequently added to carts by shoppers within the last seven days. Este tipo de recomendación se puede utilizar en todas las páginas.<br /><br />Donde se utiliza:<br /><br />- Página de inicio<br />- Categoría<br />- Detalles del producto<br />- Carro de compras<br />- Confirmación<br /><br />Etiquetas sugeridas:<br /><br /> - Más popular<br />- Tendencias<br />- Popular ahora<br />: popular recientemente<br />- Elementos populares inspirados en este elemento (PDP)<br />- Principales vendedores |

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
