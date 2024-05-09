---
title: '[!DNL Product Recommendations] Notas de la versión'
description: La información de la versión más reciente de [!DNL Product Recommendations] de Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 316059288ace6ebaf3748a294d8fe7351fc63bbd
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# [!DNL Product Recommendations] Notas de versión

Las notas de la versión contienen actualizaciones de lo siguiente [!DNL Product Recommendations] módulos:

* [!DNL Product Recommendations] metapaquete: `magento/product-recommendations`
* Compatibilidad con Page Builder en [!DNL Product Recommendations] módulo (opcional): `magento/module-page-builder-product-recommendations`
* Compatibilidad de tipo de recomendación de similitud visual para [!DNL Product Recommendations] módulo (opcional): `magento/module-visual-product-recommendations`

Se proporciona soporte para la versión publicada principal actual. Las notas de la versión de las versiones anteriores se proporcionan como referencia.
Las notas de la versión incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras
![Error](../assets/bug.svg) Problemas conocidos

Consulte la documentación para desarrolladores para [obtener más información sobre soporte del producto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Actualizaciones de servicios alojados

Estas notas describen las actualizaciones que se publicaron fuera de una versión con versiones o las mejoras realizadas en el servicio alojado.

+++Actualizaciones de servicios alojados

_18 de julio de 2023_

![Nuevo](../assets/new.svg) [!DNL Product Recommendations] ahora tiene un GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) consulta.

_25 de abril de 2023_

![Nuevo](../assets/new.svg) [!DNL Product Recommendations] Los clientes de ahora pueden aprovechar [Indexación de precios de SaaS](../price-index/price-indexing.md).

+++

## Versión principal actual

### 6.0.2 de magento/product-recommendations

_9 de mayo de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido un problema que causaba que al hacer clic en **[!DNL Add to Cart]** Un botón de un producto simple dentro de una unidad de Product Recommendations redirigía al comprador a la página de inicio en lugar de permanecer en la página actual.

### Versiones anteriores

### 6.0.1 de magento/product-recommendations

_19 de marzo de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con PHP 8.3.

### 6.0.0 de magento/product-recommendations

_22 de febrero de 2024_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) El [!DNL Catalog Sync Dashboard] es ahora el [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Este tablero reformado proporciona perspectivas sobre los flujos de datos para [!DNL Product Recommendations], [!DNL Live Search], y [!DNL Catalog Service].
![Fix](../assets/fix.svg) Se ha corregido un problema que provocaba errores de cierre de compra para [!DNL Product Recommendations].

+++5.0.0 y anteriores

### 5.0.1 de magento/product-recommendations

_15 de septiembre de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se han añadido nuevos módulos para admitir el [Indexador De Precios Saas](../price-index/price-indexing.md).
![Nuevo](../assets/new.svg) Se han añadido nuevos módulos de exportación de datos para admitir la exportación de más tipos de productos, incluidos productos agrupados y tarjetas regalo.
![Fix](../assets/fix.svg) El tamaño de la tabla de los productos y las fuentes de precios se han reducido considerablemente. Tablas `catalog_data_exporter_products` y `catalog_data_exporter_product_prices` debería ver una reducción sustancial de tamaño.

#### Limitaciones conocidas

* El `websiteCode` se devuelve incorrectamente si contiene un guion bajo (_).

### 5.0.0 de magento/product-recommendations

_20 de marzo de 2023_

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Actualizado [!DNL Product Recommendations] para admitir Adobe Commerce 2.4.6.
![Nuevo](../assets/new.svg) Esta es una versión principal. [Editar](install-configure.md#update) la raíz `composer.json` para su proyecto.
![Nuevo](../assets/new.svg) [!DNL Product Recommendations] ahora admite full [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) en Commerce (anteriormente conocido como Inventario de varias fuentes o MSI). Para habilitar la compatibilidad total, debe [actualizar](install-configure.md#update) el módulo de dependencia `commerce-data-export` a la versión 102.2.0+.

### 4.0.1 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Anteriormente, [!DNL Product Recommendations] mostraría un error cuando la moneda de visualización se cambiara a una moneda no predeterminada. El cambio de moneda ahora funciona correctamente.

### 4.0.0 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Añadido [indicadores de disponibilidad](create.md) para ayudarle a visualizar el progreso de formación de cada tipo de recomendación.
![Nuevo](../assets/new.svg) Esta es una versión principal. [Editar](install-configure.md#update) la raíz `composer.json` para su proyecto. Esta versión también requiere que proporcione dos claves de API al instalar y configurar [!DNL Product Recommendations]: [una clave de producción y una clave de zona protegida](../landing/saas.md).

#### Limitaciones conocidas

* El `websiteCode` se devuelve incorrectamente si contiene un guion bajo (_).

### 3.3.7 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido compatibilidad con PHP 8.1
![Nuevo](../assets/new.svg) Se ha mejorado el cambio de tamaño de las imágenes para que el tamaño se gestione de forma más coherente en la plantilla de visualización de referencia

### 3.3.6 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Optimizado [!DNL Product Recommendations] metapaquete enumerando explícitamente las dependencias

### 3.3.5 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Añadido [Compatibilidad con B2B](onboarding.md#b2bsupport) in [!DNL Product Recommendations]
![Nuevo](../assets/new.svg) Se han añadido nuevas fuentes a [sincronizar datos de catálogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) a Commerce Services a través de la línea de comandos

### 3.3.3 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Añadido nuevo [tipos de recomendación](type.md): conversión (ver al carro de compras), conversión (ver a compra) y visualizados recientemente. Estos nuevos tipos de recomendación están disponibles en la variable `magento/product-recommendations` módulo 3.2.2 y posterior.
![Fix](../assets/fix.svg) Se ha corregido un problema en el cual el cortafuegos de aplicaciones web (WAF) de Fastly bloqueaba incorrectamente una cookie
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual los productos asignados a la vista de tienda no predeterminada no se mostraban en la _Previsualización de producto de Recommendations_ al crear una recomendación para esa vista de tienda específica
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual algunos nombres de unidades de recomendación en Page Builder impedían que la unidad de recomendación se mostrara en la tienda

### 3.3.2 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido la falta de dependencia para la compatibilidad con B2B

### 3.3.1 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido compatibilidad con los precios de grupo de clientes B2B. Cuando se establece un [filtro de precios](filters.md) en una unidad de recomendación, los clientes B2B que iniciaron sesión ven el conjunto de precios del grupo de clientes para los productos mostrados.

### 3.3.0 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con la capa de datos del cliente de Adobe para estandarizar la recopilación de datos de comportamiento en todas las funciones y servicios de Adobe Commerce. Consulte la [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) para obtener más información.

### 3.2.6 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido un error modal de JavaScript
![Fix](../assets/fix.svg) Se ha corregido un problema en el cual el cortafuegos de aplicaciones web (WAF) de Fastly bloqueaba incorrectamente una cookie

### 3.2.5 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se cambió el nombre de Servicios de Magento a [Servicios de Commerce](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) y una usabilidad mejorada en el administrador

### 3.2.4 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de producto configurables&quot; al indexar atributos de producto

### 3.2.3 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de productos configurables&quot; durante la sincronización de catálogos
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual el código de tienda no se establecía correctamente cuando habilitaba la configuración &quot;Añadir código de tienda a la URL&quot;
![Fix](../assets/fix.svg) Se ha mejorado la detección de los cambios de configuración del Panel de administración para garantizar que estos cambios se reflejen en los datos de sincronización de catálogos

### 3.2.2 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [previsualizar resultados de recomendaciones](create.md) en tiempo de creación. Esto puede requerir que actualice el módulo a la versión más reciente.
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [supervisar y administrar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) el proceso de sincronización del catálogo desde Admin.
![Nuevo](../assets/new.svg) Añadido [filtros](filters.md) para controlar qué productos se muestran en recommendations.
![Nuevo](../assets/new.svg) Se ha añadido la [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.2.1 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con la versión 3.2.0 o posterior de `magento/product-recommendations` módulo

### 3.1.0 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [resincronizar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) su catálogo a los servicios SaaS a través de la línea de comandos.
![Nuevo](../assets/new.svg) Se agregó compatibilidad con prefijos de tabla de base de datos
![Fix](../assets/fix.svg) Se ha eliminado la compatibilidad con PHP 7.1

### 3.0.8 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido un problema por el cual se enviaban eventos para la recopilación de datos antes de configurar el módulo, lo que provocaba un tráfico no válido

### 3.0.6 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) **(Beta)** Incluye soporte para nuevas [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.0.0 de magento/module-visual-product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) **(Beta)** [Similitud visual](type.md#visualsim). Con el _Similitud visual_ tipo de recomendación, puede implementar una unidad de recomendación en la página de detalles del producto que muestre productos visualmente similares al producto que se está viendo.

### 3.0.5 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de las opciones de producto&quot; que se podía producir durante la exportación del catálogo.
![Fix](../assets/fix.svg) El símbolo de moneda en _Ingresos_ en la columna _[!DNL Product Recommendations]_ahora, el panel refleja correctamente la moneda base configurada.

### 3.0.4 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Se ha agregado compatibilidad con Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Fix](../assets/fix.svg) Implementación de símbolos mejorada en la plantilla de tienda

### 1.0.4 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido un nombre de Recomendación de producto al editar el tipo de contenido de Page Builder

### 3.0.2 magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Se ha añadido una columna de estado en la cuadrícula al seleccionar Unidades de recomendación en Page Builder
![Fix](../assets/fix.svg) Se ha corregido un problema con los protocolos http/https incorrectos en las direcciones URL de productos e imágenes

### 3.0.1 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

Esta es una versión principal. [Editar](install-configure.md#update) el archivo root composer.json del proyecto.

![Nuevo](../assets/new.svg) Buscar [!DNL Product Recommendations] en Espacios de datos SaaS alternativos. Esto le permite utilizar [!DNL Product Recommendations] se calculan en el entorno de producto en otros entornos que no sean de producción. [Cambio de espacios de datos SaaS](settings.md) describe más adelante esta función.

![Fix](../assets/fix.svg) Se ha corregido un problema que impedía el cierre de compra a los compradores que usaban uBlock Origin
![Fix](../assets/fix.svg) Se ha corregido un problema que enviaba eventos de complementos al carro de compras superfluos

### 1.0.3 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Compatibilidad con Page Builder. Con la integración de Page Builder, puede colocar unidades de Recommendations de forma precisa y granular en cualquier ubicación arbitraria del contenido creado por Page Builder. También puede aplicar estilo a los encabezados y a las unidades de recomendación. Ir a [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) para obtener más información.

### 2.0.0 de magento/product-recommendations

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/new.svg) Lanzamiento de disponibilidad general.

+++

## Documentación

Para obtener más información acerca de [!DNL Product Recommendations] y [!DNL Product Recommendations] desarrollo:

* [Guía del usuario](overview.md)
* [Documentación para desarrolladores](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
