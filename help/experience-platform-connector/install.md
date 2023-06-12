---
title: Instalación y configuración del conector de Adobe Experience Platform desde Adobe Commerce
description: Obtenga información sobre cómo instalar, configurar, actualizar y desinstalar el conector de Adobe Experience Platform desde Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 052b9fe32797e62d5802241c7b3420decf593fc1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Instalación y configuración del conector del Experience Platform

Antes de instalar la extensión, [revisar los requisitos previos](overview.md#prereqs).

## Instalación de la extensión

La extensión del conector del Experience Platform está disponible en [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Al instalar esta extensión desde la línea de comandos del servidor, se conecta a la instalación de Adobe Commerce como [servicio](../landing/saas.md). Una vez completado el proceso, **Conector del Experience Platform** y **Conector de Commerce Services** aparecen en la **Sistema** menú debajo de **Servicios** en el Commerce _Administrador_.

>[!NOTE]
>
>![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe instalar una extensión independiente. Esta extensión añade compatibilidad con eventos específicos B2B. [Más información](#install-the-b2b-extension).


1. Para descargar `experience-platform-connector` ejecute lo siguiente desde la línea de comandos:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapaquete contiene los siguientes módulos y extensiones:

   * `module-experience-connector-admin` : actualiza la IU de administración para que pueda seleccionar el ID de la secuencia de datos para una instancia de Adobe Commerce específica
   * `module-experience-connector` - Establece el `Organization ID` y `datastreamId` en el SDK de eventos de tienda
   * `data-services` : proporciona contexto de atributo para eventos de tienda. Por ejemplo, cuando se produce un evento de cierre de compra, se incluye información sobre cuántos elementos había en el carro de compras y datos de atributos del producto para esos elementos.
   * `services-id` : Conecta la instancia de Adobe Commerce a [SaaS de Adobe Commerce](../landing/saas.md) uso de claves de API de zona protegida y producción, y a Adobe Experience Platform para recuperar el ID de organización de IMS

1. (Opcional) Para incluir [!DNL Live Search] , que incluye eventos de búsqueda, instale el [[!DNL Live Search]](../live-search/install.md) extensión.

### Instalación de la extensión B2B

Para los comerciantes B2B, instale la siguiente extensión para incluir [lista de solicitudes](events.md#b2b-events) datos de evento.

Descargue la `magento/experience-platform-connector-b2b` mediante la ejecución de lo siguiente desde la línea de comandos:

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

1. Abra la raíz `composer.json` archivo y buscar `magento/experience-platform-connector`.

1. En el `require` , actualice el número de versión como se indica a continuación:

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

## Desinstalar el conector del Experience Platform {#uninstall}

Para desinstalar el conector del Experience Platform, consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
