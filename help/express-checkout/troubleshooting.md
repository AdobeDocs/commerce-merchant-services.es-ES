---
title: Resolución de problemas para la [!DNL Express Checkout]
description: Solucionar errores, problemas conocidos que puede experimentar al usar la variable [!DNL Express Checkout] para la extensión de Adobe Commerce.
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# Resolución de problemas [!DNL Express Checkout] para Adobe Commerce

>[!IMPORTANT]
>
> Esta función es para usuarios del Programa de Adoptadores Anticipados (EAP, por sus siglas en inglés) y aún no es accesible para todos los clientes. Actualmente está limitado a los clientes de EE. UU. Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce para obtener ayuda y formular preguntas.

Utilice los siguientes métodos de resolución de problemas para resolver estos problemas específicos.

## Claves de Compositor incorrectas

Si ve el siguiente error que indica que tiene las claves de Compositor incorrectas:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Compruebe que las claves del Compositor estén vinculadas al ID de Magento utilizado durante el registro de salida exprés.

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

## Estabilidad mínima en `composer.json` está configurado como estable

Si ve el siguiente error que indica que tiene las claves de Compositor incorrectas:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Establezca la estabilidad mínima en `RC` en el `composer.json` archivo.

## No hay suficiente memoria para PHP

Si ve el siguiente error que indica que no tiene suficiente memoria para PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumentar el límite de memoria](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP en su entorno en `php.ini`.

También puede especificar el límite de memoria mediante este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

Por ejemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## Dirección de envío no válida

Hay un problema conocido para la variable [!DNL Express Checkout].

Cuando la dirección de envío predeterminada no es válida, se redirige al cliente al paso de dirección de envío. La tienda solo muestra direcciones de envío válidas.

>[!WARNING]
>
> si no hay direcciones de envío válidas, el cliente no ve ninguna dirección de envío disponible.

Consulte la [detalles de envío](../express-checkout/shipping-details.md) para obtener más información.

## Agregar líneas de dirección de calle con una nueva dirección de envío

Hay un problema conocido para la variable [!DNL Express Checkout].

Cuando [iniciar sesión con una cuenta de Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) puede añadir una nueva dirección de envío con una limitación de 4 líneas por dirección de calle.

Adobe Commerce normalmente se puede configurar para admitir hasta 20 líneas de dirección de calle.

## Casilla de verificación `enable terms and conditions` no se muestra correctamente

Hay un problema conocido para la variable [!DNL Express Checkout].

Al habilitar la variable `Enable terms and conditions` en el Administrador e inicie sesión con un [!DNL Bolt] cuenta, la variable `Enable terms and conditions` no se muestra durante el cierre de compra. Consulte la [iniciar sesión](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] para obtener más información.

Consulte [términos y condiciones](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) para obtener más información sobre la configuración de administración.

## Comportamiento inesperado cuando `Display Billing Address On` está configurado como `payment page`

Hay un problema conocido para la variable [!DNL Express Checkout].

Si configura la variable `Display Billing Address On` parámetro a `payment page` y [iniciar sesión con una cuenta de Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) al marcar la variable `My billing and shipping address are the same` casilla de verificación:

![Misma dirección](assets/checked-address.png)

Se muestra el botón de radio `use existing card`.

Consulte [Cierre de compra](https://docs.magento.com/user-guide/configuration/sales/checkout.html) para obtener más información sobre `Display Billing Address On` parámetro.

## Traducción de [!DNL Express Checkout] Extensión

Adobe Commerce le permite localizar su tienda para varias regiones y mercados. Incluso puede localizar mensajes de error en la vista Administración.

Consulte la [traducción y localización](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) para obtener más información.

## Vaciar la caché

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Cache Management]** y haga clic en **[!UICONTROL Flush Cache]** para actualizar todas las cachés no válidas.

## Obtener ayuda

Contacto [!DNL Adobe Commerce] equipo de ingeniería a través del Slack asignado [Canal Programas beta de Adobe](http://adobe-beta-programs.slack.com/) para cualquier ayuda.
