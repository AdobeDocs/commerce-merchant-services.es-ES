---
title: Eventos
description: Descubra qué datos captura cada evento.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f90ef4d2732a0b0676e0899712f94b41a1c2d85a
workflow-type: tm+mt
source-wordcount: '6894'
ht-degree: 0%

---

# [!DNL Data Connection] Eventos

A continuación se enumeran los eventos de Commerce disponibles al instalar el [!DNL Data Connection] extensión. Los datos que estos eventos recopilan se envían al perímetro de Adobe Experience Platform. También puede crear lo siguiente [eventos personalizados](custom-events.md) para recopilar datos adicionales que no se proporcionen de forma predeterminada.

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
| Se activa cuando el comprador realiza un pedido. | `commerce.order` |

#### Datos recopilados de completeCheckout

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
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

Los eventos de búsqueda proporcionan datos relevantes para la intención del comprador. Una perspectiva de la intención de un comprador ayuda a los comerciantes a ver cómo buscan los artículos, en qué hacen clic y, finalmente, cómo compran o abandonan. Un ejemplo de cómo puede utilizar estos datos es si desea dirigirse a compradores existentes que buscan su producto principal, pero nunca compran el producto.

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

![B2B para Adobe Commerce](../assets/b2b.svg) Para los comerciantes B2B, debe [instalar](install.md#install-the-b2b-extension) el `experience-platform-connector-b2b` para habilitar estos eventos.

Los eventos B2B contienen [lista de solicitudes](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) información, como si se ha creado, añadido o eliminado una lista de solicitudes. Mediante el seguimiento de eventos específicos de las listas de solicitudes, puede ver los productos que sus clientes compran con frecuencia y crear campañas basadas en esos datos.

### createRequisitionList

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador crea una lista de solicitudes. | `commerce.requisitionListOpens` |

#### Datos recopilados de createRequisitionList

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
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
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.payments` | La lista de pagos de este pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador único de esta transacción de pago. |
| `commerce.order.payments.paymentAmount` | El valor del pago. |
| `commerce.order.payments.paymentType` | El método de pago de este pedido. Se han contabilizado los valores personalizados permitidos. |
| `commerce.order.payments.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.taxAmount` | El importe del impuesto pagado por el comprador como parte del pago final. |
| `commerce.order.discountAmount` | Indica el importe de descuento aplicado a todo el pedido. |
| `commerce.order.createdDate` | Fecha y hora en la que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | El código de divisa en formato ISO 4217 usado para el total del pedido. |
| `commerce.shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc. |
| `commerce.shipping.shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |
| `commerce.shipping.currencyCode` | El código de divisa en formato ISO 4217 usado para el total de envío. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `commerce.billing.address` | Dirección postal de facturación. |
| `commerce.billing.address.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle |
| `commerce.billing.address.street2` | Campo adicional para información de nivel de calle. |
| `commerce.billing.address.city` | El nombre de la ciudad. |
| `commerce.billing.address.state` | El nombre del estado. Este es un campo de forma libre. |
| `commerce.billing.address.postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `commerce.billing.address.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.id` | El elemento de línea de esta entrada de producto. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |
| `productListItems.productImageUrl` | URL de imagen principal del producto. |

### orderInvoiced

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comerciante envía una factura para solicitar el pago. | `commerce.backofficeOrderInvoiced` |

#### Datos recopilados de orderInvoiced

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.priceTotal` | El precio total de este pedido después de aplicar todos los descuentos e impuestos. |
| `commerce.order.currencyCode` | El código de divisa en formato ISO 4217 usado para el total del pedido. |
| `commerce.order.purchaseOrderNumber` | Identificador único asignado por el comprador a esta compra o contrato. |
| `commerce.order.payments` | La lista de pagos de este pedido. |
| `commerce.order.payments.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.payments.paymentType` | El método de pago de este pedido. Se han contabilizado los valores personalizados permitidos. |
| `commerce.order.payments.paymentAmount` | El valor del pago. |
| `commerce.shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc. |
| `commerce.shipping.shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.id` | El elemento de línea de esta entrada de producto. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |

### orderItemsShipped

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se envía un pedido. | `commerce.backofficeOrderItemsShipped` |

#### Datos recopilados de orderItemsShipped

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.payments` | La lista de pagos de este pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador único de esta transacción de pago. |
| `commerce.order.payments.paymentAmount` | El valor del pago. |
| `commerce.order.payments.paymentType` | El método de pago de este pedido. Se han contabilizado los valores personalizados permitidos. |
| `commerce.order.payments.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.priceTotal` | El precio total de este pedido después de aplicar todos los descuentos e impuestos. |
| `commerce.order.purchaseOrderNumber` | Identificador único asignado por el comprador a esta compra o contrato. |
| `commerce.order.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.lastUpdatedDate` | Hora a la que se actualiza por última vez un registro de pedido determinado en el sistema de comercio. |
| `commerce.shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc. |
| `commerce.shipping.shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |
| `commerce.shipping.address` | La dirección física de envío. |
| `commerce.shipping.address.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle. |
| `commerce.shipping.address.street2` | Segunda línea para información de dirección (opcional) |
| `commerce.shipping.address.city` | El nombre de la ciudad. |
| `commerce.shipping.address.state` | El nombre del estado. Este es un campo de forma libre. |
| `commerce.shipping.address.postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `commerce.shipping.address.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `commerce.shipping.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.shipping.trackingNumber` | Número de seguimiento proporcionado por el transportista para un envío de artículo de pedido. |
| `commerce.shipping.trackingURL` | Dirección URL para realizar un seguimiento del estado de envío de un artículo de pedido. |
| `commerce.shipping.shipDate` | La fecha en la que se envían uno o más artículos de un pedido. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `commerce.billing.address` | Dirección postal de facturación. |
| `commerce.billing.address.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle |
| `commerce.billing.address.street2` | Campo adicional para información de nivel de calle. |
| `commerce.billing.address.city` | El nombre de la ciudad. |
| `commerce.billing.address.state` | El nombre del estado. Este es un campo de forma libre. |
| `commerce.billing.address.postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `commerce.billing.address.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |

### orderCanceled

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador cancela un pedido. | `commerce.backofficeOrderCancelled` |

#### Datos recopilados de orderCanceled

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.purchaseOrderNumber` | Identificador único asignado por el comprador a esta compra o contrato. |
| `commerce.order.cancelDate` | La fecha y hora en que un comprador cancela un pedido. |
| `commerce.order.lastUpdatedDate` | Hora a la que se actualiza por última vez un registro de pedido determinado en el sistema de comercio. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |

### orderLineItemRefund

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se reembolsa a un comprador un artículo devuelto. | `commerce.backofficeCreditMemoIssued` |

#### Datos recopilados de orderLineItemRefund

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.lastUpdatedDate` | Hora a la que se actualiza por última vez un registro de pedido determinado en el sistema de comercio. |
| `commerce.order.purchaseOrderNumber` | Identificador único asignado por el comprador a esta compra o contrato. |
| `commerce.refunds` | La lista de reembolsos de este pedido. |
| `commerce.refunds.transactionID` | Identificador único de este reembolso. |
| `commerce.refunds.refundAmount` | El valor del reembolso. |
| `commerce.refunds.refundPaymentType` | El método de pago de este pedido. Se han contabilizado los valores personalizados permitidos. |
| `commerce.refunds.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |

### orderItemsReturnInitiated

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando un comprador solicita devolver un artículo. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Datos recopilados de orderItemsReturnInitiated

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.returns` | La información de la RMA (Autorización de Devolución de Mercancías) para este pedido. |
| `commerce.order.returns.returnID` | El identificador único de esta RMA (autorización de devolución de mercancía). |
| `commerce.order.returns.returnStatus` | El estado de la RMA (autorización de devolución de mercancía), como Pendiente, Cerrado, etc. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |
| `productListItems.returnItem` | La información de la RMA (Autorización de Devolución de Mercancías) para este artículo. |
| `productListItems.returnItem.returnStatus` | El estado del elemento devuelto, como Pendiente, Aprobado, etc. |
| `productListItems.returnItem.returnReason` | El motivo por el que se solicita una devolución para este artículo. |
| `productListItems.returnItem.returnItemCondition` | La condición del elemento para el que se solicita la devolución. |
| `productListItems.returnItem.returnResolution` | La resolución solicitada del elemento devuelto, como Reembolso, Intercambio, etc. |
| `productListItems.returnItem.returnQuantityRequested` | El número de este artículo que el comprador solicitó devolver. |
| `productListItems.returnItem.returnQuantityAuthorized` | Número de este artículo que está autorizado a devolver. |
| `productListItems.returnItem.eturnQuantityReceived` | Número de artículos devueltos recibidos. |
| `productListItems.returnItem.returnQuantityApproved` | El número de este artículo con devolución totalmente completa y aprobada. |

### orderItemReturnCompleted

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se completa un artículo que un comprador solicitó devolver. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Datos recopilados de orderItemReturnCompleted

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.returns` | La información de la RMA (Autorización de Devolución de Mercancías) para este pedido. |
| `commerce.order.returns.returnID` | El identificador único de esta RMA (autorización de devolución de mercancía). |
| `commerce.order.returns.returnStatus` | El estado de la RMA (autorización de devolución de mercancía), como Pendiente, Cerrado, etc. |
| `commerce.commerceScope` | Indica dónde se produjo un evento (vista de tienda, tienda, sitio web, etc.). |
| `commerce.commerceScope.environmentID` | El ID del entorno. ID alfanumérico de 32 dígitos separado por guiones. |
| `commerce.commerceScope.storeCode` | El código de almacén único. Puede tener muchas tiendas por sitio web. |
| `commerce.commerceScope.storeViewCode` | El código de vista de tienda único. Puede tener muchas vistas de la tienda por tienda. |
| `commerce.commerceScope.websiteCode` | El código único del sitio web. Puede tener muchos sitios web en un entorno. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |
| `productListItems.returnItem` | La información de la RMA (Autorización de Devolución de Mercancías) para este artículo. |
| `productListItems.returnItem.returnStatus` | El estado del elemento devuelto, como Pendiente, Aprobado, etc. |
| `productListItems.returnItem.returnReason` | El motivo por el que se solicita una devolución para este artículo. |
| `productListItems.returnItem.returnItemCondition` | La condición del elemento para el que se solicita la devolución. |
| `productListItems.returnItem.returnResolution` | La resolución solicitada del elemento devuelto, como Reembolso, Intercambio, etc. |
| `productListItems.returnItem.returnQuantityRequested` | El número de este artículo que el comprador solicitó devolver. |
| `productListItems.returnItem.returnQuantityAuthorized` | Número de este artículo que está autorizado a devolver. |
| `productListItems.returnItem.eturnQuantityReceived` | Número de artículos devueltos recibidos. |
| `productListItems.returnItem.returnQuantityApproved` | El número de este artículo con devolución totalmente completa y aprobada. |

### orderShipmentCompleted

| Descripción | Nombre de evento de XDM |
|---|---|
| Se activa cuando se completa un envío. | `commerce.backofficeOrderShipmentCompleted` |

#### Datos recopilados de orderShipmentCompleted

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `commerce.order` | Contiene información sobre el pedido. |
| `commerce.order.purchaseID` | Identificador único asignado por el vendedor a esta compra o contrato. No hay garantía de que el ID sea único. |
| `commerce.order.payments` | La lista de pagos de este pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador único de esta transacción de pago. |
| `commerce.order.payments.paymentAmount` | El valor del pago. |
| `commerce.order.payments.paymentType` | El método de pago de este pedido. Se han contabilizado los valores personalizados permitidos. |
| `commerce.order.payments.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `commerce.order.taxAmount` | El importe del impuesto pagado por el comprador como parte del pago final. |
| `commerce.order.createdDate` | Fecha y hora en la que se crea un nuevo pedido en el sistema de comercio. Por ejemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Detalles de envío de uno o más productos. |
| `commerce.shipping.shippingMethod` | El método de envío elegido por el cliente, como envío estándar, envío rápido, recogida en tienda, etc. |
| `commerce.shipping.shippingAmount` | El importe que el cliente tuvo que pagar por el envío. |
| `commerce.shipping.shipDate` | La fecha en la que se envían uno o más artículos de un pedido. |
| `commerce.shipping.address` | La dirección física de envío. |
| `commerce.shipping.address.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle. |
| `commerce.shipping.address.street2` | Segunda línea para información de dirección (opcional) |
| `commerce.shipping.address.city` | El nombre de la ciudad. |
| `commerce.shipping.address.state` | El nombre del estado. Este es un campo de forma libre. |
| `commerce.shipping.address.postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `commerce.shipping.address.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `commerce.billing.address` | Dirección postal de facturación. |
| `commerce.billing.address.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle |
| `commerce.billing.address.street2` | Campo adicional para información de nivel de calle. |
| `commerce.billing.address.city` | El nombre de la ciudad. |
| `commerce.billing.address.state` | El nombre del estado. Este es un campo de forma libre. |
| `commerce.billing.address.postalCode` | El código postal de la ubicación. Los códigos postales no están disponibles en todos los países. En algunos países, solo contiene parte del código postal. |
| `commerce.billing.address.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `productListItems` | Una matriz de productos en el pedido. |
| `productListItems.SKU` | Unidad de stock. El identificador único del producto. |
| `productListItems.name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto. |
| `productListItems.priceTotal` | El precio total de la línea de producto. |
| `productListItems.quantity` | Número de unidades de producto en el carro de compras. |
| `productListItems.discountAmount` | Indica el importe de descuento aplicado. |
| `productListItems.currencyCode` | El [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de divisa utilizado, como `USD` o `EUR`. |
| `productListItems.selectedOptions` | Campo utilizado para un producto configurable. |
| `productListItems.selectedOptions.attribute` | Identifica un atributo del producto configurable, como `size` o `color`. |
| `productListItems.selectedOptions.value` | Identifica el valor del atributo como `small` o `black`. |
| `productListItems.categories` | Contiene información sobre la categoría de un producto. |
| `productListItems.categories.id` | El identificador único de la categoría. |
| `productListItems.categories.name` | Nombre de la categoría. |
| `productListItems.categories.path` | La ruta a la categoría. |
