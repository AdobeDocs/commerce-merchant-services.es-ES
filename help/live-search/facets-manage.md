---
title: Administrar facetas
description: Aprenda a administrar las facetas de Live Search existentes.
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Administrar facetas

Siga estas instrucciones para actualizar las propiedades de facetas existentes o cambiar su presentación en la tienda.

## Configurar agrupaciones de facetas de precio

Consulte [Configuración](settings.md) para configurar intervalos y agrupaciones de facetas de precios.

## Editar faceta

1. Busque la faceta que desea editar.
1. Si hay muchas facetas en la lista, establezca *Filtrar por* a uno de los siguientes:

   * Anclado
   * Dinámica

   Para obtener más información, vaya a [Tipos de faceta](facets-type.md).

   ![Facetas de filtro](assets/facets-filter-by-cropped.png)

1. Para editar las propiedades de faceta, haga clic en **Más** (...).
1. Haga clic en **Editar**

   ![Editar opciones](assets/facet-edit-menu.png)

1. Para editar la etiqueta de faceta, realice una de las siguientes acciones:

   * Para un [!DNL Commerce] tienda, edite la [etiqueta de atributo](https://docs.magento.com/user-guide/stores/attributes-product.html).
   * Para una implementación sin encabezado, haga clic en el valor de la primera columna y edite el texto según sea necesario.

   ![Editar etiqueta](assets/facet-edit-label.png)

1. (Solo sin encabezado) Para cambiar el método que se usa para ordenar los valores de facetas, haga clic en el valor en la variable *Tipo de orden* y elija una de las siguientes opciones:

   * Alfabético
   * Recuento

   ![Editar recuento](assets/facets-edit-count.png)

1. En el **Valor máximo** , establezca el número máximo (de 0 a 10) de valores de filtro de facetas que se mostrarán en la tienda.
1. Cuando termine, haga clic en **Guardar**.
Los cambios no aparecerán en la tienda hasta que se publiquen.

## Fijar/desfijar faceta

El pin cambia de color cuando se hace clic y se utiliza para mover la faceta a la variable *Facetas fijadas* o *Facetas dinámicas* para obtener más información.

1. Para fijar una faceta en la parte superior del *Filtros* , busque la faceta en la *Facetas dinámicas* y haga clic en el pin gris (![Selector de clavijas](assets/btn-pin-gray.png)).
El pasador se vuelve azul y la faceta se mueve a la *Facetas fijadas* para obtener más información.
1. Para desanclar una faceta, busque la faceta en la *Facetas fijadas* y haga clic en el pin azul (![Selector de clavijas](assets/btn-pin-blue.png)).
El pasador se vuelve gris y la faceta se mueve a la *Facetas dinámicas* para obtener más información.

   ![Facetas fijadas y dinámicas](assets/facets-pinned-unpinned.png)

## Mover faceta fija

El orden de las facetas fijadas se puede cambiar moviendo la fila a una posición diferente. Las facetas fijadas tienen un *Mover* icono (![Mover selector](assets/btn-move.png)) al principio de la fila. A diferencia de las facetas fijadas, las facetas dinámicas no se pueden mover.

1. Busque la faceta en la variable *Facetas fijadas* de la lista.
1. Utilice la variable **Mover** (![Mover selector](assets/btn-move.png)) para arrastrar la fila a una nueva posición en la *Facetas fijadas* para obtener más información.
Una vez publicados los cambios, las facetas reordenadas aparecen en la tienda *Filtros* lista.

## Eliminar faceta

1. Busque la faceta en la lista y haga clic en **Más** (...).
1. Haga clic en **Eliminar**.
1. Cuando se le pida que confirme, haga clic en **Eliminar faceta**.
La faceta se elimina de la tienda después de publicar los cambios.

## Publicar cambios

1. Para actualizar la tienda con sus cambios, haga clic en **Publicar cambios**.
1. Espere unos quince minutos para que las actualizaciones aparezcan en su tienda.
