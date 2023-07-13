---
title: Sincronización de catálogo
description: Obtenga información sobre cómo exportar datos de productos desde [!DNL Commerce] servidor a [!DNL Commerce Services] de forma continua para mantener los servicios actualizados.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalogs, Data Import/Export, Catalog Service
source-git-commit: d803cd9c78ac8c5529eadf39f361d7e46045359e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Sincronización de catálogo

Adobe Commerce y Magento Open Source utilizan indexadores para compilar datos de catálogo en tablas. El proceso se activa automáticamente mediante [eventos](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como un cambio en el precio de un producto o en el nivel de inventario.

El proceso de sincronización del catálogo se ejecuta cada hora para permitir [!DNL Commerce] servicios para utilizar datos de catálogo. La sincronización de catálogos exporta datos de productos desde [!DNL Commerce] servidor a [!DNL Commerce] servicios de forma continua para mantener los servicios actualizados. Por ejemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) necesita información actual del catálogo para devolver con precisión las recomendaciones con los nombres, precios y disponibilidad correctos. Puede usar el complemento _Sincronización de catálogo_ panel para observar y administrar el proceso de sincronización de [interfaz de línea de comandos](#resynccmdline) para sincronizar el catálogo de déclencheur y reindexar los datos de producto para que los consuma [!DNL Commerce] servicios.

>[!NOTE]
>
> Para usar la variable _Sincronización de catálogo_ para la interfaz de línea de comandos, debe tener un [Clave de API y espacio de datos SaaS configurado](saas.md).

## Acceso al panel de sincronización de catálogos

>[!NOTE]
>
> El _Sincronización de catálogo_ el tablero solo está disponible cuando la variable _Product Recommendations_ Los módulos de se instalan y reflejan las proyecciones de datos relacionadas únicamente con esa función. Compatibilidad con otros servicios de Commerce como _Live Search_ y _Servicio de catálogo_ están planificados para el futuro.

Para acceder al panel de sincronización de catálogos, seleccione **Sistema** > _Transferencia de datos_ > **Sincronización de catálogo**.

Con el **Sincronización de catálogo** panel que puede:

- Ver el estado de sincronización (**En curso**, **Correcto**, **Error**)
- Ver el número total de productos sincronizados, si se realiza correctamente
- Busque productos sincronizados para ver su estado actual
- Buscar en el catálogo de la tienda por nombre, SKU, etc
- Ver los detalles del producto sincronizado en JSON para ayudar a diagnosticar una discrepancia de sincronización
- Reinicio del proceso de sincronización

### Última sincronización

Notifica un estado de sincronización de:

- **Correcto** - Muestra la fecha y la hora en que la sincronización se realizó correctamente y el número de productos actualizados
- **Error** - Muestra la fecha y la hora en que se intentó realizar la sincronización
- **En curso** - Muestra la fecha y la hora de la última sincronización correcta

>[!NOTE]
>
> El proceso de sincronización del catálogo se ejecuta automáticamente cada hora. Sin embargo, si no ve productos en la tienda o si los productos no reflejan los cambios recientes que ha realizado, puede resolver lo siguiente [problemas de sincronización del catálogo](#resolvesync).

### Productos sincronizados

Muestra el número total de productos sincronizados desde su [!DNL Commerce] catálogo. Después de la sincronización inicial, debería esperar que solo se sincronizaran los productos modificados.

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
| Tipo | Identifica el tipo de producto, como simple, configurable, descargable, etc |
| Última exportación | Fecha en la que se exportó correctamente el producto del catálogo por última vez |
| Última modificación | Fecha de la última modificación del producto en el catálogo |
| SKU | Muestra la unidad de stock del producto |
| Precio | Precio del producto |
| Visibilidad | La configuración de visibilidad de un producto, tal como se define en la [!DNL Commerce] catalogar |

## Resolver problemas de sincronización del catálogo {#resolvesync}

Cuando se sincroniza en déclencheur un archivo de datos, los datos pueden tardar hasta una hora en actualizarse y reflejarse en los componentes de la interfaz de usuario, como las unidades de recomendación. Sin embargo, si después de esperar una hora todavía nota discrepancias entre su catálogo y lo que aparece en su tienda, o si la sincronización del catálogo falló, consulte lo siguiente:

### Discrepancia de datos

1. Mostrar la vista detallada del producto en cuestión en los resultados de búsqueda.
1. Copie la salida JSON y verifique que el contenido coincida con lo que tiene en la [!DNL Commerce] catálogo.
1. Si el contenido no coincide, realice un cambio menor en el producto del catálogo, como añadir un espacio o un punto.
1. Espere a que se vuelva a sincronizar o [déclencheur de una resincronización manual](#resync).

### La sincronización no se está ejecutando

Si la sincronización no se está ejecutando según una programación o no hay nada sincronizado, consulte la [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### Error de sincronización

Si la sincronización del catálogo tiene un estado de **Error**, envíe un [ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interfaz de línea de comandos {#resynccmdline}

El `saas:resync` El comando forma parte de `magento/saas-export` paquete. Puede instalar este paquete mediante uno de los siguientes [!DNL Commerce Services] productos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) o [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Cuando se ejecuta una sincronización de datos por primera vez, es importante ejecutar el `productattributes` fuente primero, seguido de `productoverrides`, antes de ejecutar el `products` fuente.

Opciones de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

En la tabla siguiente se describe la `saas:resync` parámetros y descripciones.

| Parámetro | Descripción | ¿Requerido? |
|---| ---| ---|
| `feed` | Especifica la entidad que se debe resincronizar, como `products` | Sí |
| `no-reindex` | Vuelve a enviar los datos de catálogo existentes a [!DNL Commerce Services] sin reindexación. Cuando no se especifica este parámetro, el comando ejecuta una reindexación completa antes de sincronizar los datos. | No |

El nombre de la fuente puede ser uno de los siguientes:

- `products`— Productos en su catálogo
- `categories`— Categorías del catálogo
- `variants`— Variaciones de un producto configurable, como el color y el tamaño
- `productattributes`— atributos de producto como `activity`, `gender`, `tops`, `bottoms`, etc.
- `productoverrides`— Reglas de precios y visibilidad del catálogo específicas del cliente, como las basadas en permisos de categoría.

Cuando se sincroniza en déclencheur un dato desde la línea de comandos, los datos pueden tardar hasta una hora en actualizarse.

Si está utilizando [Indexación de precios de SaaS](../price-index/index.md) y debe volver a sincronizar, ejecute el siguiente comando:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Ejemplos

En el siguiente ejemplo, se reindexan los datos de producto del [!DNL Commerce] catalogarlo y volver a sincronizarlo con Commerce Services:

```bash
bin/magento saas:resync --feed products
```

Si no desea ejecutar un reíndice completo de los productos, puede sincronizar los datos del producto que ya se han generado:

```bash
bin/magento saas:resync --feed products --no-reindex
```
