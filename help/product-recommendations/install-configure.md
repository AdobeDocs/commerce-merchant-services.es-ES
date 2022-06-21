---
title: Instalar y configurar
description: Obtenga información sobre cómo instalar, actualizar y desinstalar [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: cfeb8b4f8e2dc1e9d2d4c0be7a7bc522488418bc
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Instalar y configurar

Implementación [!DNL Product Recommendations] en la tienda y el administrador requiere que instale el módulo y configure el [Conector de Commerce Services](../landing/saas.md). A medida que se publican las actualizaciones, puede actualizar fácilmente la instalación con la versión más reciente.

- [Instalar](#install)
- [Configurar](#configure)
- [Actualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Porque la variable [!DNL Product Recommendations] es un metapackage independiente, las actualizaciones se publican con más frecuencia que Adobe Commerce. Para asegurarse de que está actualizado con las últimas correcciones y funciones de los errores, consulte la [notas de la versión](release-notes.md).

Instale el `magento/product-recommendations` con Composer:

```bash
composer require magento/product-recommendations
```

### Agregar compatibilidad con Page Builder {#pbsupport}

[!DNL Product Recommendations] para Page Builder son un módulo opcional y se instala por separado. Para usar [!DNL Product Recommendations] con Page Builder, instale el módulo ejecutando el siguiente comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Al habilitar [!DNL Product Recommendations] en Page Builder, puede agregar una [unidad de recomendación](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) a cualquier contenido creado en Page Builder, como páginas, bloques y bloques dinámicos.

### Agregar tipo de recomendación de similitud visual {#vissimsupport}

La variable _Similitud visual_ el tipo de recomendación permite implementar una unidad de recomendación en la página de detalles del producto que muestra los productos que [visualmente similar](type.md#visualsim) al producto que se está viendo. Este tipo de recomendación es más útil cuando las imágenes y los aspectos visuales de los productos son partes importantes de la experiencia de compra. Instale el _Similitud visual_ tipo de recomendación ejecutando el siguiente comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Después de instalar el `magento/product-recommendations` , debe configurar la variable [Conector de Commerce Services](https://docs.magento.com/user-guide/configuration/services/saas.html) especificando claves de API y seleccionando un espacio de datos SaaS.

Para asegurarse de que la exportación del catálogo se esté ejecutando correctamente, confirme que la variable [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) los trabajos y [indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) se están ejecutando y `Product Feed` indexer se configura como `Update by Schedule`.

Cuando se vincula correctamente con Commerce Services a través de claves API y se especifica el espacio de datos SaaS, comienza la sincronización del catálogo. Entonces puede [verify](verify.md) los datos de comportamiento se envían a su tienda.

## Actualice su [!DNL Product Recommendations] instalación {#update}

Como todo Adobe Commerce, [!DNL Product Recommendations] utiliza Composer para la instalación y las actualizaciones. Para actualizar el `magento/product-recommendations` ejecute lo siguiente:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para actualizar a una versión principal, como de 3.0 a 4.0, debe editar la raíz `composer.json` para su proyecto. (Consulte la [notas de la versión](release-notes.md) para obtener información sobre la versión más reciente). Por ejemplo, vamos a abrir el `composer.json` y busque el `magento/product-recommendations` módulo:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Busquemos la versión principal de `3.0` a `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Guarde el `composer.json` y ejecute:

```bash
composer update magento/product-recommendations --with-dependencies
```

>[!NOTE]
>
> En las versiones 3.x.x de Product Recommendations, solo necesitaba una clave de API única. En las versiones 4.x.x y posteriores, debe proporcionar claves de API públicas y privadas de producción, así como claves de API públicas y privadas de Sandbox. Si no proporciona ambos pares de claves de API, no podrá acceder a la función Product Recommendations en el administrador. Sin embargo, la recopilación de datos continuará en su tienda y las recomendaciones existentes se seguirán mostrando a sus compradores.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Si es necesario, puede [desinstalar](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) el módulo product-recommendations.
