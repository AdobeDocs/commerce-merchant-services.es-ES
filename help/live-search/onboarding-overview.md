---
title: "Información general sobre la incorporación"
description: "[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Información general sobre la incorporación

Para empezar a usar [!DNL Live Search] para Adobe Commerce, complete el proceso de incorporación para instalar la extensión, configurar las claves de API y sincronizar el catálogo.

## Flujo de incorporación

![[!DNL Live Search] diagrama de incorporación](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatibles

* Adobe Commerce local (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Límites y umbrales

Actualmente, la variable [!DNL Live Search] la API de búsqueda/categoría tiene los límites admitidos y los límites estáticos siguientes:

### Indexación

* Indexa hasta 300 atributos de producto por vista de tienda.
* Indexa solamente los productos de la base de datos de Adobe Commerce.
* Los productos deben estar en el catálogo compartido predeterminado.
* Las páginas de CMS no están indexadas.

### Consulta

* [!DNL Live Search] no tiene acceso a la taxonomía completa del árbol de categorías, lo que hace que algunos escenarios de búsqueda de navegación en capas estén más allá de su alcance.
* [!DNL Live Search] utiliza un extremo único de GraphQL para las consultas con el fin de admitir funciones como facetas dinámicas y búsqueda según el tipo. Aunque similar a la variable [API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), hay algunas diferencias y es posible que algunos campos no sean totalmente compatibles.

Para restringir grupos de clientes con permisos de catálogo:

* Los productos deben asignarse a la categoría raíz.
* Al grupo de clientes &quot;No ha iniciado sesión&quot; se le deben otorgar permisos de navegación &quot;Permitir&quot;.
* Para restringir productos al grupo de clientes No registrado, vaya a cada categoría y establezca permisos para cada grupo de clientes.

### Reglas

* El número máximo de reglas por vista de tienda es de 50.
* El número máximo de condiciones por regla es 10.
* El número máximo de eventos por regla es de 25.

### Sinónimos

* [!DNL Live Search] puede administrar hasta 200 sinónimos por vista de tienda.

## Indexador de precios

Los clientes de Live Search pueden utilizar el nuevo [indexador de precios SaaS](../price-index/index.md), que proporciona actualizaciones de cambios de precios y tiempo de sincronización más rápidos.

### asistencia al PWA

La compatibilidad con Live Search se considera beta porque no todos los PWA se han probado con [!DNL Live Search]. La funcionalidad básica, como la búsqueda y la lista de productos, funcionan en Venia, pero es posible que algunas permutaciones de Graphql no funcionen correctamente.

* La implementación actual del PWA beta de [!DNL Live Search] requiere más tiempo de procesamiento para devolver los resultados de búsqueda que [!DNL Live Search] con la tienda de comercio nativa.
* [!DNL Live Search] en PWA no es compatible [gestión de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Filtrado directamente en `description`, `name`, `short_description` GraphQL no es compatible cuando se usa con [PWA](https://developer.adobe.com/commerce/pwa-studio/), pero se devuelven con un filtro más general.

### No admitido actualmente

* La variable [Búsqueda avanzada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) módulo se desactiva cuando [!DNL Live Search] está instalado y se elimina el vínculo Búsqueda avanzada del pie de página de la tienda.
* Múltiples ubicaciones de inventario que usa [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) u otras extensiones OMS
* Los precios del producto no incluyen [IVA](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
* [Precio de nivel](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) no es compatible con el widget de página de salida de búsqueda activa y lista de productos .

## Cookies

[!DNL Live Search] recopila datos de interacción del usuario como parte de su funcionalidad base y se utilizan cookies para almacenar estos datos. Al recopilar cualquier información de usuario, el usuario debe aceptar almacenar las cookies. [!DNL Live Search] y [!DNL Product Recommendations] comparta el flujo de datos y, por lo tanto, el mismo mecanismo de cookie. Obtenga más información sobre esto en [Gestión de restricciones de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
