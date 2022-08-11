---
title: '''[!DNL Catalog Service] Notas de la versión'''
description: La información de la última versión de [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 72913e0c0b7364e38d37fe1a8279c40a4e849c02
workflow-type: tm+mt
source-wordcount: '153'
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

* No se admiten paquetes y productos agrupados.
* No se admite el precio de nivel.
* En una matriz de imágenes, solo la primera imagen contiene funciones.
* Las imágenes de las variantes no se recuperan.
* Las actualizaciones no se reciben cuando se eliminan productos o variantes del catálogo.
