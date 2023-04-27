---
title: Instalación y configuración del conector de Adobe Experience Platform desde Adobe Commerce
description: Obtenga información sobre cómo instalar, configurar, actualizar y desinstalar el conector de Adobe Experience Platform de Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 898d49cbeb4711862a47693a0d608b74730dc845
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Instalación y configuración del conector del Experience Platform

Antes de instalar la extensión, [revisar los requisitos previos](overview.md#prereqs).

## Instalación de la extensión

La extensión del conector del Experience Platform está disponible en el [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Al instalar esta extensión desde la línea de comandos del servidor, se conecta a la instalación de Adobe Commerce como un [service](../landing/saas.md). Cuando se complete el proceso, **Conector del Experience Platform** y **Conector de Commerce Services** aparece en el **Sistema** menú bajo **Servicios** en el comercio _Administrador_.

>[!NOTE]
>
>![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe instalar una extensión independiente. Esta extensión añade compatibilidad con eventos específicos de B2B. [Más información](#install-the-b2b-extension).


1. Para descargar el `experience-platform-connector` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapackage contiene los siguientes módulos y extensiones:

   * `module-experience-connector-admin` - Actualiza la interfaz de usuario del administrador para que pueda seleccionar el ID del almacén de datos para una instancia específica de Adobe Commerce
   * `module-experience-connector` - Establece el `Organization ID` y `datastreamId` en el SDK de eventos de tienda
   * `data-services` - Proporciona contexto de atributo para eventos de tienda. Por ejemplo, cuando se produce un evento de cierre de compra, se incluye información sobre cuántos artículos estaban en el carro y los datos de atributos del producto para esos artículos.
   * `services-id` - Conecta la instancia de Adobe Commerce a [SaaS de Adobe Commerce](../landing/saas.md) uso de las claves sandbox y de la API de producción y de Adobe Experience Platform para recuperar el ID de organización de IMS

1. (Opcional) Para incluir [!DNL Live Search] , que incluye eventos de búsqueda, instale la variable [[!DNL Live Search]](../live-search/install.md) extensión.

### Instalación de la extensión B2B

Para los comerciantes B2B, instale la siguiente extensión para incluir [lista de solicitudes](events.md#b2b-events) datos de evento.

Descargue el `magento/experience-platform-connector-b2b` ejecutando lo siguiente desde la línea de comandos:

```bash
composer require magento/experience-platform-connector-b2b
```

## Actualización del conector del Experience Platform {#update}

Para actualizar el conector del Experience Platform, ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

o, para los comerciantes B2B:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Para actualizar a una versión principal como de 1.0.0 a 2.0.0, edite la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Abra la raíz `composer.json` y busque `magento/platform-connector`.

1. En el `require` , actualice el número de versión de la siguiente manera:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   o, para los comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Desinstale el conector del Experience Platform {#uninstall}

Para desinstalar el conector del Experience Platform, consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
