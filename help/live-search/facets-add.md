---
title: Agregar facetas
description: Aprenda a añadir atributos de producto filtrables como facetas de búsqueda activa.
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: f31c76404315a9fe142bf0c72ff9999c4a87365d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Agregar facetas

Cualquier atributo de producto filtrable puede utilizarse como faceta. La variable *Añadir facetas* panel enumera las facetas actuales y facilita la asignación de atributos de producto adicionales como facetas. Durante este proceso de tres pasos, se elige un atributo para utilizarlo como faceta, las propiedades se editan si es necesario y los cambios se publican en la tienda.

![Espacio de trabajo de facetas](assets/facets-add.png)

## Paso 1: Adición de una faceta

1. En el Administrador, vaya a **Marketing** > SEO y Búsqueda > **[!DNL Live Search]**.
1. En el *Facetas* , haga clic en **Añadir facetas**.
1. En el *Añadir facetas* lista, cada atributo disponible tiene un *Agregar* botón. Realice una de las siguientes acciones:

   ![Faceta añadida](assets/facets-list-add.png)

   * En el *Atributos de faceta* , elija el atributo de producto que desea usar como faceta y haga clic en **Agregar**.
   * Para buscar un atributo de producto específico, introduzca los primeros caracteres del nombre de atributo en la *Buscar* en la ventana A continuación, haga clic en **Agregar**.

      Para configurar intervalos y agrupaciones de facetas de precios, consulte [Configuración](settings.md). Para obtener más información, vaya a [Tipos de faceta](facets-type.md).
La faceta se agrega a la parte inferior del *Facetas dinámicas* y *Publicar cambios* está disponible.
   ![Faceta añadida](assets/facet-added.png)

1. Si no se encuentra la faceta que desea agregar, vaya a **Almacenes** > Atributos > **Product** y compruebe que el atributo tiene la variable [propiedades requeridas](facets.md) para usar como faceta. Si es necesario, actualice las siguientes propiedades de tienda del atributo:

   * Usar en la búsqueda - `Yes`
   * Usar en navegación por capas de resultados de búsqueda - `Yes`
   * Usar en navegación por capas - `Filterable (with results)`

1. Cuando se le solicite, actualice la caché.

   La faceta está disponible en la tienda la próxima vez que el catálogo se sincronice con [!DNL Live Search]. Si la faceta no está disponible después de dos horas, consulte [Sincronizar datos de catálogo](install.md#synchronize-catalog-data).

## Paso 2: Editar propiedades de faceta (opcional)

1. Para editar las propiedades de faceta, haga clic en **Más** (![Más selector](assets/btn-more.png)) en la columna de la derecha.
1. En el menú , haga clic en **Editar**. A continuación, ajuste las siguientes propiedades según sea necesario.

   * Etiqueta - ([Sin encabezado](facets-type.md) solo) Introduzca la etiqueta de faceta que desea utilizar.
   * Seleccionar tipo: *Seleccionar tipo* se usa para todos [!DNL Commerce] storefronts es `single select`. Para implementaciones sin encabezado, `multi-select` se puede asignar con un operador lógico (`or` o `and`) para determinar el conjunto de productos devueltos.
   * Tipo de orden : las facetas se ordenan alfabéticamente para todas [!DNL Commerce] tiendas. En implementaciones sin encabezado, las facetas se pueden ordenar alfabéticamente o por recuento. Opciones: Alfabético, Contar (solo sin encabezado)
   * Valor máximo : introduzca el número máximo de valores de facetas que se muestran en la tienda. Entradas válidas: 0 - 30; Predeterminado: 8

1. Cuando termine, haga clic en **Guardar**.

   ![Espacio de trabajo de facetas](assets/facet-edit.png)

1. Para fijar la faceta en la parte superior del *Filtros* , haga clic en el borde gris (![Selector de clavijas](assets/btn-pin-gray.png)).
1. Para cambiar el orden de la faceta fijada, haga clic en el botón **Mover** (![Mover selector](assets/btn-move.png)) y arrastre la fila a una nueva posición en la *Facetas fijadas* para obtener más información.

## Paso 3: Publicar cambios

1. Cuando finalice la faceta, haga clic en **Publicar cambios**.
1. Espere a que aparezca la faceta en la tienda.
Si la faceta no está disponible después de dos horas, consulte [Verificar exportación](install.md#synchronize-catalog-data) en las instrucciones de instalación.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Etiqueta | ([Sin encabezado](facets-type.md) solo) La variable [etiqueta de faceta](facets-type.md) que es visible en la tienda puede editarse para mantener la coherencia con su marca. |
| Seleccionar tipo | Muestra el [método de selección](facets-type.md) que está asociado al atributo product . Todas las facetas de la variable [!DNL Commerce] las tiendas son `Single select` solo. Las implementaciones sin encabezado también admiten `Multi-select` con los operadores lógicos `OR` y `AND`. |
| Tipo de orden | El método que se usa para [sort](facets-type.md) facetas. Todo [!DNL Commerce] las tiendas solo ordenan facetas alfabéticamente. Las implementaciones sin encabezado también pueden ordenarse por `Count`. Opciones:<br />Alfabético : ordena las facetas alfabéticamente.<br />Recuento : (solo sin encabezado) ordena las facetas en función del número de coincidencias encontradas. |
| Valor máximo | Número máximo de valores que se pueden mostrar en la tienda para cada faceta. Las facetas que representan un rango de valores se distribuyen de manera uniforme. Entradas válidas: 0 - 30; Predeterminado: 8 |

### Controles

| Control | Descripción |
|--- |--- |
| ![Selector de clavijas](assets/btn-pin-blue.png) | Anclar o deslizar una faceta en la parte superior de la *Filtros* lista. |
| ![Más selector](assets/btn-more.png) | Muestra un menú de más acciones que se pueden aplicar a la faceta seleccionada. Opciones: Editar, Eliminar |
| ![Mover selector](assets/btn-move.png) | Utilice la variable *Mover* para arrastrar una faceta fijada a otro lugar de la *Facetas fijadas* para obtener más información. |
