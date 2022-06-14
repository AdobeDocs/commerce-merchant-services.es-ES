---
title: Instalación
description: Agregar descripción
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Instalación

Instalación inicial completa del [!DNL Store Fulfillment] en un entorno que no sea de producción con el administrador de colas en ejecución y el almacenamiento en caché configurado para permitir la gestión de excepciones. Su entorno debe incluir otras herramientas de desarrollo para garantizar prácticas recomendadas con el fin de operar y mantener su instancia de Adobe Commerce.

## Requisitos previos

Consulte la [requisitos](solution-requirements.md) para la solución Store Fulfillment y recopile la información necesaria antes de instalar la variable [!DNL Store Fulfillment] para Adobe Commerce.

Si ha instalado una versión previa o beta de la extensión Store Fulfillment for Adobe Commerce, quítela antes de instalar la versión actual.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Requisitos de instalación

- **Acceso al cumplimiento de la tienda mediante el archivo de software Walmart Commerce Technologies (archivo .zip)**-Durante el proceso de incorporación y habilitación, trabaje con su administrador de cuentas para obtener acceso al archivo de instalación para la extensión de cumplimiento de la tienda.

- **Información de la cuenta de Adobe Commerce**-Instalación [!DNL Channel Manager] requiere un [Cuenta de comercio](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Necesita un ID de cuenta y credenciales con acceso de propietario o administrador a la variable [!DNL Adobe Commerce] proyecto.

- Para [!DNL Adobe Commerce] en los proyectos de infraestructura de nube, los instaladores de software deben tener acceso de administrador al proyecto de Cloud. Consulte [Administrar el acceso de los usuarios](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Experiencia con el Compositor y el[!DNL Commerce CLI]**—Consulte [Instalación general de CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obtener información sobre el uso de estas herramientas para instalar y administrar extensiones en el [!DNL Adobe Commerce] plataforma.

- **Experiencia en la instalación de extensiones de terceros en Adobe Commerce**-Para obtener referencia, consulte la documentación de Adobe Commerce.

   - [Instalación de una extensión para Adobe Commerce en una instancia de infraestructura de nube](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)

   - [Instalación de una extensión para una instancia local de Adobe Commerce](https://devdocs.magento.com/extensions/install/)

### Paso 1: Descargar el paquete de extensiones

Siga las instrucciones proporcionadas por los representantes de su cuenta para descargar el archivo que contiene los paquetes del Compositor para instalar la extensión de Servicios de almacenamiento.

### Paso 2: Extraer artefactos de extensión a la aplicación

Extraiga el archivo que contiene el paquete de integración para instalar la extensión de servicios de cumplimiento de almacenamiento.

1. Cree un directorio de destino para los archivos extraídos.

   - Desde la línea de comandos, vaya al directorio raíz doc del servidor web.

   - Cree un `artifacts` directorio.

1. Extraiga el archivo de archivo en el nuevo directorio.

1. Compruebe que los archivos extraídos revisando la lista de archivos.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Paso 3: Configurar la aplicación con el Compositor

Use Composer para configurar el directorio de origen de la instalación e instalar la extensión de los servicios de cumplimiento de almacenamiento.

1. Configure el repositorio de origen para la instalación del Compositor.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Agregue la extensión Servicios de cumplimiento de tiendas a `composer.json`

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Para obtener un mejor rendimiento en las instancias locales de Adobe Commerce, puede [actualizar la configuración de carga automática](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Paso 4: Actualización del esquema y los datos de la base de datos

Complete la instalación utilizando el `bin/magento setup:upgrade` para actualizar el esquema y los datos de la base de datos con los cambios para admitir la solución Store Fulfillment .

>Nota:
>Para Adobe Commerce en proyectos de infraestructura en la nube, no es necesario registrar la extensión. En su lugar, confirme los cambios de código del paso anterior y colóquelos en la rama de entorno. Los comandos para actualizar el esquema y los datos de la base de datos se ejecutan automáticamente durante el proceso de compilación e implementación de la nube.

### Paso 5: Completar la instalación

1. Registre la extensión con Adobe Commerce utilizando la variable `setup:upgrade` comando CLI del Magento.

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

1. Deshabilite el modo de mantenimiento.

   ```bash
   bin/magento maintenance:disable
   ```

### Paso 6: Verifique la instalación

Desde el servidor de Adobe Commerce, compruebe que los módulos de la extensión de Servicios de cumplimiento de almacenamiento estén instalados y habilitados.

1. Inicie sesión en el servidor.

   Para instalaciones en Adobe Commerce en infraestructura de nube, utilice SSH para iniciar sesión en el entorno remoto.

1. Compruebe que los módulos de servicios de cumplimiento de la tienda estén habilitados.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   El resultado debe incluir los siguientes módulos:

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

Si es necesario, use la variable [configuración:static-content: implementar](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy) Comando CLI para implementar archivos de vista estáticos en su entorno de producción.

```terminal
php bin/magento setup:static-content:deploy -f
```

La variable `-f` es obligatoria si utiliza un tema en blanco.

>[!NOTE]
>
>Para obtener más información, consulte [El contenido estático implementa las prácticas recomendadas en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360031624091) en el Centro de ayuda de Adobe Commerce.

