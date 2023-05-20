---
title: Requisitos de cumplimiento de tienda
description: Requisitos para el aprovisionamiento e incorporación de [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Requisitos de cumplimiento de tienda para Adobe Commerce

En las siguientes secciones se detallan los requisitos técnicos y empresariales para instalar y habilitar la solución Store Fulfillment para Adobe Commerce.

## Requisitos de plataforma y versión de software

El [!DNL Store Fulfillment] está disponible para los clientes de Adobe Commerce en las plataformas siguientes.

- Adobe Commerce en infraestructura en la nube (ECE)
- Adobe Commerce local (EE)

La solución Store Fulfillment es compatible con las versiones de software enumeradas en la *Compatibilidad de software* tabla.

**Compatibilidad de software**

| **Software** | **Versión mínima** | **Versión máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Compositor | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Para conocer los requisitos detallados, consulte Adobe Commerce [Requisitos del sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) en el *Guía de instalación de Adobe Commerce*.

## Requisitos de la aplicación Store Assist

El proceso de extremo a extremo para administrar los pedidos de recogida de la tienda se administra a través de la aplicación Store Assist instalada en dispositivos móviles. Estos dispositivos, proporcionados por el minorista o por los empleados de la tienda que utilizan sus teléfonos inteligentes personales, deben cumplir los siguientes requisitos:

**Requisitos mínimos del sistema operativo**

- Android 6
- iOS 12

**Requisitos mínimos de hardware**

- 1 GB de RAM
- 600 MB de espacio libre en disco

## Requisitos empresariales

Su empresa debe cumplir los siguientes criterios mínimos para implementar la solución Store Fulfillment:

- Solo empresas con sede en Estados Unidos

- Minoristas de comercio al consumidor (B2C), fabricantes de productos empaquetados para el consumidor (CPG) que venden directamente a consumidores (D2C) o distribuidores que venden directamente a consumidores o pequeñas empresas

- Al menos un almacén físico

- Administre su inventario de productos con Inventory management para Adobe Commerce (también conocido como MSI)

- Capacidad para sindicar el inventario comercial

- Disponibilidad de Wi-Fi de tienda en todas las ubicaciones que admitan la solución Store Fulfillment: 3 Mbps de velocidad mínima de Internet

- Los socios de tiendas y almacenes tienen acceso a dispositivos móviles iOS o Android durante sus turnos, ya sean personales o proporcionados por el comerciante

- Los productos administrados mediante la solución Store Fulfillment deben tener atributos de producto que incluyan un código de producto SKU o UPC
