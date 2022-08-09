---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] para Adobe Commerce proporciona una forma de recuperar el contenido de las páginas de visualización de productos y de las páginas de listas de productos mucho más rápido que las consultas nativas de Adobe Commerce GraphQL."'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# [!DNL Catalog Service] para Adobe Commerce

{{catalog-service-beta}}

La variable [!DNL Catalog Service] para la extensión de Adobe Commerce, proporciona datos de catálogo de modelo de vista enriquecido (solo lectura) para procesar rápida y completamente experiencias de tienda relacionadas con el producto, que incluyen:

* Páginas de detalles del producto
* Páginas de lista y categoría de productos
* Páginas de resultados de búsqueda
* Carruseles de producto
* Páginas de comparación de productos
* Cualquier otra página que represente datos del producto, como las páginas de carro, pedido y lista de deseos

La variable [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) para solicitar y recibir datos del producto. GraphQL es un lenguaje de consulta que un cliente de front-end utiliza para comunicarse con la interfaz de programación de aplicaciones (API) definida en un servidor como Adobe Commerce. GraphQL es un método de comunicación popular porque es ligero y permite que un integrador de sistemas especifique el contenido y el orden de cada respuesta.

Adobe Commerce tiene dos sistemas GraphQL. El sistema principal de GraphQL proporciona una amplia gama de consultas (operaciones de lectura) y mutaciones (operaciones de escritura) que permiten que un comprador interactúe con muchos tipos de páginas, incluidos productos, cuentas de cliente, carro de compras, cierre de compra, etc. Sin embargo, las consultas que devuelven información del producto no están optimizadas para la velocidad. El sistema de servicios GraphQL solo puede realizar consultas sobre productos e información relacionada. Estas consultas tienen un mayor rendimiento que las consultas principales similares.

## Arquitectura

En el diagrama siguiente se muestran los dos sistemas GraphQL:

![Diagrama de arquitectura del catálogo](assets/catalog-service-architecture.png)

En el sistema principal de GraphQL, el PWA envía una solicitud a la aplicación Commerce, que recibe cada solicitud, la procesa, posiblemente enviando una solicitud a través de varios subsistemas y, a continuación, devuelve una respuesta a la tienda. Este viaje de ida y vuelta puede causar tiempos de carga de página lentos, lo que puede provocar tasas de conversión más bajas.

[!DNL Catalog Service] envía consultas a una puerta de enlace de GraphQL independiente. El servicio accede a una base de datos independiente que contiene detalles del producto e información relacionada, como atributos del producto, variantes, precios y categorías. El servicio mantiene la base de datos sincronizada con Adobe Commerce mediante la indexación.
Dado que el servicio evita la comunicación directa con la aplicación, puede reducir la latencia del ciclo de solicitud y respuesta.

>[!NOTE]
>
>La puerta de enlace es para una futura integración con [!DNL Live Search] y [!DNL Product Recommendations]. En esta versión puede acceder a [!DNL Catalog Service] y las consultas de búsqueda activa desde el mismo punto final, si tiene una clave de licencia válida para ambos productos. Sin embargo, las consultas de los dos productos no comparten actualmente ningún dato de respuesta.

Los sistemas principal y de servicio de GraphQL no se comunican directamente entre sí. Puede acceder a cada sistema desde una dirección URL diferente y las llamadas requieren información de encabezado diferente. Los dos sistemas GraphQL están diseñados para utilizarse juntos. La variable [!DNL Catalog Service] El sistema GraphQL aumenta el sistema principal para que las experiencias de tienda de productos sean más rápidas.

Si lo desea, puede implementar [Mesh de API para Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) para integrar los dos sistemas Adobe Commerce GraphQL con API privadas y de terceros y otras interfaces de software mediante Adobe Developer. La red se puede configurar para garantizar que las llamadas enrutadas a cada extremo contengan la información de autorización correcta en los encabezados.

## Implementación

El proceso de instalación requiere la configuración del [Conector de Commerce Services](../landing/saas.md). Una vez hecho esto, el siguiente paso es que un integrador de sistemas actualice el código de tienda para incorporar la variable [!DNL Catalog Service] consultas. Todo [!DNL Catalog Service] las consultas se dirigen a la puerta de enlace de GraphQL. La dirección URL se proporciona durante el proceso de incorporación.

[Dispositivos Adobe Commerce](https://devdocs.magento.com/catalog-service/index.html) describe las diferencias entre el núcleo y [!DNL Catalog Service] consultas. También se incluye información de referencia para cada consulta.
