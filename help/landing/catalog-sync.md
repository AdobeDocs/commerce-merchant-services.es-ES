---
title: Sincronización del catálogo
description: Obtenga información sobre cómo exportar datos de productos desde el [!DNL Commerce] servidor a [!DNL Commerce Services] de forma permanente para mantener los servicios actualizados.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: fe5bbceb7f443e7b177ecd4812b981d6e7fd0a6b
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---

# Sincronización del catálogo

Adobe Commerce y el Magento Open Source utilizan indexadores para compilar datos de catálogo en tablas. El proceso se activa automáticamente mediante [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como un cambio en un precio de producto o nivel de inventario.

El proceso de sincronización del catálogo se ejecuta cada hora para permitir [!DNL Commerce] para utilizar los datos del catálogo. La sincronización del catálogo exporta los datos del producto desde el [!DNL Commerce] servidor a [!DNL Commerce] servicios de forma continua para mantener los servicios actualizados. Por ejemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) necesita información actual del catálogo para devolver con precisión las recomendaciones con nombres, precios y disponibilidad correctos. Puede usar la variable _Sincronización del catálogo_ tablero para observar y administrar el proceso de sincronización o [interfaz de línea de comandos](#resynccmdline) para déclencheur de sincronización de catálogos y reindexar datos de productos para consumo por [!DNL Commerce] servicios.

>[!NOTE]
>
> Para usar la variable _Sincronización del catálogo_ o la interfaz de línea de comandos, debe tener un [Clave de API y un espacio de datos SaaS configurado](saas.md).

## Acceso al tablero de sincronización del catálogo

>[!NOTE]
>
> La variable _Sincronización del catálogo_ El panel de control solo está disponible cuando está instalado el servicio Product Recommendations.

Para acceder al tablero de sincronización del catálogo, seleccione **Sistema** > _Transferencia de datos_ > **Sincronización del catálogo**.

Con la variable **Sincronización del catálogo** tablero, puede:

- Ver el estado de sincronización (**En curso**, **Correcto**, **Error**)
- Ver el número total de productos sincronizados, si se realiza correctamente
- Buscar productos sincronizados para ver su estado actual
- Buscar catálogo de tienda por nombre, SKU, etc.
- Ver los detalles del producto sincronizados en JSON para ayudar a diagnosticar una discrepancia de sincronización
- Reiniciar el proceso de sincronización

### Última sincronización

Informa de un estado de sincronización de:

- **Correcto** - Muestra la fecha y la hora en que la sincronización se realizó correctamente y el número de productos actualizados
- **Error** - Muestra la fecha y la hora en que se intentó la sincronización
- **En curso** - Muestra la fecha y la hora de la última sincronización correcta

>[!NOTE]
>
> El proceso de sincronización del catálogo se ejecuta automáticamente cada hora. Sin embargo, si no ve productos en su tienda o si los productos no reflejan los cambios recientes que ha realizado, puede resolver [problemas de sincronización del catálogo](#resolvesync).

### Productos sincronizados

Muestra el número total de productos sincronizados desde su [!DNL Commerce] catálogo. Después de la sincronización inicial, solo debería esperar que se sincronizaran los productos modificados.

## Resync {#resync}

Si debe iniciar una resincronización del catálogo antes de que se produzca la sincronización programada por hora, puede forzar una resincronización.

>[!NOTE]
>
> Forzar una resincronización déclencheur una resincronización de todo el catálogo de productos, lo que puede aumentar la carga en los recursos de hardware.

1. En el _Sincronización del catálogo_ tablero, seleccione **Configuración**.

   La variable _Configuración de sincronización de catálogo_ se abre.

1. En el _Resincronizar datos_ , haga clic en [!UICONTROL Resync].

   [!DNL Commerce] sincroniza el catálogo durante la siguiente ventana de sincronización programada. En función del tamaño del catálogo, esta operación puede tardar mucho tiempo.

## Productos de catálogo sincronizados

La variable **Productos de catálogo sincronizados** muestra la siguiente información.

| Campo | Descripción |
|---|---|
| ID | Identificador único del producto |
| Nombre | Nombre de tienda del producto |
| Tipo | Identifica el tipo de producto, como simple, configurable, descargable, etc. |
| Última exportación | Fecha en la que el producto se exportó correctamente por última vez desde el catálogo |
| Última modificación | Fecha de la última modificación del producto en el catálogo |
| SKU | Muestra la unidad de mantenimiento del producto |
| Precio | Precio del producto |
| Visibilidad | Una configuración de visibilidad del producto según se define en la variable [!DNL Commerce] catálogo |

## Resolver problemas de sincronización de catálogos {#resolvesync}

Cuando se déclencheur una resincronización de datos, los datos pueden tardar hasta una hora en actualizarse y reflejarse en los componentes de la interfaz de usuario, como las unidades de recomendación. Sin embargo, si después de esperar una hora sigue notando discrepancias entre el catálogo y lo que aparece en la tienda, o si la sincronización del catálogo falla, consulte lo siguiente:

### Discrepancia de datos

1. Muestre la vista detallada del producto en cuestión en los resultados de búsqueda.
1. Copie la salida JSON y verifique que el contenido coincida con lo que tiene en la variable [!DNL Commerce] catálogo.
1. Si el contenido no coincide, realice un cambio menor en el producto del catálogo, como agregar un espacio o un punto.
1. Espere a que se vuelva a sincronizar o [déclencheur de una resincronización manual](#resync).

### La sincronización no se está ejecutando

Si la sincronización no se está ejecutando en una programación o no se ha sincronizado nada, consulte la [Base de conocimientos](https://support.magento.com/hc/en-us/articles/360042224851).

### Error de sincronización

Si la sincronización del catálogo tiene un estado de **Error**, envíe un [ticket de asistencia](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket).

## Interfaz de línea de comandos {#resynccmdline}

La variable `saas:resync` forma parte de la función `magento/saas-export` paquete. Puede instalar este paquete utilizando uno de los [!DNL Commerce Services] productos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) o [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Cuando se déclencheur una resincronización de datos desde la línea de comandos, los datos pueden tardar hasta una hora en actualizarse.

Opciones de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

La tabla siguiente describe el `saas:resync` parámetros y descripciones.

| Parámetro | Descripción | ¿Requerido? |
|---| ---| ---|
| `feed` | Especifica qué entidad se va a resincronizar, como `products` | Sí |
| `no-reindex` | Vuelve a enviar los datos de catálogo existentes a [!DNL Commerce Services] sin reindexación. Cuando no se especifica este parámetro, el comando ejecuta un reíndice completo antes de sincronizar los datos. | No |

El nombre de la fuente puede ser uno de los siguientes:

- `products`— Productos de su catálogo
- `categories`— Categorías en el catálogo
- `variants`— Variaciones de producto de un producto configurable, como color y tamaño
- `productattributes`— Atributos de producto como `activity`, `gender`, `tops`, `bottoms`y así sucesivamente
- `productoverrides`— Precios específicos del cliente y reglas de visibilidad del catálogo, como las basadas en permisos de categoría

### Ejemplos

El siguiente ejemplo reindexa los datos del producto de la variable [!DNL Commerce] catálogo y lo vuelve a sincronizar con Commerce services:

```bash
bin/magento saas:resync --feed products
```

Si no desea ejecutar un reíndice completo de los productos, puede sincronizar los datos del producto que ya se han generado:

```bash
bin/magento saas:resync --feed products --no-reindex
```
