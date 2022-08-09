---
title: '"[!DNL Catalog Service] Notas de la versión"'
description: '"La información de la última versión de [!DNL Catalog Service] para Adobe Commerce".'
source-git-commit: 3959cc5d07f9a0da0ba772a4f3bc56adeb3c6bf3
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%

---


# [!DNL Catalog Service] Notas de la versión

{{catalog-service-beta}}

Estas notas de la versión describen las versiones más recientes de [!DNL Catalog Service] e incluyen:

* ![Nuevo](../assets/new.svg) - Nuevas funciones
* ![Corrección](../assets/fix.svg) - Correcciones y mejoras
* ![Error](../assets/bug.svg) - Problemas conocidos

## Versión beta

* ![Nuevo](../assets/new.svg) - El `products` y `refineProduct` las consultas devuelven los siguientes datos:
   * Atributos de producto predefinidos (del sistema).
   * Atributos de producto dinámicos y filtrarlos por función (página de visualización de producto/página de lista de productos).
   * Opciones de producto.
   * Imágenes del producto y filtrarlas por función (PDP/PLP).
   * Un precio específico para productos simples e intervalos de precios para productos configurables.
   * Precios e intervalos de precios del grupo de clientes. Devuelven un precio predeterminado de reserva en compradores sin un grupo de clientes.
   * Tipos de productos que utilizan precios específicos del cliente de B2B.

## Limitaciones conocidas

* No se admite el precio de nivel.
* En una matriz de imágenes, solo la primera imagen contiene funciones.
* Las imágenes de las variantes no se recuperan.
* Las actualizaciones no se reciben cuando se eliminan productos o variantes del catálogo.
