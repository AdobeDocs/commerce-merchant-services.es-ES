---
title: Configuración de la línea de comandos
description: Después de la instalación, puede configurar [!DNL Payment Services] uso de la interfaz de línea de comandos (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Configuración de la línea de comandos

Después de la instalación [!DNL Payment Services], puede configurarlo fácilmente desde [dentro de la página principal](payments-home.md) o a través de la interfaz de línea de comandos (CLI).

## Configuración de la exportación de datos

[!DNL Payment Services] combina datos de pedido exportados de [!DNL Magento Open Source] y [!DNL Adobe Commerce] con los datos de pago agregados de los proveedores de pagos para crear informes útiles. La variable [!DNL Payment Services] utiliza indexadores para recopilar de forma eficaz todos los datos necesarios para los informes.

Para obtener más información sobre los datos utilizados en [!DNL Payment Services] informes, véase [Informe del estado del pago del pedido](order-payment-status.md#data-used-in-the-report).

### Configurar cron en [!DNL Magento Open Source]

Si desea usar un `BY SCHEDULE` modo índice activado [!DNL Magento Open Source], debe configurar cron. Consulte [Configuración y ejecución de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Establecer indexadores

Los datos de pedido se exportan y se mantienen en el Servicio de Pago, utilizando uno de los dos modos de índice:`ON SAVE` (predeterminado) o `BY SCHEDULE` (recomendado).

Los siguientes índices son para [!DNL Payment Services]:

| Código | Nombre | Descripción |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Fuente de pedido de ventas | Genera índice de datos de pedido |
| `sales_order_status_data_exporter` | Fuente de estados de pedidos de venta | Genera el índice de los estados de los pedidos de venta |
| `store_data_exporter` | Fuente de tiendas | Genera un índice de datos de almacenamiento |

Para cambiar el modo de índice para los tres indexadores, ejecute:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Si no especifica ningún indizador en el comando, todos los indexadores se actualizan al mismo valor. Si desea cambiar un indexador específico, debe enumerarlo en el comando .

Para obtener más información sobre el cambio manual del modo de un indizador, consulte [Configuración de indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target=&quot;_blank&quot;} en la documentación del desarrollador. Para obtener información sobre cómo cambiarla en el Administrador, consulte [Administración de índices](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;} en la guía de usuario principal.

### Reindexar manualmente los datos

Puede reindexar manualmente los datos en lugar de esperar a que se produzcan automáticamente. Consulte [Reindex](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot;} en [Administrar los indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;} para obtener más información.

When `BY SCHEDULE` está configurado, el sistema realiza el seguimiento de las entidades cambiadas y el trabajo cron actualiza el índice para ellas en función de una programación establecida. Consulte [Ejecutar cron desde la línea de comandos](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) en [Configuración y ejecución de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) para aprender a déclencheur manual de la indexación mediante trabajos cron.

### Enviar datos reindexados al servicio de pago

Una vez indexados los datos, se envían automáticamente a [!DNL Payment Services]. También puede almacenar en déclencheur manualmente el proceso de envío de datos indexados con este comando:

```bash
bin/magento saas:resync --feed [feedName]
```

Utilice las siguientes opciones de comando:

| Comando | Descripción |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Realiza una reindexación de la fuente especificada y la envía al servicio correspondiente |
| `bin/magento saas:resync --no-reindex` | Omite la indexación y envía datos sin sincronizar desde los índices |

La variable `--feed` le permite especificar qué fuente desea enviar:

| Fuente | Descripción |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Fuente Pedidos en modo Producción |
| `paymentServicesOrdersSandbox` | Fuente Pedidos en modo Simulador para pruebas |
| `paymentServicesOrderStatusesProduction` | Estados de pedido en modo Producción |
| `paymentServicesOrderStatusesSandbox` | Estados de pedidos en modo Simulador para pruebas |
| `paymentServicesStoresProduction` | Almacenes en modo Producción |
| `paymentServicesStoresSandbox` | Almacenes en modo Sandbox |

Todos los datos necesarios para los informes se envían a [!DNL Payment Services] automáticamente si cron está configurado e instalado. También puede realizar el déclencheur manual del proceso de envío de datos cron a [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Para obtener más información sobre la reindexación y los indexadores, consulte la [Administrar los indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) en la documentación para desarrolladores.
