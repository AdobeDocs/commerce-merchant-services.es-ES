---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] para Adobe Commerce proporciona una forma de recuperar el contenido de las páginas para mostrar de productos y de las páginas de listas de productos mucho más rápido que las consultas nativas de Adobe Commerce GraphQL."'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
recommendations: noCatalog
source-git-commit: 8e349cb8cfba7c4d828a6f3666a3b27fecfdbd15
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# [!DNL Catalog Service] para Adobe Commerce

El [!DNL Catalog Service] para Adobe Commerce, la extensión proporciona datos de catálogo de modelo de vista enriquecidos (solo lectura) para procesar rápida y completamente experiencias de tienda relacionadas con el producto, incluidas las siguientes:

* Páginas de detalles del producto
* Páginas de lista y categoría de productos
* Páginas de resultados de búsqueda
* Carruseles de productos
* Páginas de comparación de productos
* Cualquier otra página que procese datos de producto, como páginas de carro de compras, pedidos y listas de deseos

El [!DNL Catalog Service] utiliza [GraphQL](https://graphql.org/) para solicitar y recibir datos de productos. GraphQL es un lenguaje de consulta que un cliente de front-end utiliza para comunicarse con la interfaz de programación de aplicaciones (API) definida en un back-end como Adobe Commerce. GraphQL es un método de comunicación popular porque es ligero y permite al integrador de sistemas especificar el contenido y el orden de cada respuesta.

Adobe Commerce tiene dos sistemas GraphQL. El sistema principal de GraphQL proporciona una amplia gama de consultas (operaciones de lectura) y mutaciones (operaciones de escritura) que permiten a un comprador interactuar con muchos tipos de páginas, incluidos productos, cuentas de clientes, carros de compras, cierres de compra y mucho más. Sin embargo, las consultas que devuelven información del producto no están optimizadas para la velocidad. El sistema de GraphQL de servicios solo puede realizar consultas en productos e información relacionada. Estas consultas tienen un mayor rendimiento que las consultas principales similares.

Los clientes del servicio de catálogo pueden usar el nuevo [Indexador de precios SaaS](../price-index/index.md), que ofrece actualizaciones de precios y tiempos de sincronización más rápidos.

## Arquitectura

El diagrama siguiente muestra los dos sistemas de GraphQL:

![Diagrama de arquitectura de catálogo](assets/catalog-service-architecture.png)

En el sistema principal de GraphQL, el PWA envía una solicitud a la aplicación de comercio, que recibe cada solicitud, la procesa, posiblemente enviando una solicitud a través de varios subsistemas y, a continuación, devuelve una respuesta a la tienda. Este recorrido de ida y vuelta puede causar tiempos de carga de página lentos, lo que potencialmente conduce a tasas de conversión más bajas.

[!DNL Catalog Service] es una puerta de enlace de Storefront Services. El servicio accede a una base de datos independiente que contiene detalles del producto e información relacionada, como atributos del producto, variantes, precios y categorías. El servicio mantiene la base de datos sincronizada con Adobe Commerce mediante la indexación.
Dado que el servicio evita la comunicación directa con la aplicación, puede reducir la latencia del ciclo de solicitud y respuesta.

Los sistemas GraphQL principales y de servicio no se comunican directamente entre sí. Puede acceder a cada sistema desde una dirección URL diferente y las llamadas requieren información de encabezado diferente. Los dos sistemas GraphQL están diseñados para utilizarse juntos. El [!DNL Catalog Service] El sistema de GraphQL aumenta el sistema principal para que las experiencias de tienda de productos sean más rápidas.

Si lo desea, puede implementar [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/) para integrar los dos sistemas Adobe Commerce GraphQL con API privadas y de terceros y otras interfaces de software mediante Adobe Developer. La malla se puede configurar para garantizar que las llamadas enrutadas a cada extremo contengan la información de autorización correcta en los encabezados.

## Detalles arquitectónicos

En las secciones siguientes se describen algunas de las diferencias entre los dos sistemas de GraphQL.

### Administración de esquemas

Dado que el Servicio de catálogo funciona como un servicio, los integradores no necesitan preocuparse por la versión subyacente de Commerce. La sintaxis de las consultas es la misma para todas las versiones. Además, el esquema es coherente para todos los comerciantes. Esta coherencia facilita la definición de prácticas recomendadas y aumenta significativamente la reutilización de los widgets de tienda.

### Simplificación de los tipos de productos

El esquema reduce la diversidad de tipos de productos a dos casos de uso:

* Los productos simples son aquellos que se definen con un único precio y cantidad. El servicio de catálogo asigna los tipos de producto simples, virtuales, descargables y de tarjeta regalo a `simpleProductViews`.

* Los productos complejos están compuestos por múltiples productos simples. Los productos simples de componente pueden tener precios diferentes. También se puede definir un producto complejo para que el comprador pueda especificar la cantidad de productos simples componentes. El servicio de catálogo asigna los tipos de producto configurables, paquetes y agrupados a `complexProductViews`.

Las opciones de producto complejas están unificadas y se distinguen por su comportamiento, no por su tipo. Cada valor de opción representa un producto simple. Este valor de opción tiene acceso a los atributos de producto simples, incluido el precio. Cuando el comprador selecciona todas las opciones de un producto complejo, la combinación de opciones seleccionadas apunta a un producto simple específico. El producto simple sigue siendo ambiguo hasta que el comprador selecciona un valor para todas las opciones disponibles.

### Precios

Los productos simples representan la unidad de venta base que tiene un precio. El servicio de catálogo calcula el precio normal antes de los descuentos, así como el precio final después de los descuentos. Los cálculos de precios pueden incluir impuestos de productos fijos. Excluyen las promociones personalizadas.

Un producto complejo no tiene un precio establecido. En su lugar, el servicio de catálogo devuelve los precios de las simples vinculadas. Por ejemplo, un comerciante puede asignar inicialmente los mismos precios a todas las variantes de un producto configurable. Si ciertos tamaños o colores son impopulares, el comerciante puede reducir los precios de esas variantes. Por lo tanto, el precio del producto complejo (configurable) al principio muestra un rango de precios, que refleja el precio de las variantes estándar y las impopulares. Una vez que el comprador ha seleccionado un valor para todas las opciones disponibles, la tienda muestra un solo precio.

>[!NOTE]
>
> Clientes de Commerce con [!DNL Catalog Service] puede aprovechar las actualizaciones más rápidas de los cambios de precios y el tiempo de sincronización en sus sitios web con el [Indexador de precios SaaS](../price-index/index.md).

## Implementación

El proceso de instalación requiere la configuración del [Conector de Commerce Services](../landing/saas.md). Una vez hecho esto, el siguiente paso es que un integrador de sistemas actualice el código de la tienda para incorporar el [!DNL Catalog Service] consultas. Todo [!DNL Catalog Service] las consultas se dirigen a la puerta de enlace de GraphQL. La dirección URL se proporciona durante el proceso de incorporación.
