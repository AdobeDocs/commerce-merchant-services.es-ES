---
title: Duración de la sesión del usuario
description: El administrador proporciona la capacidad de configurar la duración de la cookie de su usuario de Adobe Commerce para el [!DNL Quick Checkout] extensión.
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Duración de la sesión del usuario

La duración de una sesión de comprador está determinada por varios factores, que se pueden configurar en el administrador de Adobe Commerce. Consulte [Configurar la duración de la cookie](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} para obtener más información.

La duración configurada de las cookies puede afectar a su [!DNL Quick Checkout] si:

1. Debido a la inactividad, la sesión del comprador se cierra de Adobe Commerce.
1. La variable [!DNL Bolt] la sesión caduca.

Si un comprador realiza un pedido cuando su [!DNL Bolt] la sesión caduca, el pedido se coloca correctamente, pero se cierra la sesión del usuario en ambas redes.

Si el usuario sigue activo después de un cierre de compra exitoso, no se cerrará la sesión tanto de Adobe Commerce como de [!DNL Bolt].
