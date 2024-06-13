---
title: "Configuración de Live Search"
description: El [!DNL Live Search] workspace se utiliza para configurar, administrar y supervisar el rendimiento de la búsqueda.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Configuración de Live Search

El espacio de trabajo es donde se configura, administra y supervisa el rendimiento de [!DNL Live Search]. El menú de la parte superior proporciona acceso a las herramientas de cada área funcional. Las funciones disponibles reflejan la selección actual del menú.

![Workspace](assets/workspace.png)

## Establecer el ámbito

Inicialmente, la variable [ámbito](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) de todos [!DNL Live Search] La configuración se establece en `Default Store View`. Si su [!DNL Commerce] la instalación incluye varias vistas de tienda, establecer **Ámbito** a la [vista de tienda](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) donde se aplique la configuración de faceta.

## Opciones de menú

| Opción | Descripción |
|--- |--- |
| [Rendimiento](performance.md) | El panel proporciona una perspectiva del rendimiento de búsqueda de productos. |
| [Faceteado](facets.md) | Filtro de alto rendimiento que utiliza varias dimensiones de valores de atributo para restringir los criterios de búsqueda. |
| [Sinónimos](synonyms.md) | Amplíe el alcance de la búsqueda para incluir las palabras que los compradores podrían utilizar para encontrar productos que difieran de los del catálogo. |
| [Buscar comercialización](rules.md) | Dé forma a la experiencia de búsqueda con reglas lógicas que almacenan en déclencheur las acciones programadas. Impulse, entierre, fije u oculte productos para calibrar los resultados de búsqueda y lograr así sus objetivos empresariales. |
| [Comercialización por categorías](category-merch.md) | Aplicar reglas y comercialización inteligente en el nivel de categoría. |
| [GraphQL](graphql.md) | Los desarrolladores que han iniciado sesión en el administrador de su tienda pueden componer y probar consultas con datos de catálogo reales. Para obtener más información, vaya a [Información general de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) en el [!DNL Live Search] documentación para desarrolladores. |
| [Configuración](settings.md) | Determine cómo se agrupan los valores de faceta de precio por intervalo de precio en la tienda y establezca el idioma de indexación. |

## Definir atributos como en los que se puede buscar

Para obtener resultados con objetivos muy precisos, revise el conjunto de [investigable](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) atributos del producto. Para garantizar la relevancia, haga que los atributos solo se puedan buscar si contienen contenido que tenga un significado claro y conciso. Evite utilizar atributos que contengan texto menos preciso y largo, como `description`, que aunque la búsqueda está habilitada de forma predeterminada, puede reducir la precisión de los resultados de búsqueda. Por ejemplo, si una persona busca &quot;pantalones cortos&quot; y hay camisas con una descripción que incluye el término &quot;mangas cortas&quot;, entonces las camisas se incluirán en los resultados de búsqueda.

Para permitir que se puedan buscar los atributos, complete los siguientes pasos:

1. En el Administrador, vaya a **Tiendas** > *Atributo* > **Product**.
1. Seleccione el atributo en el que desea que se puedan realizar búsquedas, como `color`.
1. Seleccionar **Propiedades de tienda** y establecer **Uso en la búsqueda** hasta `yes`.

   ![Workspace](assets/attribute-searchable.png)

[!DNL Live Search] también respeta el [peso](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) de un atributo de producto, tal como se establece en Adobe Commerce. Los atributos con un peso mayor aparecerán más arriba en los resultados de búsqueda.

Siempre se pueden buscar los atributos siguientes:

* `sku`
* `name`
* `categories`

[Facetas](facets.md) son atributos de producto definidos en [!DNL Live Search] para poder filtrar. Puede definir cualquier atributo filtrable como una faceta en [!DNL Live Search], pero hay [límites](boundaries-limits.md) Consultar cuántas facetas se pueden buscar al mismo tiempo.

[Sinónimos](synonyms.md) son términos que puede definir para ayudar a guiar a los usuarios hacia el producto correcto. Los usuarios que buscan pantalones pueden escribir &quot;pantalones&quot; o &quot;pantalones&quot;. Puede establecer sinónimos para que estos términos de búsqueda lleven a los usuarios a los resultados de &quot;pantalones&quot;.

## Ajustes de configuración de Commerce

En la siguiente sección se describen los ajustes de configuración de Commerce admitidos y no admitidos para [!DNL Live Search].

### Valores de configuración admitidos

| Ajuste de configuración de Commerce | Descripción | Compatible con Popover | Admitido por el adaptador |
|---|---|---|---|
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Permitir todos los productos por página | Si se establece en `Yes`, incluye el `ALL` en el control &quot;Mostrar por página&quot;. | Sí. Máx. 500 productos | Sí. Máx. 500 productos |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Longitud mínima de la consulta | Número mínimo de caracteres permitidos en una búsqueda en el catálogo. | Sí | Sí |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Productos por página en la cuadrícula Valores permitidos | Determina el número de productos mostrados en la vista de cuadrícula. | Sí | Sí |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Productos por página en el valor predeterminado de la cuadrícula | Determina el número de productos mostrados por página de forma predeterminada en la vista de cuadrícula. | Sí. Máx. 500 productos | Sí. Máx. 500 productos |
| Tiendas > Configuración > Catálogo > Inventario > Mostrar productos sin existencias | Muestra los productos sin existencias. | Sí con versión 2.0.4 o posterior | Sí con versión 2.0.4 o posterior |
| Tiendas > Configuración > Moneda > Moneda de visualización predeterminada | La divisa principal utilizada para mostrar los precios. | Sí con 3.1.0+ | Sí con 3.1.0+ |
| Tiendas > Configuración > General > Configuración de Divisa > Opciones de Divisa > Divisa Base | La divisa principal utilizada para todas las transacciones de pago en línea. | Sí | Sí |

Los precios de la página Widget de Lista de Productos y de la ventana emergente se convierten a la moneda para mostrar predeterminada mediante las tasas de cambio configuradas.

### Valores de configuración no admitidos

| Ajuste de configuración de Commerce | Descripción | Notas |
|---|---|---|
| Tiendas > Configuración > Catálogo > Tienda > Modo de lista | Determina el formato de la lista de resultados de búsqueda. | Se representa correctamente, pero los eventos no se envían para algunas interacciones de página |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Longitud máxima de la consulta | Número máximo de caracteres permitidos en una búsqueda en el catálogo. | No implementado; los servicios de búsqueda aceptan hasta 255 caracteres |
| Configuración > Ventas > Impuestos > Configuración De Visualización De Precios > Mostrar Precios De Productos En El Catálogo | Determina si los precios de productos publicados en el catálogo incluyen o excluyen impuestos, o muestran dos versiones del precio; una con y otra sin impuestos |  |
| Tiendas > Configuración > Catálogo > Tienda > Lista de productos Ordenar por | Determina el criterio de ordenación de la lista de resultados de búsqueda. | No se aplica al [!DNL Live Search] [Widget de página de lista de productos](plp-styling.md) |

### Términos de búsqueda

[!DNL Live Search] admite [buscar redirecciones de términos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) en implementaciones en las que Adobe Commerce administra el enrutamiento, como en Luma y otros temas basados en php.
