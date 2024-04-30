---
title: Sincronización de catálogo
description: Obtenga información sobre cómo exportar datos de productos desde [!DNL Commerce] servidor a [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# Sincronización de catálogo

>[!NOTE]
>
> El tablero de sincronización de catálogos ahora es el tablero de administración de datos. Este tablero reformado ahora admite [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md), y [[!DNL Catalog Service]](../catalog-service/overview.md). Los clientes pueden obtener el tablero de administración de datos actualizando a la última versión de uno de esos servicios. Obtenga más información al respecto en la [Tablero de administración de datos](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) documentación. Este tema actual permanece para los usuarios que aún no se han actualizado y que aún tienen el panel Sincronización de catálogos.

Adobe Commerce utiliza indexadores para compilar datos de catálogo en tablas. El proceso se activa automáticamente mediante [eventos](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como un cambio en el precio de un producto o en el nivel de inventario.

El servicio de sincronización de catálogos mueve datos de producto de un [!DNL Adobe Commerce] instancia a la [!DNL Commerce Services] de forma continua para mantener los datos actualizados. Por ejemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) requiere información actual del catálogo para devolver con precisión las recomendaciones con los nombres, precios y disponibilidad correctos. Utilice el _Sincronización de catálogo_ panel para observar y administrar el proceso de sincronización de [interfaz de línea de comandos](#resynccmdline) para almacenar en déclencheur una sincronización de catálogo y reindexar los datos de producto para su consumo por [!DNL Commerce Services].

## Acceso al panel de sincronización de catálogos

Para acceder al panel de sincronización de catálogos, seleccione **Sistema** > _Transferencia de datos_ > **Sincronización de catálogo**.

Con el **Sincronización de catálogo** panel que puede:

- Ver el estado de sincronización (**En curso**, **Correcto**, **Error**)
- Ver el número total de productos sincronizados
- Busque productos sincronizados para ver su estado actual
- Buscar en el catálogo de la tienda por nombre, SKU, etc.
- Ver los detalles del producto sincronizado en JSON para ayudar a diagnosticar una discrepancia de sincronización
- Reinicio del proceso de sincronización

### Última sincronización

Notifica un estado de sincronización de:

- **Correcto** - Muestra la fecha y la hora en que la sincronización se realizó correctamente y el número de productos actualizados
- **Error** - Muestra la fecha y la hora en que se intentó realizar la sincronización
- **En curso** - Muestra la fecha y la hora de la última sincronización correcta

El proceso de sincronización del catálogo se ejecuta automáticamente cada hora. Si no ve los productos esperados en la tienda o si los productos no reflejan los cambios recientes que ha realizado, puede resolver lo siguiente [problemas de sincronización del catálogo](#resolvesync).

### Productos sincronizados

Muestra el número total de productos sincronizados desde su [!DNL Commerce] catálogo. Después de la sincronización inicial, solo se deben sincronizar los productos modificados.

## Resincronizar {#resync}

Si debe iniciar una resincronización del catálogo antes de que se produzca la sincronización programada por hora, puede forzar una resincronización.

>[!NOTE]
>
> Forzar una resincronización déclencheur una resincronización de todo el catálogo de productos, lo que puede aumentar la carga en los recursos de hardware.

1. Desde el _Sincronización de catálogo_ panel, seleccione **Configuración**.

   El _Configuración de sincronización de catálogo_ página.

1. En el _Resincronizar datos_ , haga clic en [!UICONTROL Resync].

   [!DNL Commerce] sincroniza el catálogo durante la siguiente ventana de sincronización programada. En función del tamaño del catálogo, esta operación puede tardar mucho tiempo.

## Productos de catálogo sincronizados

El **Productos de catálogo sincronizados** La tabla muestra la siguiente información.

| Campo | Descripción |
|---|---|
| ID | Identificador único del producto |
| Nombre | Nombre de tienda del producto |
| Tipo | Identifica el tipo de producto, como simple, configurable o descargable |
| Última exportación | Fecha en la que se exportó correctamente el producto del catálogo por última vez |
| Última modificación | Fecha de la última modificación del producto en el catálogo |
| SKU | Muestra la unidad de stock del producto |
| Precio | Precio del producto |
| Visibilidad | La configuración de visibilidad de un producto, tal como se define en la [!DNL Commerce] catalogar |

## Resolver problemas de sincronización del catálogo {#resolvesync}

Cuando se sincroniza en déclencheur un archivo de datos, los datos pueden tardar hasta una hora en actualizarse y se reflejarán en componentes de la interfaz de usuario como unidades de recomendación. Si sigue viendo discrepancias entre el catálogo y los datos de la tienda, o si la sincronización del catálogo ha fallado, consulte lo siguiente:

### Discrepancia de datos

1. Mostrar la vista detallada del producto en cuestión en los resultados de búsqueda.
1. Copie la salida JSON y verifique que el contenido coincida con lo que tiene en la [!DNL Commerce] catálogo.
1. Si el contenido no coincide, realice un cambio menor en el producto del catálogo, como añadir un espacio o un punto.
1. Espere a que se vuelva a sincronizar o [déclencheur de una resincronización manual](#resync).

### La sincronización no se está ejecutando

Si la sincronización no se está ejecutando según una programación o no hay nada sincronizado, consulte esto [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) artículo.

### Error de sincronización

Si la sincronización del catálogo tiene un estado de **Error**, envíe un [ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interfaz de línea de comandos {#resynccmdline}

El `saas:resync` El comando forma parte de `magento/saas-export` y está disponible de forma predeterminada con uno de los [!DNL Commerce Services] productos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) o [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Cuando ejecute una sincronización de datos por primera vez, ejecute el `productattributes` fuente primero, seguido de `productoverrides`, antes de ejecutar el `products` fuente.

Opciones de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

En la tabla siguiente se describe la `saas:resync` parámetros y descripciones.

| Parámetro | Descripción | ¿Requerido? |
|---| ---| ---|
| `feed` | Especifica la entidad que se debe resincronizar, como `products` | Sí |
| `no-reindex` | Vuelve a enviar los datos de catálogo existentes a [!DNL Commerce Services] sin reindexación. Cuando no se especifica este parámetro, el comando ejecuta una reindexación completa antes de sincronizar los datos. | No |
| `cleanup-feed` | Limpie la tabla del indizador de fuentes antes de una sincronización. | No |

El nombre de la fuente puede ser uno de los siguientes:

- `products`— Productos en su catálogo
- `productattributes`— atributos de producto como `activity`, `gender`, `tops`, `bottoms`, etc.
- `variants`— Variaciones de un producto configurable, como el color y el tamaño
- `prices` — Precios de los productos
- `scopesCustomerGroup` — Grupos de clientes
- `scopesWebsite` — Sitios web con vistas de la tienda
- `categories`— Categorías del catálogo
- `categoryPermissions` - Permisos para cada una de las categorías
- `productoverrides`— Reglas de precios y visibilidad del catálogo específicas del cliente, como las basadas en permisos de categoría.

Dependiendo del [Servicios de Commerce](../landing/saas.md) están instalados, puede tener diferentes conjuntos de fuentes disponibles para `saas:resync` comando.

No se recomienda ejecutar el `saas:resync` de forma regular. Es posible que tenga que ejecutar el comando manualmente en dos situaciones:

- La sincronización inicial
- El [ID del espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) se ha cambiado

### Sincronización inicial

Cuando déclencheur un `saas:resync` desde la línea de comandos, según el tamaño del catálogo, los datos pueden tardar entre unos minutos y unas horas en actualizarse.

Para la sincronización inicial, se recomienda ejecutar los comandos en el siguiente orden:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### Resolución de problemas

Si no ve los datos esperados en [!DNL Commerce Service], compruebe si se ha producido un problema durante la sincronización desde el [!DNL Adobe Commerce] instancia a la [!DNL Commerce Service] plataforma.

Hay dos archivos de registro en el `var/log/` directorio:

- `commerce-data-export-errors.log` - si se produjo un error durante _recolección_ fase
- `saas-export-errors.log` - si se produjo un error durante _transmitiendo_ fase

#### Comprobar carga útil de fuente

Puede resultar útil ver la carga útil de fuente que se ha enviado a [!DNL Commerce Service]. Esto se puede hacer pasando la variable de entorno `EXPORTER_EXTENDED_LOG=1`. El `no-reindex` El indicador significa que solo se envían los datos recopilados actualmente.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

La carga útil está disponible en `var/log/saas-export.log`.

#### Conservar carga útil en tabla de índice de fuentes

Comenzando desde `magento/module-data-exporter:103.0.0` algunas fuentes: fuente de productos, fuentes de precios, mantenga solo los datos mínimos requeridos en la tabla de índices.

No se recomienda conservar los datos de carga útil en la tabla de índice en la producción, pero puede resultar útil en una instancia de desarrollador. Esto se hace pasando el `PERSIST_EXPORTED_FEED=1` variable de entorno:

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### Perfilado

Si el proceso de reindexación de una fuente específica lleva una cantidad de tiempo no razonable, ejecute el generador de perfiles para recopilar datos adicionales que puedan ser útiles para el equipo de asistencia. Para ello, pase el `EXPORTER_PROFILER=1`variable de entorno:

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Los datos del analizador se almacenan en `var/log/commerce-data-export.log` con el formato:

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### Enviar una solicitud de asistencia

Si ve errores no relacionados con la configuración o con extensiones de terceros, envíe un [ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) con la mayor cantidad de información posible.
