---
title: Datos disponibles
description: Utilice los datos de los informes financieros para conciliar los informes con sistemas que no sean de comercio.
role: User
level: Intermediate
source-git-commit: ed471f363546f1d337e85568dc5079cae4507840
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Datos disponibles

Hay disponibles algunos datos de pedidos y pagos para que pueda coordinar los informes financieros de Adobe Commerce en sistemas externos.

## Reconciliación con el sistema ERP

Puede conciliar los informes financieros de Adobe Commerce con el sistema de planificación de recursos empresariales (ERP) que no sea de Adobe mediante el ID de incremento asociado a un pedido específico.

Cuando los servicios de pago envían el pedido comercial a PayPal, el ID de incremento se incluye como la variable `custom_id` _y_ en el `invoice_id` (que también contiene una cadena aleatoria después de la variable `increment_id`).

Los ID son fácilmente accesibles tanto en los detalles de actividad del comerciante para un pago como en el enlace web de PayPal.

La variable `invoice_id` y `custom_id` se muestran cerca de la parte inferior del detalle de actividad del comerciante para un pago:

![`custom_id` en detalles de actividad del comerciante](assets/merchant-activity-ids.png)

`custom_id` y `invoice_id` en los detalles del weblock de PayPal:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Consulte la documentación de las API de REST de PayPal para obtener más información:

* [`purchase_unit`, en el que `custom_id` y `invoice_id` reside](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
* [Mostrar detalles del pedido](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
