---
title: '[!DNL Catalog Service] Notas de la versión'
description: La información de la última versión de [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: d84996bc76a44b39aeaee7f8b0ed4973fbe5de37
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de la versión

Estas notas de la versión describen las versiones más recientes de [!DNL Catalog Service] e incluyen:

* ![Nuevo](../assets/new.svg) Nuevas funciones
* ![Corrección](../assets/fix.svg) Correcciones y mejoras
* ![Error](../assets/bug.svg) Problemas conocidos

## Versión 1.1

Fecha de versión: 2022-11-18 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Disponibilidad general

![Nuevo](../assets/new.svg) El servicio de catálogo ahora es compatible con el Adobe [Mesh de API](https://developer.adobe.com/graphql-mesh-gateway/).
![Corrección](../assets/fix.svg) Hemos mejorado la escalabilidad de la API y el rendimiento general.

### Limitaciones conocidas

Estas funciones aún no son compatibles:

* Precio de nivel
* No se reciben actualizaciones cuando se eliminan variantes del catálogo
* El tamaño máximo de la carga útil de atributos dinámicos es de 9 MB

## Versión 1.0

Fecha de versión: 2022-10-04 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Disponibilidad general

![Nuevo](../assets/new.svg) Ahora admiten productos agrupados y agrupados.
![Nuevo](../assets/new.svg) Se han agregado anulaciones de visibilidad B2B. Los productos ahora se pueden buscar y se pueden agregar al carro de compras para grupos de clientes específicos.
![Corrección](../assets/fix.svg) El servicio es ahora más estable y ha mejorado el rendimiento.

### Limitaciones conocidas

Estas funciones aún no son compatibles:

* Precio de nivel
* Las actualizaciones no se reciben cuando se eliminan variantes del catálogo
* El tamaño máximo de la carga útil de atributos dinámicos es &lt;9 MB
* Precio fijo de los productos del paquete
* Precio total de los productos agrupados
* Compatibilidad con tipos de producto de tarjeta de regalo, descargables y virtuales
* Precio mínimo publicitado (MAP)

## Versión 0.3: beta+

Fecha de versión: 2022-09-12 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Beta

![Nuevo](../assets/new.svg) Las imágenes para variantes son compatibles: las imágenes de producto se devuelven en función de las opciones seleccionadas
![Nuevo](../assets/new.svg) Funciones de soporte de precios: permitir que solo los miembros de grupos de clientes específicos vean el precio de los productos
![Corrección](../assets/fix.svg) Mayor estabilidad y rendimiento del servicio
![Nuevo](../assets/new.svg) Las actualizaciones se reciben cuando los productos se eliminan del catálogo

### Limitaciones conocidas

Estas funciones aún no son compatibles:

* Precio de nivel
* Paquete y productos agrupados
* No se reciben actualizaciones cuando se eliminan variantes del catálogo
* Anulaciones de visibilidad B2B: se pueden buscar productos o agregarlos al carro de compras para grupos de clientes específicos

## Versión beta

Fecha de versión: 2022-08-09 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Beta

![Nuevo](../assets/new.svg) La variable `products` y `refineProduct` las consultas devuelven los siguientes datos:

* Atributos de producto predefinidos (del sistema).
* Atributos de producto dinámicos y filtrarlos por función (página de visualización de producto/página de lista de productos).
* Opciones de producto.
* Imágenes del producto y filtrarlas por función (PDP/PLP).
* Un precio específico para productos simples e intervalos de precios para productos configurables.
* Precios e intervalos de precios del grupo de clientes. Devuelven un precio predeterminado de reserva en compradores sin un grupo de clientes.
* Tipos de productos que utilizan precios específicos del cliente de B2B.

### Limitaciones conocidas

* No se admiten paquetes y productos agrupados.
* No se admite el precio de nivel.
* En una matriz de imágenes, solo la primera imagen contiene funciones.
* Las imágenes de las variantes no se recuperan.
* Las actualizaciones no se reciben cuando se eliminan productos o variantes del catálogo.
