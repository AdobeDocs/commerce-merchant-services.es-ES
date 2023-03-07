---
title: '[!DNL Catalog Service] Notas de la versión'
description: La información de la versión más reciente de [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versión

Estas notas de la versión describen las versiones más recientes de [!DNL Catalog Service] e incluir:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

## Versión principal actual

### Versión V1.5

Fecha de versión: 2023-3-6 Compatible con Adobe Commerce (EE): 2.4.4+ Compatible con Adobe Commerce para Cloud (ECE): 2.4.4+ Estabilidad: General Disponibilidad

![Nuevo](../assets/new.svg) Añadido [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) Funcionalidad de GraphQL.
![Fix](../assets/fix.svg) Rendimiento y escalabilidad de API mejorados.

#### Limitaciones conocidas

Estas funciones aún no son compatibles:

* Paquete de productos con precio fijo
* No se recibe ninguna actualización cuando se eliminan variantes del catálogo.
* El tamaño máximo de la carga útil de atributos dinámicos es de 9 MB.
* Precio del producto del grupo. Se puede calcular con precios de productos simples.
* En una matriz de imágenes, solo la primera imagen contiene funciones.
* Muestras de color
* Carga de la página de detalles del producto mediante la dirección URL del producto.

Las siguientes limitaciones se pueden resolver mediante la API principal de GraphQL:

* Precio Mínimo Anunciado
* Precios de nivel
* Productos descargables y tarjetas regalo

### Versión V1.4

Fecha de versión: 2023-2-7 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: General Disponibilidad

![Nuevo](../assets/new.svg) Se ha publicado un metapaquete de servicio de catálogo para simplificar los pasos de instalación.
![Fix](../assets/fix.svg) Mejoras de rendimiento y escalabilidad de API.

### Versión V1.3

Fecha de versión: 2023-1-17 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Disponibilidad general

![Nuevo](../assets/new.svg) Simplificación y mejora de la experiencia de incorporación.
![Nuevo](../assets/new.svg) Hay nuevos extremos de zona protegida del cliente disponibles para pruebas previas a la producción.
![Nuevo](../assets/new.svg) Se agregó compatibilidad con productos virtuales.
![Fix](../assets/fix.svg) Mejoras de rendimiento y escalabilidad de API.

### Versión V1.1

Fecha de versión: 18-11-2022 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: General Disponibilidad

![Nuevo](../assets/new.svg) El servicio de catálogo ahora admite Adobes [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Hemos mejorado la escalabilidad de la API y el rendimiento general.

### Versión 1.0

Fecha de versión: 2022-10-04 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: General Disponibilidad

![Nuevo](../assets/new.svg) Ahora admite productos agrupados y agrupados.
![Nuevo](../assets/new.svg) Se han añadido anulaciones de visibilidad B2B. Ahora se pueden buscar productos y se pueden agregar al carro de compras para grupos de clientes específicos.
![Fix](../assets/fix.svg) El servicio es ahora más estable y ha mejorado el rendimiento.

## Versiones anteriores

+++Versiones beta

### Versión 0.3: beta+

Fecha de versión: 12-09-2022 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Beta

![Nuevo](../assets/new.svg) Compatibilidad con imágenes para variantes: las imágenes de producto se devuelven en función de las opciones seleccionadas
![Nuevo](../assets/new.svg) Funciones para el soporte de precios: permitir que solo los miembros de grupos de clientes específicos vean el precio de los productos
![Fix](../assets/fix.svg) Estabilidad y rendimiento mejorados del servicio
![Nuevo](../assets/new.svg) Las actualizaciones se reciben cuando los productos se eliminan del catálogo

### Lanzamiento beta

Fecha de versión: 2022-08-09 Compatible con Adobe Commerce (EE): 2.4.x Compatible con Adobe Commerce para Cloud (ECE): 2.4.x Estabilidad: Beta

![Nuevo](../assets/new.svg) El `products` y `refineProduct` Las consultas de devuelven los siguientes datos:

* Atributos de producto predefinidos (del sistema).
* Atributos de producto dinámicos y filtrarlos por función (página de visualización de producto/página de lista de productos).
* Opciones de producto.
* Imágenes de productos y filtrarlas por función (PDP/PLP).
* Un precio específico para productos simples y rangos de precios para productos configurables.
* Precios de grupo de clientes e intervalos de precios. Devuelven un precio predeterminado alternativo para los compradores sin grupo de clientes.
* Tipos de productos que utilizan precios específicos del cliente B2B.

+++