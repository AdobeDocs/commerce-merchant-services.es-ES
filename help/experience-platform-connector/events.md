---
title: Eventos
description: Descubra qué eventos capturan datos y vea la definición completa del esquema.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 15b7a8be65e5063606bb58755d0719b0ca54de37
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Eventos de conector de Experience Platform

A continuación se enumeran las [!DNL Commerce] eventos disponibles al instalar la extensión del conector del Experience Platform. Los datos que recopilan estos eventos se envían al perímetro de Adobe Experience Platform. También puede crear [eventos personalizados](custom-events.md) para recopilar datos adicionales no proporcionados de forma predeterminada.

Haga clic en el nombre del evento para ver la definición completa del esquema.

| Evento | Tipo |
|---|---|
| [Agregar al carro](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Tienda |
| [Ver carro de compras](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Tienda |
| [Ver página](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Tienda |
| [Ver producto](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Tienda |
| [Iniciar cierre de compra](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Tienda |
| [Completar cierre de compra](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | Tienda |
| [Iniciar sesión](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Perfil |
| [Cerrar sesión](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Perfil |
| [Crear cuenta](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Perfil |
| [Editar cuenta](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Perfil |
| [Solicitud de búsqueda enviada](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | Buscar |
| [Respuesta de búsqueda recibida](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | Buscar |

>[!NOTE]
>
> La variable `Sign In`, `Sign Out`, `Create Account`y `Update Account` se activan cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.
