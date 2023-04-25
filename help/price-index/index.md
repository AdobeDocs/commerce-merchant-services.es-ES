---
title: Indexación de Precios SaaS
description: Uso de la indexación de precios SaaS para mejorar el rendimiento
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 45999b6499f248ea4138f7de4e910c274e747a04
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Indexación de Precios SaaS

La indexación de precios de SaaS acelera el tiempo que se tarda en que los cambios de precios se reflejen en el sitio web de un cliente después de que se hayan enviado. Este módulo opcional permite que los comerciantes con catálogos grandes y complejos, o con varios sitios web o grupos de clientes, procesen los cambios de precios de forma más rápida y continua.

El mayor cuello de botella de la tubería: los procesos pesados de la computación, como la indexación y el cálculo de precios, se han movido del núcleo PHP a la infraestructura de nube de Adobe. Esto permite a los comerciantes aumentar rápidamente los recursos para impulsar los tiempos de indexación de precios y reflejar esos cambios en los sitios web a velocidades mucho más rápidas.

Todos los comerciantes que cumplan los requisitos pueden beneficiarse de estas mejoras, pero quienes verán las ganancias buenas son clientes con:

* Cambios constantes en los precios: Los comerciantes que requieren cambios repetidos en sus precios para alcanzar objetivos estratégicos como promociones frecuentes, descuentos de temporada o restricciones de inventario.
* Varios sitios web o grupos de clientes: Comerciantes con catálogos de productos compartidos en varios sitios web (dominios/marcas) y/o grupos de clientes.
* Gran número de precios únicos en sitios web o grupos de clientes: Comerciantes con amplios catálogos de productos compartidos que contienen precios únicos en sitios web o grupos de clientes, como comerciantes B2B con precios previamente negociados, marcas con diferentes estrategias de precios.

Si tiene aplicaciones de terceros que dependen del indizador de precios principal de PHP, lea la documentación y consulte con el proveedor de extensiones antes de realizar cualquier cambio.

La indexación de precios SaaS está disponible de forma gratuita para los clientes que utilizan los servicios de Adobe Commerce.

Esta miniguía describe cómo funciona la indexación de precios SaaS y cómo habilitarla.

## Requisitos del sistema

Para utilizar la indexación de precios SaaS, necesita:

* Adobe Commerce 2.4.4+
* Al menos uno de los siguientes servicios SaaS instalados:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations de producto](../product-recommendations/guide-overview.md)

## Módulos

La indexación de precios SaaS utiliza un conjunto de módulos para proporcionar funcionalidad. La lista de módulos requeridos podría ser ligeramente diferente, dependiendo de la configuración de la tienda.

Estos módulos agregan las nuevas fuentes al Administrador. Estas fuentes transfieren los datos necesarios para los cálculos de precios al indizador SaaS e ignoran el indizador de precios principal PHP.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Los clientes que utilizan Luma y Adobe Commerce Core GraphQL pueden instalar un módulo que proporcione compatibilidad con Luma y deshabilite el indexador de precios principal de PHP:

```
adobe-commerce/catalog-adapter
```

La variable `catalog-adapter` solo es compatible con 2.4.5. La compatibilidad con 2.4.4 y 2.4.6 se lanzará próximamente.
El indizador de precios principal de PHP se puede volver a habilitar si lo necesita una extensión de terceros o cualquier otro motivo.

## Advertencias

Dependiendo de factores como tipos de productos, complejidad de precios y tamaño del catálogo, la indexación de precios SaaS puede ser la solución adecuada para su tienda. Lea las siguientes limitaciones y determine si esta es una buena solución para su sitio.

Actualmente, la indexación de precios de SaaS es compatible con los tipos de producto simples, agrupados, virtuales, configurables y dinámicos de paquetes.
Próximamente habrá compatibilidad con los tipos de producto descargables, tarjetas de regalo y Fijo de paquete.

La indexación de precios SaaS admite precios básicos:

* Precio normal mínimo/máximo
* Precio final mínimo/máximo
* Precios especiales
* Precios del grupo de clientes
* Precios de las reglas del catálogo

Una vez que decida utilizar la nueva fuente de precios, puede ponerse en contacto con [Asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) para ayudarle a deshacer la acción.

Las nuevas fuentes deben sincronizarse manualmente con la variable `resync` [Comando CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). De lo contrario, los datos se actualizan en el proceso de sincronización estándar. Obtenga más información sobre [Sincronización del catálogo](../landing/catalog-sync.md) proceso.

## Situaciones de uso

### Luma sin dependencias de extensión

* Un comerciante de GraphQL básico de Luma o superior de Commerce que tenga instalado un servicio requerido (Búsqueda activa, Recommendations de productos, Servicio de catálogo)
* Ninguna extensión de terceros que dependa del indexador de precios principal PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y de paquetes

1. Habilitar nuevas fuentes.
1. Instale el adaptador de catálogo.

### Luma y Abode Commerce Core GraphQl con dependencias del indexador de precios principal PHP

* Un comerciante de GraphQL básico de Luma o superior de Commerce que tenga instalado un servicio compatible (búsqueda en directo, Recommendations de productos, servicio de catálogo)
* Con una extensión de terceros que se basa en el indexador de precios principal de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y de paquetes

1. Habilitar las nuevas fuentes
1. Instale el adaptador de catálogo.
1. Vuelva a habilitar el indizador de precios principal de PHP.
1. Utilice nuevas fuentes y el código de compatibilidad de Luma en la variable `catalog-adapter` módulo.

### Comerciante sin cabeza

* Un comerciante sin objetivos que tiene instalado un servicio compatible (Búsqueda en directo, Recommendations de productos, Servicio de catálogo)
* Sin dependencia del indizador de precios básico de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y de paquetes

1. Habilitar nuevas fuentes
1. Instale el adaptador de catálogo, que deshabilita el indizador de precios principal de PHP.

### Luma/Core GraphQL/Headless con tipos de producto no compatibles

* Luma/Comerciante sin cabeza
* Venta de tarjetas regalo, productos fijos descargables o paquetes

Con los tipos de producto actualmente no compatibles, espere a que se admita el tipo de producto completo.
