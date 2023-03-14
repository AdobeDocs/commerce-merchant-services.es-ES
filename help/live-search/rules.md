---
title: "Reglas"
description: '"[!DNL Live Search] las reglas combinan lógica con acciones para dar forma a la experiencia de compra".'
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: c4bca0c7238be653dd13b051634c662e5891767d
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Reglas

[!DNL Live Search] las reglas combinan lógica con acciones para dar forma a la experiencia de búsqueda de un comprador en su tienda. Puede utilizar reglas para impulsar, enterrar, fijar u ocultar productos con el fin de calibrar los resultados de búsqueda en tiempo real para alcanzar los objetivos de su empresa.

Cada regla tiene tres componentes principales:

* Condiciones: las condiciones que almacenan en déclencheur una acción.
* Eventos: las acciones que se realizan cuando se cumplen las condiciones.
* Detalles: nombre de la regla, y marco temporal y descripción opcionales.

Puede combinar varias condiciones y acciones, y programar una regla para que esté activa durante un periodo.

## Requisitos

Una regla simple puede tener una sola condición y un solo evento, mientras que una regla compleja puede tener hasta diez condiciones que almacenen en déclencheur hasta 25 eventos.
Las reglas pueden tener:

* Hasta diez condiciones
* Hasta 25 eventos

El texto de la consulta puede contener:

* Caracteres alfanuméricos (letras y números)
* Caracteres en mayúsculas o minúsculas. Se omiten las mayúsculas.

## Operadores lógicos

Los operadores lógicos `AND` y `OR` una dos condiciones y devuelva resultados diferentes. Todos los operadores lógicos utilizados en una regla con varias condiciones son los mismos. No es posible utilizar ambos `AND` y `OR` en la misma regla.

### Operadores de coincidencia

Los operadores de coincidencia `All` y `Any` determine el operador lógico que se utiliza para unir varias condiciones en la regla y se puede utilizar para cambiar el operador existente.

* `All` - Utiliza el `AND` operador lógico para unir varias condiciones. Una regla que utiliza el `All` El operador de coincidencia solo puede tener uno `Search query is` condición.
* `Any` - Utiliza el `OR` operador lógico para unir varias condiciones.

Al componer una regla compleja, puede resultar útil escribirla con sangría para describir las condiciones, los eventos asociados y los nombres de producto o SKU necesarios para devolver los resultados que desea lograr. A continuación, genere la regla y pruebe el resultado.

## Orden de prioridad con varias reglas

Solo se aplica una regla a un término de búsqueda a la vez.
Si se encuentran varias reglas aplicables a una frase de búsqueda, se aplican todas estas reglas. Si hay una colisión entre dos reglas—`rule 1` que aumenta sku1 pero `rule 2` oculta el mismo SKU y, a continuación, la regla aplicada más recientemente (`rule 2`) tiene prioridad.

* Las reglas se ordenan por la marca de tiempo &quot;Última modificación&quot;. La regla modificada más recientemente se aplica primero, y las reglas más antiguas después, en orden de marca de tiempo.
* El `query is` la condición tiene prioridad sobre otras condiciones. Si una regla más reciente contiene un `query contains` condición, pero una regla más antigua tiene un `query is` condición, la `query is` se aplica la regla.

### Solicitudes de tienda

Si una regla activa contiene un `query is` La condición coincide con la frase de búsqueda y se aplica. Si hay varias reglas coincidentes con un `query is` condición, se aplica la regla activa actualizada más recientemente.
De lo contrario, se aplica la regla activa actualizada más recientemente.

### Previsualizar solicitudes

Las solicitudes realizadas en el Administrador funcionan de forma ligeramente diferente. Al obtener una vista previa en Admin, se aplican todas las reglas, incluidas las caducadas y programadas.

* Si la regla que se previsualiza tiene un `query is` condición, se aplica.
* Si la regla que se previsualiza no tiene un `query is` y una regla de coincidencia activa posterior con un `query is` se encuentra la condición, el `query is` se aplica la regla.
* Si la regla que se previsualiza no tiene un `query is` y ninguna otra regla con una condición `query is` Si se encuentra la condición, se aplica la regla que se está previsualizando.

## Reglas de categoría y asignaciones de productos de categoría

[!DNL Live Search] permite filtrar por categorías.
Sin embargo, en Adobe Commerce puede crear una categoría virtual con [Asignaciones de productos de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Este tipo de categoría se crea durante la ejecución y no existe en la base de datos de categorías. Por lo tanto, L[!DNL Live Search] no se puede leer ni utilizar este tipo de categoría.
