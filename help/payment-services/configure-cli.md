---
title: Configuración de línea de comandos
description: Después de la instalación, puede configurar [!DNL Payment Services] mediante la interfaz de la línea de comandos (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Configuración de línea de comandos

Después de la instalación [!DNL Payment Services], puede configurarlo fácilmente desde [dentro del hogar](payments-home.md) o a través de la Interfaz de línea de comandos (CLI).

## Configuración de exportación de datos

[!DNL Payment Services] combina datos de pedidos exportados desde [!DNL Magento Open Source] y [!DNL Adobe Commerce] con datos de pago agregados de proveedores de pagos para crear informes útiles. El [!DNL Payment Services] La extensión de utiliza indexadores para recopilar de forma eficaz todos los datos necesarios para los informes.

Para obtener más información sobre los datos utilizados en [!DNL Payment Services] informes, consulte [Informe de estado de pago del pedido](order-payment-status.md#data-used-in-the-report).

### Configuración de cron en [!DNL Magento Open Source]

Si desea utilizar un `BY SCHEDULE` modo de índice activado [!DNL Magento Open Source], debe configurar cron. Consulte [Configurar y ejecutar cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Establecer indizadores

Los datos de pedidos se exportan y se mantienen en Payment Service, mediante uno de los dos modos de índice siguientes:`ON SAVE` (predeterminado) o `BY SCHEDULE` (recomendado).

Los siguientes índices son para [!DNL Payment Services]:

| Código | Nombre | Descripción |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Fuente de pedidos de ventas | Crea un índice de datos de pedidos |
| `sales_order_status_data_exporter` | Fuente de estados de pedidos de ventas | Crea un índice de datos de estados de pedidos de ventas |
| `store_data_exporter` | Almacena fuente | Crea un índice de datos almacenados |

Para cambiar el modo de índice de los tres indexadores, ejecute:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Si no especifica ningún indizador en el comando, todos los indizadores se actualizarán con el mismo valor. Si desea cambiar un indizador específico, debe enumerarlo en el comando.

Para obtener más información sobre cómo cambiar manualmente el modo de un indizador, consulte [Configuración de indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} en la guía del usuario principal.

### Reindexación manual de datos

Puede reindexar los datos manualmente, en lugar de esperar a que se produzca automáticamente. Consulte [Reindexar](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} para obtener más información.

Cuándo `BY SCHEDULE` Cuando el modo está configurado, el sistema rastrea las entidades cambiadas y el trabajo cron actualiza el índice para ellas en función de una programación establecida. Consulte [Ejecute cron desde la línea de comandos](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Configurar y ejecutar cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) para aprender a indexar manualmente el déclencheur mediante trabajos cron.

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

El `--feed` Este parámetro le permite especificar qué fuente desea enviar:

| Fuente | Descripción |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Fuente de pedidos en modo de producción |
| `paymentServicesOrdersSandbox` | Fuente de pedidos en modo de espacio aislado |
| `paymentServicesOrderStatusesProduction` | Estados de pedidos en modo de producción |
| `paymentServicesOrderStatusesSandbox` | Estados de pedidos en modo de espacio aislado |
| `paymentServicesStoresProduction` | Tiendas en modo de producción |
| `paymentServicesStoresSandbox` | Tiendas en modo de espacio aislado |

Todos los datos necesarios para los informes se envían a [!DNL Payment Services] automáticamente si cron está configurado e instalado. También puede almacenar en déclencheur manualmente el proceso de envío de datos cron a [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Para obtener más información sobre la reindexación y los indexadores, consulte la [Administrar los indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) en la documentación para desarrolladores.
