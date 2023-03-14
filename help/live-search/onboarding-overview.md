---
title: "Resumen de incorporación"
description: "[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 41d6bed30769d3864d93d6b3d077987a810890cc
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Resumen de incorporación

Para empezar a utilizar [!DNL Live Search] para Adobe Commerce, complete el proceso de incorporación para instalar la extensión, configurar las claves API y sincronizar el catálogo.

## Flujo de incorporación

![[!DNL Live Search] diagrama de incorporación](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce local (EE) : 2.4.4+
* Adobe Commerce en la nube (ECE) : 2.4.4+

## Límites y umbrales

Actualmente, la variable [!DNL Live Search] La API de búsqueda/categoría tiene los siguientes límites admitidos y límites estáticos:

### Indexación

* Indexa hasta 300 atributos de producto por vista de tienda.
* Indexa solo los productos de la base de datos de Adobe Commerce.
* Los productos deben estar en el catálogo compartido predeterminado.
* Las páginas de CMS no están indexadas.

### Consulta

* [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación por capas estén fuera de su alcance.
* [!DNL Live Search] utiliza un extremo único de GraphQL para que las consultas admitan características como facetas dinámicas y búsqueda mientras escribe. Aunque es similar a la [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Sin embargo, existen algunas diferencias y es posible que algunos campos no sean totalmente compatibles.

Para restringir los grupos de clientes que utilizan permisos de catálogo:

* Los productos deben asignarse a la categoría Raíz.
* El grupo de clientes &quot;Sin sesión iniciada&quot; debe tener permisos de navegación &quot;Permitir&quot;.
* Para restringir productos al grupo de clientes Sin sesión iniciada, vaya a cada categoría y defina los permisos para cada grupo de clientes.

### Reglas

* El número máximo de reglas por vista de tienda es 50.
* El número máximo de condiciones por regla es de 10.
* El número máximo de eventos por regla es de 25.

### Sinónimos

* [!DNL Live Search] puede administrar hasta 200 sinónimos por vista de tienda.

### soporte de PWA

La compatibilidad con Live Search se considera en versión beta porque no se ha probado todo PWA con [!DNL Live Search]. La funcionalidad básica, como la página de búsqueda y la lista de productos, funciona en Venia, pero es posible que algunas permutaciones de Graphql no funcionen correctamente.

* La implementación actual del PWA beta de [!DNL Live Search] requiere más tiempo de procesamiento para devolver resultados de búsqueda que [!DNL Live Search] con la tienda nativa de Commerce.
* [!DNL Live Search] el PWA in no admite [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Filtrado directamente en `description`, `name`, `short_description` no es compatible con GraphQL cuando se utiliza con [PWA](https://developer.adobe.com/commerce/pwa-studio/), pero se devuelven con un filtro más general.

### Actualmente no es compatible

* El [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) El módulo está desactivado cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
* Varias ubicaciones de inventario utilizadas por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) u otras extensiones de OMS
* Los precios de los productos no incluyen [impuesto sobre el valor añadido](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
* [Precio de nivel](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) no es compatible con la ventana emergente de Live Search y el widget de página de lista de productos.

## Cookies

[!DNL Live Search] recopila datos de interacción del usuario como parte de su funcionalidad base y se utilizan cookies para almacenar estos datos. Al recopilar cualquier información de usuario, el usuario debe aceptar almacenar cookies. [!DNL Live Search] y [!DNL Product Recommendations] compartir el flujo de datos y, por lo tanto, el mismo mecanismo de cookies. Obtenga más información al respecto en [Controlar restricciones de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
