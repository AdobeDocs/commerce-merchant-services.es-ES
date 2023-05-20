---
title: Configuración del proceso en segundo plano
description: '"Configurar los horarios para [!DNL Store Fulfillment] procesos en segundo plano utilizados en la sincronización de datos con los servicios de cumplimiento".'
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Configuración del proceso en segundo plano

La integración de Store Fulfillment utiliza procesos en segundo plano y colas de mensajes para obtener un rendimiento y una escala óptimos. Cree entornos para sus tiendas Adobe Commerce con [variables de implementación](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) que se inician automáticamente [ejecutores de cola de mensajes](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Los procesos en segundo plano se administran mediante Adobe Commerce estándar [Tareas programadas](https://docs.magento.com/user-guide/system/cron.html) funcionalidad. Estos procesos son responsables de sincronizar los datos de configuración de los pedidos y los almacenes de comerciantes con los servicios web de cumplimiento de pedidos.

## Administrar tareas programadas para la realización de tiendas

Desde Admin, vaya a **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Revise la configuración predeterminada de los servicios de Store Fulfillment. Según el volumen de procesamiento de pedidos y la disponibilidad de recursos, es posible que tenga que ajustar esta configuración.
