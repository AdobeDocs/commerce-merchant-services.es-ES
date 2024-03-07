---
title: Desarrollo del administrador de Recommendations del producto
description: Descripción general de la arquitectura y las funciones de desarrollo de Product Recommendations.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Desarrollo del administrador de Recommendations del producto

Product Recommendations es una potente herramienta de marketing que puede utilizar para aumentar las conversiones, aumentar los ingresos y estimular la participación del comprador. Product Recommendations se muestra en la tienda en forma de unidades como &quot;Los clientes que vieron este producto también vieron&quot;, &quot;Los clientes que compraron este producto también compraron&quot;, &quot;Recomendado para ti&quot;, etc. Los Recommendations de producto de Adobe Commerce están equipados con [Adobe Sensei](https://www.adobe.com/sensei.html), que utiliza inteligencia artificial y algoritmos de aprendizaje automático para realizar un análisis profundo de los datos agregados del comprador. Estos datos, cuando se combinan con su catálogo de Commerce, generan experiencias muy atractivas, relevantes y personalizadas para el comprador.

>[!NOTE]
>
>Si la tienda está implementada con PWA Studio, consulte la [Documentación del PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Si utiliza una tecnología de front-end personalizada como React o Vue JS, consulte la guía del usuario para aprender a integrar Product Recommendations en una [acéfalo](headless.md) entorno. Las instancias sin encabezado deben implementar eventos para potenciar el espacio de trabajo de recomendaciones de productos.

## Información general de arquitectura

En un nivel superior, Commerce Product Recommendations se implementa como SaaS. El lado de Commerce incluye la tienda, que contiene el recopilador de eventos y la plantilla de diseño de Recommendations, y el back-end, que incluye los servicios de datos, el módulo de exportación de SaaS y la IU de administración. Los servicios de inteligencia de Adobe Sensei se aprovechan del lado del SaaS.

![Diagrama de arquitectura de recomendaciones de productos](assets/arch-diag-sensei.svg)

Una vez instalados y configurados los módulos de recomendación, la tienda empezará a recopilar datos de comportamiento. Adobe Sensei procesa estos datos de comportamiento junto con los datos del catálogo y calcula las asociaciones de productos que aprovecha el servicio de Recommendations. En este punto, el comerciante puede crear, administrar e implementar unidades de recomendación de productos en su tienda directamente desde la IU de administración.

## Tipos de datos

Product Recommendations requiere los siguientes datos:

- **Comportamiento** : datos de la participación de un comprador en el sitio, como vistas de productos, elementos agregados a un carro de compras y compras. Commerce y Adobe Sensei no recopilan información de identificación personal.

- **Catálogo** : metadatos de producto, como nombre, precio, disponibilidad, etc.

Al instalar el `magento/product-recommendations` , Adobe Sensei agrega los datos de comportamiento y de catálogo, creando una Recommendations de producto para cada tipo de recomendación. A continuación, el servicio Product Recommendations implementa esas recomendaciones en la tienda.

>[!NOTE]
>
>Para los productos configurables, Product Recommendations utiliza la imagen del producto principal en la unidad recomendada. Si el producto configurable no tiene una imagen especificada, la unidad de recomendación estará vacía para ese producto específico.

## Pasos siguientes

Lea los temas siguientes para empezar a usar Product Recommendations:

- [Implementación de Recommendations de producto](implementation-workflow.md)

- [Instalación y configuración de Product Recommendations](install-configure.md)

- [Crear Recommendations del producto](create.md)
