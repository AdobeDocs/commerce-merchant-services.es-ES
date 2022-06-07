---
title: '"Instale el [!DNL Quick Checkout] para la extensión de Adobe Commerce"'
description: '"Siga estos pasos para instalar el [!DNL Quick Checkout] en su proyecto de Adobe Commerce."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Instale el [!DNL Quick Checkout]

La variable [!DNL Quick Checkout] para Adobe Commerce, ofrece una experiencia de cierre de compra perfecta diseñada para convertir compradores únicos en titulares de cuentas fieles.

La variable [!DNL Quick Checkout] extensión para Adobe Commerce y [!DNL Magento Open Source] se puede instalar con [!DNL Composer keys], que están vinculados a la función [ID de Magento (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} proporcionado en el proceso de suscripción. El Compositor utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que el [!DNL Composer keys] no se guardaban previamente en la variable `auth.json` archivo.

Consulte [obtenga sus claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)Tema de {target=&quot;_blank&quot;} para obtener más información sobre cómo obtener [!DNL Composer keys].

Existen dos formas de instalar esta extensión: para [Adobe Commerce en infraestructura en la nube](#magento-commerce-cloud) o [local](#on-premises) instalaciones. Estos métodos requieren que utilice la Interfaz de Línea de Comandos (CLI).

## Actualizar la configuración de estabilidad mínima

Antes de instalar la extensión, puede cambiar la variable `minimum-stability` requisito `RC` (candidato a la versión) en su `composer.json` si desea probar la versión candidata para la versión. Puede utilizar un IDE o su editor de texto favorito (como Visual Studio Code o Sublime Text).

En `composer.json` archivo, cambiar `"minimum-stability": "stable"` a `"minimum-stability": "RC"`.

## Instalación de la extensión

Puede instalar el [!DNL Quick Checkout] extensión para Adobe Commerce en infraestructura en la nube e instancias locales.

### Adobe Commerce en infraestructura en la nube

Este método se utiliza para instalar la variable [!DNL Quick Checkout] para una instancia de Commerce Cloud.

1. En la estación de trabajo local, cambie al directorio raíz del proyecto de Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/quick-checkout`.

1. Confirme y presione los cambios.

### Local

Este método se utiliza para instalar la variable [!DNL Quick Checkout] extensión para una instancia local.

1. Añadir el módulo de Cierre de compra rápido a la `require` de la sección `composer.json` archivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/quick-checkout`.

1. Actualizar Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar cambios.
1. Actualice la instancia local para garantizar que se implementa el código comprometido.

## Actualizar la extensión

Cuando lanzamos una nueva versión de [!DNL Quick Checkout], puede actualizar fácilmente la extensión de .

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/quick-checkout`.

1. Confirme y presione los cambios.

## Resolución de problemas

Es posible que vea errores al intentar instalar el [!DNL Quick Checkout] extensión.

Consulte la [solución de problemas](../quick-checkout/troubleshooting.md) para obtener más información si tiene algún problema al instalar la variable [!DNL Quick Checkout].

## Requisitos previos

Consulte la [requisitos previos](../quick-checkout/prerequisites.md) para obtener más información.
