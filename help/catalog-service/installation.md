---
title: '"Incorporación e instalación"'
description: '"Obtenga información sobre cómo instalar [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Integración e instalación

Los socios y clientes pueden empezar a usar la variable [!DNL Catalog Service] para la versión beta de Adobe Commerce publicada el 9 de agosto de 2022. Para participar, debes leer y aceptar nuestra [Términos del programa Adobe Commerce Beta](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Una vez que haya firmado el acuerdo, póngase en contacto con nuestro equipo en el [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) canal de Slack público. Proporcionaremos toda la información y los siguientes pasos necesarios para trabajar con el [!DNL Catalog Service] Versión beta.

## Requisitos previos

El proceso de incorporación para [!DNL Catalog Service] requiere acceso a la línea de comandos del servidor. Si no está familiarizado con el trabajo desde la línea de comandos, pida ayuda a un desarrollador o integrador de sistemas.

### Requisitos de software

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Compositor: 2.x, 1.x

### Plataformas compatibles

- Adobe Commerce en infraestructura de nube: 2.4.x
- Adobe Commerce local: 2.4.x

## Instalación de la extensión

Puede instalar el [!DNL Catalog Service] extensión para Adobe Commerce en infraestructura en la nube e instancias locales.

La variable [!DNL Catalog Service] se instala con las claves del Compositor, que están vinculadas al ID del Magento ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) en el proceso de suscripción. El Compositor utiliza estas claves durante la instalación inicial de [!DNL Adobe Commerce], o en situaciones en las que las claves del Compositor no se guardaban previamente en el `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obtener más información sobre la obtención de claves de Composer.

### Adobe Commerce en infraestructura en la nube

Utilice este método para instalar el [!DNL Catalog Service] para una instancia de Commerce Cloud.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la variable `require` como se indica a continuación:

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   El comando actualiza todas las dependencias.

1. Confirme y presione los cambios.

### Local

Utilice este método para instalar el [!DNL Catalog Service] extensión para una instancia local.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la variable `require` como se indica a continuación:

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   El comando actualiza todas las dependencias.

1. Actualizar Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

## Configurar la exportación del catálogo

Después de la instalación [!DNL Catalog Service], debe configurar la variable [Conector de Commerce Services](../landing/saas.md) especificando claves de API y seleccionando un espacio de datos SaaS.

Para asegurarse de que la exportación del catálogo se esté ejecutando correctamente, confirme que la variable [trabajos cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) y [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) se están ejecutando y el indizador de fuente de producto se ha configurado en Actualizar por programa.
