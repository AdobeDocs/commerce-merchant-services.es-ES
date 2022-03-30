---
title: Editar recomendación
description: Obtenga información sobre cómo editar una recomendación de producto.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Editar recomendación

La página Editar recomendación permite ajustar la configuración individual que conforma la recomendación. Todas las opciones de configuración se pueden editar excepto el tipo de página y el tipo de recomendación. Se puede editar la siguiente configuración:

- [Nombre de la recomendación](#name)
- [Etiqueta Tienda](#label)
- [Número de productos](#number)
- [Colocación y posición](#placement)
- [Filtrar productos](#filters)

La vista previa a la derecha de la página muestra cómo podría aparecer la recomendación con la configuración actual en la tienda. La variable _Vista previa de productos recomendados_ permanece visible como referencia mientras se desplaza hacia abajo por la página. La vista previa muestra una imagen en miniatura del producto, el nombre del producto, el SKU, el precio y el tipo de resultado para cada producto devuelto. El tipo de resultado indica si hay suficientes datos de comportamiento principales para generar la recomendación o si está utilizando datos de comportamiento de copia de seguridad.

![Editar Recommendations](assets/edit-recommendation.png)

## Editar una recomendación

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Recommendations de producto**.

1. Seleccione la recomendación que desee editar.

1. Haga clic en **Editar**. A continuación, siga las instrucciones que se indican a continuación para realizar los cambios que necesite.

1. Cuando termine, haga clic en **Guardar cambios**.

### Nombre de la recomendación {#name}

Elija un nombre descriptivo que indique el propósito de la recomendación. El nombre es para referencia interna y no aparece en la tienda.

![Editar nombre](assets/edit-name.png)

### Etiqueta Tienda {#label}

Introduzca el texto que desea utilizar como etiqueta para la unidad de recomendación en la tienda.

![Editar etiqueta](assets/edit-storefront-label.png)

### Número de productos {#number}

Ajuste el control deslizante para mostrar hasta 20 productos en la unidad de recomendaciones.

![Editar número de productos](assets/edit-number-of-products.png)

### Colocación y posición {#placement}

1. Elija la ubicación de la página donde aparecerá la unidad de recomendación en la tienda.

   - En la parte inferior del contenido principal
   - En la parte superior del contenido principal

   ![Editar ubicación](assets/edit-placement.png)

1. Para cambiar el orden de las recomendaciones que se incluyen en la unidad, utilice el **Mover** ![Mover selector](assets/icon-move.png) para arrastrar las recomendaciones a su posición.

   ![Editar posición](assets/edit-position.png)

### Filtrar productos {#filters}

Cualquier cambio realizado en el producto [filtros](filters.md) se reflejan en la variable _Vista previa de productos recomendados_. Solo se permiten los productos que coinciden con los filtros de inclusión. No se recomiendan los productos que coincidan con cualquier filtro de exclusión.

La variable _Inclusiones_ y _Exclusiones_ Las pestañas muestran los filtros disponibles de cada tipo. En la lista, cada filtro activo se marca con un punto azul.

- Para mostrar los detalles de cada filtro, haga clic en el nombre del filtro.
- Para cambiar el estado del filtro, establezca la variable **Activar filtro** alternar con la variable `on` o `off` posición.

![Editar filtros](assets/edit-filters.png)

La configuración del filtro describe los productos que se incluyen o excluyen en la unidad de recomendaciones. Por ejemplo, la variable _Categoría_ la configuración de inclusión del filtro indica al sistema que incluya solo productos de las categorías seleccionadas.

![Editar filtro de categoría](assets/edit-filter-category.png)
