---
title: "[!DNL Manage the Data Export extension]"
description: '"Obtenga información sobre cómo actualizar el [!DNL Data Export] y para eliminar o deshabilitar los servicios de exportación de datos que no son necesarios".'
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Administración de la extensión de exportación de datos SaaS

El [!DNL data export] La extensión para servicios SaaS es una colección de módulos que permiten la recopilación y sincronización de datos entre Adobe Commerce y los servicios de Commerce conectados.

Se incluyen módulos específicos en los metapaquetes para las extensiones de servicios de Adobe Commerce como [Live Search](/help/live-search/overview.md), [Product Recommendations](/help/product-recommendations/overview.md), y [Servicio de catálogo](/help/catalog-service/overview.md). Si utiliza estos servicios, no se requiere ninguna instalación independiente para habilitar la extensión de exportación de datos.

## Eliminación o desactivación de las funciones de exportación de datos de Commerce

Si no necesita uno de los módulos de exportación de datos de comercio instalados, utilice el `magento:module:disable` Comando CLI para deshabilitarlo.

Por ejemplo, existe un [API de categorías](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) que utiliza los datos de fuentes de permisos de categorías internamente. Si no utiliza esta API, puede deshabilitar la exportación de datos para la fuente de permisos para categorías.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Actualización de un módulo a una versión específica

Puede actualizar cualquiera de los módulos de exportación de datos de comercio instalados mediante Composer. Por ejemplo, puede actualizar un módulo a una versión especificada y también actualizar las dependencias necesarias.

1. Inicie sesión en el servidor de aplicaciones de Commerce.

1. Desde la línea de comandos, actualice el módulo mediante Composer:

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Si la instancia de Commerce está implementada en la infraestructura de Cloud, actualice la extensión desde el directorio del proyecto de Cloud. Consulte [Actualización de una extensión](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) en el _Guía de Adobe Commerce sobre infraestructura en la nube_.




