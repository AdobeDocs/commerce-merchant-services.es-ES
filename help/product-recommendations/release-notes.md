---
title: '[!DNL Product Recommendations] Notas de la versión'
description: La información de la versión más reciente de [!DNL Product Recommendations] de Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 40cf5c5dc6242b5efe3822b9c574fe5b219cfcd8
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 0%

---

# [!DNL Product Recommendations] Notas de versión

Las notas de la versión contienen actualizaciones de lo siguiente [!DNL Product Recommendations] módulos:

* [!DNL Product Recommendations] metapaquete: `magento/product-recommendations`
* Compatibilidad con Page Builder en [!DNL Product Recommendations] módulo (opcional): `magento/module-page-builder-product-recommendations`
* Compatibilidad de tipo de recomendación de similitud visual para [!DNL Product Recommendations] módulo (opcional): `magento/module-visual-product-recommendations`

Las notas de la versión incluyen:

![Nuevo](../assets/new.svg) Nuevas funciones
![Fix](../assets/fix.svg) Correcciones y mejoras

Consulte la documentación para desarrolladores para [obtenga información acerca de la compatibilidad del producto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Versión principal actual

### 4.0.1 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Anteriormente, Product Recommendations mostraba un error cuando la moneda de visualización se cambiaba a una moneda no predeterminada. El cambio de moneda ahora funciona correctamente.

### 4.0.0 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Añadido [indicadores de disponibilidad](create.md) para ayudarle a visualizar el progreso de formación de cada tipo de recomendación.
![Nuevo](../assets/new.svg) Esta es una versión principal. [Editar](install-configure.md#update) la raíz `composer.json` para su proyecto. Esta versión también requiere que proporcione dos claves de API al instalar y configurar Product Recommendations: [una clave de producción y una clave de zona protegida](../landing/saas.md).

#### Limitaciones conocidas

* El `websiteCode` se devuelve incorrectamente si contiene un guion bajo (_).

### Versiones anteriores

+++3.3.7 y anteriores

### 3.3.7 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido compatibilidad con PHP 8.1
![Nuevo](../assets/new.svg) Se ha mejorado el cambio de tamaño de las imágenes para que el tamaño se gestione de forma más coherente en la plantilla de visualización de referencia

### 3.3.6 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Optimizado [!DNL Product Recommendations] metapaquete enumerando explícitamente las dependencias

### 3.3.5 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Añadido [Compatibilidad con B2B](onboarding.md#b2bsupport) en Product Recommendations
![Nuevo](../assets/new.svg) Se han añadido nuevas fuentes a [sincronizar datos de catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) a Commerce Services a través de la línea de comandos

### 3.3.3 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Añadido nuevo [tipos de recomendación](type.md): conversión (ver al carro de compras), conversión (ver a compra) y visualizados recientemente. Estos nuevos tipos de recomendación están disponibles en la variable `magento/product-recommendations` módulo 3.2.2 y posterior.
![Fix](../assets/fix.svg) Se ha corregido un problema en el cual el cortafuegos de aplicaciones web (WAF) de Fastly bloqueaba incorrectamente una cookie
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual los productos asignados a la vista de tienda no predeterminada no se mostraban en la _Previsualización de producto de Recommendations_ al crear una recomendación para esa vista de tienda específica
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual algunos nombres de unidades de recomendación en Page Builder impedían que la unidad de recomendación se mostrara en la tienda

### 3.3.2 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido la falta de dependencia para la compatibilidad con B2B

### 3.3.1 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido compatibilidad con los precios de grupo de clientes B2B. Cuando se establece un [filtro de precios](filters.md) en una unidad de recomendación, los clientes B2B que iniciaron sesión ven el conjunto de precios del grupo de clientes para los productos mostrados.

### 3.3.0 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con la capa de datos del cliente de Adobe para estandarizar la recopilación de datos de comportamiento en todas las funciones y servicios de Adobe Commerce. Consulte la [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) para obtener más información.

### 3.2.6 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido un error modal de JavaScript
![Fix](../assets/fix.svg) Se ha corregido un problema en el cual el cortafuegos de aplicaciones web (WAF) de Fastly bloqueaba incorrectamente una cookie

### 3.2.5 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se cambió el nombre de Servicios de Magento a [Servicios de Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) y una usabilidad mejorada en el administrador

### 3.2.4 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de producto configurables&quot; al indexar atributos de producto

### 3.2.3 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de opciones de productos configurables&quot; durante la sincronización de catálogos
![Fix](../assets/fix.svg) Se ha corregido un problema por el cual el código de tienda no se establecía correctamente cuando habilitaba la configuración &quot;Añadir código de tienda a la URL&quot;
![Fix](../assets/fix.svg) Se ha mejorado la detección de los cambios de configuración del Panel de administración para garantizar que estos cambios se reflejen en los datos de sincronización de catálogos

### 3.2.2 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [previsualizar resultados de recomendaciones](create.md) en tiempo de creación. Esto puede requerir que actualice el módulo a la versión más reciente.
![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [supervisar y administrar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) el proceso de sincronización del catálogo desde Admin.
![Nuevo](../assets/new.svg) Añadido [filtros](filters.md) para controlar qué productos se muestran en recommendations.
![Nuevo](../assets/new.svg) Se ha añadido la [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.2.1 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha agregado compatibilidad con la versión 3.2.0 o posterior de `magento/product-recommendations` módulo

### 3.1.0 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido la capacidad de [resincronizar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) su catálogo a los servicios SaaS a través de la línea de comandos.
![Nuevo](../assets/new.svg) Se agregó compatibilidad con prefijos de tabla de base de datos
![Fix](../assets/fix.svg) Se ha eliminado la compatibilidad con PHP 7.1

### 3.0.8 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido un problema por el cual se enviaban eventos para la recopilación de datos antes de configurar el módulo, lo que provocaba un tráfico no válido

### 3.0.6 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) **(Beta)** Incluye soporte para nuevas [Similitud visual](type.md#visualsim) tipo de recomendación.

### 1.0.0 de magento/module-visual-product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) **(Beta)** [Similitud visual](type.md#visualsim). Con el _Similitud visual_ tipo de recomendación, puede implementar una unidad de recomendación en la página de detalles del producto que muestre productos visualmente similares al producto que se está viendo.

### 3.0.5 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha corregido el error &quot;No se pueden recuperar los datos de las opciones de producto&quot; que se podía producir durante la exportación del catálogo.
![Fix](../assets/fix.svg) El símbolo de moneda en _Ingresos_ en la columna _Product Recommendations_ ahora, el panel refleja correctamente la moneda base configurada.

### 3.0.4 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Se ha agregado compatibilidad con Adobe Commerce 2.4.0

### 3.0.3 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Fix](../assets/fix.svg) Implementación de símbolos mejorada en la plantilla de tienda

### 1.0.4 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido un nombre de Recomendación de producto al editar el tipo de contenido de Page Builder

### 3.0.2 magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Se ha añadido una columna de estado en la cuadrícula al seleccionar Unidades de recomendación en Page Builder
![Fix](../assets/fix.svg) Se ha corregido un problema con los protocolos http/https incorrectos en las direcciones URL de productos e imágenes

### 3.0.1 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

Esta es una versión principal. [Editar](install-configure.md#update) el archivo root composer.json del proyecto.

![Nuevo](../assets/new.svg) Buscar [!DNL Product Recommendations] en Espacios de datos SaaS alternativos. Esto le permite utilizar recomendaciones de productos calculadas en su entorno de productos en otros entornos que no sean de producción. [Cambio de espacios de datos SaaS](settings.md) describe más adelante esta función.

![Fix](../assets/fix.svg) Se ha corregido un problema que impedía el cierre de compra a los compradores que usaban uBlock Origin
![Fix](../assets/fix.svg) Se ha corregido un problema que enviaba eventos de complementos al carro de compras superfluos

### 1.0.3 de magento/module-page-builder-product-recommendations para Page Builder

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Compatibilidad con Page Builder. Con la integración de Page Builder, puede colocar unidades de Recommendations de forma precisa y granular en cualquier ubicación arbitraria del contenido creado por Page Builder. También puede aplicar estilo a los encabezados y a las unidades de recomendación. Ir a [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) para obtener más información.

### 2.0.0 de magento/product-recommendations

[!BADGE Compatibilidad]{type=Informative tooltip="Compatibilidad"}

![Nuevo](../assets/new.svg) Lanzamiento de disponibilidad general.

+++

## Documentación

Para obtener más información acerca de [!DNL Product Recommendations] y [!DNL Product Recommendations] desarrollo:

* [Guía del usuario](overview.md)
* [Documentación para desarrolladores](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
