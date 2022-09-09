---
title: Datos disponibles
description: Utilice los datos de los informes financieros para conciliar los informes con sistemas que no sean de comercio.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Datos disponibles

Hay disponibles algunos datos de pedidos y pagos para que pueda coordinar los informes financieros de Adobe Commerce en sistemas externos.

## Reconciliación con el sistema ERP

Puede conciliar los informes financieros de Adobe Commerce con el sistema de planificación de recursos empresariales (ERP) que no sea de Adobe mediante el ID de incremento asociado a un pedido específico.

Cuando los servicios de pago envían el pedido comercial a PayPal, el ID de incremento se incluye como la variable `custom_id`. La variable `custom_id` es visible en el detalle de actividad comercial para un pago y en el enlace web de PayPal.

`custom_id` en la parte inferior del detalle de actividad del comerciante para un pago:

![`custom_id` en detalles de actividad del comerciante](assets/merchant-activity.png)

`custom_id` en los detalles del weblock de PayPal:

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

Consulte la documentación de las API de REST de PayPal para obtener más información:

* [`purchase_unit` en el que `custom_id` reside](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
* [Mostrar detalles del pedido](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
