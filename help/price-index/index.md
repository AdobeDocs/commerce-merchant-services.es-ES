---
title: Indexación de precios de SaaS
description: Uso de la indexación de precios SaaS para mejorar el rendimiento
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# Indexación de precios de SaaS

La indexación de precios de SaaS acelera el tiempo que tardan los cambios de precios en reflejarse en el sitio web de un cliente de SaaS después de enviarse. Este módulo opcional permite a los comerciantes con catálogos grandes y complejos, o con múltiples sitios web o grupos de clientes, procesar los cambios de precios de forma más rápida y continua.

El mayor cuello de botella de la canalización: los procesos computacionales pesados como la indexación y el cálculo de precios, se han trasladado del núcleo de PHP a la infraestructura en la nube del Adobe. Esto permite a los comerciantes ampliar rápidamente los recursos para aumentar los tiempos de indexación de precios y reflejar esos cambios en los sitios web a velocidades mucho más rápidas.

El flujo de datos de indexación principal a los servicios SaaS tiene este aspecto:

![Flujo de datos predeterminado](assets/old_way.png)

Con la indexación de precios SaaS, el flujo es:

![Flujo de datos de indexación de precios SaaS](assets/new_way.png)

Todos los comerciantes que cumplan los requisitos pueden beneficiarse de estas mejoras, pero los que verán las ganancias más buenas son los clientes con:

* Cambios constantes en los precios: los comerciantes que necesitan cambios repetidos en sus precios para cumplir objetivos estratégicos como promociones frecuentes, descuentos estacionales o reducciones de existencias.
* Varios sitios web o grupos de clientes: comerciantes con catálogos de productos compartidos en varios sitios web (dominios/marcas) o grupos de clientes.
* Gran cantidad de precios únicos en sitios web o grupos de clientes: comerciantes con catálogos de productos compartidos extensos que contienen precios únicos en sitios web o grupos de clientes, como comerciantes B2B con precios negociados previamente, marcas con diferentes estrategias de precios.

Si tiene aplicaciones de terceros que dependen del indexador de precios principal de PHP, lea la documentación y consulte con el proveedor de la extensión antes de realizar cualquier cambio.

La indexación de precios SaaS está disponible de forma gratuita para los clientes que utilizan los servicios de Adobe Commerce.

Esta miniguía describe cómo funciona la indexación de precios SaaS y cómo habilitarla.

## Requisitos del sistema

Para utilizar la indexación de precios SaaS, necesita:

* Adobe Commerce 2.4.4+
* Al menos uno de los siguientes servicios SaaS instalados:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Product Recommendations](../product-recommendations/guide-overview.md)

## Módulos

La indexación de precios SaaS utiliza un conjunto de módulos para proporcionar funcionalidad. La lista de módulos necesarios puede ser ligeramente diferente, según la configuración de la tienda.

Estos módulos agregan las nuevas fuentes al administrador. Estas fuentes transfieren los datos necesarios para los cálculos de precios al indexador SaaS e ignoran el indexador de precios principal de PHP.

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Los clientes que utilizan Luma y Adobe Commerce Core GraphQL pueden instalar un módulo que proporcione compatibilidad con Luma y Core GraphQL y deshabilite el indexador de precios principal de PHP:

```
adobe-commerce/catalog-adapter
```

El `catalog-adapter` solo es compatible con 2.4.5. La compatibilidad con 2.4.4 y 2.4.6 se publicará en un futuro próximo.
El indexador de precios principal de PHP puede volver a activarse si es necesario por una extensión de terceros o por cualquier otra razón.

## Advertencias

Según factores como el tipo de producto, la complejidad del precio y el tamaño del catálogo, la indexación de precios SaaS puede ser la solución adecuada para su tienda. Lea las siguientes limitaciones y determine si esta es una buena solución para su sitio.

Actualmente, la indexación de precios SaaS admite tipos de producto simples, agrupados, virtuales, configurables y dinámicos agrupados.
Próximamente se admitirán los tipos de productos descargables, tarjetas de regalo y paquetes fijos

Las nuevas fuentes deben sincronizarse manualmente con `resync` [comando CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). De lo contrario, los datos se actualizan en el proceso de sincronización estándar. Obtenga más información acerca de [Sincronización de catálogo](../landing/catalog-sync.md) proceso.

## Escenarios de uso

### Luma sin dependencias de extensión

* Un comerciante principal de GraphQL de Luma o Adobe Commerce que tiene instalado un servicio requerido (Live Search, Product Recommendations, Servicio de catálogo)
* No hay extensiones de terceros que dependan del indexador de precios principal de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar nuevas fuentes.
1. Instale el adaptador del catálogo.

### GraphQl principal de Luma y Adobe Commerce con dependencias de indexador de precios principal de PHP

* Un comerciante principal de GraphQL de Luma o Adobe Commerce que tiene instalado un servicio compatible (Live Search, Product Recommendations, Servicio de catálogo)
* Con una extensión de terceros que depende del indexador de precios principal de PHP
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar las nuevas fuentes
1. Instale el adaptador del catálogo.
1. Vuelva a habilitar el indexador de precios principal de PHP.
1. Utilice nuevas fuentes y el código de compatibilidad de Luma en la `catalog-adapter` módulo.

### Comerciante sin encabezado

* Un comerciante sin encabezado que tiene instalado un servicio compatible (Live Search, Product Recommendations, Servicio de catálogo)
* Sin dependencia en el indexador de precios PHP Core
* Venta de productos dinámicos simples, configurables, agrupados, virtuales y agrupados

1. Habilitar nuevas fuentes
1. Instale el adaptador de catálogo, que desactiva el indexador de precios principal de PHP.

### Luma/Core GraphQL/Headless con tipos de producto no compatibles

* Comerciante de Luma/sin encabezado
* Venta de tarjetas de regalo, productos descargables o paquetes fijos

Con tipos de producto no compatibles actualmente, espere a que se admita todo el tipo de producto.
