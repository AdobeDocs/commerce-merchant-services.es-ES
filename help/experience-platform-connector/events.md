---
title: Eventos
description: Descubra qué eventos capturan datos y vea la definición completa del esquema.
source-git-commit: 566abe09b8c1b0837a833b2f8fcfe1e81bb6963d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Eventos de señalización del proyecto

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

>[!NOTE]
>
> La variable `Sign In`, `Sign Out`, `Create Account`y `Update Account` se activan cuando se intenta realizar la acción específica. No indica que la acción se haya realizado correctamente.
