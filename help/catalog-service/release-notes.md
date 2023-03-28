---
title: '''[!DNL Catalog Service] Notas de la versión'
description: La información de la última versión de [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: c65717c449793dccfed101e1411b22c69fba308d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de la versión

Estas notas de la versión describen las versiones más recientes de [!DNL Catalog Service] e incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Corrección](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

## Versión principal actual

### Versión 1.6

_28 de marzo de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se agregaron muestras al [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) consulta.
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de obtener `entityId` using [Mesh de API](mesh.md).

#### Limitaciones conocidas

Estas funciones aún no son compatibles:

* Paquete de productos con precio fijo
* No se reciben actualizaciones cuando se eliminan variantes del catálogo.
* El tamaño máximo para la carga útil de atributos dinámicos es de 9 MB.
* Precio de producto de grupo. Se puede calcular con precios de producto simples.
* En una matriz de imágenes, solo la primera imagen contiene funciones.

Las siguientes limitaciones se pueden resolver utilizando la red de API y la API principal de GraphQL:

* Precio mínimo publicitario
* [Precio de nivel](mesh.md)
* Productos descargables y tarjetas de regalo

### Versión 1.5

_6 de marzo de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) Funcionalidad de GraphQL.
![Corrección](../assets/fix.svg) Rendimiento y escalabilidad de API mejorados.

### Versión 1.4

_7 de febrero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha publicado el paquete de metapaquete catálogo-servicio para simplificar los pasos de instalación.
![Corrección](../assets/fix.svg) Mejoras de escalabilidad y rendimiento de la API.

### Versión 1.3

_17 de enero de 2023_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha simplificado y mejorado la experiencia de integración.
![Nuevo](../assets/new.svg) Hay nuevos extremos de entorno limitado para clientes disponibles para pruebas previas a la producción.
![Nuevo](../assets/new.svg) Se agregó compatibilidad con productos virtuales.
![Corrección](../assets/fix.svg) Mejoras de escalabilidad y rendimiento de la API.

### Versión 1.1

_18 de noviembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) El servicio de catálogo ahora es compatible con el Adobe [Mesh de API](https://developer.adobe.com/graphql-mesh-gateway/).
![Corrección](../assets/fix.svg) Mejora de la escalabilidad de la API y rendimiento general.

### Versión 1.0

_4 de octubre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Ahora admiten productos agrupados y agrupados.
![Nuevo](../assets/new.svg) Se han agregado anulaciones de visibilidad B2B. Los productos ahora se pueden buscar y se pueden agregar al carro de compras para grupos de clientes específicos.
![Corrección](../assets/fix.svg) El servicio es ahora más estable y ha mejorado el rendimiento.

## Versiones anteriores

Versiones ++Beta

### Versión 0.3: beta+

_12 de septiembre de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Las imágenes para variantes son compatibles: las imágenes de producto se devuelven en función de las opciones seleccionadas
![Nuevo](../assets/new.svg) Funciones de soporte de precios: permitir que solo los miembros de grupos de clientes específicos vean el precio de los productos
![Corrección](../assets/fix.svg) Mayor estabilidad y rendimiento del servicio
![Nuevo](../assets/new.svg) Las actualizaciones se reciben cuando los productos se eliminan del catálogo

### Versión beta

_9 de agosto de 2022_

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) La variable `products` y `refineProduct` las consultas devuelven los siguientes datos:

* Atributos de producto predefinidos (del sistema).
* Atributos de producto dinámicos y filtrarlos por función (página de visualización de producto/página de lista de productos).
* Opciones de producto.
* Imágenes del producto y filtrarlas por función (PDP/PLP).
* Un precio específico para productos simples e intervalos de precios para productos configurables.
* Precios e intervalos de precios del grupo de clientes. Devuelven un precio predeterminado de reserva en compradores sin un grupo de clientes.
* Tipos de productos que utilizan precios específicos del cliente de B2B.

+++
