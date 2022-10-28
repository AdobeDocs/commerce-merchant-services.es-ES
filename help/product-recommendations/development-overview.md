---
title: Desarrollo del administrador de Product Recommendations
description: Información general sobre la arquitectura y las funciones de desarrollo de Product Recommendations.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Desarrollo del administrador de Product Recommendations

Product Recommendations es una potente herramienta de marketing que puede utilizar para aumentar las conversiones, aumentar los ingresos y estimular la participación del comprador. El Recommendations de producto aparece en la tienda en forma de unidades como &quot;Los clientes que vieron este producto también vieron&quot;, &quot;Los clientes que compraron este producto también compraron&quot;, &quot;Recomendado para usted&quot;, etc. Adobe Commerce Product Recommendations funciona mediante [Adobe Sensei](https://www.adobe.com/sensei.html), que utiliza inteligencia artificial y algoritmos de aprendizaje automático para realizar un análisis profundo de los datos agregados del comprador. Cuando estos datos se combinan con su catálogo de comercio, se obtienen experiencias muy interesantes, relevantes y personalizadas para el comprador.

>[!NOTE]
>
>Si la tienda se implementa mediante PWA Studio, consulte la [documentación del PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si utiliza una tecnología de front-end personalizada, como React o Vue JS, consulte la guía del usuario para aprender a integrar Product Recommendations en un [headless](headless.md) entorno.

## Información general de arquitectura

En un nivel superior, Commerce Product Recommendations se implementa como SaaS. El lado de Comercio incluye la tienda, que contiene el recopilador de eventos y la plantilla de diseño de recomendaciones, y el servidor, que incluye los servicios de datos, el módulo de exportación de SaaS y la interfaz de usuario del administrador. Los servicios de inteligencia de Adobe Sensei se aprovechan del lado SaaS.

![Diagrama de arquitectura de recomendaciones de productos](assets/arch-diag-sensei.svg)

Una vez instalados y configurados los módulos de recomendación, la tienda empezará a recopilar datos de comportamiento. Adobe Sensei procesa estos datos de comportamiento junto con los datos del catálogo y calcula las asociaciones de productos que utiliza el servicio de recomendaciones. En este punto, el comerciante puede crear, administrar e implementar unidades de recomendación de productos en su tienda directamente desde la interfaz de usuario del administrador.

## Tipos de datos

Product Recommendations requiere los siguientes datos:

- **Comportamiento** : datos de la participación de un comprador en el sitio, como vistas de productos, artículos agregados al carro de compras y compras. Commerce y Adobe Sensei no recopilan información de identificación personal.

- **Catálogo** : metadatos del producto, como nombre, precio, disponibilidad, etc.

Al instalar el `magento/product-recommendations` , Adobe Sensei agrega los datos de comportamiento y catálogo, creando Product Recommendations para cada tipo de recomendación. A continuación, el servicio Product Recommendations implementa esas recomendaciones en su tienda.

## Pasos siguientes

Lea los siguientes temas para empezar a usar Product Recommendations:

- [Cómo implementar Product Recommendations](implementation-workflow.md)

- [Instalación y configuración de Product Recommendations](install-configure.md)

- [Crear Recommendations de producto](create.md)
