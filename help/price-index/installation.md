---
title: Instalación manual de indexación de precios SaaS
description: Instalación de la indexación de precios SaaS para la versión anterior
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: be0b8f4c26f11c31da3e5422bb4f4c4af10f2a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Instalación manual de indexación de precios SaaS

La indexación de precios SaaS está disponible de forma predeterminada para [última versión](index.md#Requirements) de Commerce Services.
Si no tiene la versión más reciente y desea habilitar la indexación de precios SaaS para su instancia de Adobe Commerce, utilice esta miniguía.

## Requisitos previos

* Adobe Commerce 2.4.4+
* Al menos uno de los siguientes servicios SaaS instalados:

   * [Servicio de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Product Recommendations](../product-recommendations/guide-overview.md)

## Instalación de los módulos necesarios

Según la configuración, el proceso de instalación puede ser ligeramente diferente.
Existen extensiones que agregan las nuevas fuentes y el código de compatibilidad, y una extensión que elimina la fuente de precios predeterminada.

1. Añada los siguientes módulos a su `composer.json` archivo:

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. Ejecute el comando de actualización:

   ```bash
   bin/magento setup:upgrade
   ```

Después de la actualización, hay tres fuentes nuevas disponibles:

* `prices` - responsable de la entrega de datos de precios al servicio
* `scopesCustomerGroup` - responsable de prestar los grupos de clientes al servicio
* `scopesWebsite` : responsable de la entrega de sitios web, grupos de tiendas y vistas de tiendas al servicio


1. Configure las nuevas fuentes para que se configuren en el modo &quot;Actualizar según lo programado&quot;:

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Reindexe las nuevas fuentes:

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Ejecute los indexadores anteriores manualmente, según sea necesario. De lo contrario, los datos se actualizan en el proceso de sincronización estándar. Más información sobre la [Sincronización de catálogo](../landing/catalog-sync.md) servicio.


Los usuarios de Luma y Adobe Commerce Core GraphQL pueden instalar el [`Catalog Adapter`](catalog-adapter.md) que proporciona compatibilidad con Luma y Core GraphQl y deshabilita el indexador de precios de productos de Adobe Commerce.

## Advertencias

Antes `103.0.0` versión, indexación de precios SaaS admitida Tipos de producto simples, agrupados, virtuales, configurables y dinámicos agrupados.
La compatibilidad con los tipos de productos Descargable, Tarjetas de regalo y Paquete fijo está disponible a partir de `magento/module-saas-price:103.0.0` y disponibles de forma predeterminada para los servicios de Commerce admitidos.

Las nuevas fuentes deben sincronizarse manualmente con `resync` [comando CLI](../landing/catalog-sync.md#resynccmdline). De lo contrario, los datos se actualizan en el proceso de sincronización estándar. Obtenga más información acerca de [Sincronización de catálogo](../landing/catalog-sync.md) proceso.