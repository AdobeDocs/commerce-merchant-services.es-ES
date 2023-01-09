---
title: "Reglas"
description: '"[!DNL Live Search] las reglas combinan lógica con acciones para dar forma a la experiencia de compra".'
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 941fdc25f93679593cb3c5db0d29d7a561fcce58
workflow-type: tm+mt
source-wordcount: '296'
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
