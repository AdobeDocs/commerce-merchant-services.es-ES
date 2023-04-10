---
title: Eventos
description: Descubra qué datos captura cada evento.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 8e5fb65363b2fa39f44da86d7ba0cc5459b18768
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Eventos de conector de Experience Platform

A continuación se enumeran los eventos de comercio disponibles al instalar la extensión del conector del Experience Platform. Los datos que recopilan estos eventos se envían al perímetro de Adobe Experience Platform. También puede crear [eventos personalizados](custom-events.md) para recopilar datos adicionales no proporcionados de forma predeterminada.

Además de los datos que recopilan los eventos siguientes, también obtiene [otros datos](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) proporcionado por el SDK web de Adobe Experience Platform.

## Eventos de tienda

Los eventos de tienda recopilan datos de comportamiento anónimos de sus compradores a medida que navegan por su sitio. Los datos que recopilan estos eventos se pueden utilizar para crear promociones y campañas dirigidas a un conjunto específico de compradores.

>[!NOTE]
>
>Todos los eventos de tienda incluyen el [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que incluye la dirección de correo electrónico del comprador, cuando está disponible, y ECID. Al incluir estos datos de perfil en cada evento, no es necesario importar una cuenta de usuario de Adobe Commerce por separado.

### addToCart

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se agrega un producto al carro de compras o cuando se incrementa la cantidad de un producto en el carro de compras. | `commerce.productListAdds` |

#### Datos recopilados de addToCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListAdds` | Indica si un producto se agregó a un carro de compras. Un valor de `1` indica que se agregó un producto. |
| `productListItems` | Una matriz de productos agregados al carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto agregadas al carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | ID exclusivo que identifica el carro de compras del cliente |

### openCart

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se crea un nuevo carro de compras, que es cuando se agrega un producto a un carro vacío. | `commerce.productListOpens` |

#### Datos recopilados de openCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListOpens` | Indica si se creó un carro de compras. Un valor de `1` indica que se creó un carro de compras. |
| `productListItems` | Una matriz de productos agregados al carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto agregadas al carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | ID exclusivo que identifica el carro de compras del cliente |

### removeFromCart

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cada vez que se elimina un producto o cada vez que se reduce la cantidad de un producto en el carro de compras. | `commerce.productListRemovals` |

#### Datos recopilados de removeFromCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListRemovals` | Indica si un producto se eliminó del carro de compras. Un valor de `1` indica que un producto se eliminó del carro de compras. |
| `productListItems` | Una matriz de productos eliminados del carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto eliminadas del carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | ID exclusivo que identifica el carro de compras del cliente |

### shoppingCartView

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se carga cualquier página del carro de compras. | `commerce.productListViews` |

#### Datos recopilados de shoppingCartView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListViews` | Indica si se ha visto una lista de productos |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | ID exclusivo que identifica el carro de compras del cliente |

### pageView

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se carga cualquier página. | `web.webpagedetails.pageViews` |

#### Datos recopilados de pageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `pageViews` | Indica si se cargó una página. A `value` de `1` indica que la página se ha cargado. |

### productPageView

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se carga cualquier página de producto. | `commerce.productViews` |

#### Datos recopilados de productPageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productViews` | Indica si se vio el producto |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

### startCheckout

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando el comprador hace clic en un botón de cierre de compra. | `commerce.checkouts` |

#### Datos recopilados de startCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `checkouts` | Indica si se produjo una acción durante el proceso de cierre de compra |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda para el producto |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | ID exclusivo que identifica el carro de compras del cliente |

### completeCheckout

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando el comprador realiza un pedido. | `commerce.order` |

#### Datos recopilados de completeCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `purchases` | Indica si se ha aceptado un pedido |
| `order` | Contiene información sobre el pedido realizado para uno o más productos |
| `purchaseID` | Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único. |
| `orderType` | Indica el tipo de pedido que se realizó, como Cierre de compra o Compra instantánea |
| `payments` | La lista de pagos para este pedido |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago. Por ejemplo, `USD` o `EUR`. |
| `paymentAmount` | El valor del pago |
| `paymentType` | Método de pago para esta orden. Las opciones son: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | Identificador de transacción único para esta partida de pago |
| `shipping` | Detalles de envío de uno o más productos. |
| `shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en la tienda, etc. |
| `shippingAmount` | El coste total de envío de los artículos del carro de compras |
| `promotionID` | Identificador único de la promoción, si lo hay |
| `personalEmail` | Especifica la dirección de correo electrónico personal |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y en las normas posteriores |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moneda utilizado para los totales de pedidos. |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

## Eventos de perfil

Los eventos de perfil incluyen información de la cuenta, como `signIn`, `signOut`, `createAccount`y `editAccount`. Estos datos se utilizan para ayudar a rellenar los detalles clave del cliente que son necesarios para definir mejor los segmentos o ejecutar campañas de marketing, como si desea dirigirse a compradores que residan en Nueva York.

### signIn

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador intenta iniciar sesión. | `userAccount.login` |

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de signIn

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `eventType` | El tipo de evento principal para este registro de serie temporal, como: `userAccount.login` |
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Captura el ID de cuenta de usuario |
| `personalEmailID` | Especifica el identificador único del correo electrónico personal |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y en las normas posteriores |
| `userAccount` | Indica los detalles de lealtad, las preferencias, los procesos de inicio de sesión y otras preferencias de cuenta |
| `login` | Indica si un visitante ha intentado iniciar sesión |

### signOut

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador intenta cerrar sesión. | `userAccount.logout` |

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de signOut

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `eventType` | El tipo de evento principal para este registro de serie temporal, como: `userAccount.logout` |
| `userAccount` | Indica los detalles de lealtad, las preferencias, los procesos de inicio de sesión y otras preferencias de cuenta |
| `logout` | Indica si un visitante ha intentado cerrar la sesión |

### createAccount

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador intenta crear una cuenta. | `userAccount.createProfile` |

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de createAccount

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `eventType` | El tipo de evento principal para este registro de serie temporal, como: `account.createProfile` |
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Captura el ID de cuenta de usuario |
| `accountType` | Captura el tipo de cuenta de usuario, como `Personal` o `Company`, si procede |
| `personalEmailID` | Especifica el identificador único del correo electrónico personal |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y en las normas posteriores |
| `userAccount` | Indica los detalles de lealtad, las preferencias, los procesos de inicio de sesión y otras preferencias de cuenta |
| `createProfile` | Indica si un usuario ha creado un perfil de cuenta |

### editAccount

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador intenta editar una cuenta. | `userAccount.updateProfile` |

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de editAccount

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `eventType` | El tipo de evento principal para este registro de serie temporal, como: `account.updateProfile` |
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Captura el ID de cuenta de usuario |
| `accountType` | Captura el tipo de cuenta de usuario, como `Personal` o `Company`, si procede |
| `personalEmailID` | Especifica el identificador único del correo electrónico personal |
| `personalEmail` | Especifica la dirección de correo electrónico personal |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y en las normas posteriores |
| `userAccount` | Indica los detalles de lealtad, las preferencias, los procesos de inicio de sesión y otras preferencias de cuenta |
| `updateProfile` | Indica si un usuario ha actualizado su perfil de cuenta |

## Eventos de búsqueda

Los eventos de búsqueda proporcionan datos relevantes para la intención del comprador. La perspectiva de la intención de un comprador ayuda a los comerciantes a ver cómo los compradores están buscando artículos, en qué hacen clic y, en última instancia, compran o abandonan. Un ejemplo de cómo utilizar estos datos es si desea dirigirse a compradores existentes que busquen el producto principal pero que nunca compren el producto principal.

Utilice la variable `uniqueIdentifier` campo encontrado en las dos `searchRequestSent` y `searchResponseReceived` para hacer referencia cruzada a una solicitud de búsqueda con la respuesta de búsqueda correspondiente.

### searchRequestSent

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa mediante los siguientes eventos en la ventana emergente &quot;buscar mientras escribe&quot;:<br><br>Pulse Intro, Haga Clic En _Ver todo_<br><br> Se activa mediante los siguientes eventos en las páginas de resultados de búsqueda:<br><br>Seleccione un filtro, Cambiar el orden (_Ordenar por_), Cambiar la dirección de clasificación (ascendente o descendente), Cambiar el número de resultados por página (_Mostrar # por página_), Vaya a la página siguiente, Vaya a la página anterior, Vaya a una página diferente | `searchRequest` |

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.

#### Datos recopilados de searchRequestSent

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchRequest` | Indica si se ha enviado una solicitud de búsqueda |
| `id` | El ID exclusivo para esta solicitud de búsqueda en particular |
| `filter` | Indica si se aplicaron filtros para limitar los resultados de búsqueda |
| `attribute` (filtro) | La faceta de un elemento que se usa para determinar si se incluye en los resultados de búsqueda |
| `value` | Valores de atributo utilizados para determinar qué elementos se incluyen en los resultados de búsqueda |
| `isRange` | Cuando es verdadero, los valores indican los extremos de un rango aceptable de valores |
| `sort` | Indica cómo se deben ordenar los resultados de la búsqueda |
| `attribute` (ordenar) | Un atributo utilizado para ordenar elementos en los resultados de búsqueda |
| `order` | El orden en el que se devuelven los resultados de la búsqueda |
| `query` | Términos buscados |

### searchResponseReceived

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando la búsqueda activa devuelve resultados para la página de resultados de búsqueda o de pov &quot;search as you type&quot;. | `searchResponse` |

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.

#### Datos recopilados de searchResponseReceived

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchResponse` | Indica si se ha recibido una respuesta de búsqueda |
| `id` | El ID exclusivo para esta respuesta de búsqueda en particular |
| `suggestions` | Matriz de cadenas que incluyen los nombres de productos y categorías que existen en el catálogo y que son similares a la consulta de búsqueda |
| `numberOfResults` | El número de productos devueltos |
| `productListItems` | Una matriz de productos en el carro de compras. |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `productImageUrl` | URL de la imagen principal del producto |

## Eventos B2B

![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe [instalar](install.md#install-the-b2b-extension) el `experience-platform-connector-b2b` para habilitar estos eventos.

Los eventos B2B contienen [lista de solicitudes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) información como, por ejemplo, si se creó, agregó o eliminó una lista de solicitudes. Al rastrear eventos específicos de listas de solicitudes, puede ver qué productos compran sus clientes con frecuencia y crear campañas basadas en esos datos.

### createRequisitionList

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador crea una nueva lista de solicitudes. | `commerce.requisitionListOpens` |

#### Datos recopilados de createRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente |
| `ID` | Identificador único de la lista de solicitudes |
| `name` | Nombre de la lista de solicitudes especificada por el cliente |
| `description` | Descripción de la lista de solicitudes especificada por el cliente |

### addToRequisitionList

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador agrega un producto a una lista de solicitudes existente o cuando crea una lista nueva. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` no es compatible con páginas de vista de categoría o con productos configurables. Se admite en páginas de vistas de productos y para productos simples.

#### Datos recopilados de addToRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente |
| `ID` | Identificador único de la lista de solicitudes |
| `name` | Nombre de la lista de solicitudes especificada por el cliente |
| `description` | Descripción de la lista de solicitudes especificada por el cliente |
| `productListItems` | Conjunto de productos que se agregaron a la lista de solicitudes |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `quantity` | Número de unidades de producto agregadas |
| `priceTotal` | El precio total del artículo de línea de producto |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

### removeFromRequisitionList

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador elimina un producto de una lista de solicitudes. | `commerce.requisitionListRemovals` |

#### Datos recopilados de removeFromRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente |
| `ID` | Identificador único de la lista de solicitudes |
| `name` | Nombre de la lista de solicitudes especificada por el cliente |
| `description` | Descripción de la lista de solicitudes especificada por el cliente |
| `productListItems` | Conjunto de productos que se agregaron a la lista de solicitudes |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `quantity` | Número de unidades de producto agregadas |
| `priceTotal` | El precio total del artículo de línea de producto |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

## Eventos de back office

Los eventos de back office contienen información sobre el estado de un pedido, por ejemplo, si se realizó, canceló, reembolsó, envió o completó un pedido. Los datos que recopilan estos eventos del lado del servidor muestran una vista 360 del pedido del comprador. Esta vista ayuda a los comerciantes a enfocar o analizar mejor el estado de todo el pedido al desarrollar campañas de marketing. Por ejemplo, puede identificar tendencias en ciertas categorías de productos que funcionan bien en diferentes momentos del año. Por ejemplo, ropa de invierno que se vende mejor durante meses más fríos o ciertos colores de producto que los compradores están interesados a lo largo de los años. Además, los datos de estado de los pedidos pueden ayudarle a calcular el valor de cliente de por vida al comprender la propensión de un comprador a realizar la conversión según pedidos anteriores.

>[!NOTE]
>
>Todos los eventos de back office incluyen [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que proporciona la dirección de correo electrónico del comprador. Al incluir estos datos de perfil en cada evento, no es necesario importar una cuenta de usuario de Adobe Commerce por separado.

### orderPlacked

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador realiza un pedido. | `commerce.backofficeOrderPlaced` |

#### Datos recopilados de orderPlacing

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `address` | La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y en las normas posteriores |
| `eventType` | `commerce.backofficeOrderPlaced` |
| `productListItems` | Una matriz de productos en el pedido |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `quantity` | Número de unidades de producto en el carro de compras |
| `priceTotal` | El precio total del artículo de línea de producto |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `order` | Contiene información sobre el pedido |
| `purchaseID` | Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único |
| `purchaseOrderNumber` | Identificador único asignado por el comprador para esta compra o contrato |
| `payments` | La lista de pagos para este pedido |
| `paymentType` | Método de pago para esta orden. Se permiten valores personalizados y enumerados. |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago |
| `paymentAmount` | El valor del pago |
| `taxAmount` | El importe del impuesto pagado por el comprador como parte del pago final |
| `createdDate` | Hora y fecha en que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00` |
| `shipping` | Detalles de envío de uno o más productos |
| `shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en la tienda, etc. |
| `shippingAddress` | Dirección de envío física |
| `street1` | Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle |
| `shippingAmount` | La cantidad que el cliente tuvo que pagar por el envío. |
| `billingAddress` | Dirección postal de facturación |
| `street1` | Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle |
| `street2` | Campo adicional para información a nivel de calle |
| `city` | El nombre de la ciudad |
| `state` | Nombre del estado. Se trata de un campo de forma libre. |
| `postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles para todos los países. En algunos países, esto solo contiene parte del código postal. |
| `country` | Nombre del territorio administrado por el gobierno. distinto de `xdm:countryCode`, se trata de un campo de forma libre que puede tener el nombre del país en cualquier idioma. |

### orderItemsShipped

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando se envía un pedido. | `commerce.backofficeOrderItemsShipped` |

#### Datos recopilados de orderItemsShipped

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y estándares posteriores| |`eventType`|`commerce.backofficeOrderItemsShipped`| |`productListItems`|Una matriz de productos en el pedido| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de mantenimiento de existencias. Identificador único del producto.| |`quantity`|Número de unidades de producto en el carro de compras| |`priceTotal`|El precio total del artículo de línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador para esta compra o contrato| |`payments`|La lista de pagos para este pedido| |`paymentType`|El método de pago de esta orden. Se permiten valores personalizados y enumerados.| |`currencyCode`|El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago| |`paymentAmount`|El valor del pago| |`trackingNumber`|El número de seguimiento proporcionado por el transportista para un envío de artículos de pedido| |`trackingURL`|Dirección URL para rastrear el estado de envío de un artículo de pedido| |`lastUpdatedDate`|La hora en que se actualiza por última vez un registro de pedido concreto en el sistema de comercio| |`shipping`|Detalles de envío de uno o varios productos| |`shippingMethod`|El método de envío elegido por el cliente, como la entrega estándar, la entrega rápida, la recogida en la tienda, etc.| |`shippingAddress`|Dirección física de envío| |`street1`|Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle| |`shippingAmount`|El importe que el cliente tuvo que pagar por el envío.| |`billingAddress`|Dirección postal de facturación| |`street1`|Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle| |`street2`|Campo adicional para información a nivel de calle| |`city`|Nombre de la ciudad| |`state`|El nombre del estado. Se trata de un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles para todos los países. En algunos países, esto solo contiene parte del código postal.| |`country`|Nombre del territorio administrado por el Gobierno. distinto de `xdm:countryCode`, se trata de un campo de forma libre que puede tener el nombre del país en cualquier idioma.|

### orderCancelled

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador cancela un pedido. | `commerce.backofficeOrderCancelled` |

#### Datos recopilados de orderCancelled

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y estándares posteriores| |`eventType`|`commerce.backofficeOrderCancelled`| |`productListItems`|Una matriz de productos en el pedido| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de mantenimiento de existencias. Identificador único del producto.| |`quantity`|Número de unidades de producto en el carro de compras| |`priceTotal`|El precio total del artículo de línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador para esta compra o contrato| |`cancelDate`|La fecha y hora en que un comprador cancela un pedido| |`lastUpdatedDate`|La hora en que se actualiza por última vez un registro de pedido concreto en el sistema de comercio|

### creditMemoEmitido

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador devuelve un elemento en un pedido. | `commerce.backofficeCreditMemoIssued` |

#### Datos recopilados de creditMemoEmitido

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y estándares posteriores| |`eventType`|`commerce.backofficeCreditMemoIssued`| |`productListItems`|Una matriz de productos en el pedido| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador para esta compra o contrato| |`lastUpdatedDate`|La hora en que se actualiza por última vez un registro de pedido concreto en el sistema de comercio|

### orderSendCompleted

| Descripción | Nombre de evento XDM |
|---|---|
| Se activa cuando un comprador devuelve un elemento en un pedido. | `commerce.backofficeOrderShipmentCompleted` |

#### Datos recopilados de orderSendCompleted

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y estándares posteriores| |`eventType`|`commerce.backofficeOrderShipmentCompleted`| |`productListItems`|Una matriz de productos en el pedido| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de mantenimiento de existencias. Identificador único del producto.| |`quantity`|Número de unidades de producto en el carro de compras| |`priceTotal`|El precio total del artículo de línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor para esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador para esta compra o contrato| |`taxAmount`|El importe fiscal pagado por el comprador como parte del pago final.| |`createdDate`|La hora y la fecha en que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00`| |`payments`|La lista de pagos para este pedido| |`paymentType`|El método de pago de esta orden. Se permiten valores personalizados y enumerados.| |`currencyCode`|El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa usado para esta partida de pago| |`paymentAmount`|El valor del pago| |`shipping`|Detalles de envío de uno o varios productos| |`shippingMethod`|El método de envío elegido por el cliente, como la entrega estándar, la entrega rápida, la recogida en la tienda, etc.| |`shippingAddress`|Dirección física de envío| |`street1`|Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle| |`shippingAmount`|El importe que el cliente tuvo que pagar por el envío.| |`personalEmail`|Especifica la dirección de correo electrónico personal| |`address`|La dirección técnica, por ejemplo, `name@domain.com` tal como se define comúnmente en RFC2822 y estándares posteriores| |`billingAddress`|Dirección postal de facturación| |`street1`|Información de nivel de calle principal, número de apartamento, número de calle y nombre de calle| |`street2`|Campo adicional para información a nivel de calle| |`city`|Nombre de la ciudad| |`state`|El nombre del estado. Se trata de un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles para todos los países. En algunos países, estos datos solo contienen parte del código postal.| |`country`|Nombre del territorio administrado por el Gobierno. distinto de `xdm:countryCode`, se trata de un campo de forma libre que puede tener el nombre del país en cualquier idioma.|
