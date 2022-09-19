---
title: Vacíos
description: Los vacíos permiten liberar los fondos en una cuenta de tarjeta de crédito o débito bloqueada o reservada por una autorización por el monto de una compra.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Vacíos

con [!DNL Payment Services], puede utilizar la funcionalidad de comercio existente para anular transacciones. Los vacíos permiten liberar los fondos en una cuenta de tarjeta de crédito o débito bloqueada o reservada por una autorización por el monto de una compra.

>[!NOTE]
>
>Solo puede anular una transacción si el pago aún no se ha capturado.

Si su tienda está [configurado](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para autorizar solo (no capturar) fondos en el punto de venta, una compra en la tienda resulta en un pedido con un `Processing` en el Administrador de comercio.

También puede [cancelar una solicitud](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target=&quot;_blank&quot;} que no se factura. Las autorizaciones no capturadas también se anulan como parte de ese proceso de cancelación.

>[!NOTE]
>
>La cancelación de un pedido también produce un vacío, pero la anulación de un pedido no déclencheur una cancelación.

Para obtener más información sobre los pasos básicos que sigue un pedido, consulte la [Flujo de trabajo de pedido](https://docs.magento.com/user-guide/sales/order-workflow.html){target=&quot;_blank&quot;} en la guía del usuario principal.

Para obtener más información sobre la funcionalidad void y cómo anular una transacción de pedido, consulte [Procesamiento de un pedido](https://docs.magento.com/user-guide/sales/order-processing.html){target=&quot;_blank&quot;} en la guía de usuario principal.
