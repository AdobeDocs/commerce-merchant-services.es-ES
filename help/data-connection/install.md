---
title: Instalar [!DNL Data Connection]
description: Obtenga información sobre cómo instalar, actualizar y desinstalar la extensión  [!DNL Data Connection] de Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Instalar [!DNL Data Connection]

Antes de instalar la extensión, [revise los requisitos previos](overview.md#prereqs).

## Instalación de la extensión

La extensión [!DNL Data Connection] está disponible en [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Cuando instala esta extensión desde la línea de comandos del servidor, se conecta a su instalación de Adobe Commerce como un [servicio](../landing/saas.md). Una vez completado el proceso, **[!DNL Data Connection]** y **Commerce Services Connector** aparecen en el menú **Sistema** en **Servicios** en Commerce _Admin_.

![[!DNL Data Connection] vista de administración de la extensión](assets/epc-adminui.png)

>[!IMPORTANT]
>
>Aunque el nombre de la extensión ha cambiado del conector del Experience Platform a [!DNL Data Connection], el nombre del paquete permanece `experience-platform-connector` para admitir la compatibilidad con versiones anteriores.

1. Para descargar el paquete `experience-platform-connector`, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapaquete contiene los siguientes módulos y extensiones:

   * `module-experience-connector-admin`: actualiza la IU de administración para que pueda seleccionar el ID de la secuencia de datos para una instancia de Adobe Commerce específica.
   * `module-experience-connector` - Establece `Organization ID` y `datastreamId` en el SDK de eventos de tienda.
   * `data-services`: proporciona contexto de atributo para eventos de tienda. Por ejemplo, cuando se produce un evento de cierre de compra, se incluye información sobre cuántos elementos había en el carro de compras y datos de atributos del producto para esos elementos.
   * `services-id`: conecta su instancia de Adobe Commerce a [Adobe Commerce SaaS](../landing/saas.md) mediante la zona protegida y las claves de API de producción, y a Adobe Experience Platform para recuperar el ID de organización de IMS.
   * `orders-connector`: conecta el servicio de estado del pedido a su instancia de Adobe Commerce.

1. (Opcional) Para incluir [!DNL Live Search] datos, que comprenden [eventos de búsqueda](events.md#search-events), instale la extensión [[!DNL Live Search]](../live-search/install.md).

1. (Opcional) Para incluir datos B2B, que comprenden [eventos de solicitud](events.md#b2b-events), instale la [extensión B2B](#install-the-b2b-extension).

### Instalación de los eventos de Adobe I/O

Después de instalar la extensión `experience-platform-connector`, debe instalar los Eventos de Adobe I/O para Adobe Commerce.

Los siguientes pasos se aplican tanto a Adobe Commerce en la infraestructura en la nube como a las instalaciones locales.

1. Si está ejecutando Commerce 2.4.4 o 2.4.5, utilice el siguiente comando para cargar los módulos de eventos:

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 y versiones posteriores cargan estos módulos automáticamente.

1. Actualice las dependencias del proyecto.

   ```bash
   composer update
   ```

1. Habilite los nuevos módulos:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Finalice la instalación en función del tipo de implementación: local o Adobe Commerce en infraestructura en la nube.

#### On-Premise

En entornos locales, debe habilitar manualmente la generación de código y los eventos de Adobe Commerce:

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### Infraestructura en la nube

En Adobe Commerce en la infraestructura de la nube, habilite la variable global `ENABLE_EVENTING` en `.magento.env.yaml`. [Más información](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Transfiera y envíe los archivos actualizados al entorno de Cloud. Cuando finalice la implementación, habilite el envío de eventos con el siguiente comando:

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Instalación de la extensión B2B

Para los comerciantes B2B, instale la siguiente extensión para incluir [datos de evento de lista de solicitudes](events.md#b2b-events).

Descargue la extensión `magento/experience-platform-connector-b2b` ejecutando lo siguiente desde la línea de comandos:

```bash
composer require magento/experience-platform-connector-b2b
```

## Actualizar la extensión [!DNL Data Connection] {#update}

Para actualizar la extensión [!DNL Data Connection], ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

O, para los comerciantes B2B:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Para actualizar a una versión principal como de 2.0.0 a 3.0.0, edite el archivo raíz [!DNL Composer] `.json` del proyecto de la siguiente manera:

1. Abra el archivo raíz `composer.json` y busque `magento/experience-platform-connector`.

1. En la sección `require`, actualice el número de versión de la siguiente manera:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **Guardar** `composer.json`. A continuación, ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   O, para los comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Desinstalar la extensión [!DNL Data Connection] {#uninstall}

Para desinstalar la extensión [!DNL Data Connection], consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
