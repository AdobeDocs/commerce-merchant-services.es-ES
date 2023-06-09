---
title: Finalizar compra
description: Personalice el cierre de compra para adaptarlo a las necesidades de sus clientes.
source-git-commit: b57c1e2b9d18ba3b843d18df7219efe3bade65e6
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Finalizar compra

Puede configurar el cierre de compra para Adobe Commerce [!DNL Payment Services] para adaptarse mejor a sus compradores. Funcionalidad como [orden de anulación automática](#order-auto-voided-if-error) y [depósito de tarjetas de crédito](#credit-card-vaulting) asegúrese de que sus compradores tengan una experiencia de usuario fluida.

## Pedido anulado automáticamente en caso de error

Si se produce un error durante la desprotección, [!DNL Payment Services] anula/cancela automáticamente el pedido.

Aparece un mensaje de error en la página de cierre de compra del comprador. El mensaje puede variar.

![Error al comprobar](assets/user-checkout-error.png "Error al retirar")

También aparece un comentario sobre el pedido cancelado en el Administrador de un específico [pedido](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en).

![Comentario de pedido cancelado en Administración para pedido](assets/admin-checkout-error.png "Comentario de pedido cancelado en Administración para pedido")

Si un comprador obtiene autorización para un pedido, pero el pedido no se creó ni se convirtió en un `Capture`, el orden se anula automáticamente. Este proceso garantiza que no se reserve crédito en la tarjeta de crédito del comprador y evita la tarifa del proveedor de pagos que se produce cuando la autorización se anula al final del período estándar de 29 días.

>[!NOTE]
>
>La anulación automática de pedidos solo se produce cuando el cliente utiliza un método de pago establecido en `Authorize` modo, no `Authorize and Capture` modo.

## Cierre de compra desde la página del producto

Cuando un cliente cierra la compra directamente desde la página del producto, usando PayPal o [!DNL Pay Later] botones, solo se compra el artículo representado en la página de producto actual. Los artículos que ya residen en el carro de compras del cliente no se agregan al flujo de cierre de compra y no se compran.

Esta función permite al cliente adquirir rápidamente el artículo que está viendo en ese momento, conservando los artículos que había añadido anteriormente al carro de compras.
Si el cliente cancela el pedido, el artículo de la página de producto actual se agrega al carro de compras del cliente.

Cuando un cliente introduce el flujo de cierre de compra desde la página del producto, la página de cierre de compra se simplifica: la vista solo muestra datos y opciones relacionados con el pedido.

## Bóveda de tarjetas de crédito

Los compradores pueden guardar la información de su tarjeta de crédito para futuras compras en el sitio web (cualquier tienda dentro de la cuenta del mismo comerciante).

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información
