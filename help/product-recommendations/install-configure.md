---
title: Instalar y configurar
description: Obtenga información sobre cómo instalar, actualizar y desinstalar  [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Instalar y configurar

La implementación de [!DNL Product Recommendations] en tu tienda y administrador requiere que instales el módulo y configures [Commerce Services Connector](../landing/saas.md). A medida que se lanzan las actualizaciones, puede actualizar fácilmente la instalación con la versión más reciente.

- [Instalar](#install)
- [Configurar](#configure)
- [Actualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Dado que el módulo [!DNL Product Recommendations] es un metapaquete independiente, las actualizaciones se publican con mayor frecuencia que Adobe Commerce. Para asegurarse de que está al día con las últimas correcciones de errores y características, consulte las [notas de la versión](release-notes.md).

Instale el módulo `magento/product-recommendations` con Composer:

```bash
composer require magento/product-recommendations
```

### Añadir compatibilidad con Page Builder {#pbsupport}

[!DNL Product Recommendations] para Page Builder es un módulo opcional y se instala por separado. Para usar [!DNL Product Recommendations] con Page Builder, instale el módulo ejecutando el siguiente comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Al habilitar [!DNL Product Recommendations] en Page Builder, puede agregar una [unidad de recomendación](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) activa y existente a cualquier contenido creado en Page Builder, como páginas, bloques y bloques dinámicos.

Consulte [Uso de [!DNL Product Recommendations] con contenido de Page Builder](page-builder.md) para obtener más instrucciones.

### Agregar tipo de recomendación de similitud visual {#vissimsupport}

El tipo de recomendación _Similitud visual_ le permite implementar una unidad de recomendación en la página de detalles del producto que muestra productos [visualmente similares](type.md#visualsim) al producto que se está viendo. Este tipo de recomendación es más útil cuando las imágenes y los aspectos visuales de los productos son partes importantes de la experiencia de compra. Instale el tipo de recomendación _Visual similarity_ ejecutando el siguiente comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Después de instalar el módulo `magento/product-recommendations`, debe configurar [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) especificando las claves de API y seleccionando un espacio de datos SaaS.

Para asegurarse de que la exportación del catálogo se está ejecutando correctamente, confirme que los trabajos [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) y los [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) se están ejecutando y que el indexador `Product Feed` está establecido en `Update by Schedule`.

Cuando se vincula correctamente a Commerce Services mediante claves de API y se especifica el espacio de datos SaaS, se inicia la sincronización del catálogo. Entonces puedes [verificar](verify.md) que los datos de comportamiento se están enviando a tu tienda.

## Actualice la instalación de [!DNL Product Recommendations] {#update}

Al igual que todo Adobe Commerce, [!DNL Product Recommendations] usa Composer para la instalación y las actualizaciones. Para actualizar el módulo `magento/product-recommendations`, ejecute lo siguiente:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para actualizar a una versión principal, como de la 3.0 a la 4.0, debe editar el archivo raíz `composer.json` de su proyecto. (Vea las [notas de la versión](release-notes.md) para obtener información sobre la versión más reciente). Por ejemplo, vamos a abrir el archivo principal `composer.json` y buscar el módulo `magento/product-recommendations`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Vamos a pasar la versión principal de `3.0` a `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Guarde el archivo `composer.json` y ejecute:

```bash
composer update magento/product-recommendations --with-dependencies
```

O si ha instalado los módulos `magento/module-visual-product-recommendations` y `magento/module-page-builder-product-recommendations`:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> En las versiones 3.x.x de Product Recommendations, solo se necesitaba una sola clave de API. En las versiones 4.x.x y posteriores, debe proporcionar claves de API públicas y privadas de producción, así como claves de API públicas y privadas de zona protegida. Si no proporciona ambos pares de claves API, no podrá acceder a la función de Product Recommendations en el Administrador. La recopilación de datos, sin embargo, continuará en su tienda y las recomendaciones existentes se seguirán mostrando a sus compradores.

## Cortafuegos

Para permitir que Product Recommendations pase a través de un firewall, agregue `commerce.adobe.io` a la lista de permitidos.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Si es necesario, puede [desinstalar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) el módulo de recomendaciones de productos.
