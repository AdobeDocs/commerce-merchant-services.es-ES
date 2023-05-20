---
title: Informe de pagos
description: Utilice el informe Pagos para obtener una transparencia total del importe de pago, el volumen procesado y los informes detallados sobre la transacción para la reconciliación financiera.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 0%

---

# Informe de pagos

[!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] le ofrece informes completos para que pueda obtener una visión clara de los pedidos y pagos de su tienda.

![Vista de informes financieros](assets/reports-justpayouts.png)

Hay dos vistas de informes de pagos disponibles para que pueda ver información detallada sobre todos los pagos:

* **[Vista de visualización de datos de pagos](#payouts-data-visualization-view)**: gráfico disponible en la página de inicio de servicios de pago que es una representación visual de los importes agregados por día desde la vista de informe Pagos
* **[Vista de informe de pagos](#payouts-report-view)**: informe disponible en Pagos que muestra información detallada sobre los pagos de todas las transacciones

Las vistas de pagos muestran información completa sobre los pagos de un vistazo, lo que permite una total transparencia del importe del pago, el volumen procesado y la creación de informes detallados sobre la transacción para la reconciliación financiera.

>[!NOTE]
>
>Los informes de pagos solo muestran los pedidos capturados (la acción de pago se establece en [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method))—o [marcado como `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## Vista de visualización de datos de pagos

La vista de visualización de datos Pagos está disponible en la página de inicio de Servicios de pago. Es una representación visual de las cantidades agregadas por día del cuadro detallado [Vista de informe de pagos](#payouts-report-view).

En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** para ver el gráfico de visualización de datos de créditos frente a débitos y los promedios móviles a lo largo del tiempo.

![Visualización de datos de pago en el administrador](assets/payouts-report.png)

Clic **[!UICONTROL View Report]** para ir a la tabla detallada [Vista de informe de pagos](#payouts-report-view).

### Personalizar periodo de transacciones

De forma predeterminada, se muestran 30 días de transacciones.

Desde la vista de visualización de datos de pagos, puede personalizar el periodo de tiempo para las transacciones de pago que desee ver seleccionando un intervalo de fecha:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. La vista de visualización de datos Pagos se puede ver en la sección Pagos.
1. Haga clic en **[!UICONTROL Range]** filtro selector.
1. Elija el intervalo de fechas aplicable: 30 días, 15 días o 7 días.
1. Ver la información de transacciones de las fechas especificadas.

### Información de transacciones

Los importes de transacción para un intervalo de fechas seleccionado se muestran a la izquierda de la vista de visualización de datos Pagos. Las fechas del intervalo de fechas seleccionado se muestran en la parte inferior de la vista. Si no hubo pagos en una fecha en particular, esa fecha no aparecerá.

La vista de visualización de datos Pagos incluye la siguiente información.

| Datos | Descripción |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Rango de importes para las transacciones en un lapso de tiempo específico; datos en el eje Y (izquierda) |
| Intervalo de fechas | Intervalo de fechas para el lapso de tiempo especificado; datos en el eje X (inferior) |
| Crédito | Pagos por el período de tiempo especificado |
| Débito | Débitos (devoluciones) para el período especificado |
| Promedio móvil | Representación del pago promedio para cada fecha en el lapso de tiempo especificado |
| Neto para rango | Importe de pago neto para el lapso de tiempo especificado (rango) |

## Vista de informe de pagos

La vista Informe de pagos está disponible en la vista Pagos de Payment Services. Incluye toda la información disponible sobre los pagos de tu tienda. El [Vista de visualización de datos de pagos](#payouts-data-visualization-view) en Página de inicio de servicios de pago, se muestra una representación visual de los importes agregados por día en esta vista de informe más detallada.

En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** para ver la vista detallada del informe Pagos tabulares.

![Transacciones de pago en el administrador](assets/payouts-report-new.png)

Puede configurar esta vista, según las secciones de este tema, para presentar mejor los datos que desee ver.

Consulte los ID de pedido y transacción de comercio vinculados, los importes de transacción, el método de pago por transacción y mucho más, todo ello dentro del informe Pagos en el Administrador.

Puede descargar transacciones de pago en un formato de archivo .csv para su uso en software de contabilidad o gestión de pedidos existente.

>[!NOTE]
>
>Los datos mostrados en esta tabla se ordenan en orden descendente (`DESC`) de forma predeterminada, con `TRANS DATE`. El `TRANS DATE` es la fecha y hora en que se inició la transacción.

### Seleccionar fuente de datos

En la vista Informe de pagos, puede seleccionar el origen de datos—_[!UICONTROL Live]_o_[!UICONTROL Sandbox]_: para el que se desea ver los resultados del informe.

![Selección de fuentes de datos](assets/datasource.png)

If _[!UICONTROL Live]_es la fuente de datos seleccionada, donde puede ver información de informes de sus tiendas activas. If [!UICONTROL Sandbox]_ es la fuente de datos seleccionada, puede ver información del informe para su entorno de espacio aislado.

Las selecciones de fuentes de datos funcionan de la siguiente manera:

* Si no tiene ningún almacén que esté en el modo Activo, la selección de la fuente de datos toma el valor predeterminado _[!UICONTROL Sandbox]_.
* Si tiene tiendas (una o varias) en el modo Activo, la selección de la fuente de datos toma el valor predeterminado _[!UICONTROL Live]_.
* Las exportaciones de informes siempre respetan la selección de fuente de datos.

Para seleccionar la fuente de datos del informe Estado de Pagos del Pedido:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Clic **[!UICONTROL Data source]** y seleccione _[!UICONTROL Live]_o_[!UICONTROL Sandbox]_.

   Los resultados del informe se regeneran en función del origen de datos seleccionado.

### Ver transacciones

De forma predeterminada, se muestran 30 días de transacciones.

El número de filas devueltas en una búsqueda, o mostradas en los 30 días predeterminados de transacciones, se muestra encima de la cuadrícula de la vista Pagos junto con el filtro del selector de calendario de fechas de transacción.

Desplácese a la izquierda y a la derecha para ver [información para cada transacción de pago](#column-descriptions) en el informe diario, incluidos la fecha de transacción, el ID de referencia, el número de factura y los detalles del método de pago.

#### Personalizar periodo de transacciones

En la vista de informe Pagos, puede personalizar el periodo de tiempo de las transacciones de pago que desee consultar introduciendo fechas específicas o seleccionando un rango de fechas en el selector de fechas:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Haga clic en el filtro Selector de calendario de fechas de transacción.
1. Seleccione el intervalo de fechas aplicable.
1. Ver los estados de pagos en la cuadrícula para las fechas especificadas.

### Mostrar y ocultar columnas

La vista de informe Pagos muestra la mayoría de las columnas de información disponibles de forma predeterminada. Sin embargo, puede personalizar qué columnas ve en el informe.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Haga clic en _Configuración de columna_ icono (![icono de configuración de columna](assets/column-settings.png)).
1. Para personalizar qué columnas ve en el informe, marque o desmarque columnas en la lista.

   La vista de informe Pagos mostrará inmediatamente los cambios realizados en el menú Configuración de columna. Las preferencias de columna se guardarán y permanecerán en vigor si se aleja de la vista Informes.

### Descargar transacciones

Puede descargar un archivo .csv que contenga todas las transacciones visibles en la cuadrícula de la vista Pagos.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personalice el intervalo de fechas y el periodo de tiempo de sus transacciones](#customize-transactions-timeframe).
1. Haga clic en _Descargar_ (![](assets/icon-download.png)) icono.

Las transacciones de pago se descargan en formato .csv.

### Descripciones de columna

Los informes de pago incluyen la siguiente información.

| Columna | Descripción |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Proveedor de pago |
| [!UICONTROL Provider trans] | ID de transacción |
| [!UICONTROL Trans date] | Fecha y hora en que se inició la transacción |
| [!UICONTROL Type] | Tipo de transacción—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Consulte [Tipos de transacciones](#transaction-types) para obtener más información. |
| [!UICONTROL Status] | Estado actual de la transacción—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Código de transacción que indica el crédito (*CR*) o débito (*DR.*) |
| [!UICONTROL Reference ID] | ID de transacción original con el que se relaciona este evento |
| [!UICONTROL Invoice] | ID de factura (uno por pedido) de la transacción |
| [!UICONTROL Commerce order] | ID de pedido de comercio <br> <br>Para ver información relacionada [información del pedido](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, haga clic en el ID. |
| [!UICONTROL Commerce trans] | ID de transacción comercial <br> <br>Para ver información relacionada [información de transacción](https://docs.magento.com/user-guide/sales/transactions.html){target="_blank"}, haga clic en el ID. |
| [!UICONTROL Pay method] | Tipo de tarjeta de crédito—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL APPLE_PAY]*, *[!UICONTROL CREDIT_CARD]*—y el proveedor de tarjetas asociado (como *Visa* o *MasterCard*) |
| [!UICONTROL Trans amt] | Importe de la transacción |
| [!UICONTROL Cur] | Unidad de divisa para importe de transacción |
| [!UICONTROL Pending] | Importe aún por desembolsar |
| [!UICONTROL Cur] | Unidad de divisa para el importe pendiente |
| [!UICONTROL Seller amt] | Importe de los fondos transferidos a o desde un cliente <br> <br>Los fondos que salen de la cuenta de vendedor muestran un prefijo guión (-). |
| [!UICONTROL Cur] | Unidad de divisa del importe del vendedor |
| [!UICONTROL Partner fee] | Tarifas de socio asociadas con la transacción <br> <br>Los fondos que se mueven fuera de la cuenta de cuota de socio muestran un prefijo guión (-). |
| [!UICONTROL Cur] | Unidad monetaria de la tarifa de socio |
| [!UICONTROL Prov fees] | Tarifas asociadas con la transacción <br> <br>Los fondos que salen de la cuenta de tarifas del proveedor muestran un prefijo guión (-). |
| [!UICONTROL Cur] | Unidad monetaria de la tarifa de proveedor |
| [!UICONTROL Fee %] | Porcentaje del importe de la transacción cargado como tarifa |
| [!UICONTROL Fixed fee] | Importe fijo de tarifa de proveedor |
| [!UICONTROL Chbk fee] | Cargo por devolución de cargo asociado con la transacción <br> <br>Un prefijo de guión (-) indica que se ha revertido la tarifa de contracargo. |
| [!UICONTROL Cur] | Unidad de divisa de la tarifa de refacturación |
| [!UICONTROL Hold amt] | Importe retenido o liberado de la suspensión <br> <br>Un prefijo de guión (-) indica que se están liberando fondos en espera. |
| [!UICONTROL Cur] | Unidad de divisa para el importe de retención |
| [!UICONTROL Recoup amt] | Importe recuperado de la cuenta de recuperación <br> <br>Los fondos que salen de la cuenta de recuperación muestran un prefijo guión (-). |
| [!UICONTROL Cur] | Unidad de divisa para el importe de recuperación |

### Tipos de transacciones

Estos tipos de transacciones se pueden anotar en las transacciones de pago.

| Informe | Descripción |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Dinero movido entre un comprador y un vendedor para un pedido |
| [!UICONTROL AUTH] | Transacciones de anulación de autorización y autorización |
| [!UICONTROL BONUS] | -- |
| [!UICONTROL CHARGEBACK] | Transacciones de reversión de comisión y comisión de reintegro |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | Comisiones de socios, cuotas de pago y transacciones de inversión de cuotas |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | Recuperaciones de cuentas bancarias o de pérdidas |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
