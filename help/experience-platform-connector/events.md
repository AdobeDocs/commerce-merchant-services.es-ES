---
title: Eventos
description: Descubra qué datos captura cada evento.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: aaaab3d11c15a69856711a41e889a5d0208aedd2
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 0%

---

# Eventos de conector de Experience Platform

A continuación se enumeran los eventos de comercio disponibles al instalar la extensión del conector del Experience Platform. Los datos que recopilan estos eventos se envían al perímetro de Adobe Experience Platform. También puede crear [eventos personalizados](custom-events.md) para recopilar datos adicionales no proporcionados de forma predeterminada.

Además de los datos que recopilan los eventos siguientes, también obtiene [otros datos](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) proporcionado por el SDK web de Adobe Experience Platform.

>[!NOTE]
>
>Todos los eventos de tienda incluyen el `personID` , que es un identificador único de la persona.

## addToCart

Se activa cuando se agrega un producto al carro de compras o cuando se incrementa la cantidad de un producto en el carro de compras.

### Nombre de evento XDM

`commerce.productListAdds`

### Tipo

Tienda

### Datos recopilados

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

## openCart

Se activa cuando se crea un nuevo carro de compras, que es cuando se agrega un producto a un carro vacío.

### Nombre de evento XDM

`commerce.productListOpens`

### Tipo

Tienda

### Datos recopilados

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

## removeFromCart

Se activa cada vez que se elimina un producto o cada vez que se reduce la cantidad de un producto en el carro de compras.

### Nombre de evento XDM

`commerce.productListRemovals`

### Tipo

Tienda

### Datos recopilados

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

## shoppingCartView

Se activa cuando se carga cualquier página del carro de compras.

### Nombre de evento XDM

`commerce.productListViews`

### Tipo

Tienda

### Datos recopilados

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

## pageView

Se activa cuando se carga cualquier página.

### Nombre de evento XDM

`web.webpagedetails.pageViews`

### Tipo

Tienda

### Datos recopilados

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `pageViews` | Indica si se cargó una página. A `value` de `1` indica que la página se ha cargado. |

## productPageView

Se activa cuando se carga cualquier página de producto.

### Nombre de evento XDM

`commerce.productViews`

### Tipo

Tienda

### Datos recopilados

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

## startCheckout

Se activa cuando el comprador hace clic en un botón de cierre de compra.

### Nombre de evento XDM

`commerce.checkouts`

### Tipo

Tienda

### Datos recopilados

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

## completeCheckout

Se activa cuando el comprador realiza un pedido.

### Nombre de evento XDM

`commerce.order`

### Tipo

Tienda

### Datos recopilados

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
| `productListItems` | Una matriz de productos en el carro de compras |
| `SKU` | Unidad de mantenimiento de existencias. Identificador único del producto. |
| `name` | El nombre para mostrar o el nombre legible en lenguaje natural del producto |
| `priceTotal` | El precio total del artículo de línea de producto |
| `quantity` | Número de unidades de producto en el carro de compras |
| `discountAmount` | Indica la cantidad de descuento aplicada |
| `currencyCode` | La variable [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moneda utilizado para los totales de pedidos. |
| `productImageUrl` | URL de la imagen principal del producto |
| `selectedOptions` | Campo utilizado para un producto configurable. `attribute` identifica un atributo del producto configurable, como `size` o `color` y `value` identifica el valor del atributo como `small` o `black`. |

## signIn

Se activa cuando un comprador intenta iniciar sesión.

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

### Nombre de evento XDM

`userAccount.login`

### Tipo

Perfil

### Datos recopilados

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

## signOut

Se activa cuando un comprador intenta cerrar sesión.

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

### Nombre de evento XDM

`userAccount.logout`

### Tipo

Perfil

### Datos recopilados

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `eventType` | El tipo de evento principal para este registro de serie temporal, como: `userAccount.logout` |
| `userAccount` | Indica los detalles de lealtad, las preferencias, los procesos de inicio de sesión y otras preferencias de cuenta |
| `logout` | Indica si un visitante ha intentado cerrar la sesión |

## createAccount

Se activa cuando un comprador intenta crear una cuenta.

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

### Nombre de evento XDM

`userAccount.createProfile`

### Tipo

Perfil

### Datos recopilados

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

## editAccount

Se activa cuando un comprador intenta editar una cuenta.

>[!NOTE]
>
> Este evento se activa cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.

### Nombre de evento XDM

`userAccount.updateProfile`

### Tipo

Perfil

### Datos recopilados

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

## searchRequestSent

Se activa mediante los siguientes eventos en la ventana emergente &quot;buscar mientras escribe&quot;:

- Pulse Intro
- Haga clic en _Ver todo_

Se activa mediante los siguientes eventos en las páginas de resultados de búsqueda:

- Seleccionar un filtro
- Cambiar el orden (_Ordenar por_)
- Cambiar la dirección de clasificación (ascendente o descendente)
- Cambiar el número de resultados por página (_Mostrar # por página_)
- Vaya a la página siguiente
- Vaya a la página anterior
- Navegar a otra página

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.

### Nombre de evento XDM

`searchRequest`

### Tipo

Buscar

### Datos recopilados

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchRequest` | Indica si se ha enviado una solicitud de búsqueda |
| `filter` | Indica si se aplicaron filtros para limitar los resultados de búsqueda |
| `attribute` (filtro) | La faceta de un elemento que se usa para determinar si se incluye en los resultados de búsqueda |
| `value` | Valores de atributo utilizados para determinar qué elementos se incluyen en los resultados de búsqueda |
| `isRange` | Cuando es verdadero, los valores indican los extremos de un rango aceptable de valores |
| `sort` | Indica cómo se deben ordenar los resultados de la búsqueda |
| `attribute` (ordenar) | Un atributo utilizado para ordenar elementos en los resultados de búsqueda |
| `order` | El orden en el que se devuelven los resultados de la búsqueda |
| `query` | Términos buscados |

## searchResponseReceived

Se activa cuando la búsqueda activa devuelve resultados para la página de resultados de búsqueda o de pov &quot;search as you type&quot;.

>[!NOTE]
>
>Los eventos de búsqueda no son compatibles con Adobe Commerce Enterprise Edition con el módulo B2B instalado.

### Nombre de evento XDM

`searchResponse`

### Tipo

Buscar

### Datos recopilados

En la tabla siguiente se describen los datos recopilados para este evento.

| Campo | Descripción |
|---|---|
| `searchResponse` | Indica si se ha recibido una respuesta de búsqueda |
| `suggestions` | Matriz de cadenas que incluyen los nombres de productos y categorías que existen en el catálogo y que son similares a la consulta de búsqueda |
| `numberOfResults` | El número de productos devueltos |
| `productListItems` | Una matriz de productos en el carro de compras. Incluye el `SKU`(Unidad de mantenimiento de existencias) y `name` del producto (nombre para mostrar o nombre legible en lenguaje natural). |
