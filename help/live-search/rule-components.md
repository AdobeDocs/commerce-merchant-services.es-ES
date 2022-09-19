---
title: "Componentes de regla"
description: '"Obtenga información sobre [!DNL Live Search] componentes y operadores de regla".'
exl-id: 4065aec3-a8d4-4d55-b939-16ad7b0f33ee
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Componentes de regla

Una regla describe las condiciones necesarias para almacenar en déclencheur eventos que cambian los resultados de búsqueda devueltos en respuesta a la consulta de un comprador.

## Requisitos

Una regla simple puede tener una sola condición y un solo evento, mientras que una regla compleja puede tener hasta diez condiciones que déclencheur hasta 25 eventos.
Las reglas pueden tener:

* Hasta diez condiciones
* Hasta 25 eventos

El texto de la consulta puede contener:

* Caracteres alfanuméricos (letras y números)
* Caracteres en mayúsculas o minúsculas

## Operadores lógicos

Los operadores lógicos `AND` y `OR` una dos condiciones y devuelve resultados diferentes. Todos los operadores lógicos utilizados en una regla con varias condiciones son los mismos. No es posible utilizar ambos `AND` y `OR` en la misma regla.

### Operadores de coincidencias

Los operadores de coincidencia `All` y `Any` determine el operador lógico que se utiliza para unir varias condiciones en la regla y que se puede utilizar para cambiar el operador existente.

* `All` - Utiliza la variable `AND` operador lógico para unir varias condiciones. Una regla que utilice la variable `All` El operador de coincidencia solo puede tener una `Search query is` condición.
* `Any` - Utiliza la variable `OR` operador lógico para unir varias condiciones.

Al componer una regla compleja, puede ayudar a escribirla con sangría para describir las condiciones, los eventos asociados y los nombres de producto o SKU necesarios para devolver los resultados que desea obtener. A continuación, cree la regla y pruebe el resultado.
