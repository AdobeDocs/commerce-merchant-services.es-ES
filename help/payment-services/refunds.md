---
title: Reembolsos
description: Crear reembolsos para [!DNL Payment Services] pedidos del administrador como parte del proceso de abono.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Reembolsos

Reembolsos para [!DNL Payment Services] los pedidos se crean en el administrador como parte del proceso de abono. Una nota de abono es un documento que muestra la cantidad que se debe al cliente, para un reembolso total o parcial, que puede aplicarse a una compra o reembolsarse directamente al cliente. Las notas de crédito solo pueden emitirse para pedidos que [facturado](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}.

Consulte [Notas de Abono](https://docs.magento.com/user-guide/sales/credit-memos.html){target=&quot;_blank&quot;} en nuestra guía de usuario principal para obtener más información y aprender a emitir e imprimir notas de crédito.

Para pedidos procesados con PayPal o una tarjeta de crédito, puede:

* Devolver todo el importe del pedido
* Devolver una cantidad parcial de un pedido (o varias cantidades parciales)
* Devolver un importe menor que el valor de un artículo de pedido específico

Consulte [Emisión de una Nota de Crédito](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target=&quot;_blank&quot;} en nuestra guía de usuario principal para obtener más información.

>[!NOTE]
>
>Se produce un error en los pedidos procesados con tarjeta de crédito o PayPal si se intenta reembolsar parcialmente un pedido por un importe superior al importe del pedido restante (importe original menos el total de reembolsos existentes), o si se emite un reembolso por un importe bueno superior al importe total del pedido.

La variable [!UICONTROL Payment Action] en [!UICONTROL Payment Settings] configuration: o bien `Authorize` o `Authorize and Capture`—determina la variable [flujo de trabajo de devolución básico](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target=&quot;_blank&quot;} para pedidos.

Consulte la [Sección de configuración de acciones de pago](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;} de _Emisión de una Nota de Crédito_ para obtener más información.
