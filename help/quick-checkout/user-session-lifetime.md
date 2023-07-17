---
title: Duración de sesión de usuario
description: El administrador permite configurar la duración de las cookies del usuario de Adobe Commerce para [!DNL Quick Checkout] extensión.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Duración de sesión de usuario

La duración de una sesión de comprador está determinada por varios factores que puede configurar el administrador de Adobe Commerce. Consulte [Configuración de la duración de la cookie](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} para obtener más información.

La duración configurada de las cookies puede afectar a su [!DNL Quick Checkout] si:

1. Debido a la inactividad, la sesión del comprador se ha cerrado en Adobe Commerce.
1. El [!DNL Bolt] la sesión caduca.

Si un comprador realiza un pedido cuando su [!DNL Bolt] la sesión caduca, el pedido se realiza correctamente pero el usuario ha cerrado la sesión en ambas redes.

Si el usuario sigue activo después de un cierre de compra correcto, no se cerrará la sesión de tanto Adobe Commerce como [!DNL Bolt].
