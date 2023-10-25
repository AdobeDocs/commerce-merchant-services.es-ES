---
title: Crear nueva recomendación
description: Obtenga información sobre cómo crear una unidad de recomendación de productos.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 24a930178873535f23331c9c5295c482d5b8e384
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 0%

---

# Crear nueva recomendación

Cuando crea una recomendación, crea un _unidad de recomendación_ que contiene el producto recomendado _items_.

![Unidad de recomendación](assets/unit.png)
_Unidad de recomendación_

Cuando activa la unidad de recomendación, Adobe Commerce empieza a [recopilar datos](workspace.md) para medir impresiones, vistas, clics, etc. El [!DNL Product Recommendations] La tabla muestra las métricas de cada unidad de recomendación para ayudarle a tomar decisiones comerciales fundadas.

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Product Recommendations** para mostrar el _Product Recommendations_ workspace.

1. Especifique el [Vista de tienda](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) donde desee que se muestren las recomendaciones.

   >[!NOTE]
   >
   > Las unidades de recomendación de Page Builder deben crearse en la vista de tienda predeterminada, pero luego pueden utilizarse en cualquier lugar. Para obtener más información sobre la creación de recomendaciones de productos con Page Builder, consulte [Añadir contenido: Recommendations del producto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Clic **Crear recomendación**.

1. En el _Asigne un nombre a la recomendación_ , introduzca un nombre descriptivo para la referencia interna, como `Home page most popular`.

1. En el _Seleccionar tipo de página_ , seleccione la página en la que desea que aparezca la recomendación entre las siguientes opciones:

   * Página principal
   * Categoría
   * Detalles del producto
   * Carrito
   * Confirmación
   * [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Puede crear hasta cinco unidades de recomendación activas para cada tipo de página y hasta 25 para Page Builder. El tipo de página aparece atenuado cuando se alcanza el límite.

   ![Nombre y página de la recomendación](assets/create-recommendation.png)
   _Nombre de recomendación y ubicación de página_

1. En el _Seleccionar tipo de recomendación_ , especifique la [tipo de recomendación](type.md) desea que aparezca en la página seleccionada. En algunas páginas, la variable [ubicación](placement.md) de recomendaciones se limita a determinados tipos.

1. En el _Etiqueta de visualización de tienda_ , introduzca la [etiqueta](placement.md#recommendation-labels) que es visible para los compradores, como &quot;Principales vendedores&quot;.

1. En el _Elija el número de productos_ , utilice el control deslizante para especificar cuántos productos desea que aparezcan en la unidad de recomendación.

   El valor predeterminado es `5`, con un máximo de `20`.

1. En el _Seleccionar ubicación_ , especifique la ubicación donde aparecerá la unidad de recomendación en la página.

   * Al final del contenido principal
   * Al principio del contenido principal

1. (Opcional) Para cambiar el orden de las recomendaciones, seleccione y mueva las filas de la _Elegir posición_ tabla.

   El _Elegir posición_ Esta sección muestra todas las recomendaciones (si las hay) creadas para el tipo de página seleccionado.

   ![Orden de recomendación](assets/create-recommendation-select-placement.png)
   _Orden de recomendación en la página_

1. (Opcional) En el _Filtros_ sección, [aplicar filtros](filters.md) para controlar qué productos aparecen en la unidad de recomendación.

   ![Filtros de recomendación](assets/create-recommendation-filter-products.png)
   _Filtros de productos de Recommendations_

1. Cuando termine, haga clic en una de las siguientes opciones:

   * **Guardar como borrador** para editar la unidad de recomendación más adelante. No se puede modificar el tipo de página o el tipo de recomendación de una unidad de recomendación en estado de borrador.

   * **Activar** para habilitar la unidad de recomendación en la tienda.

## Indicadores de preparación

Algunos tipos de recomendación utilizan datos de comportamiento de sus compradores para lo siguiente [entrenar modelos de aprendizaje automático](behavioral-data.md) para crear recomendaciones personalizadas.

Solo requiere datos de catálogo. No se necesitan datos de comportamiento para estos:

* _Más parecido a esto_
* _Vistos recientemente_
* _Similitud visual_

Basado en los últimos seis meses de datos de comportamiento de la tienda:

* _Vio esto, vio aquello._
* _Vio esto, compró aquello._
* _Compré esto, compré aquello._
* _Recomendado para usted_

Los tipos de recomendación basados en popularidad utilizan los últimos siete días de datos de comportamiento de tienda:

* Más visitados
* Más comprados
* Añadido al carro
* Tendencia

Se espera que los valores del indicador de preparación fluctúen debido a factores como el tamaño general del catálogo, el volumen de eventos de interacción de productos (vistas, adiciones al carro de compras, compras) y el porcentaje de SKU que registran esos eventos en un intervalo de tiempo determinado, como se ha indicado anteriormente. Por ejemplo, durante el tráfico máximo de la temporada de vacaciones, los indicadores de disponibilidad pueden mostrar valores más altos que en tiempos de volumen normal.

Para ayudarle a visualizar el progreso de formación de cada tipo de recomendación, la variable _Seleccionar tipo de recomendación_ muestra una medida de la disponibilidad para cada tipo. Estos indicadores de preparación se calculan en función de un par de factores:

* Tamaño suficiente del conjunto de resultados: ¿Hay suficientes resultados devueltos en la mayoría de los casos para evitar el uso de? [recomendaciones de copia de seguridad](behavioral-data.md#backuprecs)?

* Variedad del conjunto de resultados suficiente: ¿los productos que se devuelven representan una variedad de productos del catálogo? El objetivo con este factor es evitar tener una minoría de productos siendo los únicos recomendados en todo el sitio.

En función de los factores anteriores, se calcula y se muestra un valor de disponibilidad. Un tipo de recomendación se considera listo para implementar cuando su valor de preparación es del 75 % o superior. Un tipo de recomendación se considera parcialmente listo cuando su preparación es de al menos el 50 %. Un tipo de recomendación se considera no listo para implementarse cuando su valor de preparación es inferior al 50 %. Estas son directrices generales, pero cada caso individual puede variar en función de la naturaleza de los datos recopilados, tal como se ha descrito anteriormente.

![Tipo de recomendación](assets/create-recommendation-select-type.png)
_Tipo de recomendación_

>[!NOTE]
>
>Los indicadores nunca pueden alcanzar el 100%.

## Previsualizar Recommendations {#preview}

El _Previsualización de productos recomendados_ el panel siempre está disponible con una selección de muestra de productos que podrían aparecer en la unidad de recomendación cuando se implemente en la tienda.

Para probar una recomendación cuando se trabaja en un entorno que no es de producción, puede recuperar datos de recomendación de un [fuente diferente](settings.md). Esto permite a los comerciantes experimentar con las reglas y previsualizar las recomendaciones antes de implementarlas en la producción.

| Campo | Descripción |
|---|---|
| Nombre | El nombre del producto. |
| SKU | La unidad de stock asignada al producto |
| Precio | El precio del producto. |
| Tipo de resultado | Principal: indica que hay suficientes datos de formación recopilados para mostrar una recomendación.<br />Copia de seguridad: indica que no se han recopilado suficientes datos de formación, por lo que se utiliza una recomendación de copia de seguridad para rellenar el espacio. Ir a [Datos de comportamiento](behavioral-data.md) para obtener más información sobre los modelos de aprendizaje automático y las recomendaciones de backup. |

A medida que cree su unidad de recomendación, experimente con el tipo de página, el tipo de recomendación y los filtros para obtener comentarios inmediatos en tiempo real sobre los productos que se incluirán. A medida que empiece a comprender qué productos aparecen, puede configurar la unidad de recomendación para satisfacer sus necesidades comerciales.

Adobe Commerce [filtros](filters.md) recomendaciones para evitar mostrar productos duplicados cuando se implementan varias unidades de recomendaciones en una sola página. Como resultado, los productos que aparecen en el panel de vista previa pueden diferir de los que aparecen en la tienda.

>[!NOTE]
>
> No puede previsualizar el `Recently viewed` Tipo de recomendación porque los datos no están disponibles en el Administrador.
