---
title: Servicio de ingesta de fuentes
description: Obtenga información acerca del servicio de ingesta de fuentes para Adobe Commerce
source-git-commit: 12b1e89924a2eb89494bcb884fc3bc14e87b2b1c
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Servicio de ingesta de fuentes

>[!NOTE]
>
>El servicio de ingesta de fuentes se encuentra actualmente en versión beta privada. Todavía no está disponible para uso general.

El servicio de ingesta de fuentes reduce el tiempo que se tarda en procesar los cambios de productos (actualizaciones de precios, adición de nuevos atributos) al omitir la instancia de Adobe Commerce y mover los datos de catálogo de un Enterprise Resource Planning (ERP) de terceros directamente a los servicios de Adobe Commerce.

Este servicio es para clientes que almacenan y administran su catálogo de productos en un sistema externo a la aplicación principal de Adobe Commerce.

A los clientes con catálogos grandes y complejos o que reciben actualizaciones frecuentes les preocupa que los nuevos datos puedan tardar más de lo deseado en aparecer en la tienda en directo. Dado que el servicio de catálogo sabe qué datos necesita para procesar estas actualizaciones, no es necesario enviar los datos a través del producto principal de comercio, solo para reenviarlos al servicio de catálogo. La eliminación de este paso intermedio es donde se encuentran las ganancias de eficiencia.

## Flujos de ingesta de fuentes

Según la configuración de Adobe Commerce, el almacenamiento y los flujos de datos pueden seguir diferentes rutas.

* En una instancia estándar de Adobe Commerce, el catálogo de productos se almacena en la base de datos principal.
* Al utilizar los servicios de Adobe Commerce, los datos del catálogo se copian de la base de datos principal al servicio y se procesan y entregan desde allí.
* Al almacenar los datos del catálogo en un sistema de terceros (ERP, MDM, PIM), los datos fluyen a través de la aplicación principal de Commerce y, a continuación, a los servicios de Commerce.
* Con Feed Ingestion Service, los datos de productos pasan directamente del sistema de terceros a la infraestructura de servicios de Commerce.

![Servicio de ingesta de fuentes](assets/feed-ingestion.png)

Al omitir la aplicación principal de Commerce y mover los datos directamente a los servicios de Commerce, las actualizaciones de productos se reflejan en la tienda más rápido. Los datos del catálogo principal, como los SKU, se envían a la aplicación principal de Commerce para un procesamiento independiente.

## Unirse a la versión beta

El servicio de ingesta de fuentes está diseñado para:

* Clientes de medianas empresas con implementaciones sin encabezado
* Clientes con catálogos grandes y complejos
* Clientes que no utilizan el administrador de Adobe Commerce para administrar los datos del catálogo y que, en su lugar, utilizan un sistema ERP o de terceros para administrar los datos del catálogo

Si está interesado en unirse al programa beta, póngase en contacto con el equipo de en sagonzal@adobe.com.
