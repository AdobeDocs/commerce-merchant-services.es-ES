---
title: "Reglas"
description: '"[!DNL Live Search] las reglas combinan lógica con acciones para dar forma a la experiencia de compra".'
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 7307702a62a6b2c3e6c6083a59f2ac3587b0985e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Reglas

[!DNL Live Search] las reglas combinan lógica con acciones para dar forma a la experiencia de búsqueda de un comprador en su tienda. Puede usar reglas para aumentar, enterrar, fijar u ocultar productos para calibrar los resultados de búsqueda en tiempo real y así lograr sus objetivos empresariales.

Cada regla tiene tres componentes principales:

* Condiciones : las condiciones que dan déclencheur a una acción.
* Eventos : acciones que se realizan cuando se cumplen las condiciones.
* Detalles: el nombre de la regla y la descripción y el lapso de tiempo opcionales.

Puede combinar varias condiciones y acciones, y programar una regla para que esté activa durante un periodo.

## Requisitos

Una regla simple puede tener una sola condición y un solo evento, mientras que una regla compleja puede tener hasta diez condiciones que déclencheur hasta 25 eventos.
Las reglas pueden tener:

* Hasta diez condiciones
* Hasta 25 eventos

El texto de la consulta puede contener:

* Caracteres alfanuméricos (letras y números)
* Caracteres en mayúsculas o minúsculas. Se ignora la capitalización.

## Operadores lógicos

Los operadores lógicos `AND` y `OR` una dos condiciones y devuelve resultados diferentes. Todos los operadores lógicos utilizados en una regla con varias condiciones son los mismos. No es posible utilizar ambos `AND` y `OR` en la misma regla.

### Operadores de coincidencias

Los operadores de coincidencia `All` y `Any` determine el operador lógico que se utiliza para unir varias condiciones en la regla y que se puede utilizar para cambiar el operador existente.

* `All` - Utiliza la variable `AND` operador lógico para unir varias condiciones. Una regla que utilice la variable `All` El operador de coincidencia solo puede tener una `Search query is` condición.
* `Any` - Utiliza la variable `OR` operador lógico para unir varias condiciones.

Al componer una regla compleja, puede ayudar a escribirla con sangría para describir las condiciones, los eventos asociados y los nombres de producto o SKU necesarios para devolver los resultados que desea obtener. A continuación, cree la regla y pruebe el resultado.

## Orden de prioridad con varias reglas

Solo se aplica una regla a un término de búsqueda en cualquier momento.
Si se encuentran varias reglas aplicables a una frase de búsqueda, se aplican todas estas reglas. Si hay un conflicto entre dos reglas—`rule 1` que aumenta sku1 pero `rule 2` oculta la misma SKU y la regla aplicada más recientemente (`rule 2`) tiene prioridad.

* Las reglas se ordenan mediante la marca de tiempo &quot;Última modificación&quot;. La regla modificada más recientemente se aplica primero, y las reglas más antiguas después de eso, en orden de marca de tiempo.
* La variable `query is` tiene prioridad sobre otras condiciones. Si una regla más reciente contiene una `query contains` , pero una regla anterior tiene un `query is` condición, `query is` se aplica.

### Solicitudes de tienda

Si una regla activa que contiene un `query is` coincide con la frase de búsqueda, se aplica. Si hay varias reglas coincidentes con una `query is` , se aplica la regla activa actualizada más recientemente.
De lo contrario, se aplica la regla activa actualizada más recientemente.

### Vista previa de solicitudes

Las solicitudes realizadas en Admin funcionan de forma ligeramente diferente. Al obtener una vista previa en Admin, se aplican todas las reglas, incluidas las caducadas y programadas.

* Si la regla que se está previsualizando tiene un `query is` , se aplica.
* Si la regla que se está previsualizando no tiene un `query is` y una regla consecuente activa que coincida con una `query is` se encuentra la condición de `query is` se aplica.
* Si la regla que se está previsualizando no tiene un `query is` y ninguna otra regla con un `query is` se encuentra, se aplica la regla que se está previsualizando.

## Reglas de categoría y asignaciones de producto de categoría

[!DNL Live Search] le permite filtrar por categorías.
Sin embargo, en Adobe Commerce puede crear una categoría virtual con [Asignaciones de productos de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Este tipo de categoría se crea durante la ejecución y no existe en la base de datos de categorías. Por lo tanto, [!DNL Live Search] no puede leer ni utilizar este tipo de categoría.
