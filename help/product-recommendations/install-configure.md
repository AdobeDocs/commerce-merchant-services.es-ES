---
title: Instalar y configurar
description: Obtenga información sobre cómo instalar, actualizar y desinstalar [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Instalar y configurar

Implementación [!DNL Product Recommendations] a su tienda y el administrador requiere que instale el módulo y configure el [Conector de Commerce Services](../landing/saas.md). A medida que se lanzan las actualizaciones, puede actualizar fácilmente la instalación con la versión más reciente.

- [Instalar](#install)
- [Configurar](#configure)
- [Actualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Debido a que el [!DNL Product Recommendations] El módulo de es un metapaquete independiente, las actualizaciones se publican con más frecuencia que Adobe Commerce. Para asegurarse de que está al día con las últimas correcciones de errores y funciones, consulte la [notas de la versión](release-notes.md).

Instale el `magento/product-recommendations` con Composer:

```bash
composer require magento/product-recommendations
```

### Añadir compatibilidad con Page Builder {#pbsupport}

[!DNL Product Recommendations] para Page Builder es un módulo opcional y se instala por separado. Para usar [!DNL Product Recommendations] con Page Builder, instale el módulo ejecutando el siguiente comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Al habilitar [!DNL Product Recommendations] en Page Builder, puede agregar un activo existente [unidad de recomendación](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a cualquier contenido creado en Page Builder, como páginas, bloques y bloques dinámicos.

Consulte [Uso de [!DNL Product Recommendations] con contenido de Page Builder](page-builder.md) para obtener más instrucciones.

### Agregar tipo de recomendación de similitud visual {#vissimsupport}

El _Similitud visual_ el tipo de recomendación le permite desplegar una unidad de recomendación en la página de detalles del producto que muestra los productos que [visualmente similar](type.md#visualsim) al producto que se está viendo. Este tipo de recomendación es más útil cuando las imágenes y los aspectos visuales de los productos son partes importantes de la experiencia de compra. Instale el _Similitud visual_ tipo de recomendación ejecutando el siguiente comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Después de instalar el `magento/product-recommendations` , debe configurar el módulo [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) especificando las claves API y seleccionando un espacio de datos SaaS.

Para asegurarse de que la exportación del catálogo se ejecuta correctamente, confirme que la variable [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) trabajos y la [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) están en ejecución y el `Product Feed` el indexador se ha establecido en `Update by Schedule`.

Cuando se vincula correctamente a Commerce Services a través de claves de API y se especifica el espacio de datos SaaS, se inicia la sincronización del catálogo. Puede hacer lo siguiente [verificar](verify.md) Compruebe que los datos de comportamiento se envían a su tienda.

## Actualice su [!DNL Product Recommendations] instalación {#update}

Al igual que todos los Adobe Commerce, [!DNL Product Recommendations] utiliza Composer para la instalación y las actualizaciones. Para actualizar el `magento/product-recommendations` , ejecute lo siguiente:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para actualizar a una versión principal, como de 3.0 a 4.0, debe editar la raíz `composer.json` para su proyecto. (Consulte la [notas de la versión](release-notes.md) para obtener información sobre la versión más reciente). Por ejemplo, vamos a abrir el `composer.json` y busque el archivo `magento/product-recommendations` módulo:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Vamos a golpear la versión principal de `3.0` hasta `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Guarde el `composer.json` archivo y ejecutar:

```bash
composer update magento/product-recommendations --with-dependencies
```

O si ha instalado el `magento/module-visual-product-recommendations` y `magento/module-page-builder-product-recommendations` módulos:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> En las versiones 3.x.x de Product Recommendations, solo se necesitaba una sola clave de API. En las versiones 4.x.x y posteriores, debe proporcionar claves de API públicas y privadas de producción, así como claves de API públicas y privadas de zona protegida. Si no proporciona ambos pares de claves API, no podrá acceder a la función de Product Recommendations en el Administrador. La recopilación de datos, sin embargo, continuará en su tienda y las recomendaciones existentes se seguirán mostrando a sus compradores.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Si es necesario, puede [desinstalar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) el módulo de recomendaciones de productos.
