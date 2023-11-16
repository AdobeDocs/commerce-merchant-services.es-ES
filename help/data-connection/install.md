---
title: Instalar [!DNL Data Connection]
description: Obtenga información sobre cómo instalar, actualizar y desinstalar el [!DNL Data Connection] de Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 2392cb4257f6efdcb8fc3e38c007148e03e338fd
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Instalar [!DNL Data Connection]

Antes de instalar la extensión, [revisar los requisitos previos](overview.md#prereqs).

## Instalación de la extensión

El [!DNL Data Connection] La extensión de está disponible en [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Al instalar esta extensión desde la línea de comandos del servidor, se conecta a la instalación de Adobe Commerce como [servicio](../landing/saas.md). Una vez completado el proceso, **[!DNL Data Connection]** y **Conector de Commerce Services** aparecen en la **Sistema** menú debajo de **Servicios** en el Commerce _Administrador_.

>[!IMPORTANT]
>
>Mientras que el nombre de la extensión ha cambiado de conector de Experience Platform a [!DNL Data Connection], el nombre del paquete permanece `experience-platform-connector` para admitir la compatibilidad con versiones anteriores.

1. Para descargar `experience-platform-connector` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapaquete contiene los siguientes módulos y extensiones:

   * `module-experience-connector-admin` : actualiza la IU de administración para que pueda seleccionar el ID de la secuencia de datos para una instancia de Adobe Commerce específica.
   * `module-experience-connector` - Establece el `Organization ID` y `datastreamId` en el SDK de eventos de tienda.
   * `data-services` : proporciona contexto de atributo para eventos de tienda. Por ejemplo, cuando se produce un evento de cierre de compra, se incluye información sobre cuántos elementos había en el carro de compras y datos de atributos del producto para esos elementos.
   * `services-id` : Conecta la instancia de Adobe Commerce a [SaaS de Adobe Commerce](../landing/saas.md) uso de claves de API de zona protegida y producción, y a Adobe Experience Platform para recuperar el ID de organización de IMS.
   * `orders-connector` : conecta el servicio de estado del pedido a la instancia de Adobe Commerce.

1. (Opcional) Para incluir [!DNL Live Search] datos, que incluyen [eventos de búsqueda](events.md#search-events), instale el [[!DNL Live Search]](../live-search/install.md) extensión.

1. (Opcional) Incluir datos B2B, que comprenden [eventos de solicitud](events.md#b2b-events), instale el [Extensión B2B](#install-the-b2b-extension).

### Configuración del conector de pedidos

Después de instalar el `experience-platform-connector` extensión, debe finalizar la instalación del `orders-connector` módulo basado en el tipo de implementación: local o Adobe Commerce en infraestructura en la nube.

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

En Adobe Commerce en la infraestructura de la nube, habilite la `ENABLE_EVENTING` variable global en `.magento.env.yaml`. [Más información](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

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

Para los comerciantes B2B, instale la siguiente extensión para incluir [lista de solicitudes](events.md#b2b-events) datos de evento.

Descargue la `magento/experience-platform-connector-b2b` mediante la ejecución de lo siguiente desde la línea de comandos:

```bash
composer require magento/experience-platform-connector-b2b
```

## Actualice el [!DNL Data Connection] extensión {#update}

Para actualizar el [!DNL Data Connection] , ejecute lo siguiente desde la línea de comandos:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

O, para los comerciantes B2B:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Para actualizar a una versión principal como de 2.0.0 a 3.0.0, edite la raíz del proyecto [!DNL Composer] `.json` como se indica a continuación:

1. Abra la raíz `composer.json` archivo y buscar `magento/experience-platform-connector`.

1. En el `require` , actualice el número de versión como se indica a continuación:

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

## Desinstale el [!DNL Data Connection] extensión {#uninstall}

Para desinstalar [!DNL Data Connection] extensión, consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
