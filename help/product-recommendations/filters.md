---
title: Filtrar productos
description: Defina las condiciones que incluyen o excluyen productos para que no se utilicen como recomendaciones.
exl-id: baab28ff-b529-4cbc-adb7-4fa225e87d4a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# Filtrar productos

Adobe Commerce aplica automáticamente filtros predeterminados no configurables a las unidades de recomendación. Si tiene varias unidades de recomendación implementadas en una página, Adobe Commerce elimina cualquier producto que se repita en las unidades. Sólo se utiliza la primera referencia a un producto repetido, para dar cabida a otros productos que se recomiendan. Adobe Commerce también filtra todos los productos comprados anteriormente y los que están en el carro de compras.

Cuando [crear](create.md) en una unidad de recomendación, puede definir filtros que controlan qué productos se pueden mostrar en las recomendaciones. Estos filtros se basan en un conjunto de condiciones de inclusión o exclusión que usted defina. En las recomendaciones solo aparecen los productos que coinciden con todas las condiciones de inclusión. No se recomiendan los productos que coincidan con cualquiera de las condiciones de exclusión.

Puede configurar varios filtros y habilitar solo los que desee seleccionando la opción en cada página de filtro. Esto le permite crear borradores de filtros para su uso futuro. El número de filtros habilitados se muestra en cada pestaña.

## Condiciones

Las condiciones pueden ser estáticas o dinámicas.

- Una condición estática utiliza atributos de producto existentes para determinar qué productos pueden aparecer en la unidad. Por ejemplo, puede especificar que solo los productos en existencias con un precio bueno a 25 $ aparezcan en la unidad. Las condiciones estáticas están disponibles en todos los tipos de página.

- Claves de condición dinámica del contexto actual de un comprador, como la categoría o el producto que se está viendo en ese momento. Por ejemplo, al crear una recomendación de producto para implementarla en páginas de detalles del producto, puede crear una condición para recomendar solo productos que se encuentren dentro de un rango de precios relativo del producto visualizado actualmente. Las condiciones dinámicas están disponibles en todos los tipos de página excepto en la página principal y en las páginas con recomendaciones que se colocan con el Creador de páginas.

### Operadores lógicos

Los operadores lógicos `AND` y `OR` se utilizan para unir varias condiciones. Si se utilizan tanto los filtros de inclusión como de exclusión, las inclusiones se evalúan primero para determinar todos los productos posibles que se pueden recomendar y, a continuación, los productos que coinciden con cualquier filtro de exclusión se eliminan de la lista.

- `AND` - Une dos condiciones de inclusión-filtrado
- `OR` : une dos condiciones de filtrado de exclusión

>[!NOTE]
>
> Los filtros de inclusión y exclusión reemplazan las exclusiones de categoría heredadas en las versiones 3.2.2 y posteriores del `magento/product-recommendations` módulo. Consulte la [notas de la versión](release-notes.md) para obtener más información sobre las versiones de Adobe Commerce.

## Tipos de filtros {#filtertypes}

![Filtros](assets/rec-conditions.png)

### Categoría

Los filtros basados en la categoría de un producto utilizan asignaciones de categoría directas y sus subcategorías. Por ejemplo, habilitar una condición de exclusión para la categoría `Gear` excluye los productos asignados a `Gear` y todas sus subcategorías como `Gear/Bags` o `Gear/Fitness Equipment`. Para los comerciantes B2B, el filtro Category se adhiere a cualquier [categorías de productos específicas del cliente]https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html) que ha configurado.

Adobe Commerce recomienda utilizar la siguiente configuración de filtro de categoría al implementar recomendaciones en los tipos de página:

| Página | Filtrar por |
|---|---|
| Página principal | No filtre productos. |
| Categoría | Filtre productos en la categoría específica. |
| Detalles del producto | Filtre productos en las mismas categorías. |
| Carro de compras | Filtrar categorías de productos en el carro de compras. |
| Confirmación del pedido | Filtrar categorías de productos comprados. |

### Product

Los filtros de producto especifican qué productos específicos son elegibles, o no, para ser mostrados en las recomendaciones. No puede seleccionar productos que estén desactivados o que no sean visibles de forma individual, ya que estos productos no pueden aparecer nunca en las recomendaciones.

### Tipo

Un filtro basado en el tipo de producto incluye o excluye todos los productos de un tipo específico. Los tipos admitidos son _Sencilla_, _Configurable_, _Virtual_, _Descargable_ o _Tarjeta de regalo_. _Paquete_ y _Agrupado_ los productos de aún no son compatibles.

### Visibilidad

Filtra productos en función de la visibilidad, como: _Catálogo_, _Buscar_, o ambas.

### Precio

Un filtro basado en el precio del producto utiliza el precio final para realizar la comparación. El precio final incluye cualquier descuento o precio especial disponible para compradores anónimos. Para los comerciantes B2B, el precio mostrado refleja el [precios de grupo específicos del cliente](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) ha configurado.

### Estado de stock

Los siguientes filtros de exclusión se pueden usar para filtrar productos en función del estado de existencias:

- Sin existencias (solo exclusión) Excluye productos que no están en existencias.
- Bajo en existencias (solo exclusión) Excluye los productos con un bajo nivel de existencias. El estado de existencias bajas se basa en la variable _Solo X Umbral izquierdo_ en [Configuración de inventario](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/inventory.html).
