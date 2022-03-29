---
title: Información general sobre la incorporación
description: Búsqueda activa Flujo de incorporación, requisitos del sistema, límites y limitaciones
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Información general sobre la incorporación

Para empezar a utilizar Live Search para Adobe Commerce, debe completar algunos pasos de integración para instalar la extensión, configurar las claves de API y sincronizar el catálogo.

## Flujo de incorporación

![Diagrama de integración de Live Search](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce en prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Límites y umbrales

En este momento, la API de búsqueda/categoría de Live Search tiene los siguientes límites admitidos y límites estáticos:

### Indexación

* Indexa hasta 300 atributos de producto por vista de tienda
* Indexa solo los productos de la base de datos de Adobe Commerce
* No indexa páginas de CMS

### Límites de consulta

* La búsqueda activa no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación en capas estén más allá de su alcance.
* La búsqueda en directo utiliza un extremo único de GraphQL para las consultas con el fin de admitir funciones como facetas inteligentes y la búsqueda en el momento en que escribes. Aunque similar a la variable [API de Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql), hay algunas diferencias y es posible que algunos campos no sean totalmente compatibles en este momento.

### versión beta del PWA

* La versión beta de PWA para Live Search no es compatible [gestión de eventos](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* GraphQL no admite los siguientes atributos de producto cuando se utilizan en relación con la versión beta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### No compatible en este momento

* La variable [Búsqueda avanzada](https://docs.magento.com/user-guide/catalog/search-advanced.html) se desactiva cuando está instalada la búsqueda activa y se elimina el vínculo Búsqueda avanzada en el pie de página de la tienda.
* [Grupos de clientes](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Grupos de precios personalizados](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Múltiples ubicaciones de inventario que usa [MCOM](https://docs.magento.com/user-guide/mcom.html) u otras extensiones OMS
* [Capacidades integradas B2B](https://business.adobe.com/products/magento/b2b-ecommerce.html)
