---
title: Área de trabajo de facetas
description: Aprenda a navegar por el espacio de trabajo de facetas de Live Search.
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: a8943e56cc074a96d3f9e1009b76fa589b76a8a4
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Área de trabajo de facetas

La variable [!DNL Live Search] workspace enumera todas las facetas que están disponibles actualmente y proporciona acceso a las herramientas necesarias para configurar y administrar facetas. Las facetas fijadas aparecen primero en la lista de facetas existentes, seguido de facetas dinámicas. La lista se puede filtrar para que muestre todas las facetas, o solo las que están ancladas o son dinámicas.

![Espacio de trabajo de facetas](assets/faceting-workspace.png)

## Establecer el ámbito

Si la instalación de Adobe Commerce incluye varias vistas de tiendas, establezca **Ámbito** a [vista de tienda](https://docs.magento.com/user-guide/configuration/scope.html) donde se aplica la configuración de faceta.

## Filtrar la lista

1. Haga clic en el **Filtrar por** control.
1. Elija una de las siguientes opciones:

   * Todos los filtros
   * Anclado
   * Dinámica

   ![Espacio de trabajo de facetas](assets/facets-filter-by.png)

## Adición de una faceta

1. Haga clic en **Añadir facetas**.
1. Consulte [Agregar facetas](facets-add.md) para obtener instrucciones detalladas.

## Descripciones de columnas

| Columna | Descripción |
|--- |--- |
| (primera columna) | Enumera las facetas fijadas y dinámicas por el [label](facets-type.md) que es visible para el comprador. |
| Seleccionar tipo | La variable [método de selección](facets-type.md) que se asigna al atributo de producto correspondiente. La variable `single select` se usa para todos [!DNL Commerce] tiendas. Para implementaciones sin encabezado, `multi-select` se puede asignar con un operador lógico (`or` o `and`) para determinar el conjunto de productos devueltos. |
| Tipo de ordenación | La variable [orden de clasificación](facets-type.md) de valores de facetas. Las facetas se ordenan alfabéticamente para todas [!DNL Commerce] tiendas. Para [headless] implementaciones, las facetas se pueden ordenar alfabéticamente o por recuento. Opciones: Alfabético, Contar (solo sin encabezado) |
| Valor máximo | Número de valores de facetas disponibles en la tienda como filtros, con un máximo de 10. |

## Controles

| Control | Descripción |
|--- |--- |
| Añadir facetas | Abre el [editor de facetas](facets-add.md). |
| Filtrar por | Determina la variable [tipo de facetas](facets-type.md) que aparecen en la lista. Opciones: Todo, anclado, dinámico |
