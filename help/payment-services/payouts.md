---
title: Informe de rutas
description: Utilice el informe de pagos para obtener una total transparencia en el importe del pago, el volumen procesado y los informes detallados sobre el nivel de transacción para la reconciliación financiera.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: aff1a43fedab473b84d02068a7d3fbd33b4fe093
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# Informe de rutas

[!DNL Payment Services] para Adobe Commerce y Magento Open Source le ofrece informes completos para que pueda obtener una visión clara de los pedidos y pagos de su tienda.

![Vista Informes financieros](assets/reports-view.png)

El informe de pagos muestra información completa de los pagos de un vistazo, lo que permite una total transparencia en el importe del pago, el volumen procesado y los informes detallados sobre el nivel de transacción para la reconciliación financiera.

No es necesario abrir varios tableros o vistas para hacer referencias cruzadas de pedidos y pagos, ni reconciliar cuentas. [!DNL Payment Services] para Adobe Commerce y Magento Open Source le permite realizar todas estas acciones desde un solo lugar (informe de pagos) para que pueda ver y administrar sus pagos de forma eficaz.

Consulte ID de transacción y pedidos de comercio vinculados, importes de transacción, método de pago por transacción y mucho más, todo dentro del informe Pagos en el Administrador.

Puede descargar transacciones de pago en formato de archivo .csv para utilizarlo en software de gestión de pedidos o cuentas existentes.

>[!NOTE]
>
>Los datos mostrados en esta tabla se ordenan en orden descendente (`DESC`) de forma predeterminada, con la variable `TRANS DATE`. La variable `TRANS DATE` es la fecha y hora en que se inició la transacción.

## Disponibilidad

En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![Transacciones de pago en el administrador](assets/payouts-report.png)

## Seleccionar fuente de datos

En la vista de informe de pagos, puede seleccionar la fuente de datos:_[!UICONTROL Live]_o [!UICONTROL Sandbox]_: para el cual desea ver los resultados del informe.

![Selección de fuentes de datos](assets/datasource.png)

If _[!UICONTROL Live]_es la fuente de datos seleccionada; puede ver la información de informes de las tiendas activas. If [!UICONTROL Sandbox]_ es la fuente de datos seleccionada; puede ver la información del informe para su entorno de espacio aislado.

Las selecciones de fuentes de datos funcionan de la siguiente manera:

* Si no tiene ninguna tienda en el modo Activo, la selección de la fuente de datos toma como valor predeterminado [!UICONTROL Sandbox]_.
* Si tiene alguna tienda (una o varias) en el modo Activo, la selección de la fuente de datos toma el valor predeterminado _[!UICONTROL Live]_.
* Las exportaciones de informes siempre respetan la selección del origen de datos.

Para seleccionar la fuente de datos para el informe Estado de pago de pedido:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Haga clic en **[!UICONTROL Data source]** y seleccione _[!UICONTROL Live]_o [!UICONTROL Sandbox]_.

   Los resultados del informe se regeneran según la fuente de datos seleccionada.

## Ver transacciones

De forma predeterminada, en la cuadrícula se muestran 30 días de transacciones.

El número de filas devueltas en una búsqueda, o mostradas en los 30 días de transacciones predeterminados, se muestra encima de la cuadrícula de vista Pagos junto al filtro Selector de calendario Fechas de transacción .

Desplácese a la izquierda y a la derecha para ver [información para cada transacción de pago](#column-descriptions) en el informe diario, incluidos la fecha de transacción, el ID de referencia, el número de factura y los detalles de método de pago.

### Personalización del intervalo de tiempo de las transacciones

Desde la vista Pagos, puede personalizar el intervalo de tiempo para las transacciones de pago que desee ver introduciendo fechas específicas o seleccionando un intervalo de fechas del selector de fechas:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Haga clic en el filtro Selector de calendario de fechas de transacción .
1. Elija el intervalo de fechas aplicable.
1. Vea los estados de las ganancias en la cuadrícula para las fechas especificadas.

## Descargar transacciones

Puede descargar un archivo .csv que contenga todas las transacciones visibles en la cuadrícula de vista de pagos.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personalización del intervalo de fechas para las transacciones](#customize-transactions-timeframe).
1. Haga clic en el _Descargar_ (![](assets/icon-download.png)).

Las transacciones de pago se descargan en formato .csv .

## Información de transacciones

La vista Pagos muestra información exhaustiva sobre cada transacción mostrada en la cuadrícula.

### Descripciones de columnas

Los informes de pago incluyen la siguiente información.

| Columna | Descripción |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Proveedor de pago |
| [!UICONTROL Provider trans] | ID de transacción |
| [!UICONTROL Trans date] | Fecha y hora en que se inició la transacción |
| [!UICONTROL Type] | Tipo de transacción—*[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Consulte [Tipos de transacciones](#transaction-types) para obtener más información. |
| [!UICONTROL Status] | Estado actual de la operación—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Código de transacción que indica Crédito (*CR*) o débito (*DR*) |
| [!UICONTROL Reference ID] | ID de transacción original para el que este evento está relacionado |
| [!UICONTROL Invoice] | ID de factura (uno por pedido) de la transacción |
| [!UICONTROL Commerce order] | ID de pedido de comercio <br> <br>Para ver [información del pedido](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, haga clic en el ID. |
| [!UICONTROL Commerce trans] | ID de transacción de comercio <br> <br>Para ver [información de transacción](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, haga clic en el ID. |
| [!UICONTROL Pay method] | Tipo de tarjeta de crédito—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*—y el proveedor de tarjetas asociado (por ejemplo, *Visa* o *MasterCard*) |
| [!UICONTROL Trans amt] | Importe de la transacción |
| [!UICONTROL Cur] | Unidad de divisa para el importe de transacción |
| [!UICONTROL Pending] | Cantidad pendiente de desembolso |
| [!UICONTROL Cur] | Unidad de divisa para el importe pendiente |
| [!UICONTROL Seller amt] | Importe de los fondos transferidos a un cliente o de éste <br> <br>Los fondos que salen de la cuenta de vendedor muestran un prefijo de guión (-). |
| [!UICONTROL Cur] | Unidad de divisa del importe del vendedor |
| [!UICONTROL Partner fee] | Tarifas de socio asociadas con la transacción <br> <br>Los fondos que se mueven fuera de la cuenta de tarifa de socio muestran un prefijo (-) de guión. |
| [!UICONTROL Cur] | Unidad de divisa para la tarifa del socio |
| [!UICONTROL Prov fees] | Tarifas asociadas con la transacción <br> <br>Los fondos que se mueven fuera de la cuenta de tarifa del proveedor muestran un prefijo de guión (-). |
| [!UICONTROL Cur] | Unidad de divisa para la tarifa del proveedor |
| [!UICONTROL Fee %] | Porcentaje del importe de la transacción cobrado como comisión |
| [!UICONTROL Fixed fee] | Cantidad fija de cuota de proveedor |
| [!UICONTROL Chbk fee] | Tarifa de recarga asociada con la transacción <br> <br>El prefijo de guión (-) indica que se ha invertido la tarifa de devolución de gastos. |
| [!UICONTROL Cur] | Unidad de divisa para la tasa de recarga |
| [!UICONTROL Hold amt] | Cantidad retenida o liberada de la suspensión <br> <br>El prefijo de guión (-) indica que se liberan fondos en espera. |
| [!UICONTROL Cur] | Unidad de divisa para el importe de retención |
| [!UICONTROL Recoup amt] | Importe recuperado de la cuenta de recuperación <br> <br>Los fondos que se mueven fuera de la cuenta de recuperación muestran un prefijo de guión (-). |
| [!UICONTROL Cur] | Unidad de divisa para el importe recuperado |

### Tipos de transacciones

Estos tipos de transacciones pueden anotarse en las transacciones de pago.

| Informe | Descripción |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Dinero movido entre un comprador y un vendedor para un pedido |
| [!UICONTROL AUTH] | Autorización y autorización anulan transacciones |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Transacciones de reversión de comisiones y comisiones de recarga |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Tarifas de socio, comisiones de pago y transacciones de inversión de comisiones |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Recuperaciones de cuentas bancarias o de pérdidas |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
