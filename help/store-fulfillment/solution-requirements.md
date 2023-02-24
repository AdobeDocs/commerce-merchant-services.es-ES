---
title: Requisitos de cumplimiento de la tienda
description: Requisitos para el aprovisionamiento e incorporación de la variable [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Requisitos de cumplimiento de la tienda para Adobe Commerce

En las siguientes secciones se detallan los requisitos técnicos y empresariales para instalar y habilitar la solución Store Fulfillment para Adobe Commerce.

## Requisitos de versiones de software y plataforma

La variable [!DNL Store Fulfillment] está disponible para los clientes de Adobe Commerce en las siguientes plataformas.

- Adobe Commerce en infraestructura de nube (ECE)
- Adobe Commerce local (EE)

La solución Store Fulfillment es compatible con las versiones de software enumeradas en la *Compatibilidad del software* tabla.

**Compatibilidad de software**

| **Software** | **Versión mínima** | **Versión máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Compositor | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Para conocer los requisitos detallados, consulte Adobe Commerce . [Requisitos del sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) en el *Guía de instalación de Adobe Commerce*.

## Requisitos de la aplicación de asistencia de la tienda

El proceso completo para administrar los pedidos de recogida de tiendas se administra mediante la aplicación de asistencia de tiendas instalada en dispositivos móviles. Estos dispositivos (proporcionados por el minorista o por los empleados de la tienda que utilizan sus teléfonos inteligentes personales) deben cumplir los siguientes requisitos:

**Requisitos mínimos del sistema operativo**

- Android 6
- iOS 12

**Requisitos mínimos de hardware**

- 1 GB de RAM
- 600 MB de espacio libre en disco

## Requisitos empresariales

Su empresa debe cumplir los siguientes criterios mínimos para implementar la solución de cumplimiento de almacenamiento:

- Solo empresas basadas en EE. UU.

- Comerciales a consumidores (B2C) minoristas, productos envasados al consumidor (CPG) Fabricantes que venden directamente a los consumidores (D2C) o distribuidores que venden directamente a consumidores o pequeñas empresas

- Al menos un almacén físico o almacén

- Administrar el inventario de productos con Inventory management para Adobe Commerce (también conocido como MSI)

- Capacidad de sindicación de inventario de comerciantes

- Almacene la disponibilidad de Wi-Fi en todas las ubicaciones que admitan la solución Store Fulfillment: Velocidad mínima de Internet de 3 Mbps

- Los asociados de almacén y almacén tienen acceso a dispositivos móviles iOS o Android durante sus turnos, ya sea personales o proporcionados por el comerciante

- Los productos que se administran mediante la solución Store Fulfillment deben tener atributos de producto que incluyan un SKU o código de producto UPC
