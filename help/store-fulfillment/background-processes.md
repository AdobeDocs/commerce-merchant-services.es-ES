---
title: Configuración del proceso en segundo plano
description: "Configure las programaciones de [!DNL Store Fulfillment] procesos en segundo plano utilizados para sincronizar datos con los servicios de cumplimiento."
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Configuración del proceso en segundo plano

La integración de entrega de almacenamiento utiliza procesos en segundo plano y colas de mensajes para obtener un rendimiento y una escala óptimos. Cree entornos para las tiendas de Adobe Commerce mediante [variables de implementación](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) que se inicia automáticamente [ejecute la cola de mensajes](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Los procesos en segundo plano se administran mediante el Adobe Commerce estándar [Tareas programadas](https://docs.magento.com/user-guide/system/cron.html) funcionalidad. Estos procesos son responsables de sincronizar los datos de configuración de los almacenes de pedidos y comerciales con los servicios web de cumplimiento de los almacenes.

## Administrar tareas programadas para el cumplimiento de la tienda

Desde el administrador, vaya a **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Revise la configuración predeterminada de los servicios de cumplimiento de la tienda. Según el volumen de procesamiento de los pedidos y la disponibilidad de los recursos, es posible que tenga que ajustar esta configuración.
