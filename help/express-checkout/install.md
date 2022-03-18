---
title: Instale el [!DNL Express Checkout] para la extensión de Adobe Commerce
description: Siga estos pasos para instalar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce.
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Instale el [!DNL Express Checkout]

>[!IMPORTANT]
>
> Esta función es para usuarios del Programa de Adoptadores Anticipados (EAP, por sus siglas en inglés) y aún no es accesible para todos los clientes. Actualmente está limitado a los clientes de EE. UU. Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.

La variable [!DNL Express Checkout] para Adobe Commerce, ofrece una experiencia de cierre de compra perfecta diseñada para convertir compradores únicos en titulares de cuentas fieles.

La variable [!DNL Express Checkout] para Adobe Commerce y Magento Open Source se pueden instalar con las claves Composer, que están vinculadas al [ID de Magento (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} proporcionado en el proceso de suscripción. El Compositor utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que las claves del Compositor no se guardaban previamente en el `auth.json` archivo.

Consulte [obtenga sus claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} para obtener más información sobre la obtención de claves de Compositor.

Existen dos formas de instalar esta extensión: para [Adobe Commerce en infraestructura en la nube](#magento-commerce-cloud) o [local](#on-premises) instalaciones. Estos métodos requieren que utilice la Interfaz de Línea de Comandos (CLI).

## Actualizar la configuración de estabilidad mínima

Antes de instalar la extensión, puede cambiar la variable `minimum-stability` requisito `RC` (candidato a la versión) en su `composer.json` si desea probar la versión candidata para la versión. Puede utilizar un IDE o su editor de texto favorito (como Visual Studio Code o Sublime Text).

En `composer.json` archivo, cambiar `"minimum-stability": "stable"` a `"minimum-stability": "RC"`.

## Instalación de la extensión

Puede instalar el [!DNL Express Checkout] extensión para Adobe Commerce en infraestructura en la nube e instancias locales.

### Adobe Commerce en infraestructura en la nube

Este método se utiliza para instalar la variable [!DNL Express Checkout] para una instancia de Commerce Cloud.

1. En la estación de trabajo local, cambie al directorio raíz del proyecto de Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/express-checkout`.

1. Confirme y presione los cambios.

### Local

Este método se utiliza para instalar la variable [!DNL Express Checkout] extensión para una instancia local.

1. Añadir el módulo de salida exprés al `require` de la sección `composer.json` archivo:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/express-checkout`.

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

Cuando lanzamos una nueva versión de [!DNL Express Checkout], puede actualizar fácilmente la extensión de .

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/express-checkout`.

1. Confirme y presione los cambios.

## Resolución de problemas

Es posible que vea errores al intentar instalar el [!DNL Express Checkout] extensión.

Consulte la [solución de problemas](../express-checkout/troubleshooting.md) para obtener más información si tiene algún problema al instalar la variable [!DNL Express Checkout].

## Requisitos previos

Consulte la [requisitos previos](../express-checkout/prerequisites.md) para obtener más información.
