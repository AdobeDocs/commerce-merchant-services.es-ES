---
title: Instalar [!DNL Payment Services]
description: Instale la extensión Servicios de pago .
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 647848c58213ea7f85d8a2c025146aa065042433
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

La instalación del [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] es un paso previo para usar [!DNL Payment Services].

![[!DNL Payment Services] vista de administración de extensiones](assets/admin-view.png)

La variable [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] se puede instalar con las claves del Compositor, que están vinculadas al ID del Magento ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) en el proceso de suscripción. El Compositor utiliza estas claves durante la instalación inicial de [!DNL Adobe Commerce], o en situaciones en las que las claves del Compositor no se guardaban previamente en el `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obtener más información sobre la obtención de claves de Composer.

Existen dos formas de instalar esta extensión: para [[!DNL Adobe Commerce] en la infraestructura de nube](install.md#adobe-commerce-on-cloud-infrastructure) o [Local](install.md#on-premises) instalaciones. Estos métodos requieren que utilice la Interfaz de Línea de Comandos (CLI).

## Instalación de la extensión

Puede instalar el [!DNL Payment Services] extensión para ambas [!DNL Adobe Commerce] en infraestructura de nube e instancias locales.

### [!DNL Adobe Commerce] en la infraestructura de nube

Este método se utiliza para instalar la variable [!DNL Payment Services] para una instancia de Commerce Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer require magento/payment-services`.

1. Confirme y presione los cambios.

### Local

Este método se utiliza para instalar la variable [!DNL Payment Services] extensión para una instancia local.

1. Para obtener la extensión, ejecute estos comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer require magento/payment-services`.

1. Actualización [!DNL Adobe Commerce]:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar cambios.
1. Para garantizar que se implementa el código comprometido, actualice la instancia local .

## Actualizar la extensión

Cuando una nueva versión de [!DNL Payment Services] se ha publicado, puede actualizar fácilmente la extensión.

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update
   ```

   La variable `composer update` actualiza todas las dependencias. Si no desea actualizar todas las dependencias al mismo tiempo, utilice este comando en su lugar: `composer update magento/payment-services`.

1. Confirme y presione los cambios.

## Resolución de problemas

Es posible que vea errores al intentar instalar el [!DNL Payment Services] extensión. Utilice los siguientes métodos de resolución de problemas para resolver los errores.

### Claves de Compositor incorrectas

Si ve el siguiente error que indica que tiene claves de Compositor incorrectas:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Compruebe que las claves del Compositor estén vinculadas al ID de Magento utilizado durante [!DNL Payment Services] registro.

Para ver qué claves de Compositor están configuradas:

1. Busque la ubicación de la variable `auth.json` archivo:

   ```bash
   composer config --global home
   ```

1. Consulte la `auth.json` archivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [qué claves están asociadas con su ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### No hay suficiente memoria para PHP

Si ve el siguiente error que indica que no tiene suficiente memoria para PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumentar el límite de memoria](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP en su entorno en `php.ini`.

También puede especificar el límite de memoria mediante este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Por ejemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
