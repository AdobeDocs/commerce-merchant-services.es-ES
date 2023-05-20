---
title: Instalación de indexación de precios SaaS
description: Instalación de la indexación de precios SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Instalación de indexación de precios SaaS

La configuración de la indexación de precios SaaS requiere la instalación de nuevos módulos y la ejecución de comandos CLI. Los administradores necesitan acceso desde la línea de comandos para completar esta instalación.

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
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
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

Los usuarios de Luma y Adobe Commerce Core GraphQL pueden instalar el `catalog-adapter` que proporciona compatibilidad con Luma y Core GraphQl y desactiva el indexador de precios principal de PHP.
Para usar la variable `catalog-adapter` módulo, [!DNL Live Search] y [!DNL Catalog Service] primero debe instalarse y configurarse. Siga las [Instalar [!DNL Live Search]](../live-search/install.md) y [Instalación del servicio de catálogo](../catalog-service/installation.md) instrucciones antes de continuar.

Para configurar Live Search y el adaptador de catálogo, siga [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) instrucciones.

```bash
composer require adobe-commerce/catalog-adapter
```

Si es necesario, el indexador de precios PHP puede ser reactivado con el siguiente comando:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
