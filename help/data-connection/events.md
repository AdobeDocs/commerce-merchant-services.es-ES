---
title: Eventos de comportamiento
description: Descubra qué datos captura cada evento de comportamiento.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '4496'
ht-degree: 0%

---

# [!DNL Data Connection] Eventos de comportamiento

A continuación se enumeran los eventos de comportamiento de Commerce disponibles al instalar el [!DNL Data Connection] extensión. Los datos que estos eventos recopilan se envían a Adobe Experience Platform. También puede crear lo siguiente [eventos personalizados](custom-events.md) para recopilar datos adicionales que no se proporcionen de forma predeterminada.

Además de los datos que recopilan los siguientes eventos, también obtiene lo siguiente [otros datos](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) proporcionadas por el SDK web de Adobe Experience Platform.

Los eventos de comportamiento recopilan datos de comportamiento anónimos de los compradores a medida que navegan por el sitio. Puede utilizar los datos que recopilan estos eventos para crear promociones y campañas dirigidas a un conjunto específico de compradores.

>[!NOTE]
>
>Todos los eventos de comportamiento incluyen [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que incluye la dirección de correo electrónico del comprador, cuando está disponible, y ECID.

## Eventos de tienda

Los eventos de tienda capturan datos de las interacciones de los compradores en el sitio e incluyen eventos como [`addToCart`](#addtocart), [`pageView`](#pageview), [`createAccount`](#createaccount), [`editAccount`](#editaccount), [`startCheckout`](#startcheckout), [`completeCheckout`](#completecheckout), [`signIn`](#signin), [`signOut`](#signout), etc. Los eventos de tienda solo se aplican a productos simples y configurables.

### addToCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se añade un producto al carro de compras o cuando se incrementa la cantidad de un producto en el carro de compras. | `commerce.productListAdds` |

#### Datos recopilados de addToCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListAdds` | Indica si se ha añadido un producto a un carro de compras. Un valor de `1` indica que se ha añadido un producto. |
| `commerce.cart.cartID` | ID único que identifica el carro de compras del cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### openCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se crea un carro de compras nuevo, es decir, cuando se agrega un producto a un carro de compras vacío. | `commerce.productListOpens` |

#### Datos recopilados de openCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListOpens` | Indica si se ha creado un carro de compras. Un valor de `1` indica que se creó un carro de compras. |
| `commerce.cart.cartID` | ID único que identifica el carro de compras del cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### removeFromCart

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cada vez que se elimina un producto o cada vez que se reduce la cantidad de un producto en el carro de compras. | `commerce.productListRemovals` |

#### Datos recopilados de removeFromCart

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListRemovals` | Indica si un producto se ha eliminado del carro de compras. Un valor de `1` indica que se ha eliminado un producto del carro de compras. |
| `commerce.cart.cartID` | ID único que identifica el carro de compras del cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### shoppingCartView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página del carro de compras. | `commerce.productListViews` |

#### Datos recopilados de shoppingCartView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productListViews` | Indica si se ha visto una lista de productos. |
| `commerce.cart.cartID` | ID único que identifica el carro de compras del cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### pageView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página. | `web.webpagedetails.pageViews` |

#### Datos recopilados de pageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `web.webPageDetails.pageViews` | Indica si se ha cargado una página. A `value` de `1` indica que se cargó la página. |
| `web.webPageDetails.URL` | La URL normativa o habitual de la página web. Puede ser la dirección URL real utilizada para llegar a la página, que se registraría mediante `Web Link`. |
| `web.webPageDetails.name` | Nombre normativo de la página web. Este nombre no es necesariamente el título de página ni está asociado directamente con el contenido de la página, pero se utiliza para organizar las páginas de un sitio con fines de clasificación. |
| `web.webReferrer.URL` | Dirección URL de la página web que visitó un comprador antes de hacer clic en un vínculo al sitio. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

### productPageView

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se carga cualquier página de producto. | `commerce.productViews` |

#### Datos recopilados de productPageView

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.productViews` | Indica si se ha visto el producto. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### startCheckout

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando el comprador hace clic en un botón de cierre de compra. | `commerce.checkouts` |

#### Datos recopilados de startCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.checkouts` | Indica si se ha producido una acción durante el proceso de cierre de compra. |
| `commerce.cart.cartID` | ID único que identifica el carro de compras del cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### completeCheckout

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando el comprador realiza un pedido. | `commerce.purchases` |

#### Datos recopilados de completeCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.purchases` | Indica si se ha aceptado un pedido. |
| `commerce.order` | Contiene información sobre el pedido realizado de uno o más productos. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.payments` | La lista de pagos de este pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador único de esta transacción de pago. |
| `commerce.order.payments.paymentAmount` | El valor del pago. |
| `commerce.order.payments.paymentType` | El método de pago de este pedido. Las opciones son: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.taxAmount` | El importe del impuesto pagado por el comprador como parte del pago final. |
| `commerce.order.discountAmount` | Indica el importe de descuento aplicado a todo el pedido. |
| `commerce.order.createdDate` | Fecha y hora en la que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc. |
| `commerce.shipping.shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |  | `shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

## Eventos de perfil de cliente

Los eventos de perfil capturados desde la tienda incluyen información de la cuenta, como `signIn`, `signOut`, `createAccount`, y `editAccount`. Estos datos se utilizan para rellenar los detalles clave del cliente que se necesitan para definir mejor los segmentos o ejecutar campañas de marketing, como enviar ofertas de descuento de suscripción, confirmaciones de cambio de cuenta, etc. Hay eventos de perfil similares capturados del [del lado del servidor](events-backoffice.md#customer-profile-events).

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Un actor, contacto o propietario individual. |
| `person.accountID` | Registra el ID de cuenta de usuario. |
| `person.accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede. |
| `person.personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.login` | Indica si un visitante intentó iniciar sesión. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.logout` | Indica si un visitante intentó cerrar la sesión. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Un actor, contacto o propietario individual. |
| `person.accountID` | Registra el ID de cuenta de usuario. |
| `person.accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede. |
| `person.personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.updateProfile` | Indica si un usuario ha actualizado su perfil de cuenta. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Un actor, contacto o propietario individual. |
| `person.accountID` | Registra el ID de cuenta de usuario. |
| `person.accountType` | Registra el tipo de cuenta de usuario, como `Personal` o `Company`, si procede. |
| `person.personalEmailID` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `personalEmail` | Registra los detalles de contacto: un correo electrónico e información asociada. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.updateProfile` | Indica si un usuario ha actualizado su perfil de cuenta. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

## Buscar eventos

Los eventos de búsqueda proporcionan datos relevantes para la intención del comprador. Una perspectiva de la intención de un comprador ayuda a los comerciantes a ver cómo buscan los artículos, en qué hacen clic y, finalmente, cómo compran o abandonan. Un ejemplo de cómo puede utilizar estos datos es si desea dirigirse a compradores existentes que buscan su producto principal, pero nunca compran el producto. Debe instalar el [[!DNL Live Search]](../live-search/install.md) para acceder a estos eventos.

Utilice el `searchRequest.id` y `searchResponse.id` campos encontrados en ambos `searchRequestSent` y `searchResponseReceived` eventos para hacer referencias cruzadas de una solicitud de búsqueda con la respuesta de búsqueda correspondiente.

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchRequest` | Indica si se ha enviado una solicitud de búsqueda. |
| `searchRequest.id` | El ID único de esta solicitud de búsqueda en particular. |
| `searchRequest.value` | El valor cuantificable de la solicitud. |
| `siteSearch` | Contiene información sobre la búsqueda. |
| `siteSearch.filter` | Indica si se aplicó algún filtro para limitar los resultados de búsqueda. |
| `siteSearch.filter.attribute` (filtro) | La faceta de un elemento utilizada para determinar si se debe incluir en los resultados de búsqueda. |
| `siteSearch.filter.isRange` | Cuando es True, los valores indican puntos finales de un intervalo aceptable de valores. |
| `siteSearch.filter.value` | Valor de atributo utilizado para determinar qué elementos se incluyen en los resultados de búsqueda. |
| `siteSearch.sort` | Indica cómo se deben ordenar los resultados de búsqueda. |
| `siteSearch.sort.attribute` (ordenar) | Atributo utilizado para ordenar elementos en los resultados de búsqueda. |
| `siteSearch.sort.order` | Orden en el que se devuelven los resultados de la búsqueda. |
| `siteSearch.query` | Los términos buscados. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

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
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `searchResponse` | Indica si se ha recibido una respuesta de búsqueda. |
| `searchResponse.id` | El ID único de esta respuesta de búsqueda en particular. |
| `searchResponse.value` | El valor cuantificable de la respuesta. |
| `siteSearch.numberOfResults` | El número de productos devueltos. |
| `siteSearch.suggestions` | Matriz de cadenas que incluye los nombres de productos y categorías que existen en el catálogo y que son similares a la consulta de búsqueda. |
| `productListItems` | Una matriz de productos que se agregaron al carro de compras. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

## Eventos B2B

![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe [instalar](install.md#install-the-b2b-extension) el `experience-platform-connector-b2b` para acceder a estos eventos.

Los eventos B2B contienen [lista de solicitudes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) información, como si se ha creado, añadido o eliminado una lista de solicitudes. Mediante el seguimiento de eventos específicos de las listas de solicitudes, puede ver los productos que sus clientes compran con frecuencia y crear campañas basadas en esos datos.

### createRequisitionList

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador crea una lista de solicitudes. | `commerce.requisitionListOpens` |

#### Datos recopilados de createRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListOpens` | Indica la inicialización de una nueva lista de solicitudes. |
| `commerce.requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente. |
| `commerce.requisitionList.ID` | Identificador único de la lista de solicitudes. |
| `commerce.requisitionList.name` | Nombre de la lista de solicitudes especificada por el cliente. |
| `commerce.requisitionList.description` | Descripción de la lista de solicitudes especificada por el cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |

### addToRequisitionList

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador añade un producto a una lista de solicitudes existente o al crear una lista. | `commerce.requisitionListAdds` |

#### Datos recopilados de addToRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListAdds` | Indica la adición de uno o más productos a una lista de solicitudes. |
| `commerce.requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente. |
| `commerce.requisitionList.ID` | Identificador único de la lista de solicitudes. |
| `commerce.requisitionList.name` | Nombre de la lista de solicitudes especificada por el cliente. |
| `commerce.requisitionList.description` | Descripción de la lista de solicitudes especificada por el cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Matriz de productos que se agregaron a la lista de solicitudes. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### removeFromRequisitionList

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador elimina un producto de una lista de solicitudes. | `commerce.requisitionListRemovals` |

#### Datos recopilados de removeFromRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requsitionListRemovals` | Indica la eliminación de uno o más productos de una lista de solicitudes. |
| `commerce.requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente. |
| `commerce.requisitionList.ID` | Identificador único de la lista de solicitudes. |
| `commerce.requisitionList.name` | Nombre de la lista de solicitudes especificada por el cliente. |
| `commerce.requisitionList.description` | Descripción de la lista de solicitudes especificada por el cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `productListItems` | Matriz de productos que se agregaron a la lista de solicitudes. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |

### deleteRequisitionList

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador elimina una lista de solicitudes. | `commerce.requisitionListDeletes` |

#### Datos recopilados de deleteRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListDeletes` | Indica que se ha eliminado una lista de solicitudes. |
| `commerce.requisitionList` | Las propiedades de la lista de solicitudes creada por el cliente. |
| `commerce.requisitionList.ID` | Identificador único de la lista de solicitudes. |
| `commerce.requisitionList.name` | Nombre de la lista de solicitudes especificada por el cliente. |
| `commerce.requisitionList.description` | Descripción de la lista de solicitudes especificada por el cliente. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
