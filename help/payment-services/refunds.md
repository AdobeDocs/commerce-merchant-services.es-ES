---
title: Reembolsos
description: Crear reembolsos para [!DNL Payment Services] pedidos en el administrador como parte del proceso de abono.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Reembolsos

Reembolsos por [!DNL Payment Services] Los pedidos se crean en el administrador como parte del proceso de abono. Una nota de abono es un documento que muestra el importe que se debe al cliente, para un reembolso completo o parcial, que se puede aplicar a una compra o reembolsar directamente al cliente. Las notas de abono solo se pueden emitir para pedidos que [facturado](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Consulte [Notas de abono](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} en nuestra guía de usuario principal para obtener más información y aprender a emitir e imprimir notas de crédito.

Para pedidos procesados con PayPal o una tarjeta de crédito, puede:

* Devolver el importe total del pedido
* Devolución de un importe parcial de un pedido (o de varios importes parciales)
* Devolución de una cantidad inferior al valor de un artículo de pedido específico

Consulte [Emisión de una nota de crédito](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} en nuestra guía del usuario principal para obtener más información.

>[!NOTE]
>
>Se produce un error en los pedidos procesados con PayPal o con tarjeta de crédito si intenta reembolsar parcialmente un pedido por un importe superior al importe del pedido restante (importe original menos el total de los reembolsos existentes) o si emite un reembolso por un importe superior al importe total del pedido.

El [!UICONTROL Payment Action] configuración en su [!UICONTROL Payment Settings] configuration: bien `Authorize` o `Authorize and Capture`: permite determinar el [flujo de trabajo básico de reembolsos](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} para pedidos.

Consulte la [Sección Configuración de acción de pago](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} de _Emisión de una nota de crédito_ para obtener más información.
