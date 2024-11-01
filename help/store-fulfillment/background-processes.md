---
title: Configuración del proceso en segundo plano
description: "Configure las programaciones de  [!DNL Store Fulfillment] procesos en segundo plano utilizados en la sincronización de datos con los servicios de cumplimiento."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Configuración del proceso en segundo plano

La integración de Store Fulfillment utiliza procesos en segundo plano y colas de mensajes para obtener un rendimiento y una escala óptimos. Genere entornos para sus tiendas Adobe Commerce usando [variables de implementación](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) que inician automáticamente [ejecutores de cola de mensajes](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework).

Los procesos en segundo plano se administran mediante la funcionalidad estándar de [Tareas programadas](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron) de Adobe Commerce. Estos procesos son responsables de sincronizar los datos de configuración de los pedidos y los almacenes de comerciantes con los servicios web de cumplimiento de pedidos.

## Administrar tareas programadas para la realización de tiendas

Desde el administrador, vaya a **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Revise la configuración predeterminada de los servicios de Store Fulfillment. Puede personalizar esta configuración en función del volumen de procesamiento de pedidos y la disponibilidad de recursos.
