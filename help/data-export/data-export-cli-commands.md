---
title: Interfaz de línea de comandos de exportación de datos SaaS
description: '"Aprenda a utilizar los comandos de la interfaz de la línea de comandos para administrar fuentes y procesos para [!DNL data export extension] para servicios SaaS de Adobe Commerce".'
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Referencia de la interfaz de la línea de comandos para la exportación de datos SaaS

Los desarrolladores y administradores de sistemas pueden administrar las operaciones de sincronización para la exportación de datos SaaS mediante [Herramienta de línea de comandos de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI). El `saas:resync` El comando se incluye en `magento/saas-export` paquete.

El Adobe no recomienda el uso de `saas:resync` mandar regularmente. Los escenarios habituales para utilizar el comando son:

- La sincronización inicial
- El [ID del espacio de datos SaaS](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) se ha cambiado y debe sincronizar los datos con el nuevo espacio de datos.
- Resolución de problemas

## Sincronización inicial

Cuando déclencheur un `saas:resync` desde la línea de comandos, según el tamaño del catálogo, los datos pueden tardar entre unos minutos y unas pocas horas en actualizarse.

>[!NOTE]
>Si utiliza Live Search o Product Recommendations, no es necesario que inicie la sincronización. El proceso se inicia automáticamente después de conectar el servicio a la instancia de Commerce.

## Ejemplos de comandos

Antes de usar `saas:resync` comandos, revise la [descripciones de opciones](#command-options).

- Realice una resincronización completa de una fuente de entidades.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Las fuentes que ya se han exportado correctamente no se vuelven a sincronizar.

- Sincronizar completamente los datos de fuente y limpieza especificados

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Usar solo después de realizar una [!DNL Data Space ID Cleanup] operación.

- Para las fuentes de exportación inmediatas, reenvíe todos los datos a servicios de Commerce conectados sin truncar los datos de índice de la tabla de fuentes

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Enumerar comandos y opciones disponibles con descripciones.

  ```
  bin/magento saas:resync --help
  ```

## Opciones de comando

Las siguientes opciones están disponibles para administrar `saas:resync` operaciones.

>[!NOTE]
>
>El `saas:resync` Este comando también admite opciones avanzadas para mejorar los comandos de exportación de datos aumentando el tamaño del lote y agregando el procesamiento de subprocesos múltiples. Consulte [Personalizar procesamiento de exportación](customize-export-processing.md).

### `feed`

Esta opción requerida especifica qué entidad de fuente se debe resincronizar, como `products`.

El `feed` el valor de opción puede incluir cualquiera de las fuentes de entidad disponibles:

- `products`: fuente de datos del producto
- `productAttributes`: fuente de datos de atributos del producto
- `categories`: fuente de datos de categorías
- `variants`: fuente de datos de variaciones de productos configurables
- `prices`: fuente de datos de precios del producto
- `categoryPermissions`: fuente de datos de permisos de categoría
- `productOverrides`: fuente de datos de permisos del producto
- `inventoryStockStatus`: fuente de datos de estado de stock de inventario
- `scopesWebsite`: sitios web con tiendas y fuentes de datos de vistas de tiendas
- `scopesCustomerGroup`: fuente de datos de grupos de clientes
- `orders`: fuente de datos de pedidos de ventas

Dependiendo del [Servicios de Commerce](../landing/saas.md) están instalados, es posible que tenga un conjunto diferente de fuentes disponibles para el `saas:resync` comando.

### `no-reindex`

Esta opción vuelve a enviar los datos del catálogo existentes a [!DNL Commerce Services] sin reindexación. Si no se especifica esta opción, el comando ejecuta una reindexación completa antes de sincronizar los datos.

El comportamiento de esta opción depende de si la fuente se exporta en [modo de exportación heredado o inmediato](data-synchronization.md#synchronization-modes)

- Para fuentes de exportación heredadas, el proceso de sincronización no trunca los datos indexados en la tabla de fuentes. En su lugar, vuelve a enviar todos los datos al servicio de Adobe Commerce.
- En el caso de las fuentes de exportación inmediatas, esta opción se ignora si se especifica. Para estas fuentes, el proceso de resincronización no trunca el índice y solo vuelve a sincronizar las actualizaciones o los elementos con errores anteriores.

### `cleanup`

Esta opción limpia la tabla del indizador de fuentes antes de una sincronización. Cuando se especifica, la exportación de datos de SaaS ejecuta una resincronización completa para la fuente especificada y limpia todos los datos existentes en la tabla de fuentes.

El Adobe recomienda utilizar este comando únicamente después de ejecutar el [!DNL Data Space ID Cleanup] operación.

>[!WARNING]
>
>**No utilice esta opción con regularidad**. Puede provocar problemas de sincronización de datos en los servicios de Adobe Commerce. Por ejemplo, la variable `delete product event` podría no propagarse al servicio Adobe Commerce si la variable `cleanup` se utiliza la opción.

## Resolución de problemas

Si no ve los datos esperados en los servicios de Commerce conectados, solucione los problemas comprobando los registros de errores de exportación de datos y utilizando `saas:resync` comando con variables de entorno para revisar las cargas útiles y los datos del generador de perfiles. Consulte [Revisar registros y solucionar problemas](troubleshooting-logging.md).
