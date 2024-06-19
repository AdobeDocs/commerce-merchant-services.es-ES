---
title: Revisar registros y solucionar problemas
description: '"Aprenda a solucionar problemas [!DNL data export] errores al utilizar los registros de exportación de datos y exportación de saas".'
feature: Services
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Revisar registros y solucionar problemas

El [!DNL data export] La extensión de proporciona registros para rastrear la recopilación de datos y los procesos de sincronización.

## Registros

Los registros están disponibles en `var/log` en el servidor de aplicaciones de Commerce.

| nombre del registro | filename | description |
|-----------------| ----------| -------------|
| Registro de exportación de datos SaaS | `commerce-data-export.log` | Proporciona información sobre las actividades de exportación de datos, como eventos de entidad y déclencheur de resincronización completos.  Cada registro tiene una estructura específica y proporciona información sobre la fuente, la operación, el estado, el tiempo transcurrido, el ID de proceso y el llamador. |
| Registro de errores de exportación de datos SaaS | `data-export-errors.log` | Proporciona mensajes de error y seguimientos de pila para los errores que se producen durante el proceso de sincronización de datos. |
| Registro de exportación de SaaS | `saas-export.log` | Proporciona información sobre los datos enviados a los servicios SaaS de Commerce. |
| Registro de errores de exportación de SaaS | `saas-export-errors.log` | Proporciona información sobre los errores que se producen al enviar datos a los servicios SaaS de Commerce. |

Si no ve los datos esperados para un servicio de Adobe Commerce, utilice los registros de error de la extensión de exportación de datos para determinar dónde se produjo el problema.

Puede ampliar los registros con datos adicionales para el seguimiento y la resolución de problemas. Consulte [Registro extendido](#extended-logging).

### Formato de registro

Cada registro tiene la siguiente estructura.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>La cadena basada en JSON está embellecida para mejorar la legibilidad.

En la tabla siguiente se describen los tipos de operación que se pueden registrar en los registros.

| Operación | Descripción | Ejemplo de llamador |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| sincronización completa | La sincronización completa recopila y envía todos los datos al SaaS de una fuente determinada. | `bin/magento saas:resync --feed=products` |
| reindexación parcial | La sincronización parcial recopila y envía datos a SaaS solo para las entidades actualizadas de una fuente determinada. Este registro solo está presente si existen entidades actualizadas. | `bin/magento cron:run --group=index` |
| reintentar elementos con errores | Reenvía elementos de una fuente determinada a SaaS si la operación de sincronización anterior ha fallado debido a un error de la aplicación o del servidor de Commerce. Este registro solo está presente si existen elementos con error. | `bin/magento cron:run --group=saas_data_exporter`  (cualquier grupo cron &quot;*_data_exporter&quot;) |
| sincronización completa (heredada) | Sincronización completa para una fuente determinada en el modo de exportación heredado. | `bin/magento saas:resync --feed=categories` |
| reindexación parcial (heredada) | Envía entidades actualizadas a SaaS para una fuente determinada en el modo de exportación heredado. Este registro solo está presente si existen entidades actualizadas. | `bin/magento cron:run --group=index` |
| sincronización parcial (heredada) | Envía entidades actualizadas a SaaS para una fuente determinada en el modo de exportación heredado. Este registro solo está presente si existen entidades actualizadas. | `bin/magento cron:run --group=saas_data_exporter` (cualquier grupo cron &quot;*_data_exporter&quot;) |


### Ejemplos de registro

De forma predeterminada, durante una resincronización completa, el progreso se rastrea y registra cada 30 segundos. Este es un ejemplo de entrada de registro.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

En este ejemplo, la variable `status` Los valores de proporcionan información sobre la operación de sincronización:

- **`"Progress 2/5"`** indica que se han completado 2 de 5 iteraciones. El número de iteraciones depende del número de entidades exportadas.
- **`"processed: 200"`** indica que se han procesado 200 elementos.
- **`"synced: 100"`** indica que se enviaron 100 artículos a SaaS. Se espera que `"synced"` is not equal to `"processed"`. A continuación se muestra un ejemplo:
   - **`"synced" < "processed"`** significa que la tabla de fuentes no detectó ningún cambio en el elemento, en comparación con la versión sincronizada anteriormente. Estos elementos se omiten durante la operación de sincronización.
   - **`"synced" > "processed"`** el mismo id de entidad (por ejemplo, `Product ID`) puede tener varios valores en diferentes ámbitos. Por ejemplo, se puede asignar un producto a cinco sitios web. En este caso, es posible que tenga &quot;1 elemento procesado&quot; y &quot;5 sincronizados&quot; elementos.

+++ Ejemplo: Registro de resincronización completo para la fuente de precios

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## Visualización y solución de problemas de registros con New Relic

Si almacena los registros de Adobe Commerce en New Relic, puede agregar reglas de análisis para mejorar la legibilidad y la experiencia de consulta.

1. Inicie sesión en New Relic.

1. Ir a `Logs => Parsing`.

1. Clic `Create parsing rule`.

1. Configure la regla de análisis añadiendo los siguientes valores.

   - **Filtrar registros basados en NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Regla de análisis**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

En este ejemplo se agrega una regla que permite consultar los registros de New Relic por tipo de fuente específico, operación, etc.

**Ejemplo de cadena de consulta**—`feed.feed:"products" and feed.status:"Complete"`

## Registro extendido

Puede utilizar variables de entorno para ampliar los registros con datos adicionales para el seguimiento y la resolución de problemas.

### Comprobación de la carga útil de fuente

Incluya la carga útil de fuente en el registro de exportación de SaaS agregando el `EXPORTER_EXTENDED_LOG=1` variable de entorno al volver a sincronizar la fuente.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

Una vez finalizada la operación, la carga útil de fuente está disponible para su revisión en el registro de exportación de SaaS (`var/.log/saas-export.log`).

### Conservar carga útil en tabla de índice de fuentes

Para la extensión de exportación de datos SaaS de Commerce (`magento/module-data-exporter`) 103.3.0 y versiones posteriores, las fuentes de exportación inmediatas mantienen solo los datos mínimos requeridos en la tabla de índices. Las fuentes incluyen todas las fuentes de estado de stock de catálogo e inventario.

No se recomienda conservar los datos de carga útil en la tabla de índices en los entornos de producción, pero puede resultar útil en un entorno de desarrollo. Incluya la carga útil de fuente en el índice agregando el `PERSIST_EXPORTED_FEED=1` variable de entorno al volver a sincronizar la fuente.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Ejecute el generador de perfiles para solucionar problemas de rendimiento lento

Si el proceso de reindexación de una fuente específica lleva una cantidad de tiempo no razonable, ejecute el generador de perfiles para recopilar datos adicionales que puedan ser útiles para el equipo de asistencia.

Ejecute el generador de perfiles agregando `EXPORTER_PROFILER=1` variable de entorno al ejecutar el comando reindex.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Los datos del analizador se almacenan en el registro de exportación de datos (`var/log/commerce-data-export.log`) con el siguiente formato:

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```




