---
title: Extensión de adaptador de catálogo
description: Uso del adaptador de catálogo para representar los precios de Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: a637ece6e806771dfc6359dacececf8ccf05b983
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Adaptador de catálogo

El `Catalog Adapter` La extensión de deshabilita el indexador de precios de producto predeterminado de Adobe Commerce y, en su lugar, utiliza los precios proporcionados desde el [Servicio de catálogo](../catalog-service/overview.md).
El indexador de precios de productos Adobe Commerce está desactivado y no se puede activar con estos módulos de extensión instalados. Solo eliminando o deshabilitando esta extensión se puede volver a habilitar el indexador de precios de producto predeterminado.

## Requisitos

* Adobe Commerce 2.4.4+
* Tener instalados los siguientes servicios de Commerce:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)

## Instalación

Para usar la variable `catalog-adapter` módulo, [!DNL Live Search] y [!DNL Catalog Service] primero debe instalarse y configurarse. Siga las [Instalar [!DNL Live Search]](../live-search/install.md) y [Instalación del servicio de catálogo](../catalog-service/installation.md) instrucciones antes de continuar.

Una vez instalados esos servicios, ejecute el siguiente comando:

```bash
composer require adobe-commerce/catalog-adapter
```

## Volver a habilitar el indexador de precios de productos de Adobe Commerce

Si tiene aplicaciones de terceros que dependen del indexador predeterminado de precios de productos de Adobe Commerce, puede volver a activarlas con los siguientes comandos:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Deshabilitar indizador de precios de productos para escenario de tienda sin encabezado

Si tiene una instancia de Commerce sin encabezado, es posible que tenga que deshabilitar el indexador de precios de productos Adobe Commerce para reducir la carga en la instancia de Adobe Commerce.
Esto se hace instalando el `magento/module-price-indexer-disabler` módulo:

```bash
composer require magento/module-price-indexer-disabler
```

## Escenarios de uso

Los siguientes son algunos ejemplos comunes `Catalog Adapter` escenarios.

### Sin dependencias en el indexador de precios de productos Adobe Commerce

* Es un comerciante de Luma o Adobe Commerce Core GraphQL que tiene instalado un servicio requerido (Live Search, Product Recommendations, Servicio de catálogo)
* No hay extensiones de terceros que dependan del indexador de precios de productos de Adobe Commerce

1. Instale el adaptador del catálogo.

### Con dependencias en el indexador de precios de productos Adobe Commerce

* Es un comerciante de Luma o Adobe Commerce Core GraphQL que tiene instalado un servicio compatible (Live Search, Product Recommendations, Servicio de catálogo)
* Utilice una extensión de terceros que dependa del indexador de precios de productos de Adobe Commerce

1. Instale el adaptador del catálogo.
1. Vuelva a habilitar el indexador de precios de producto predeterminado de Adobe Commerce.

### Instancias de comercio sin encabezado

* Un comerciante con una instancia de Commerce sin encabezado con los servicios necesarios instalados (Live Search, Product Recommendations, Servicio de catálogo)
* No se depende del indexador de precios de producto predeterminado de Adobe Commerce

1. Instale el `magento/module-price-indexer-disabler` del paquete del adaptador de catálogo.
