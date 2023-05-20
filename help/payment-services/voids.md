---
title: Vacíos
description: Las anulaciones le permiten liberar los fondos en una cuenta de tarjeta de crédito o débito que están bloqueados o mantenidos a un lado por una autorización para el importe de una compra.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Vacíos

Con [!DNL Payment Services], puede utilizar la funcionalidad existente de Commerce para anular transacciones. Las anulaciones le permiten liberar los fondos en una cuenta de tarjeta de crédito o débito que están bloqueados o mantenidos a un lado por una autorización para el importe de una compra.

>[!NOTE]
>
>Solo puede anular una transacción si el pago aún no se ha registrado.

Si su tienda es [configurado](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para autorizar solo (no capturar) los fondos en el punto de venta, una compra en su tienda resulta en un pedido con una `Processing` en el Administrador de comercio.

También puede [cancelar una solicitud](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} que no se factura. Las autorizaciones no capturadas también se anulan como parte de ese proceso de cancelación.

>[!NOTE]
>
>La cancelación de un pedido también produce un vacío, pero la anulación de un pedido no déclencheur una cancelación.

Para obtener más información sobre los pasos básicos por los que pasa un pedido, consulte la [Flujo de trabajo de pedidos](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} tema en la guía del usuario principal.

Para obtener más información sobre la funcionalidad void y cómo anular una transacción de pedido, consulte [Procesamiento de un pedido](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} en la guía del usuario principal.
