---
title: Instalación
description: '"Instale el [!DNL Store Fulfillment solution] para una tienda Adobe Commerce que use Composer para PHP".'
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---


# Instalación

Completar la instalación inicial del [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] extensión en un entorno que no es de producción con el administrador de colas en ejecución y el almacenamiento en caché configurado para permitir el control de excepciones. Asegúrese de que el entorno de desarrollo incluya herramientas de desarrollo para garantizar las prácticas recomendadas de funcionamiento y mantenimiento de la instancia de Adobe Commerce.

>[!TIP]
>
>Actualice la extensión Store Fulfillment para Adobe Commerce local siguiendo las [instrucciones de actualización](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html) en el _Guía de actualización de Adobe Commerce_. Para obtener información sobre la infraestructura en la nube de Adobe Commerce, consulte [Actualización de una extensión](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html#upgrade-an-extension) en el *Guía de Commerce en la infraestructura de Cloud*.

## Requisitos previos

Revise la [requisitos](solution-requirements.md) para la solución Store Fulfillment y recopile la información necesaria antes de instalar o actualizar el [!DNL Store Fulfillment] para Adobe Commerce.

Si ha instalado una versión preliminar o beta de la extensión Store Fulfillment for Adobe Commerce, utilice el siguiente comando para eliminarla antes de instalar la versión actual.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Requisitos de instalación

- **Acceso al archivo de software Store Fulfillment by Walmart Commerce Technologies (archivo .zip)**: durante el proceso de incorporación y activación, colabore con su administrador de cuentas para obtener acceso al archivo de instalación de la extensión Store Fulfillment.

- **Información de cuenta de Adobe Commerce**-Instalación del [!DNL Store Fulfillment] La solución requiere un [[!DNL Commerce] account](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. Necesita un ID de cuenta y credenciales con acceso de propietario o administrador a [!DNL Adobe Commerce] proyecto.

- Para [!DNL Adobe Commerce] en los proyectos de infraestructura en la nube, los instaladores de software deben tener acceso de administrador al proyecto en la nube. Consulte [Administrar el acceso de usuario](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Experiencia con Composer y el[!DNL Commerce CLI]**: consulte [Instalación general de CLI](https://devdocs.magento.com/extensions/install/){target="_blank"} para obtener información acerca del uso de estas herramientas para instalar y administrar extensiones en [!DNL Adobe Commerce] plataforma.

- **Experimente la instalación de extensiones de terceros en Adobe Commerce**: para referencia, consulte la documentación de Adobe Commerce.

   - [Instalación de una extensión para una instancia de Adobe Commerce en la nube](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Instalación de una extensión para una instancia local de Adobe Commerce](https://devdocs.magento.com/extensions/install/).

### Paso 1: Descargar el paquete de extensiones

Siga las instrucciones proporcionadas por los representantes de su cuenta para descargar el archivo que contiene los paquetes de Composer para instalar la extensión Store Fulfillment Services.

### Paso 2: Extraer artefactos de extensión en la aplicación

Extraiga el archivo que contiene el paquete de integración para instalar la extensión Store Fulfillment Services.

1. Cree un directorio de destino para los archivos extraídos.

   - Desde la línea de comandos, vaya al directorio raíz del documento del servidor web.

   - Crear un `artifacts` directorio.

1. Extraiga el archivo en el nuevo directorio.

1. Compruebe que los archivos se han extraído correctamente revisando la lista de archivos.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Paso 3: Configurar la aplicación mediante Composer

Use Composer para configurar el directorio de origen para la instalación e instalar la extensión Store Fulfillment Services.

1. Configure el repositorio de origen para la instalación del Compositor.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Añadir la extensión de Store Fulfillment Services a `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Para obtener un mejor rendimiento en las instancias locales de Adobe Commerce, puede [actualizar la configuración de carga automática](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Paso 4: Actualizar el esquema y los datos de la base de datos

Complete la instalación utilizando el `bin/magento setup:upgrade` para actualizar el esquema y los datos de la base de datos con los cambios necesarios para admitir la solución Store Fulfillment.

>[!NOTE]
>
>Para Adobe Commerce en proyectos de infraestructura en la nube, no es necesario registrar la extensión. En su lugar, confirme los cambios de código del paso anterior y envíelos a la rama de entorno. Los comandos para actualizar el esquema y los datos de la base de datos se ejecutan automáticamente durante el proceso de generación e implementación en la nube.

### Paso 5: completar la instalación

1. Registre la extensión de con Adobe Commerce utilizando `setup:upgrade` Comando CLI del Magento.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Si se le solicita, vuelva a compilar su [!DNL Commerce] proyecto.

   ```bash
   bin/magento setup:di:compile
   ```

1. Limpie la caché.

   ```bash
   bin/magento cache:clean
   ```

1. Desactive el modo de mantenimiento.

   ```bash
   bin/magento maintenance:disable
   ```

### Paso 6: Verificar la instalación

Desde el servidor de Adobe Commerce, compruebe que los módulos de la extensión Store Fulfillment Services estén instalados y habilitados.

1. Inicie sesión en el servidor de.

   Para instalaciones sobre Adobe Commerce en la infraestructura en la nube, [usar SSH para iniciar sesión en el entorno remoto](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. Compruebe que los módulos Servicios de Store Fulfillment estén activados.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   La salida debe incluir los siguientes módulos:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Pasos adicionales

Si es necesario, utilice el [configurar:static-content:implementar](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} Comando CLI para implementar archivos de vista estática en el entorno de producción.

```terminal
php bin/magento setup:static-content:deploy -f
```

El `-f` es necesaria si utiliza una temática en blanco.

>[!NOTE]
>
>Para obtener más información, consulte la [Contenido estático: implemente prácticas recomendadas en Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) artículo en el Centro de ayuda de Adobe Commerce.


