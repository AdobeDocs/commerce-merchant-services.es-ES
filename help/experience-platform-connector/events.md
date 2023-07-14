---
title: Eventos
description: Descubra qué datos captura cada evento.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: e8818893d90f91df5b281905eb6bc30df34723ec
workflow-type: tm+mt
source-wordcount: '4779'
ht-degree: 0%

---

# Eventos del conector del Experience Platform

A continuación, se enumeran los eventos de Commerce disponibles al instalar la extensión del conector de Experience Platform. Los datos que estos eventos recopilan se envían al perímetro de Adobe Experience Platform. También puede crear lo siguiente [eventos personalizados](custom-events.md) para recopilar datos adicionales que no se proporcionen de forma predeterminada.

Además de los datos que recopilan los siguientes eventos, también obtiene lo siguiente [otros datos](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) proporcionadas por el SDK web de Adobe Experience Platform.

## Eventos de tienda

Los eventos de tienda recopilan datos de comportamiento anónimos de sus compradores a medida que navegan por el sitio. Puede utilizar los datos que recopilan estos eventos para crear promociones y campañas dirigidas a un conjunto específico de compradores. Los datos de eventos de tienda solo incluyen productos simples y configurables.

>[!NOTE]
>
>Todos los eventos de tienda incluyen [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que incluye la dirección de correo electrónico del comprador, cuando está disponible, y ECID. Al incluir estos datos de perfil en cada evento, no necesita importar una cuenta de usuario independiente de Adobe Commerce.

### addToCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se añade un producto al carro de compras o cuando se incrementa la cantidad de un producto en el carro de compras. | `commerce.productListAdds` |

#### Datos recopilados de addToCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListAdds` | Indica si se ha añadido un producto a un carro de compras. Un valor de `1` indica que se ha añadido un producto. |
| `productListItems` | Una matriz de productos agregados al carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | El número de unidades de producto agregadas al carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | El ID único que identifica el carro de compras del cliente |

### openCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se crea un carro de compras nuevo, es decir, cuando se agrega un producto a un carro de compras vacío. | `commerce.productListOpens` |

#### Datos recopilados de openCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListOpens` | Indica si se ha creado un carro de compras. Un valor de `1` indica que se creó un carro de compras. |
| `productListItems` | Una matriz de productos agregados al carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | El número de unidades de producto agregadas al carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | El ID único que identifica el carro de compras del cliente |

### removeFromCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cada vez que se elimina un producto o cada vez que se reduce la cantidad de un producto en el carro de compras. | `commerce.productListRemovals` |

#### Datos recopilados de removeFromCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListRemovals` | Indica si un producto se ha eliminado del carro de compras. Un valor de `1` indica que se ha eliminado un producto del carro de compras. |
| `productListItems` | Una matriz de productos eliminados del carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | El número de unidades de producto eliminadas del carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | El ID único que identifica el carro de compras del cliente |

### shoppingCartView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página del carro de compras. | `commerce.productListViews` |

#### Datos recopilados de shoppingCartView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productListViews` | Indica si se ha visto una lista de productos |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | El ID único que identifica el carro de compras del cliente |

### pageView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página. | `web.webpagedetails.pageViews` |

#### Datos recopilados de pageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `pageViews` | Indica si se ha cargado una página. A `value` de `1` indica que se cargó la página. |

### productPageView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página de producto. | `commerce.productViews` |

#### Datos recopilados de productPageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `productViews` | Indica si el producto se vio |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

### startCheckout

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando el comprador hace clic en un botón de cierre de compra. | `commerce.checkouts` |

#### Datos recopilados de startCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `checkouts` | Indica si se ha producido una acción durante el proceso de cierre de compra |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moneda del producto |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |
| `cartID` | El ID único que identifica el carro de compras del cliente |

### completeCheckout

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando el comprador realiza un pedido. | `commerce.order` |

#### Datos recopilados de completeCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `purchases` | Indica si se ha aceptado un pedido |
| `order` | Contiene información sobre el pedido realizado de uno o más productos |
| `purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `orderType` | Indica el tipo de pedido realizado, como Pago y envío o Compra instantánea |
| `payments` | La lista de pagos de este pedido |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago. Por ejemplo, `USD` o `EUR`. |
| `paymentAmount` | El valor del pago |
| `paymentType` | El método de pago de este pedido. Las opciones son: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | El identificador único de transacción de este elemento de pago |
| `shipping` | Detalles de envío de uno o más productos. |
| `shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc |
| `shippingAmount` | El coste total de envío de los artículos del carro de compras |
| `promotionID` | Identificador único de la promoción, si lo hay |
| `personalEmail` | Especifica la dirección de correo electrónico personal |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total de la línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para los totales del pedido. |
| `productImageUrl` | URL de imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

## Eventos de perfil

Los eventos de perfil incluyen información de la cuenta, como `signIn`, `signOut`, `createAccount`, y `editAccount`. Estos datos se utilizan para rellenar los detalles clave del cliente que se necesitan para definir mejor los segmentos o ejecutar campañas de marketing, como si desea dirigirse a los compradores que viven en Nueva York.

### signIn

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador intenta iniciar sesión. | `userAccount.login` |

>[!NOTE]
>
> Este evento se activa cuando se intenta la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de signIn

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Registra el ID de cuenta de usuario |
| `accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede |
| `personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta |
| `login` | Indica si un visitante intentó iniciar sesión |

### signOut

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador intenta cerrar la sesión. | `userAccount.logout` |

>[!NOTE]
>
> Este evento se activa cuando se intenta la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de signOut

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta |
| `logout` | Indica si un visitante intentó cerrar la sesión |

### createAccount

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador intenta crear una cuenta. | `userAccount.createProfile` |

>[!NOTE]
>
> Este evento se activa cuando se intenta la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de createAccount

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Registra el ID de cuenta de usuario |
| `accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede |
| `personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta |
| `createProfile` | Indica si un usuario ha creado un perfil de cuenta |

### editAccount

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador intenta editar una cuenta. | `userAccount.updateProfile` |

>[!NOTE]
>
> Este evento se activa cuando se intenta la acción específica. No indica que la acción se haya realizado correctamente.

#### Datos recopilados de editAccount

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `person` | Un actor, contacto o propietario individual |
| `accountID` | Registra el ID de cuenta de usuario |
| `accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede |
| `personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada |
| `address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta |
| `updateProfile` | Indica si un usuario ha actualizado su perfil de cuenta |

## Buscar eventos

Los eventos de búsqueda proporcionan datos relevantes para la intención del comprador. Una perspectiva de la intención de un comprador ayuda a los comerciantes a ver cómo buscan los artículos, en qué hacen clic y, finalmente, cómo compran o abandonan. Un ejemplo de cómo puede utilizar estos datos es si desea dirigirse a compradores existentes que buscan su producto principal, pero nunca compran el producto.

Utilice el `uniqueIdentifier` campo encontrado en ambos `searchRequestSent` y `searchResponseReceived` eventos para hacer referencia a una solicitud de búsqueda en la respuesta de búsqueda correspondiente.

### searchRequestSent

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa mediante los siguientes eventos en la ventana emergente &quot;buscar mientras escribe&quot;:<br><br>Pulse Intro Y Haga Clic En _Ver todo_<br><br> Se activa mediante los siguientes eventos en las páginas de resultados de búsqueda:<br><br>Seleccione un filtro, Cambiar el orden (_Ordenar por_), Cambiar la dirección de clasificación (ascendente o descendente), Cambiar el número de resultados por página (_Mostrar número por página_), Navegar a la página siguiente, Navegar a la página anterior, Navegar a una página diferente | `searchRequest` |

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con la extensión B2B instalada.

#### Datos recopilados de searchRequestSent

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchRequest` | Indica si se ha enviado una solicitud de búsqueda |
| `id` | El ID único de esta solicitud de búsqueda concreta |
| `filter` | Indica si se aplicó algún filtro para limitar los resultados de búsqueda |
| `attribute` (filtro) | La faceta de un elemento utilizada para determinar si se debe incluir en los resultados de búsqueda |
| `value` | Valores de atributo utilizados para determinar qué elementos se incluyen en los resultados de búsqueda |
| `isRange` | Cuando es true, los valores indican puntos finales de un intervalo aceptable de valores |
| `sort` | Indica cómo se deben ordenar los resultados de búsqueda |
| `attribute` (ordenar) | Atributo utilizado para ordenar elementos en los resultados de búsqueda |
| `order` | Orden en el que se devuelven los resultados de la búsqueda |
| `query` | Los términos buscados |

### searchResponseReceived

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando Live Search devuelve los resultados de la página emergente &quot;buscar mientras escribes&quot; o de la página de resultados de búsqueda. | `searchResponse` |

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con la extensión B2B instalada.

#### Datos recopilados de searchResponseReceived

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchResponse` | Indica si se ha recibido una respuesta de búsqueda |
| `id` | El ID único de esta respuesta de búsqueda en particular |
| `suggestions` | Matriz de cadenas que incluye los nombres de productos y categorías que existen en el catálogo y que son similares a la consulta de búsqueda |
| `numberOfResults` | El número de productos devueltos |
| `productListItems` | Una matriz de productos en el carro de compras. |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `productImageUrl` | URL de imagen principal del producto |

## Eventos B2B

![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe [instalar](install.md#install-the-b2b-extension) el `experience-platform-connector-b2b` para habilitar estos eventos.

Los eventos B2B contienen [lista de solicitudes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) información, como si se ha creado, añadido o eliminado una lista de solicitudes. Mediante el seguimiento de eventos específicos de las listas de solicitudes, puede ver los productos que sus clientes compran con frecuencia y crear campañas basadas en esos datos.

### createRequisitionList

| Descripción | Nombre de evento de XDM |
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

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador añade un producto a una lista de solicitudes existente o al crear una nueva lista. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` no es compatible con las páginas de vista de categorías ni con los productos configurables. Se admite en páginas de vista de productos y para productos simples.

#### Datos recopilados de addToRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente |
| `ID` | Identificador único de la lista de solicitudes |
| `name` | Nombre de la lista de solicitudes especificada por el cliente |
| `description` | Descripción de la lista de solicitudes especificada por el cliente |
| `productListItems` | Matriz de productos que se agregaron a la lista de solicitudes |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `quantity` | El número de unidades de producto añadidas |
| `priceTotal` | El precio total de la línea de producto |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

### removeFromRequisitionList

| Descripción | Nombre de evento de XDM |
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
| `productListItems` | Matriz de productos que se agregaron a la lista de solicitudes |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `quantity` | El número de unidades de producto añadidas |
| `priceTotal` | El precio total de la línea de producto |
| `discountAmount` | Indica el importe de descuento aplicado |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

## Eventos de back office

Los eventos de back office contienen información sobre el estado de un pedido, como si se ha realizado, cancelado, reembolsado, enviado o completado. Los datos que recopilan estos eventos del lado del servidor muestran una vista 360 del pedido del comprador. Esta vista ayuda a los comerciantes a dirigir o analizar mejor todo el estado del pedido al desarrollar campañas de marketing. Por ejemplo, puede identificar tendencias en ciertas categorías de productos que funcionan bien en diferentes épocas del año. Por ejemplo, ropa de invierno que se vende mejor durante los meses más fríos o ciertos colores de producto que los compradores están interesados en los últimos años. Además, los datos de estado de los pedidos pueden ayudarle a calcular el valor de cliente de por vida al comprender la tendencia de un comprador a realizar conversiones en función de pedidos anteriores.

>[!NOTE]
>
>Todos los eventos de back office incluyen [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que proporciona la dirección de correo electrónico del comprador. Al incluir estos datos de perfil en cada evento, no necesita importar una cuenta de usuario independiente de Adobe Commerce.

### orderPlayed

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador realiza un pedido. | `commerce.backofficeOrderPlaced` |

#### Datos recopilados de orderPlayed

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes |
| `productListItems` | Una matriz de productos en el pedido |
| `id` | El elemento de línea de esta entrada de producto. El producto en sí se identifica mediante la variable `product` field. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `SKU` | Unidad de stock. El identificador único del producto. |
| `quantity` | Número de unidades de producto en el carro de compras |
| `priceTotal` | El precio total de la línea de producto |
| `discountAmount` | Indica el importe de descuento aplicado |
| `commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `order` | Contiene información sobre el pedido |
| `purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único |
| `priceTotal` | El precio total de este pedido después de aplicar todos los descuentos e impuestos |
| `currencyCode` | El código de divisa en formato ISO 4217 usado para el total del pedido |
| `purchaseOrderNumber` | Identificador único asignado por el comprador a esta compra o contrato |
| `payments` | La lista de pagos de este pedido |
| `paymentType` | El método de pago de este pedido. Se permiten valores personalizados enumerados. |
| `currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago |
| `paymentAmount` | El valor del pago |
| `taxAmount` | El importe del impuesto pagado por el comprador como parte del pago final |
| `createdDate` | Fecha y hora en la que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00` |
| `shipping` | Detalles de envío de uno o más productos |
| `shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc |
| `shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |
| `address` | Dirección física de envío |
| `street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle |
| `street2` | Campo adicional para información de nivel de calle |
| `city` | El nombre de la ciudad |
| `state` | El nombre del estado. Este es un campo de forma libre. |
| `postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `billingAddress` | Dirección postal de facturación |
| `street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle |
| `street2` | Campo adicional para información de nivel de calle |
| `city` | El nombre de la ciudad |
| `state` | El nombre del estado. Este es un campo de forma libre. |
| `postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `personalEmail` | Una dirección de correo electrónico personal |
| `address` | La dirección técnica como, por ejemplo, name@domain.com, tal y como se define en RFC2822 y estándares subsiguientes |

### orderItemsShipped

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se envía un pedido. | `commerce.backofficeOrderItemsShipped` |

#### Datos recopilados de orderItemsShipped

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes| |`productListItems`|Una matriz de productos en el pedido| |`id`|El elemento de línea de esta entrada de producto. El producto en sí se identifica mediante la variable `product` field.| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de stock. El identificador único del producto.| |`quantity`|El número de unidades de producto en el carro de compras| |`priceTotal`|El precio total de la línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`commerceScope`|Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.).| |`environmentID`|El ID de entorno. ID alfanumérico de 32 dígitos separado por guiones.| |`storeCode`|El código de almacén único. Puede tener muchas tiendas por sitio web.| |`storeViewCode`|El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda.| |`websiteCode`|El código único del sitio web. Puede tener muchos sitios web en un entorno.| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único| |`priceTotal`|El precio total de este pedido después de aplicar todos los descuentos e impuestos| |`currencyCode`|El código de divisa en formato ISO 4217 usado para el total del pedido| |`purchaseOrderNumber`|Identificador único asignado por el comprador a esta compra o contrato| |`payments`|La lista de pagos de este pedido| |`paymentType`|El método de pago de este pedido. Se permiten valores personalizados enumerados.| |`currencyCode`|El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago| |`paymentAmount`|El valor del pago| |`lastUpdatedDate`|Hora a la que se actualizó por última vez un registro de pedido determinado en el sistema de comercio| |`shipping`|Detalles de envío de uno o más productos| |`shippingMethod`|El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc.| |`trackingNumber`|El número de seguimiento proporcionado por el transportista para un envío de artículo de pedido| |`trackingURL`|Dirección URL para realizar un seguimiento del estado de envío de un artículo de pedido| |`shipDate`|La fecha en la que se envían uno o más artículos de un pedido| |`address`|Dirección física de envío| |`street1`|Información principal de la dirección postal, número de piso, número de calle y nombre de la calle| |`street2`|Campo adicional para información de nivel de calle| |`city`|El nombre de la ciudad| |`state`|El nombre del estado. Este es un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal.| |`country`|El nombre del territorio administrado por el Gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma.| |`shippingAmount`|El importe que el cliente tuvo que pagar por el envío.| |`billingAddress`|Dirección postal de facturación| |`street1`|Información principal de la dirección postal, número de piso, número de calle y nombre de la calle| |`street2`|Campo adicional para información de nivel de calle| |`city`|El nombre de la ciudad| |`state`|El nombre del estado. Este es un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal.| |`country`|El nombre del territorio administrado por el Gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma.| |`personalEmail`|Una dirección de correo electrónico personal| |`address`|La dirección técnica, por ejemplo, &quot;name@domain.com&quot;, tal como se define en RFC2822 y estándares subsiguientes|

### orderCanceled

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador cancela un pedido. | `commerce.backofficeOrderCancelled` |

#### Datos recopilados de orderCanceled

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes| |`productListItems`|Una matriz de productos en el pedido| |`id`|El elemento de línea de esta entrada de producto. El producto en sí se identifica mediante la variable `product` field.| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de stock. El identificador único del producto.| |`quantity`|El número de unidades de producto en el carro de compras| |`priceTotal`|El precio total de la línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`commerceScope`|Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.).| |`environmentID`|El ID de entorno. ID alfanumérico de 32 dígitos separado por guiones.| |`storeCode`|El código de almacén único. Puede tener muchas tiendas por sitio web.| |`storeViewCode`|El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda.| |`websiteCode`|El código único del sitio web. Puede tener muchos sitios web en un entorno.| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador a esta compra o contrato| |`cancelDate`|La fecha y hora en que un comprador cancela un pedido| |`lastUpdatedDate`|Hora a la que se actualizó por última vez un registro de pedido determinado en el sistema de comercio| |`personalEmail`|Una dirección de correo electrónico personal| |`address`|La dirección técnica, por ejemplo, &quot;name@domain.com&quot;, tal como se define en RFC2822 y estándares subsiguientes|

### creditMemoIssued

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador devuelve un artículo en un pedido. | `commerce.backofficeCreditMemoIssued` |

#### Datos recopilados de creditMemoIssued

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes| |`productListItems`|Una matriz de productos en el pedido| |`id`|El elemento de línea de esta entrada de producto. El producto en sí se identifica mediante la variable `product` field.| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de stock. El identificador único del producto.| |`quantity`|El número de unidades de producto en el carro de compras| |`priceTotal`|El precio total de la línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único| |`purchaseOrderNumber`|Identificador único asignado por el comprador a esta compra o contrato| |`lastUpdatedDate`|Hora a la que se actualizó por última vez un registro de pedido determinado en el sistema de comercio| |`personalEmail`|Una dirección de correo electrónico personal| |`address`|La dirección técnica, por ejemplo, &quot;name@domain.com&quot;, tal como se define en RFC2822 y estándares subsiguientes|

### orderShipmentCompleted

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador devuelve un artículo en un pedido. | `commerce.backofficeOrderShipmentCompleted` |

#### Datos recopilados de orderShipmentCompleted

En la tabla siguiente se describen los datos recopilados para este evento.
|Campo|Descripción| |—|—| |`address`|La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes| |`productListItems`|Una matriz de productos en el pedido| |`id`|El elemento de línea de esta entrada de producto. El producto en sí se identifica mediante la variable `product` field.| |`name`|El nombre para mostrar o el nombre legible en lenguaje natural del producto| |`SKU`|Unidad de stock. El identificador único del producto.| |`quantity`|El número de unidades de producto en el carro de compras| |`priceTotal`|El precio total de la línea de producto| |`discountAmount`|Indica el importe de descuento aplicado| |`order`|Contiene información sobre el pedido| |`purchaseID`|Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único| |`priceTotal`|El precio total de este pedido después de aplicar todos los descuentos e impuestos| |`currencyCode`|El código de divisa en formato ISO 4217 usado para el total del pedido| |`purchaseOrderNumber`|Identificador único asignado por el comprador a esta compra o contrato| |`taxAmount`|El importe del impuesto pagado por el comprador como parte del pago final.| |`createdDate`|La fecha y hora en que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00`| |`payments`|La lista de pagos de este pedido| |`paymentType`|El método de pago de este pedido. Se permiten valores personalizados enumerados.| |`currencyCode`|El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado para este elemento de pago| |`paymentAmount`|El valor del pago| |`shipping`|Detalles de envío de uno o más productos| |`shippingMethod`|El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc.| |`address`|Dirección física de envío| |`street1`|Información principal de la dirección postal, número de piso, número de calle y nombre de la calle| |`street2`|Campo adicional para información de nivel de calle| |`city`|El nombre de la ciudad| |`state`|El nombre del estado. Este es un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal.| |`country`|El nombre del territorio administrado por el Gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma.| |`shippingAmount`|El importe que el cliente tuvo que pagar por el envío.| |`address`|La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes| |`billingAddress`|Dirección postal de facturación| |`street1`|Información principal de la dirección postal, número de piso, número de calle y nombre de la calle| |`street2`|Campo adicional para información de nivel de calle| |`city`|El nombre de la ciudad| |`state`|El nombre del estado. Este es un campo de forma libre.| |`postalCode`|El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, estos datos solo contienen parte del código postal.| |`country`|El nombre del territorio administrado por el Gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma.| |`personalEmail`|Una dirección de correo electrónico personal| |`address`|La dirección técnica, por ejemplo, &quot;name@domain.com&quot;, tal como se define en RFC2822 y estándares subsiguientes|
