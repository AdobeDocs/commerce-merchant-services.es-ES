---
title: "Agregar facetas"
description: '"Aprenda a añadir atributos de producto filtrables como [!DNL Live Search] facetas".'
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Agregar facetas

Cualquier atributo de producto filtrable puede utilizarse como faceta. El *Añadir facetas* el panel enumera las facetas actuales y facilita la asignación de atributos de producto adicionales como facetas. Durante este proceso de tres pasos, se elige un atributo para utilizarlo como faceta, las propiedades se editan si es necesario y los cambios se publican en la tienda.

![Faceting workspace](assets/facets-add.png)

## Paso 1: Añadir una faceta

1. En el Administrador, vaya a **Marketing** > SEO y búsqueda > **[!DNL Live Search]**.
1. En el *Faceteado* pestaña, haga clic en **Añadir facetas**.
1. En el *Añadir facetas* , cada atributo disponible tiene un ![Botón Añadir](assets/btn-add.png). Complete cualquiera de las siguientes opciones:

   * En el *Atributos de faceteado* , elija el atributo de producto que desea utilizar como faceta y haga clic en **Añadir**.
   * Para buscar un atributo de producto específico, introduzca los primeros caracteres del nombre del atributo en la *Buscar* cuadro. A continuación, haga clic en **Añadir**.

      Para configurar intervalos y agrupaciones de facetas de precios, consulte [Configuración](settings.md). Para obtener más información, vaya a [Tipos de faceta](facets-type.md).
La faceta se añade al final de la *Facetas dinámicas* y la *Publicar cambios* está disponible.

1. Si la faceta que desea agregar no se encuentra, vaya a **Tiendas** > Atributos > **Product** y compruebe que el atributo tiene el atributo [propiedades requeridas](facets.md) para que se utilice como faceta. Si es necesario, actualice las siguientes propiedades de tienda del atributo:

   * Uso en la búsqueda: `Yes`
   * Uso en la navegación por capas de resultados de búsqueda - `Yes`
   * Uso en la navegación por capas - `Filterable (with results)`

1. Cuando se le solicite, actualice la caché.

   La faceta estará disponible en la tienda la próxima vez que se sincronice el catálogo con [!DNL Live Search]. Si la faceta no está disponible después de dos horas, consulte [Sincronización de datos de catálogo](install.md#synchronize-catalog-data).

## Paso 2: Editar las propiedades de la faceta (opcional)

1. Para editar las propiedades de faceta, haga clic en **Más** (![Selector de más](assets/btn-more.png)) en la columna de la derecha.
1. En el menú, haga clic en **Editar**. A continuación, ajuste las siguientes propiedades según sea necesario.

   * Etiqueta - ([Headless](facets-type.md) (solo) Introduzca la etiqueta de faceta que desee utilizar.
   * Tipo de orden: las facetas se ordenan alfabéticamente para todos [!DNL Commerce] escaparates. En el caso de implementaciones sin encabezado, las facetas se pueden ordenar alfabéticamente o por recuento. Opciones: Alfabético, Recuento (solo sin encabezado)
   * Valor máximo: introduzca el número máximo de valores de faceta mostrados en la tienda. Entradas válidas: 0 - 30; Predeterminado: 8

1. Cuando termine, haga clic en **Guardar**.

   ![Faceting workspace](assets/facet-edit.png)

1. Para anclar la faceta a la parte superior del *Filtros* , haga clic en la chincheta gris (![Anclar selector](assets/btn-pin-gray.png)).
1. Para cambiar el orden de la faceta anclada, haga clic en el icono **Mover** (![Selector de movimiento](assets/btn-move.png)) y arrastre la fila a una nueva posición en el *Facetas ancladas* sección.

## Paso 3: Publicar cambios

1. Una vez completada la faceta, haga clic en **Publicar cambios**.
1. Espere a que la faceta aparezca en la tienda.
Si la faceta no está disponible después de dos horas, consulte [Verificar exportación](install.md#synchronize-catalog-data) en las instrucciones de instalación.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Etiqueta | ([Headless](facets-type.md) solo) La variable [etiqueta de faceta](facets-type.md) que es visible en la tienda y se puede editar para mantener la coherencia con la marca. |
| Tipo de orden | El método que se usa para [sort](facets-type.md) facetas. Todo [!DNL Commerce] las tiendas ordenan las facetas solo alfabéticamente. Las implementaciones sin encabezado también pueden ordenar por `Count`. Opciones:<br />Alfabético: ordena las facetas alfabéticamente.<br />Recuento: (solo sin encabezado) Ordena las facetas según el número de coincidencias encontradas. |
| Valor máximo | Número máximo de valores que se pueden mostrar en la tienda para cada faceta. Las facetas que representan un rango de valores se distribuyen de forma uniforme. Entradas válidas: 0 - 30; Predeterminado: 8 |

### Controles

| Control | Descripción |
|--- |--- |
| ![Anclar selector](assets/btn-pin-blue.png) | Fija o libera una faceta en la parte superior del *Filtros* lista. |
| ![Selector de más](assets/btn-more.png) | Muestra un menú de más acciones que se pueden aplicar a la faceta seleccionada. Opciones: Editar, Eliminar |
| ![Selector de movimiento](assets/btn-move.png) | Utilice el *Mover* para arrastrar una faceta anclada a otro lugar de la *Facetas ancladas* sección. |
