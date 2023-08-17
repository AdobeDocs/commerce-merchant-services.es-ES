---
title: "Instalar [!DNL Quick Checkout] para la extensión de Adobe Commerce"
description: '"Siga estos pasos para instalar [!DNL Quick Checkout] en su proyecto de Adobe Commerce".'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Instalar [!DNL Quick Checkout]

El [!DNL Quick Checkout] extensión para Adobe Commerce y [!DNL Magento Open Source] se puede instalar con [!DNL Composer keys], que están vinculados a la cuenta de Commerce [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} se proporciona en el proceso de suscripción. Composer utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en que [!DNL Composer keys] no se han guardado previamente en `auth.json` archivo.

Consulte [obtener las claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} para obtener más información acerca de la obtención de [!DNL Composer keys].

Existen dos formas de instalar esta extensión: para [Adobe Commerce en la infraestructura en la nube](#magento-commerce-cloud) o [local](#on-premises) instalaciones. Estos métodos requieren que utilice la interfaz de línea de comandos (CLI).

## Actualizar la configuración de estabilidad mínima

Antes de instalar la extensión, asegúrese de que la variable `minimum-stability` en su campo `composer.json` el archivo está establecido en `"stable"`:

`"minimum-stability": "stable"`

## Instalación de la extensión

Puede instalar el [!DNL Quick Checkout] extensión para Adobe Commerce en la infraestructura en la nube e instancias locales.

### Adobe Commerce en la infraestructura en la nube

Este método se utiliza para instalar el [!DNL Quick Checkout] para una instancia de Commerce Cloud.

1. En la estación de trabajo local, cambie al directorio raíz del proyecto de Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   El `composer update` El comando actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando: `composer update magento/quick-checkout`.

1. Confirme y envíe los cambios.

### On-Premise

Este método se utiliza para instalar el [!DNL Quick Checkout] extensión para una instancia local.

1. Agregue el módulo Cierre rápido de compra a `require` de la sección `composer.json` archivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   El `composer update` El comando actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando: `composer update magento/quick-checkout`.

1. Actualizar Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Confirme los cambios.
1. Actualice la instancia local para asegurarse de que se implementa el código confirmado.

## Actualización de la extensión

Cuando lanzamos una nueva versión de [!DNL Quick Checkout], puede actualizar fácilmente su extensión.

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update
   ```

   El `composer update` El comando actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando: `composer update magento/quick-checkout`.

1. Confirme y envíe los cambios.

## Resolución de problemas

Puede ver errores al intentar instalar el [!DNL Quick Checkout] extensión.

Si encuentra algún problema durante la [!DNL Quick Checkout] proceso de instalación, consulte [Solucionar problemas de cierre rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) en el Centro de ayuda de Adobe Commerce.

## Requisitos previos

Consulte la [requisitos previos](../quick-checkout/prerequisites.md) para obtener más información.
