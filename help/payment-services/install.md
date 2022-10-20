---
title: Instalar [!DNL Payment Services]
description: Instale la extensión Servicios de pago .
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

Descarga e instalación del [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] es un paso previo para usar [!DNL Payment Services].

![[!DNL Payment Services] vista de administración de extensiones](assets/admin-view.png)

## Descargar la extensión

Primero debe descargar la extensión desde [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) antes de instalarlo.

1. Vaya a la [Extensión Servicios de pago en el Commerce Marketplace](https://marketplace.magento.com/magento-payment-services.html).
1. Para elegir la edición y la versión, cambie **[!UICONTROL Edition]** y **[!UICONTROL Your store version]** a sus selecciones preferidas.
1. Haga clic **[!UICONTROL Add to Cart]**.
1. Complete el cierre de compra y haga clic en **[!UICONTROL Place Order]**.
1. Consulte el correo electrónico asociado con su descarga de Marketplace para obtener la confirmación del pedido y detalles.

## Instalación de la extensión

Puede instalar el [!DNL Payment Services] extensión para ambas [!DNL Adobe Commerce] en la infraestructura de nube y en las instancias locales, que están vinculadas a su cuenta de comercio [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) en el proceso de suscripción. [!DNL Magento Open Source] los clientes de utilizan las instrucciones locales.

El Compositor utiliza estas claves durante la instalación inicial de [!DNL Adobe Commerce], o en situaciones en las que las claves del Compositor no se guardaban previamente en el `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obtener más información sobre la obtención de claves de Composer.

Consulte [Instalación de una extensión](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) para obtener más información sobre qué considerar antes de descargar e instalar una extensión.

### [!DNL Adobe Commerce] en la infraestructura de nube

Este método se utiliza para instalar la variable [!DNL Payment Services] para una instancia de Commerce Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice la variable `composer update` para actualizar todas las dependencias raíz.

1. Confirme y presione los cambios.

### Configuraciones locales y otras configuraciones

Este método se utiliza para instalar la variable [!DNL Payment Services] extensión para una instancia local y [!DNL Magento Open Source] clientes.

1. Para obtener la extensión, ejecute estos comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice la variable `composer update` para actualizar todas las dependencias raíz.

1. Actualice la instancia:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar cambios.
1. Para asegurarse de que el código comprometido está implementado, actualice la instancia de .

## Actualizar la extensión

Cuando una nueva versión de [!DNL Payment Services] se ha publicado, puede actualizar fácilmente la extensión.

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice la variable `composer update` para actualizar todas las dependencias raíz.

1. Confirme y presione los cambios.

## Resolución de problemas

Es posible que vea errores al intentar instalar el [!DNL Payment Services] extensión. Utilice los siguientes métodos de resolución de problemas para resolver los errores.

### Claves de Compositor incorrectas

Si ve el siguiente error que indica que tiene claves de Compositor incorrectas:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Compruebe que las claves del Compositor son válidas y que tiene acceso a otros paquetes del Magento.

Para ver qué claves de Compositor están configuradas:

1. Busque la ubicación de la variable `auth.json` archivo:

   ```bash
   composer config --global home
   ```

1. Consulte la `auth.json` archivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [qué claves están asociadas a su cuenta de Commerce `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

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
