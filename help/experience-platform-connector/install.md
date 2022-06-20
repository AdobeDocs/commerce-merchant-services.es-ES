---
title: Instalación y configuración del conector de Adobe Experience Platform desde Adobe Commerce
description: Obtenga información sobre cómo instalar, configurar, actualizar y desinstalar el conector de Adobe Experience Platform de Adobe Commerce.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Instalación y configuración del conector del Experience Platform

Antes de instalar la extensión, [revisar los requisitos previos](overview.md#prereqs).

## Instalación de la extensión

1. Instale el paquete de metal del conector del Experience Platform.

   ```bash
   composer require magento/platform-connector
   ```

   Este metapackage contiene los siguientes módulos:

   * `module-platform-connector-admin` : actualiza la interfaz de usuario del administrador
   * `module-platform-connector` - Establece el `ImsOrgId` y `datastreamId` en el SDK de eventos de tienda de Magento

1. Instale la extensión de Commerce Data Services para incluir eventos de perfil y cierre de compra.

   ```bash
   composer require magento/data-services
   ```

   La extensión Commerce Data Services proporciona contexto de atributos para eventos de tienda. Por ejemplo, cuando se produce un evento de cierre de compra, se incluye información sobre cuántos artículos estaban en el carro y los datos de atributos del producto para esos artículos.

1. Instale Commerce Service Connector.

   ```bash
   composer require magento/commerce-services
   ```

   Commerce Service Connector le permite conectar la instancia de Adobe Commerce a [SaaS de Adobe Commerce](../landing/saas.md) y a Adobe Experience Platform.

1. (Opcional) Para incluir [!DNL Live Search] , que incluye eventos de búsqueda, instale la variable [[!DNL Live Search]](../live-search/install.md) extensión.

## Actualización del conector del Experience Platform {#update}

Para actualizar el conector del Experience Platform, ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/platform-connector --with-dependencies
```

Para actualizar a una versión principal como de 1.0.0 a 2.0.0, edite la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Abra la raíz `composer.json` y busque `magento/platform-connector`.

1. En el `require` , actualice el número de versión de la siguiente manera:

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Desinstale el conector del Experience Platform {#uninstall}

Para desinstalar el conector del Experience Platform, consulte [desinstalar módulos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
