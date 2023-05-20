---
title: Instalar [!DNL Payment Services]
description: Instale la extensión Servicios de pago.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

Descarga e instalación de [!DNL Payment Services] extensión para [!DNL Adobe Commerce] y [!DNL Magento Open Source] es un paso previo para utilizar [!DNL Payment Services].

![[!DNL Payment Services] vista de administración de extensiones](assets/admin-view.png)

## Descargar la extensión

Primero debe descargar la extensión desde [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) antes de instalarlo.

1. Vaya a [Extensión de servicios de pago en el Commerce Marketplace](https://marketplace.magento.com/magento-payment-services.html).
1. Para elegir la edición y la versión, alterne **[!UICONTROL Edition]** y **[!UICONTROL Your store version]** a sus selecciones preferidas.
1. Clic **[!UICONTROL Add to Cart]**.
1. Complete el cierre de compra y haga clic en **[!UICONTROL Place Order]**.
1. Consulte el correo electrónico asociado a la descarga de Marketplace para obtener confirmación y detalles del pedido.

## Instalación de la extensión

Puede instalar el [!DNL Payment Services] extensión para ambos [!DNL Adobe Commerce] en la infraestructura en la nube y en instancias locales, que están vinculadas a su cuenta de Commerce [mageide](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) se proporciona en el proceso de suscripción. [!DNL Magento Open Source] los clientes utilizan las instrucciones locales.

Composer utiliza estas teclas durante la instalación inicial de [!DNL Adobe Commerce]o en situaciones en las que las claves del Compositor no se habían guardado previamente en `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obtener más información sobre cómo obtener claves de Composer.

Consulte [Instalación de una extensión](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) para obtener más información sobre qué considerar antes de descargar e instalar una extensión.

### [!DNL Adobe Commerce] en la infraestructura en la nube

Este método se utiliza para instalar el [!DNL Payment Services] para una instancia de Commerce Cloud.

1. Actualice su `composer.json` archivo:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice el `composer update` para actualizar todas las dependencias raíz.

1. Confirme y envíe los cambios.

### Configuraciones locales y de otro tipo

Este método se utiliza para instalar el [!DNL Payment Services] extensión para una instancia local y [!DNL Magento Open Source] clientes.

1. Para obtener la extensión, ejecute estos comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice el `composer update` para actualizar todas las dependencias raíz.

1. Actualice la instancia:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Confirme los cambios.
1. Para asegurarse de que el código confirmado esté implementado, actualice la instancia

## Actualización de la extensión

Cuando una nueva versión de [!DNL Payment Services] se ha lanzado, puede actualizar fácilmente su extensión.

1. Para obtener la versión más reciente del paquete:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Utilice el `composer update` para actualizar todas las dependencias raíz.

1. Confirme y envíe los cambios.

## Solución de problemas

Puede ver errores al intentar instalar el [!DNL Payment Services] extensión. Utilice los siguientes métodos de solución de problemas para resolver los errores.

### Claves de composición incorrectas

Si ve el siguiente error que indica que tiene las claves Compositor incorrectas:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Compruebe que las claves de Composer son válidas y que tiene acceso a otros paquetes de Magento.

Para ver qué claves del Compositor están configuradas:

1. Buscar la ubicación de `auth.json` archivo:

   ```bash
   composer config --global home
   ```

1. Ver el `auth.json` archivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [qué claves están asociadas a su cuenta de Commerce `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Memoria insuficiente para PHP

Si ve el siguiente error que indica que no tiene suficiente memoria para PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumento del límite de memoria](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP en su entorno en `php.ini`.

Como alternativa, puede especificar el límite de memoria mediante este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Por ejemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
