---
title: "Información general sobre la incorporación"
description: "[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Información general sobre la incorporación

Para empezar a usar [!DNL Live Search] para Adobe Commerce, complete el proceso de incorporación para instalar la extensión, configurar las claves de API y sincronizar el catálogo.

## Flujo de incorporación

![[!DNL Live Search] diagrama de incorporación](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce en prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Límites y umbrales

En este momento, la variable [!DNL Live Search] la API de búsqueda/categoría tiene los límites admitidos y los límites estáticos siguientes:

### Indexación

* Indexa hasta 300 atributos de producto por vista de tienda.
* Indexa solamente los productos de la base de datos de Adobe Commerce.
* Las páginas de CMS no están indexadas.

### Consulta

* [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación en capas estén más allá de su alcance.
* [!DNL Live Search] utiliza un punto final único de GraphQL para las consultas con el fin de admitir funciones como facetas inteligentes y search-as-you-type. Aunque similar a la variable [API de Magento GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), hay algunas diferencias y es posible que algunos campos no sean totalmente compatibles en este momento.

### Reglas

* El número máximo de reglas por vista de tienda es de 50.
* El número máximo de condiciones por regla es 10.
* El número máximo de eventos por regla es de 25.

### Sinónimos

* [!DNL Live Search] puede administrar hasta 200 sinónimos por vista de tienda.

### versión beta del PWA

* La implementación actual del PWA beta de la búsqueda activa requiere más tiempo de procesamiento para devolver los resultados de búsqueda que la búsqueda en vivo con la tienda de comercio nativa.
* La versión beta de PWA para [!DNL Live Search] no es compatible [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* GraphQL no admite los siguientes atributos de producto cuando se utilizan en relación con la versión beta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### No compatible en este momento

* La variable [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) módulo se desactiva cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
* [Grupos de precios personalizados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Múltiples ubicaciones de inventario que usa [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) u otras extensiones OMS
* Los precios del producto no incluyen [IVA](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
