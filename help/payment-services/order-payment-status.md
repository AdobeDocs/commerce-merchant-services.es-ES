---
title: Informe del estado del pago del pedido
description: Utilice el informe de estado de pago de pedidos para obtener visibilidad sobre el estado de pago de sus pedidos e identificar cualquier problema potencial.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 39c0140961fa9de5075087bbc3fbec0e14560860
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---

# Informe del estado del pago del pedido

[!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] ofrece informes completos para que pueda obtener una visión clara de los pedidos y pagos de su tienda.

![Vista Informes financieros](assets/report-view.png)

El informe de estado del pago de pedidos ayuda a comprender fácilmente dónde se encuentra un pedido específico en el flujo del proceso de efectivo. Este informe le permite ver rápidamente el estado de pago de sus pedidos e identificar cualquier problema potencial.

No es necesario abrir varias vistas para realizar manualmente pedidos de referencia y pagos. [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source] le permite obtener una vista de pájaro de sus pedidos y pagos, todo dentro del informe de estado del pago de pedidos .

Consulte estados de pago, estados facturados y enviados, estados de reembolso, estados de disputa, etc., todo dentro de este informe en el Administrador.

Puede descargar transacciones de estado de pago de pedidos en formato de archivo .csv para utilizarlas en software de gestión de pedidos o cuentas existente.

>[!NOTE]
>
>No puede ver los informes financieros si no lo ha hecho [modo Activo incorporado y activado](production.md#enable-live-payments) para [!DNL Payment Services].

## Datos utilizados en el informe

La variable [!DNL Payment Services] utiliza los datos de pedidos, y los combina con los datos de pago agregados de otras fuentes (incluyendo PayPal), para proporcionar informes significativos y altamente útiles.

Los datos del pedido se exportan y se mantienen en el servicio de pago. Cuando [cambiar o agregar estados de pedidos](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;} o [editar una vista de tienda](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [almacenar](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}, o nombre de sitio web, esos datos se combinan con los datos de pago y el informe de estado del pago del pedido se rellena con la información combinada.

Hay dos pasos en este proceso:

1. El índice se cambia con los datos `ON SAVE` (cada vez que se cambia la información del pedido o de la tienda) o `BY SCHEDULE` (en una programación cron preconfigurada), según cómo esté configurada en [Administración de índices](https://docs.magento.com/user-guide/system/index-management.html){target=&quot;_blank&quot;} en Admin.

   De forma predeterminada, se produce la indexación de datos `ON SAVE`, lo que significa que cada vez que algo cambia en el orden, el estado del pedido, la vista del almacén, el almacén o el sitio web, el proceso de reindexación se produce inmediatamente.

1. Los datos indexados se envían al servicio de pago, que luego se rellena en el informe de estado de pago del pedido.

Los únicos datos que se exportan y recopilan a efectos de presentación de informes son los datos utilizados por el informe Estado del pago del pedido.

>[!NOTE]
>
>Los datos mostrados en esta tabla se ordenan en orden descendente (`DESC`) de forma predeterminada, con la variable `ORDER DATE`. La variable `ORDER DATE` es la marca de fecha y hora en la que se creó el pedido.

### Configuración de la exportación de datos

Aunque, de forma predeterminada, la reindexación se produce en `ON SAVE` , se recomienda indexar en `BY SCHEDULE` en el menú contextual. La variable `BY SCHEDULE` El índice se ejecuta en un programa cron de un minuto y los datos modificados aparecen en el informe de estado del pedido en un plazo de dos minutos a partir de cualquier cambio de datos. Esta reindexación programada le ayuda a reducir cualquier presión en su tienda, especialmente si tiene un gran volumen de pedidos entrantes, ya que ocurre en una programación (no a medida que se realiza cada pedido).

Puede cambiar el modo de índice:`ON SAVE` o `BY SCHEDULE`—[en el](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}.

Para obtener información sobre cómo configurar la exportación de datos, consulte [Configuración de la línea de comandos](configure-cli.md#configure-data-export).

## Disponibilidad

En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** para ver los estados de pago de sus pedidos.

![Estados de pago de pedidos en el Administrador](assets/order-payment-status-report.png)

## Seleccionar fuente de datos

En la vista Informe de estado de pago del pedido, puede seleccionar la fuente de datos:_[!UICONTROL Live]_o_[!UICONTROL Sandbox]_: para el cual desea ver los resultados del informe.

![Selección de fuentes de datos](assets/datasource.png)

If _[!UICONTROL Live]_es la fuente de datos seleccionada, puede ver la información del informe de las tiendas que use [!DNL Payment Services] en_[!UICONTROL Live]_ en el menú contextual. If [!UICONTROL Sandbox]_ es la fuente de datos seleccionada; puede ver la información del informe para su entorno de espacio aislado.

Las selecciones de fuentes de datos funcionan de la siguiente manera:

* Si no tiene ninguna tienda que use [!DNL Payment Services] en el modo Activo, la selección de la fuente de datos toma como valor predeterminado _[!UICONTROL Sandbox]_.
* Si tiene alguna tienda (una o varias) que use [!DNL Payment Services] en el modo Activo, la selección de la fuente de datos toma como valor predeterminado _[!UICONTROL Live]_.
* Las exportaciones de informes siempre respetan la selección del origen de datos.

Para seleccionar la fuente de datos para su [!UICONTROL Order Payment Status] informe:

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Haga clic en **[!UICONTROL Data source]** y seleccione _[!UICONTROL Live]_o_[!UICONTROL Sandbox]_.

   Los resultados del informe se regeneran según la fuente de datos seleccionada.

## Personalizar intervalo de tiempo de fechas

Desde la vista Informe de estado de pago de pedidos , puede personalizar el intervalo de tiempo de los estados que desee ver seleccionando fechas específicas. De forma predeterminada, en la cuadrícula se muestran 30 días de estados de pago de pedidos.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Haga clic en el **[!UICONTROL Order dates]** filtro de selector de calendario.
1. Elija el intervalo de fechas aplicable.
1. Vea los estados de pago de pedidos para las fechas especificadas en la cuadrícula.

## Mostrar y ocultar columnas

El informe Estado de Pago de Pedido muestra todas las columnas de información disponibles de forma predeterminada. Sin embargo, puede personalizar qué columnas ve en el informe.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Haga clic en el _Configuración de columna_ icono (![icono de configuración de columna](assets/column-settings.png)).
1. Para personalizar qué columnas ve en el informe, marque o desmarque las columnas de la lista.

   El informe Estado del pago del pedido mostrará inmediatamente cualquier cambio que haya realizado en el menú Configuración de columna . Las preferencias de columna se guardarán y permanecerán en vigor si se sale de la vista del informe.

## Ver estados

La vista Informe de estado de pago de Pedido muestra información completa sobre el estado de transacción y el estado de pago de cada pedido de Servicios de Pago.

### Estado de la transacción

De forma predeterminada, en la cuadrícula se muestran 30 días de estados de pago de pedidos.

Desplácese a la izquierda y a la derecha para ver [información de estado del pago de pedido](#column-descriptions), incluida la fecha de pedido, la fecha autorizada, facturada, enviada, el estado de pago, etc.

El número de filas devueltas en una búsqueda, o mostradas en los 30 días predeterminados de los estados de pago del pedido, se muestran encima de la cuadrícula de vista Estado del pago del pedido junto al filtro Selector de calendario de fechas del pedido.

### Estado de pago

La columna Estado de pago muestra el estado actual de cualquier pago. A `Capture failed` el pago muestra un estado de alerta roja y un `Voided` el pago muestra un estado de alerta gris.

### Estado del reembolso

La columna Estado del reembolso muestra el estado actual de cualquier reembolso. A `Capture failed` el pago muestra un estado de alerta roja y un `Voided` el pago muestra un estado de alerta gris.

## Actualización de datos de informes

La vista del informe de estado de pago del pedido muestra un _[!UICONTROL Last updated]_marca de tiempo que muestra la última vez que se actualizó la información del informe. De forma predeterminada, los datos del informe de estado de pago del pedido se actualizan automáticamente cada tres horas.

También puede forzar una actualización manual de los datos del informe de estado de pago de pedidos para ver la información de informe más actualizada.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Haga clic en el _Actualizar_ icono (![icono actualizar](assets/refresh-button-med.png)).

   Los datos del informe de estado de pago del pedido se actualizan y *[!UICONTROL Update complete]* y la información más reciente está presente en la cuadrícula.

## Ver conflictos

Puede ver cualquier disputa sobre los pedidos de su tienda, y navegar al Centro de Resolución de PayPal para tomar medidas sobre ellos, desde el informe de estado del pago del pedido.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Vaya a la **[!UICONTROL Disputes column]**.
1. Ver las disputas de un pedido específico y ver [el estatuto de disputa](#order-payment-status-information).
1. Haga clic en el vínculo ID de disputa (comenzando por _PP-D_) para ir a la [Centro de resolución de PayPal](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. Adoptar las medidas apropiadas para la controversia, según sea necesario.

   Para ordenar los conflictos por estado, haga clic en el encabezado de la columna Disputas.

## Descargar estados de pago de pedido

Puede descargar un archivo .csv con todos los estados visibles en la cuadrícula de vista Estado del pago del pedido , independientemente de si está viendo los 30 días predeterminados de estados o un intervalo de tiempo personalizado.

1. En el _Administrador_ barra lateral, vaya a **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Si desea ver los estados de un intervalo de tiempo distinto a los últimos 30 días, [personalizar el intervalo de fechas para los estados](#customize-dates-timeframe).
1. Haga clic en el _Descargar_ (![icono de descarga](assets/icon-download.png)).

Los estados de pago del pedido se descargan en formato .csv .

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## Información de estado del pago de pedido

La vista Estado del pago del pedido muestra información exhaustiva sobre cada estado mostrado en la cuadrícula.

### Descripciones de columnas

Los informes de estado de pago de pedidos incluyen la siguiente información.

| Columna | Descripción |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID de pedido de comercio<br> <br>Para ver [información del pedido](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, haga clic en el ID. |
| [!UICONTROL Order Date] | Marca de fecha y hora del pedido |
| [!UICONTROL Authorized Date] | Marca de fecha y hora de la autorización de pago |
| [!UICONTROL Order Status] | Comercio actual [estado de pedido](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | Estado de factura del pedido—*[!UICONTROL No]*, *[!UICONTROL Partial]* o *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Estado de envío del pedido—*[!UICONTROL No]*, *[!UICONTROL Partial]* o *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Cantidad total general del pedido |
| [!UICONTROL Cur] | Tipo de divisa del pedido |
| [!UICONTROL Pay Status] | Estado del pago de una orden específica |
| [!UICONTROL Paid Amt] | Importe pagado en un pedido |
| [!UICONTROL Cur] | Tipo de divisa de la cantidad pagada en un pedido |
| [!UICONTROL Refund Status] | Estado de un reembolso de un pedido (como información de devoluciones, RMA y notas de crédito)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* o *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Total del importe reembolsado de una orden |
| [!UICONTROL Cur] | Tipo de divisa de la cantidad reembolsada para un pedido |
| [!UICONTROL Disputes] | Situación de cualquier litigio relativo a una orden (información de litigios y acusaciones)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* o *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Método de pago utilizado en la transacción de comercio para un pedido |
| [!UICONTROL Website] | Sitio web desde el cual se realizó el pedido |
| [!UICONTROL Store] | Almacén desde el que se realizó el pedido |
| [!UICONTROL Store View] | Vista de almacén desde la que se realizó el pedido |
