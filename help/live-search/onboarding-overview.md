---
title: "Resumen de incorporación"
description: "[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Resumen de incorporación

Para empezar a utilizar [!DNL Live Search] para Adobe Commerce, complete el proceso de incorporación para instalar la extensión, configurar las claves API y sincronizar el catálogo.

## Flujo de incorporación

![[!DNL Live Search] diagrama de incorporación](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4+
* PHP 8.1, 8.2
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce en local (EE) : 2.4.4+
* Adobe Commerce en la nube (ECE) : 2.4.4+

## Límites y umbrales

En este momento, la variable [!DNL Live Search] La API de búsqueda/categoría tiene los siguientes límites admitidos y límites estáticos:

### Indexación

* Indexa hasta 300 atributos de producto por vista de tienda.
* Indexa solo los productos de la base de datos de Adobe Commerce.
* Las páginas de CMS no están indexadas.

### Consulta

* [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación por capas estén fuera de su alcance.
* [!DNL Live Search] utiliza un extremo único de GraphQL para que las consultas admitan características como facetas inteligentes y búsqueda mientras escribe. Aunque es similar a la [API de Magento GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Sin embargo, existen algunas diferencias y es posible que algunos campos no sean totalmente compatibles en este momento.

### Reglas

* El número máximo de reglas por vista de tienda es 50.
* El número máximo de condiciones por regla es de 10.
* El número máximo de eventos por regla es de 25.

### Sinónimos

* [!DNL Live Search] puede administrar hasta 200 sinónimos por vista de tienda.

### Versión beta de PWA

* La implementación actual del PWA beta de Live Search requiere más tiempo de procesamiento para devolver resultados de búsqueda que Live Search con la tienda de comercio nativa.
* La versión beta de PWA para [!DNL Live Search] no admite [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* GraphQL no admite los siguientes atributos de producto cuando se utilizan en relación con la versión beta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### No compatible en este momento

* El [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) El módulo está desactivado cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
* [Grupos de precios personalizados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Varias ubicaciones de inventario utilizadas por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) u otras extensiones de OMS
* Los precios de los productos no incluyen [impuesto sobre el valor añadido](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
