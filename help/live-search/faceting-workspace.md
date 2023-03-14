---
title: "Faceting Workspace"
description: '"Aprenda a rodear el [!DNL Live Search] faceting workspace".'
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: e166c8cb9d715dce573195a188b5335c02d8fd0c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Faceting Workspace

El [!DNL Live Search] workspace enumera todas las facetas que están disponibles actualmente y proporciona acceso a las herramientas que necesita para configurar y administrar las facetas. Las facetas ancladas aparecen primero en la lista de facetas existentes, seguidas de las facetas dinámicas. La lista se puede filtrar para mostrar todas las facetas o solo aquellas que estén ancladas o sean dinámicas.

![Faceting workspace](assets/faceting-workspace.png)

## Establecer el ámbito

Si la instalación de Adobe Commerce incluye varias vistas de tienda, establezca **Ámbito** a la [vista de tienda](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) donde se aplique la configuración de faceta.

## Filtrado de la lista

1. Haga clic en **Filtrar por** control.
1. Elija una de las siguientes opciones:

   * Todos los filtros
   * Anclado
   * Dinámico

## Añadir una faceta

1. Clic **Añadir facetas**.
1. Consulte [Agregar facetas](facets-add.md) para obtener instrucciones detalladas.

## Descripciones de columna

| Columna | Descripción |
|--- |--- |
| (primera columna) | Enumera las facetas ancladas y dinámicas mediante [etiqueta](facets-type.md) que es visible para el comprador. |
| Tipo de orden | El [orden](facets-type.md) de valores de faceta. Las facetas se ordenan alfabéticamente para todos [!DNL Commerce] escaparates. Para [acéfalo] En las implementaciones de, las facetas se pueden ordenar alfabéticamente o por recuento. Opciones: Alfabético, Recuento (solo sin encabezado) |
| Valor máximo | El número de valores de faceta disponibles en la tienda como filtros, con un máximo de 10. |

## Controles

| Control | Descripción |
|--- |--- |
| Añadir facetas | Abre el [editor de facetas](facets-add.md). |
| Filtrar por | Determina el [tipo de facetas](facets-type.md) que aparecen en la lista. Opciones: Todo, Anclado, Dinámico |
