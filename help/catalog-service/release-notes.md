---
title: '[!DNL Catalog Service] Notas de la versión'
description: La información de la versión más reciente de [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 77716f8fd74a7ba390fea5e4454b01152b024da0
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versión

Estas notas de la versión describen las versiones más recientes de [!DNL Catalog Service].
Se proporciona soporte para la versión publicada principal actual. Las notas de la versión de las versiones anteriores se proporcionan como referencia.
Las actualizaciones incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

## Versión principal actual

### Versión V1.18

_11 de abril de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con PHP 8.3.

![Nuevo](../assets/new.svg) El [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) y [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) las consultas ahora devuelven datos de opciones personalizables para productos simples y complejos.<!--DATA-5538-->

## Versiones anteriores

+++ Versiones anteriores

### Versión V1.17

_22 de febrero de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ya está disponible. Este tablero reformado proporciona perspectivas sobre los flujos de datos para [!DNL Product Recommendations], [!DNL Live Search], y [!DNL Catalog Service]. La compatibilidad con esta función se introdujo en la versión 3.1.0 de la `catalog-service` metapaquete.

### Versión V1.16

_13 de febrero de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) La API del servicio de catálogo ahora admite vídeos de productos.
![Fix](../assets/fix.svg) Ahora se admiten productos agrupados con precios fijos.
![Fix](../assets/fix.svg) Las opciones sin existencias ahora se muestran en el widget PDP.

#### Limitaciones conocidas

Estas funciones aún no son compatibles:

* El tamaño máximo de la carga útil de atributos dinámicos es de 9 MB.
* Precio del producto del grupo. Este valor se puede calcular con precios de productos simples.
* En una matriz de imágenes, solo la primera imagen contiene funciones.

Las siguientes limitaciones se pueden resolver mediante API Mesh y la API principal de GraphQL:

* Precio Mínimo Anunciado
* [Precios de nivel](mesh.md)

### Versión V1.13

_12 de octubre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El servicio de catálogo admite `inStock` indicador para variantes de producto.
![Nuevo](../assets/new.svg) El `urlKey` y `externalId` Se han añadido campos de al esquema de GraphQL.
![Nuevo](../assets/new.svg) Ahora se admiten productos descargables y tarjetas regalo.

### Versión V1.12

_19 de septiembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El servicio de catálogo ahora utiliza [Indexación de precios de SaaS](../price-index/price-indexing.md).
![Fix](../assets/fix.svg) Esta versión incluye correcciones de errores y mejoras en el lado del servicio.

### Versión V1.11

_18 de julio de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El servicio de catálogo ahora admite [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) GraphQL consulta el Recommendations del producto.

### Versión V1.10

_27 de junio de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) La API del servicio de catálogo ahora admite `related products`.

### Versión V1.7

_12 de abril de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El servicio de catálogo ahora limpia las variantes de producto eliminadas.
![Fix](../assets/fix.svg) Mejoras de rendimiento y escalabilidad de la infraestructura.

### Versión V1.6

_28 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se han añadido muestras a [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) consulta.
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de `entityId` usando [API Mesh](mesh.md).

### Versión V1.5

_6 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Añadido [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) Funcionalidad de GraphQL.
![Fix](../assets/fix.svg) Rendimiento y escalabilidad de API mejorados.

### Versión V1.4

_7 de febrero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha publicado un metapaquete de servicio de catálogo para simplificar los pasos de instalación.
![Fix](../assets/fix.svg) Mejoras de rendimiento y escalabilidad de API.

### Versión V1.3

_17 de enero de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Simplificación y mejora de la experiencia de incorporación.
![Nuevo](../assets/new.svg) Hay nuevos extremos de zona protegida del cliente disponibles para pruebas previas a la producción.
![Nuevo](../assets/new.svg) Se agregó compatibilidad con productos virtuales.
![Fix](../assets/fix.svg) Mejoras de rendimiento y escalabilidad de API.

### Versión V1.1

_18 de noviembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El servicio de catálogo ahora admite Adobes [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Fix](../assets/fix.svg) Se ha mejorado la escalabilidad de la API y el rendimiento general.

### Versión 1.0

_4 de octubre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Ahora admite productos agrupados y agrupados.
![Nuevo](../assets/new.svg) Se han añadido anulaciones de visibilidad B2B. Ahora se pueden buscar productos y se pueden agregar al carro de compras para grupos de clientes específicos.
![Fix](../assets/fix.svg) El servicio es ahora más estable y ha mejorado el rendimiento.

### Versión 0.3: beta+

_12 de septiembre de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Compatibilidad con imágenes para variantes: las imágenes de producto se devuelven en función de las opciones seleccionadas
![Nuevo](../assets/new.svg) Funciones para el soporte de precios: permitir que solo los miembros de grupos de clientes específicos vean el precio de los productos
![Fix](../assets/fix.svg) Estabilidad y rendimiento mejorados del servicio
![Nuevo](../assets/new.svg) Las actualizaciones se reciben cuando los productos se eliminan del catálogo

### Lanzamiento beta

_9 de agosto de 2022_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El `products` y `refineProduct` Las consultas de devuelven los siguientes datos:

* Atributos de producto predefinidos (del sistema).
* Atributos de producto dinámicos y filtrarlos por función (página de visualización de producto/página de lista de productos).
* Opciones de producto.
* Imágenes de productos y filtrarlas por función (PDP/PLP).
* Un precio específico para productos simples y rangos de precios para productos configurables.
* Precios de grupo de clientes e intervalos de precios. Devuelven un precio predeterminado alternativo para los compradores sin grupo de clientes.
* Tipos de productos que utilizan precios específicos del cliente B2B.
