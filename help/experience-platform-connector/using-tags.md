---
title: Recopilación de datos de comercio mediante etiquetas de Adobe Experience Platform
description: Obtenga información sobre cómo recopilar datos de comercio mediante etiquetas de Adobe Experience Platform.
exl-id: 852fc7d2-5a5f-4b09-8949-e9607a928b44
source-git-commit: 4af50842c883d3aef7bf50d6a68b82321b784591
workflow-type: tm+mt
source-wordcount: '2276'
ht-degree: 0%

---

# Recopilación de datos de comercio mediante etiquetas de Adobe Experience Platform

Aunque puede utilizar el conector del Experience Platform para publicar y suscribirse a eventos de tienda, es posible que algunos comerciantes ya estén utilizando una solución de recopilación de datos, como el [Etiquetas de Adobe Experience Platform](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en). Para estos comerciantes, Adobe Commerce proporciona una opción de solo publicación en el conector del Experience Platform que utiliza el SDK de Evento de Adobe Commerce.

![Flujo de datos del conector del Experience Platform](assets/tags-data-flow.png)
_Flujo de datos del conector del Experience Platform con etiquetas_

En este tema, aprenderá a asignar los valores de evento de tienda que proporciona el conector del Experience Platform a la solución de etiquetas de Adobe Experience Platform que ya está utilizando.

## Recopilación de datos de eventos de Adobe Commerce

Para recopilar datos de eventos de comercio:

- Instale el [SDK de eventos de Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-sdk). Para las tiendas PHP, consulte la [instalar](install.md) tema. Para ver las tiendas de los PWA Studio, consulte la [guía del PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

   >[!NOTE]
   >
   > Do **not** [configure](connect-data.md) el ID de organización y el ID de almacén de datos.

## Asignación de datos de tienda de comercio a Adobe Experience Platform

Para asignar datos de tienda de comercio a Adobe Experience Platform, configure e instale lo siguiente desde etiquetas de Adobe Experience Platform:

1. [Configuración de una propiedad de etiqueta](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) en la recopilación de datos de Adobe Experience Platform.

1. En **Creación**, seleccione **Extensiones** e instale y configure las siguientes extensiones:

   - [Capa de datos del cliente de Adobe](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [SDK web de Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [Publicar etiqueta](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) al entorno de desarrollo.

1. Siga las **Asignación de eventos** pasos a continuación para configurar elementos de datos y reglas para eventos específicos.

### Asignación de eventos

Como la recopilación de datos mediante etiquetas es diferente del uso del SDK de Evento de Adobe Commerce, es importante comprender los términos equivalentes que se utilizan en ambos marcos.

| Término de etiquetas de Adobe Experience Platform | Término del SDK de Adobe Commerce Event |
|---|---|
| _elementos de datos_ | context |
| _reglas_ | evento |
|  | _condiciones de regla_ - oyentes de eventos (de ACDL)<br><br>_acciones de regla_ : controladores de eventos (enviar a Adobe Experience Platform) |

Al actualizar los elementos de datos y las reglas en las etiquetas de Adobe Experience Platform con datos de evento específicos de Adobe Commerce, hay algunos pasos comunes que debe seguir.

Por ejemplo, vamos a agregar el Adobe Commerce `signOut` a las etiquetas de Adobe Experience Platform. Los pasos descritos a continuación, excepto para los valores específicos establecidos, describen cómo agregar [elementos de datos](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) y [reglas](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule), que se aplican a todos los eventos de Adobe Commerce que agregue a las etiquetas .

1. Crear un elemento de datos:

   ![Crear nuevo elemento de datos](assets/create-new-data-elements.png)
   _Crear nuevo elemento de datos_

1. Establezca **Nombre** a `sign out`.

1. Establezca **Extensión** a `Adobe Experience Platform Web SDK`.

1. Establezca **Tipo de elemento de datos** a `XDM object`.

1. Seleccione el **Sandbox** y **Esquema** que desea actualizar.

1. En **userAccount** > **cierre de sesión**, establezca la variable **value** en **Visitor Logout** a `1`.

   ![Actualizar el valor de Cerrar sesión](assets/signout-value.png)
   _Actualizar el valor de Cerrar sesión_

1. Select **Guardar**.

1. Crear una regla:

   ![Crear nueva regla](assets/create-new-rule.png)
   _Crear nueva regla_

1. Select **Agregar** under **EVENTOS**.

1. Establezca **Extensión** a `Adobe Client Data Layer`.

1. Establezca **Tipo de evento** a `Data Pushed`.

1. Select **Evento específico** y establezca la variable **Evento o clave para registrarse** a `sign-out`.

1. Select **Conservar cambios** para guardar la nueva regla.

1. Agregue una acción.

1. Establezca **Extensión** a `Adobe Experience Platform Web SDK`.

1. Establezca **Tipo de acción** a `Send Event`.

1. Establezca **Instancia** a `Alloy`.

1. Establezca **Tipo** a `userAccount.logout`.

1. Establezca **Datos XDM** a `%sign out%`.

1. Haga clic en **Guardar**.

   Ha creado un elemento de datos en el esquema para la variable `signOut` de Adobe Commerce. Además, ha creado una regla con una acción específica que debe producirse cuando se activa ese evento desde la tienda de Adobe Commerce.

Repita los pasos anteriores en etiquetas para cada uno de los eventos de Adobe Commerce que se describen a continuación.

### Eventos disponibles

Para cada uno de los eventos siguientes, asigne los eventos de Adobe Commerce a su XDM siguiendo los pasos anteriores.

- [`signOut`](#signout)
- [`signIn`](#signin)
- [`createAccount`](#createaccount)
- [`editAccount`](#editaccount)
- [&quot;pageView&quot;](#pageview)
- [&quot;productView&quot;](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [&quot;viewCart&quot;](#viewcart)
- [`removeFromCart`](#removefromcart)
- [`initiateCheckout`](#initiatecheckout)
- [`placeOrder`](#placeorder)

### signOut {#signout}

#### Elementos de datos

Cree el siguiente elemento de datos:

1. Cerrar sesión:

   - **Nombre**: `Sign out`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `userAccount` > `logout`
   - **Visitor Logout**: **Valor** = `1`

#### Reglas 

- **Nombre**: `Sign out`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `sign-out`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `userAccount.logout`
- **Datos XDM**: `%sign-out%`

### signIn {#signin}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Correo electrónico de la cuenta:

   - **Nombre**: `account email`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.emailAddress`

1. Tipo de cuenta:

   - **Nombre**: `account type`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.accountType`

1. ID de cuenta:

   - **Nombre**: `account id`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta***: `accountContext.accountId`

1. Iniciar sesión:

   - **Nombre**: `sign in`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `person` > `accountID`
   - **ID de cuenta**: **Valor** = `%account id%`
   - **Grupo de campos**: `person` > `accountType`
   - **Tipo de cuenta**: **Valor** = `%account type%`
   - **Grupo de campos**: `person` > `personalEmailID`
   - **Dirección de correo electrónico personal**: **Valor** = `%account email%`
   - **Grupo de campos**: `personalEmail` > `address`
   - **Dirección**: **Valor** = `%account email%`
   - **Grupo de campos**: `userAccount` > `login`
   - **Inicio de sesión de visitante**: **Valor** = `1`

#### Reglas 

- **Nombre**: `sign in`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `sign-in`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `userAccount.login`
- **Datos XDM**: `%sign in%`

### createAccount {#createaccount}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Correo electrónico de la cuenta:

   - **Nombre**: `account email`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.emailAddress`

1. Tipo de cuenta:

   - **Nombre**: `account type`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.accountType`

1. ID de cuenta:

   - **Nombre**: `account id`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.accountId`

1. Crear cuenta:

   - **Nombre**: `Create account`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `person` > `accountID`
   - **ID de cuenta**: **Valor** = `%account id%`
   - **Grupo de campos**: `person` > `accountType`
   - **Tipo de cuenta**: **Valor** = `%account type%`
   - **Grupo de campos**: `person` > `personalEmailID`
   - **Dirección de correo electrónico personal**: **Valor** = `%account email%`
   - **Grupo de campos**: `personalEmail` > `address`
   - **Dirección**: **Valor** = `%account email%`
   - **Grupo de campos**: `userAccount` > `createProfile`
   - **Creación de perfil de cuenta**: **Valor** = `1`

#### Reglas 

- **Nombre**: `Create account`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `create-account`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `userAccount.createProfile`
- **Datos XDM**: `%create account%`

### editAccount {#editaccount}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Correo electrónico de la cuenta:

   - **Nombre**: `account email`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.emailAddress`

1. Tipo de cuenta:

   - **Nombre**: `account type`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.accountType`

1. ID de cuenta:

   - **Nombre**: `account id`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `accountContext.accountId`

1. Editar cuenta:

   - **Nombre**: `Edit account`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `person` > `accountID`
   - **ID de cuenta**: **Valor** = `%account id%`
   - **Grupo de campos**: `person` > `accountType`
   - **Tipo de cuenta**: **Valor** = `%account type%`
   - **Grupo de campos**: `person` > `personalEmailID`
   - **Dirección de correo electrónico personal**: **Valor** = `%account email%`
   - **Grupo de campos**: `personalEmail` > `address`
   - **Dirección**: **Valor** = `%account email%`
   - **Grupo de campos**: `userAccount` > `updateProfile`
   - **Creación de perfil de cuenta**: **Valor** = `1`

#### Reglas

- **Nombre**: `Edit account`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `edit-account`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `userAccount.updateProfile`
- **Datos XDM**: `%edit account%`

### pageView {#pageview}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Nombre de la página:

   - **Nombre**: `page name`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `pageContext.pageName`

#### Reglas 

- **Nombre**: `page view`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `page-view`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `web.webPageDetails.pageViews`
- **Datos XDM**: `%page view%`

### productView {#productview}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Nombre del producto:

   - **Nombre**: `product name`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.name`

1. SKU de producto:

   - **Nombre**: `product sku`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.sku`

1. Moneda del producto:

   - **Nombre**: `product currency`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.currencyCode`

1. Código de moneda:

   - **Nombre**: `currency code`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('product currency') || _satellite.getVar('storefront').storeViewCurrencyCode
   ```

1. Precio especial:

   - **Nombre**: `special price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.specialPrice`

1. Precio regular:

   - **Nombre**: `regular price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.regularPrice`

1. Precio del producto:

   - **Nombre**: `product price`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price')
   ```

1. Vista del producto:

   - **Nombre**: `product view`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Select **Proporcionar elementos individuales** y haga clic en el botón **Agregar elemento** botón. Como esta vista es para un PDP, puede rellenar con un solo artículo.
   - **Grupo de campos**: `productListItems` > `name`
   - **Nombre**: **Valor** = `%product name%`
   - **Grupo de campos**: `productListItems` > `SKU`
   - **SKU**: **Valor** = `%product sku%`
   - **Grupo de campos**: `productListItems` > `priceTotal`
   - **Precio total**: **Valor** = `%product price%`
   - **Grupo de campos**: `productListItems` > `currencyCode`
   - **Código de moneda**: **Valor** = `%currency code%`
   - **Grupo de campos**: `commerce` > `productViews` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `product view`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `product-page-view`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.productViews`
- **Datos XDM**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Entrada de búsqueda

   - **Nombre**: `search input`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `searchInputContext.units[0]`

1. Buscar frase de entrada

   - **Nombre**: `search input phrase`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('search input').phrase;
   ```

1. Buscar clasificación de entrada

   - **Nombre**: `search input sort`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. Buscar filtros de entrada

   - **Nombre**: `search input filters`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. Solicitud de búsqueda:

   - **Nombre**: `search request`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `siteSearch` > `phrase`
   - **value**: Aún no está disponible
   - **Grupo de campos**: `siteSearch` > `sort`. Select **Proporcionar todo el objeto**.
   - **Grupo de campos**: `siteSearch` > `filter`. Select **Proporcionar todo el objeto**.
   - **Grupo de campos**: `searchRequest` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `search request sent`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `search-request-sent`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `searchRequest`
- **Datos XDM**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Resultados de la búsqueda:

   - **Nombre**: `search results`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `searchResultsContext.units[0]`

1. Resultados de la búsqueda:

   - **Nombre**: `search result number of products`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('search result').products.length;
   ```

1. Productos de resultados de búsqueda:

   - **Nombre**: `search result products`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. Sugerencias de resultados de búsqueda:

   - **Nombre**: `search result products`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. Respuesta de búsqueda:

   - **Nombre**: `search response`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `siteSearch` > `suggestions`. Select **Proporcionar todo el objeto**.
   - **Elemento de datos**: `%search result suggestions%`
   - **Grupo de campos**: `siteSearch` > `numberOfResults`
   - **value**: `%search result number of products%`
   - **Grupo de campos**: `productListItems`. Select **Proporcionar todo el objeto**.
   - **Elemento de datos**: `%search result products%`
   - **Grupo de campos**: `searchResponse` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `search response received`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `search-response-received`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `searchResponse`
- **Datos XDM**: `%search response%`

### addToCart {#addtocart}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Nombre del producto:

   - **Nombre**: `product name`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.name`

1. Sku del producto:

   - **Nombre**: `product sku`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.sku`

1. Código de moneda:

   - **Nombre**: `currency code`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.currencyCode`

1. Precio especial del producto:

   - **Nombre**: `product special price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.specialPrice`

1. Precio regular del producto:

   - **Nombre**: `product regular price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.regularPrice`

1. Precio del producto:

   - **Nombre**: `product price`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Carro de compras:

   - **Nombre**: `cart`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `shoppingCartContext`

1. ID del carro de compras:

   - **Nombre**: `cart id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Agregar al carro:

   - **Nombre**: `add to cart`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Select **Proporcionar elementos individuales** y haga clic en el botón **Agregar elemento** botón. Como esta vista es para un PDP, puede rellenar con un solo artículo.
   - **Grupo de campos**: `productListItems` > `name`
   - **Nombre**: **Valor** = `%product name%`
   - **Grupo de campos**: `productListItems` > `SKU`
   - **SKU**: **Valor** = `%product sku%`
   - **Grupo de campos**: `productListItems` > `priceTotal`
   - **Precio total**: **Valor** = `%product price%`
   - **Grupo de campos**: `productListItems` > `currencyCode`
   - **Código de moneda**: **Valor** = `%currency code%`
   - **Grupo de campos**: `commerce` > `cart` > `cartID`
   - **ID del carro de compras**: **Valor** = `%cart id%`
   - **Grupo de campos**: `commerce` > `productListAdds` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `add to cart`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `add-to-cart`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.productListAdds`
- **Datos XDM**: `%add to cart%`

### viewCart {#viewcart}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Tienda:

   - **Nombre**: `storefront`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `storefrontInstanceContext`

1. Carro de compras:

   - **Nombre**: `cart`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `shoppingCartContext`

1. ID del carro de compras:

   - **Nombre**: `cart id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Elementos de la lista de productos:

   - **Nombre**: `product list items:`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Ver carro:

   - **Nombre**: `view cart`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Para `productListItems`, puede haber varios elementos precalculados. Select **productListItems** > **Rellenar toda la matriz**.
   - **Elemento de datos**: `%product list items%`
   - **Grupo de campos**: `commerce` > `cart` > `cartID`
   - **ID del carro de compras**: **Valor** = `%cart id%`
   - **Grupo de campos**: `commerce` > `productListViews` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `view cart`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `shopping-cart-view`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.productListViews`
- **Datos XDM**: `%view cart%`

### removeFromCart {#removefromcart}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Nombre del producto:

   - **Nombre**: `product name`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.name`

1. Sku del producto:

   - **Nombre**: `product sku`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.sku`

1. Código de moneda:

   - **Nombre**: `currency code`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.currencyCode`

1. Precio especial del producto:

   - **Nombre**: `product special price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.specialPrice`

1. Precio regular del producto:

   - **Nombre**: `product regular price`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `productContext.pricing.regularPrice`

1. Precio del producto:

   - **Nombre**: `product price`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Carro de compras:

   - **Nombre**: `cart`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `shoppingCartContext`

1. ID del carro de compras:

   - **Nombre**: `cart id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Eliminar del carro de compras:

   - **Nombre**: `remove from cart`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Select **Proporcionar elementos individuales** y haga clic en el botón **Agregar elemento** botón. Como esta vista es para un PDP, puede rellenar con un solo artículo.
   - **Grupo de campos**: `productListItems` > `name`
   - **Nombre**: **Valor** = `%product name%`
   - **Grupo de campos**: `productListItems` > `SKU`
   - **SKU**: **Valor** = `%product sku%`
   - **Grupo de campos**: `productListItems` > `priceTotal`
   - **Precio total**: **Valor** = `%product price%`
   - **Grupo de campos**: `productListItems` > `currencyCode`
   - **Código de moneda**: **Valor** = `%currency code%`
   - **Grupo de campos**: `commerce` > `cart` > `cartID`
   - **ID del carro de compras**: **Valor** = `%cart id%`
   - **Grupo de campos**: `commerce` > `productListRemovals` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `remove from cart`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `remove-from-cart`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.productListRemovals`
- **Datos XDM**: `%remove from cart%`

### initiateCheckout {#initiatecheckout}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Tienda:

   - **Nombre**: `storefront`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `storefrontInstanceContext`

1. Carro de compras:

   - **Nombre**: `cart`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `shoppingCartContext`

1. ID del carro de compras:

   - **Nombre**: `cart id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Elementos de la lista de productos:

   - **Nombre**: `product list items`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Iniciar cierre de compra:

   - **Nombre**: `initiate checkout`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Para `productListItems`, puede haber varios elementos precalculados. Select **productListItems** > **Rellenar toda la matriz**.
   - **Elemento de datos**: `%product list items%`
   - **Grupo de campos**: `commerce` > `cart` > `cartID`
   - **ID del carro de compras**: **Valor** = `%cart id%`
   - **Grupo de campos**: `commerce` > `checkouts` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `initiate checkout`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `initiate-checkout`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.checkouts`
- **Datos XDM**: `%initiate checkout%`

### placeOrder {#placeorder}

#### Elementos de datos

Cree los siguientes elementos de datos:

1. Tienda:

   - **Nombre**: `storefront`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `storefrontInstanceContext`

1. Carro de compras:

   - **Nombre**: `cart`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `shoppingCartContext`

1. ID del carro de compras:

   - **Nombre**: `cart id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Pedido:

   - **Nombre**: `order`
   - **Extensión**: `Adobe Client Data Layer`
   - **Tipo de elemento de datos**: `Data Layer Computed State`
   - **[Opcional] ruta**: `orderContext`

1. Orden comercial:

   - **Nombre**: `commerce order`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. Envío de pedido:

   - **Nombre**: `order shipping`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. ID de promoción:

   - **Nombre**: `promotion id`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. Elementos de la lista de productos:

   - **Nombre**: `product list items`
   - **Extensión**: `Core`
   - **Tipo de elemento de datos**: `Custom Code`
   - **Abrir editor**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Realizar pedido:

   - **Nombre**: `place order`
   - **Extensión**: `Adobe Experience Platform Web SDK`
   - **Tipo de elemento de datos**: `XDM object`
   - **Grupo de campos**: `productListItems`. Para `productListItems`, puede haber varios elementos precalculados. Select **productListItems** > **Rellenar toda la matriz**.
   - **Elemento de datos**: `%product list items%`
   - **Grupo de campos**: `commerce` > `order`
   - **Identificador único**: **Valor** = `%commerce order%`
   - **Grupo de campos**: `commerce` > `shipping`
   - **Identificador único**: **Valor** = `%order shipping%`
   - **Grupo de campos**: `commerce` > `promotionID`
   - **ID de promoción**: **Valor** = `%promotion id%`
   - **Grupo de campos**: `commerce` > `purchases` > `value`
   - **value**: **Valor** = `1`

#### Reglas 

- **Nombre**: `place order`
- **Extensión**: `Adobe Client Data Layer`
- **Tipo de evento**: `Data Pushed`
- **Evento específico**: `place-order`

##### Acciones

- **Extensión**: `Adobe Experience Platform Web SDK`
- **Tipo de acción**: `Send event`
- **Tipo**: `commerce.order`
- **Datos XDM**: `%place order%`

## Configuración de identidad

Los perfiles del conector del Experience Platform se unen y se generan en función del `personID` y `personalEmail` campos de identidad en eventos de experiencias XDM. 

Si tiene una configuración anterior que depende de diferentes campos, puede seguir usándolos. Para definir los campos de identidad de perfil de conector de Experience Platform, debe definir los siguientes campos:

- `personalEmail` - Solo eventos de cuenta : siga los pasos descritos anteriormente para los eventos de cuenta
- `personID` - Todos los demás eventos:

   - Si ya está capturando `ECID` en las etiquetas , puede establecer `personID` en todas las reglas del SDK web de Adobe Experience Platform a `%ECID%`.
   - Para capturar `ECID` en las etiquetas , debe agregar una **Código personalizado** a las reglas de evento de envío siguiendo las [Documentación de etiquetas](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html). Consulte el ejemplo siguiente.

### Ejemplo

Las siguientes imágenes muestran cómo configurar un `pageView` evento con `personID` en el conector del Experience Platform:

1. Configure el elemento de datos con código personalizado para ECID:

   ![Configuración del elemento de datos con código personalizado](assets/set-custom-code-ecid.png)
   _Configuración del elemento de datos con código personalizado_

1. Añadir código personalizado ECID:

   ![Código para establecer ECID en un elemento de datos](assets/code-to-set-ecid.png)
   _Código para establecer ECID en un elemento de datos_

1. Actualice el esquema XDM con personID definido como ECID:

   ![Establezca personID como ECID](assets/set-personid-as-ecid.png)
   _Establezca personID como ECID_

1. Definir acciones de regla que recuperen ECID:

   ![Recuperar ECID](assets/rule-retrieve-ecid.png)
   _Recuperar ECID_

## Configuración del consentimiento

El consentimiento de recopilación de datos del conector Adobe Commerce y Experience Platform está habilitado de forma predeterminada. La exclusión se administra mediante la variable [`mg_dnt` cookie](https://docs.magento.com/user-guide/stores/cookie-reference.html). Puede seguir los pasos descritos aquí si decide utilizar `mg_dnt` para administrar el consentimiento. La variable [Documentación del SDK web de Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) tiene varias opciones adicionales para administrar el consentimiento.

1. Cree un **Código personalizado principal** elemento de datos (`%do not track cookie%`) para la variable `mg_dnt` cookie:

   ![Crear no rastrear elemento de datos](assets/element-dnt-cookie.png)
   _Crear no rastrear elemento de datos_

1. Cree un **Código personalizado principal** elemento de datos (`%consent%`) que devuelve `out` si la cookie está configurada y `in` de lo contrario:

   ![Crear elemento de datos de consentimiento](assets/element-consent-dnt-cookie.png)
   _Crear elemento de datos de consentimiento_

1. Configurar la extensión del SDK web de Adobe Experience Platform con `%consent%` elemento de datos:

   ![Actualizar SDK con consentimiento](assets/config-sdk-consent.png)
   _Actualizar SDK con consentimiento_

## Advertencias

- Si no se siguen los pasos para desactivar la recopilación de Experience Platform, los eventos se cuentan dos veces
- La no configuración de asignaciones/eventos como se describe en este tema puede afectar a los tableros de Adobe Analytics
- No puede configurar Target a través del conector del Experience Platform si la recopilación de datos está deshabilitada
