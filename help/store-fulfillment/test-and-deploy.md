---
title: Probar e implementar el cumplimiento de la tienda
description: Pruebe el plan para verificar la funcionalidad de cumplimiento de la tienda. Las pruebas abarcan la API de sincronización de inventario, el flujo de trabajo de cumplimiento completo para pedidos cancelados, la administración de usuarios de la aplicación de satisfacción de tienda y la experiencia de registro de cliente.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2652'
ht-degree: 0%

---


# Prueba e implementación del cumplimiento de la tienda para Adobe Commerce

Una vez que haya completado el proceso de incorporación en su entorno de desarrollo, puede iniciar el proceso para probar e implementar la solución de satisfacción de almacenamiento en su entorno de producción.

**Requisitos previos**

Antes de probar o sincronizar cualquier información, almacenamiento u pedido, compruebe que ha completado las siguientes tareas:

- Se ha completado el [Configuración general](enable-general.md) para los servicios de entrega de tiendas.

- [Agregue y valide las credenciales de la cuenta y los detalles de conexión para los entornos de simulación de pruebas y producción](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Confirme que la variable [Integración de Adobe Commerce](connect-set-up-service.md#configure-store-fulfillment-account-credentials) para la solución Store Fulfillment está disponible y autorizada.

## Preparación para pruebas

La configuración de la conexión debe completarse antes de poder crear pedidos de prueba o realizar pruebas de integración. Antes de realizar la prueba, también debe verificar que los datos del almacén estén sincronizados.

1. Sincronice las fuentes de descarga de la tienda.

   - Vaya a **[!UICONTROL Stores > Sources]**.

   - Select **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. Desde la cuadrícula de la tienda, compruebe que las tiendas estén marcadas como `Synced` antes de crear órdenes de prueba.

## Ejemplo de plan de prueba

Los comerciantes validan la funcionalidad básica de la solución de entrega de almacenamiento durante las fases de configuración y prueba de una implementación. Este plan de prueba de ejemplo proporciona un punto de partida para las pruebas. Añada escenarios adicionales según sus necesidades.

>[!NOTE]
>
>Después de completar la incorporación inicial para la solución de entrega de almacenamiento o actualizar una instalación existente, pruebe siempre la aplicación en un entorno que no sea de producción antes de implementarla en producción.

Este plan de ensayo de muestra abarca las siguientes áreas funcionales:

| Área funcional | Función | Función |
|-------------------------------------|------------------------------------------|----------------------------------|
| Sincronización de inventario y pedidos | Sincronización de API de inventario | Administrador de Adobe Commerce |
| De principio a fin | Flujos de trabajo de cancelación de pedidos | Asociado de cliente, administrador y tienda |
| Administrador | Permisos de la aplicación de cumplimiento de la tienda | Administrador |
| Adobe Commerce Frontend | Tipos de productos | Cliente, administrador |
| Cierre de compra en el front-end</br>Formulario de registro | Experiencia del registro | Cliente, administrador |
| Aplicación de asistencia de la tienda | Pedido</br>Seleccionar</br>Prueba</br>y Handoff | Asociado de tienda |




### Sincronización de API de inventario

Esta sección del plan de prueba cubre la sincronización de inventario y pedidos para comprobar que las actualizaciones de las fuentes de recogida y las existencias se sincronizan correctamente entre Adobe Commerce y la solución de entrega de tiendas.

**Área funcional**: Sincronización de inventario y pedidos</br>
**Función:** Administrador</br>
**Tipo de prueba:** Todos los positivos

<table>
<thead>
<tr>
<th>Función</th>
<th>Escenario de prueba</th>
<th>Resultados esperados</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Agregar origen de existencias de recogida</strong></td>
<td>Guarde una nueva fuente de existencias de recogida.</td>
<td>La sincronización en tiempo real envía los detalles de origen al servicio de GIF de Walmart en un plazo de 5 minutos.</td>
</tr>
<tr>
<td><strong>Actualizar el origen de existencias de recogida existente</strong></td>
<td>Guarde las actualizaciones en una fuente de existencias de recogida existente.</td>
<td>La operación de sincronización en tiempo real envía los detalles al GIF de Walmart en un plazo de 5 minutos</td>
</tr>
<tr>
<td><strong>Fuente de stock de recogida</br><code>Is Synced</code> status</br><code>Is Synced</code></strong></td>
<td>Guarde las actualizaciones en una fuente de existencias de recogida existente.</td>
<td>Después de una operación correcta, la variable <code>Is Synced</code> de la página Administrar origen <code>No</code> a <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>Proceso de reserva de existencias modificado</strong></td>
<td>Cree y envíe un nuevo pedido de un producto.</td>
<td>La cantidad vendible del producto disminuye en consecuencia.</td>
</tr>
<tr>
<td><strong>Nueva solicitud push, sincronización de API: pedido del cliente</strong></td>
<td>El cliente envía un pedido de recogida de tienda.</td>
<td><ul><li>En la vista Orden de administración, una <strong>Usuario administrador de Adobe Commerce</strong> ve que el estado de sincronización de pedidos se ha actualizado a <code>Sent</code></li><li>El registro de detalles del pedido incluye el mensaje <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nuevo pedido push, sincronización de API: el administrador envía el pedido</strong></td>
<td>Un Adobe Commerce <strong>Administrador</strong> envía un pedido de recogida.</td>
<td><ul><li>En la vista Orden de administración, el estado de sincronización de pedidos se actualiza a <code>Sent</code>.</li><li>El registro de detalles del pedido incluye el mensaje <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nueva inserción de pedido, cola de excepción<strong></td>
<td>Identifique varios productos virtuales y descargables en el administrador de Adobe Commerce que se puedan completar a través de Adobe Commerce sin necesidad de interactuar con el servicio de cumplimiento (FaaS).</td>
<td>Estos productos se eliminan o se marcan correctamente en la exportación para evitar un conflicto descendente con los FaaS.</td>
</tr>
</tbody>
</table>

### Flujos de trabajo de cancelación de pedidos

Esta sección del plan de prueba incluye escenarios para probar el flujo de trabajo de extremo a extremo de los pedidos que se cancelan a través de Adobe Commerce.

**Área funcional:** Administrador de Adobe Commerce</br>
**Función:** De principio a fin (administrador, asociado de tienda, cliente)</br>
**Tipo de resultado de la prueba:** Positivo para todos los escenarios

<table style="table-layout:fixed">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Cancelación total del pedido</strong></td>
<td><ol>
<li>Realizar pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe la creación de la factura (si se autoriza y captura) y la recepción del correo electrónico de la factura.</li>
<li>Cree una nota de crédito con todos los productos pedidos desde la vista Factura.</li>
</ol>
</td>
<td>
<ul>
<td>
<li>Historial de pedidos actualizado con <code>We refunded $X online. Transaction ID: transactionID</code> y <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>El estado del pedido es <code>Closed</code>. (Hemos establecido REVISIÓN DE PAGOS ahora).</li>
<li>Nota de crédito creada en Adobe Commerce. (Espere hasta que cron funcione).</li>
<li>Si todos los artículos han sido seleccionados, listo para recibir correo electrónico <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> el indicador es <code>true</code>.)</li>
<li>Si no se han seleccionado todos los artículos, cancele el correo electrónico y el programa HISTORIAL MOSTRAR COMENTARIO . <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> el indicador es <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>Cancelación parcial de pedido<strong></td>
<td>
<ol>
<li>Realice un pedido con al menos dos productos.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Espere dos horas para la liquidación de transacciones.</li>
<li>Crear nota de crédito con solo una parte de los productos pedidos desde la vista Factura.</li>
</td>
<td>
<ul>
<li>Actualización del historial de pedidos: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Actualización del historial de pedidos: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Recibo del correo electrónico de devolución del pedido: <code>$x amount was refunded</code></li>
<li>El estado del pedido es <code>Processing</code>.</li>
<li>Nota de crédito creada en Adobe Commerce (Esperar hasta que cron funcione).</li>
<li>Si no se seleccionaron algunos artículos, confirme que la variable [!UICONTROL Ready for Pickup] se muestra el correo electrónico con la sección nilpick o return . <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> el indicador es <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Preparado para la recogida</br></br>Cancelación completa</br>(todos los productos se establecen como seleccionados con 0 qty)</br></strong></td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Vaya a Postman y ejecute la solicitud Listo para la recogida con todos los productos configurados como <code>picked</code> con <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>Historial de pedidos actualizado: <code>We refunded $X offline</code></li>
<li>El estado del pedido es <code>CLOSED</code>.
<li>Se crea la nota de crédito. (Espere hasta que cron funcione).</li>
<li>Correo electrónico de reembolso recibido: <code>$x amount was refunded</code></li>
<li>Correo electrónico de cancelación de pedido enviado.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Listo para la recogida - Cancelación parcial</strong></br></br><strong>(Algunos productos se recogen y otros se recogen con <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Vaya a Postman y ejecute la solicitud Listo para la recogida con parte de los productos configurados como seleccionados con 0 qty y el resto de ellos seleccionados.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> con [!UICONTROL Ready for Pickup Items] y [!UICONTROL Canceled Items] tablas. </li>
<li>El estado del pedido está LISTO PARA RECOPILACIÓN. </li>
<li>Historial de pedidos actualizado: <code>We refunded $X offline.</code>
<li>Historial de pedidos actualizado: <code>Order notified as partly canceled at: Date and hour</code>
<li>Correo electrónico de reembolso recibido: <code>$x amount was refunded</code>
<li>Se crea la nota de abono. (Espere hasta que cron funcione).</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Listo para la recogida - Cancelación parcial</br></br>Algunos productos se recogen y otros se recogen con <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Vaya a Postman y ejecute la solicitud Listo para la recogida con parte de los productos configurados como seleccionados con 0 qty y el resto de ellos seleccionados.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> con [!UICONTROL Ready for Pickup Items] y [!UICONTROL Canceled Items] tablas. </li>
<li>El estado del pedido está LISTO PARA RECOPILACIÓN. </li>
<li>Historial de pedidos actualizado: <code>We refunded $X offline.</code>
<li>Historial de pedidos actualizado: <code>Order notified as partly canceled at: Date and hour</code>
<li>Correo electrónico de reembolso recibido: <code>$x amount was refunded</code>
<li>Se crea la nota de abono. (Espere hasta que cron funcione).</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensados (durante la dispensación) </br></br>Cancelación completa (todos los productos se establecen como rechazados)</strong>
</td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Vaya a Postman y ejecute la solicitud Listo para la recogida con todos los productos configurados según se hayan seleccionado.</li>
<li>Abra el buzón y busque el correo electrónico Listo para la recogida . A continuación, haga clic en **[!UICONTROL Confirm Arrival]**.</li>
<li>Registrarse.</li>
<li>Vaya a Postman y ejecute la solicitud dispensada con todos los productos definidos como rechazados.</li>
</ol>
<td><ul>
<li>Historial de pedidos actualizado: <code>We refunded $X offline.</code></li>
<li>Correo electrónico de reembolso recibido: <code>$x amount was refunded</code></li>
<li>Estado establecido en <code>CLOSED</code>.</li>
<li>Nota de crédito creada. (Espere hasta que cron funcione).</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensados (durante la dispensación)</br></br>Cancelación parcial</br>(Algunos productos se dispensan; algunos se rechazan).</strong>
</br></td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Vaya a Postman y ejecute la solicitud Listo para la recogida con todos los productos definidos tal y como se han seleccionado.</li>
<li>Abra el buzón. Busque el correo electrónico preparado para la recogida y seleccione <code>Confirm Arrival</code>.</li>
<li>Registrarse.</li>
<li>Vaya a Postman y ejecute la solicitud dispensada con algunos productos configurados como dispensados y otros configurados como rechazados</li>
</ol>
</td>
<td>
<li>Historial de pedidos actualizado: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>Correo electrónico de reembolso recibido: <code>$x amount was refunded</code>
<li>Estado de pedido establecido en <code>Ready for pickup Dispensed</code>
<li>Nota de crédito creada. (Espere hasta que cron funcione).</li>
</td>
</tr>
<tr>
<td> <strong>Nuevo RMA después del retorno (completo)</strong>
</td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se ha creado (si se autoriza y captura) y que se ha recibido el correo electrónico de la factura.</li>
<li>Elija todos los productos con Postman.</li>
<li>Registrarse.</li>
<li>Haga un dispensario.</li>
<li>Vaya a order y seleccione<strong>[!UICONTROL Create returns]=
<li>Cree la RMA.</li>
</ol>
</td>
<td>
<ul>
<li>Se creó la RMA y se muestra debajo de la variable <strong>[!UICONTROL Returns]</b> en la vista Pedido.</li>
<li>El cliente recibió un correo electrónico de confirmación de RMA.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Nuevo RMA después del retorno — Parcial</strong>
</td>
<td>
<ol>
<li>Realice el pedido.</li>
<li>Espere hasta que se sincronice el pedido.</li>
<li>Compruebe que la factura se haya creado (si es de autorización y captura) y que el correo electrónico de la factura se haya recibido.</li>
<li>Elija todos los productos con Postman.</li>
<li>Registrarse.</li>
<li>Haga un dispensario.</li>
<li>Realice el pedido y seleccione  <strong>[!UICONTROL Create returns]</strong></li>
<li>Cree la RMA con parte de los productos pedidos.</li>
</ol>
<td>
<ul>
<li>RMA creada y mostrada debajo de <strong>[!UICONTROL Returns]</strong> en la vista Pedido.</li>
<li>El cliente recibió el correo electrónico de confirmación de RMA.</li>
<li>Después de crear RMA, obtenga la autorización de RMA: Desde el administrador, vaya a <strong>[!UICONTROL Sales > Returns]</strong>. Seleccione la RMA que ha creado y autorícela.</li>
<li>Compruebe que el cliente ha recibido el correo electrónico de confirmación de autorización de RMA.</li>
<li>Compruebe que el reembolso se añadió al historial de transacciones y pedidos.</li>
</ul>
</td>
</tr>
</table>


### Permisos de la aplicación de cumplimiento de la tienda

Esta sección del plan de prueba cubre la administración de cuentas para los usuarios de aplicaciones de cumplimiento de la tienda.

- Confirme que un asociado de almacén puede autenticarse con una nueva cuenta de usuario creada desde el administrador de Adobe Commerce.
- Confirme que las actualizaciones de cuentas existentes se aplican correctamente.

**Área funcional:** Administrador de Adobe Commerce</br>
**Función:** Administrador, asociado de almacén</br>
**Tipo de prueba:** Todos los positivos

<table style="table-layout:auto">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Administración de cuentas de usuario: crear cuenta</strong></br></br>
</td>
<td>
<ol>
<li><strong>Administrador</strong> — Inicie sesión en el administrador de Adobe Commerce</li>
<li>Vaya a <strong>[!UICONTROL System] &gt; Permisos de la aplicación de cumplimiento de la tienda &gt; Todos los usuarios de la aplicación de cumplimiento de la tienda</strong></li>
<li><strong>Agregar nuevo usuario.</strong></li>
</ol>
<td>
<ul>
<li>Cuenta creada correctamente.</li>
<li>La nueva cuenta de usuario se muestra en la sección [!UICONTROL Store Fulfillment Users] tablero.</li>
<li><strong>Asociado de tienda</strong> inicie sesión en la aplicación Store Assist con una nueva cuenta de usuario.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Administración de cuentas de usuario: actualizar cuenta de usuario existente</strong>
</td>
<td>
<ol>
<li>Inicie sesión en el administrador de Adobe Commerce con la cuenta de usuario del administrador.</li>
<li>Vaya a <strong>[!UICONTROL System] &gt; Permisos de la aplicación de cumplimiento de la tienda &gt; Todos los usuarios de la aplicación de cumplimiento de la tienda</strong>.</li>
<li>En la lista Cuenta de usuario , abra una cuenta de usuario activa existente seleccionando <strong>[!UICONTROL Edit]</strong>.
<li>Desactivar la cuenta cambiando <strong>[!UICONTROL Is Active]</strong> a <strong>No</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>En el <strong>[!UICONTROL Store Fulfillment App Users]</strong> tablero, el estado de la cuenta actualizada cambió a <strong>[!UICONTROL Inactive]</strong>.</li>
<li>El asociado de almacén no puede iniciar sesión en la aplicación de asistencia de tienda con las credenciales de cuenta inactivas.</li>
</ul>
</td>
</tr>
</table>

## Tipos de productos de Adobe Commerce

Los escenarios de prueba para los tipos de producto de Adobe Commerce verifican que los clientes vean la información correcta sobre los productos, las existencias y los métodos de entrega para diferentes tipos de productos:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] en la tienda de Adobe Commerce.

**Área funcional:** Adobe Commerce Frontend</br>
**Función:** Usuario de la aplicación de asistencia de la tienda (asociado de la tienda)</br>
**Tipo de prueba:** Todos los positivos

<table style="table-layout:auto">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Comentarios</th>
</tr>
<tr>
<td><strong>Productos configurables</strong>
</td>
<td>
<ul>
<li>Compruebe que el usuario solo puede ver esas opciones configurables, qué fuente está habilitada, qué stock está asignado y que hay algunos elementos en existencias; compruebe los productos secundarios.</li>
<li>Compruebe que, al seleccionar un almacén diferente, las opciones que no están disponibles se muestran como tachadas.</li>
<li>Compruebe que, si el usuario selecciona un almacén diferente, las opciones configurables quedan sin seleccionar.</li>
<li>Compruebe que si un producto configurable ya está en el carro de compras y un usuario selecciona un almacén diferente, el producto se muestra como no disponible.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Productos agrupados</strong>
</td>
<td>
<ul>
<li>Compruebe que los métodos Delivery y [!UICONTROL Add to cart] se desactivan para el cliente cuando todos los productos secundarios tienen
<code>qty</code> configure como <code>0</code>.</li>
<li>Compruebe que los métodos Delivery estén habilitados para el cliente cuando al menos uno de los productos secundarios haya <code>qty</code> configure como <code>0.</code></li>
<li>Compruebe que [!UICONTROL Store Pickup Delivery] es visible y está activo solo para los productos que tienen [!UICONTROL Available for Store Pickup] activada. (Compruebe el producto secundario).</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Productos virtuales</strong>
</td>
<td>
Compruebe que los productos virtuales no ofrecen la variable  [!UICONTROL In-store Pickup] método de envío.
<td></td>
</td>
</tr>
<tr>
<td><strong>Paquete de productos</strong>
</td>
<td>
<ul>
<li>Compruebe si al menos un producto secundario tiene [!UICONTROL Available for Store Pickup] está desactivada, la opción Store Pickup delivery no está disponible para el cliente.</li>
<li>Compruebe si al menos un producto secundario tiene [!UICONTROL Available for Home Delivery] está desactivada, la opción Entrega a casa no está disponible para el cliente.</li>
<li>Compruebe si al menos uno de los productos secundarios de un paquete no está en existencias, el paquete (producto principal) también se muestra como [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Experiencia del registro

Esta sección del plan de prueba cubre la experiencia de registro para los pedidos de recogida de tiendas para las siguientes capacidades:

- Contacto de recogida alternativo: compruebe el flujo de trabajo para añadir un [!UICONTROL Alternate Pickup Contact] y seleccionando un [!UICONTROL Preferred Contact] en los pedidos de la tienda.

- Formulario de registro: compruebe el flujo de trabajo para enviar una solicitud de registro para los pedidos de recogida de la tienda.

**Áreas funcionales:** Cierre de carro, Formulario de registro para pedidos de recogida de tienda</br>
**Función:** Administrador, cliente, asociado de tienda</br>
**Tipo de prueba:** Todos los positivos

### Contacto de recogida alternativo


**Área funcional:** Cierre de carro de compras</br>
**Función:** Cliente</br>
**Tipo de prueba:** Todos los positivos

<table style="table-layout:auto">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Contacto de recogida alternativo</br>
Registro</br><strong>
</td>
<td>
Un cliente envía un pedido con la opción Recogida en la tienda .</td>
<td>Durante el proceso de cierre de compra, el cliente ve la variable [!UICONTROL Alternate Pickup Contact] la opción en el paso Envío.
</td>
</tr>
<tr>
<td><strong>Contacto preferido de recogida alternativa, proteger</strong>
<td>
Un cliente envía un pedido con la opción Recogida en la tienda . Durante el cierre de compra, el cliente agrega un [!UICONTROL Alternate Pickup Contact].</td>
<td>Durante el proceso de cierre de compra, el cliente ve la variable [!UICONTROL Preferred Contact] en el paso de envío.</td>
</td>
</tr>
<tr>
<td><strong>Detalles de contacto de recogida alternativos, proteger</strong>
</td>
<td>
Un cliente envía un pedido con la opción Recogida en la tienda . Durante el cierre de compra, el cliente selecciona [!UICONTROL Alternate Pickup Contact] en el paso de envío.
</td>
<td>El cliente ve opciones de entrada para introducir detalles de contacto: [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]y [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Recogida alternativa, Proteger correo electrónico</strong>
</td>
<td>Un cliente envía un pedido con la opción Recogida en la tienda . Durante el cierre de compra, el cliente selecciona [!UICONTROL Alternate Pickup Contact] en el paso de envío, agrega los detalles de contacto y envía el pedido.</td>
<td>Tanto el cliente como el contacto alternativo reciben un correo electrónico de registro para el pedido.</td>
</tr>
<td><strong>Recogida alternativa, detalle del pedido</strong></td>
<td>Un cliente envía un pedido con la opción Recogida en la tienda . Durante el cierre de compra, el cliente selecciona [!UICONTROL Alternate Pickup Contact] en el paso de envío, agrega los detalles de contacto y envía el pedido.</td>
<td>El administrador ve la información de contacto adicional sobre el pedido guardado.</td>
</tr>
<tr>
<td><strong>Contacto de recogida alternativo, vista de orden de asociación de tienda</strong>
</td>
<td>Un cliente envía un pedido con la opción Recogida en la tienda . Durante el cierre de compra, el cliente selecciona [!UICONTROL Alternate Pickup Contact] en el paso de envío, agrega los detalles de contacto y envía el pedido.</td>
<td>El asociado de almacén puede ver la información de contacto adicional sobre el pedido en FaaS/ChaaS.</td>
</td>
</tr>
</tbody>
</table>

### Formulario de facturación


**Área funcional:** Formulario de registro</br>
**Función:** Cliente</br>
**Tipo de prueba:** Todos los positivos

<table style="table-layout:auto">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Comprobar en acción: enviar solicitud</strong>
</td>
<td>En el formulario de registro, un cliente completa todos los campos obligatorios y envía la solicitud.</td>
<td>El cliente recibe una respuesta de éxito.</td>
</tr>
<tr>
<td><strong>Comprobar en acción: ver detalles de solicitudes</strong></td>
<td>Un cliente envía correctamente una solicitud de registro.</td>
<td>El estado del pedido se actualiza en el sistema de FaaS y el Asociado de almacenamiento puede ver los detalles de la solicitud de registro en el FaaS.
</td>
</tr>
<tr>
<td><strong>Proteger en acción: enviar solicitud solo una vez</strong></td>
<td>Después de enviar una solicitud de registro para un pedido, un cliente selecciona el vínculo para registrarlo por segunda vez.</td>
<td>En el formulario de registro, el cliente no ve ninguna opción para editar o volver a enviar el formulario.</td>
</tr>
<tr>
<td><strong>Comprobar en acción: confirmar llegada</strong></td>
<td>Se marca un pedido de recogida en la tienda listo para su recogida en los FaaS. El cliente recibe un correo electrónico preparado para la recogida y selecciona [!UICONTROL Confirm Arrival].</td>
<td>El cliente ve el formulario de registro para el pedido.</td>
</tr>
</tbody>
</table>

## Aplicación de asistencia de la tienda

Esta sección del plan de prueba cubre escenarios para probar los flujos de trabajo de pedido, selección y entrega en la aplicación de asistencia de tienda.

**Área funcional:** Aplicación de asistencia de la tienda</br>
**Función:** Asociado de tienda</br>
**Tipo de prueba:** Todos los positivos

<table style="table-layout:auto">
<tr>
<th>Función</th>
<th>Situación</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td>
<strong>Ruta de acceso fácil de recoger de un solo pedido, recogida en el borde de la curva</strong></td>
<td>Elija artículos de una y varias cantidades. No hay nilpicks ni acopio en el lado de la curva (con ensayo).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Selección de varios pedidos: ruta feliz, recogida de curvas</strong></td>
<td>Artículos únicos y multicantidad. No hay nilpicks ni acopio en el lado del cursor (con ensayo)</td>
<td></td>
</tr>
<tr>
<td><strong>Selección de un solo pedido: recuperación de ruta feliz en la tienda</strong></td>
<td>Artículos únicos y multicantidad. No hay nilpicks ni se realiza la recogida en el lugar de almacenamiento (con ensayo)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Selección de varios pedidos: ruta feliz, recogida en la tienda</strong></td>
<td>Elija artículos de una y varias cantidades. No hay nilpicks ni acopio en el lado de la curva (con ensayo).</td>
<td></td>
</tr>
<tr>
<td><strong>Selección de un único pedido: ruta no feliz, recogida en la tienda</strong></td>
<td>Seleccionar elementos únicos y de varias cantidades con selección parcial y simple y, en su lugar, recoger (con ensayo)</td>
</td>
<td></td>
</tr>
<td><strong>Selección de varios pedidos: no es una recuperación feliz del lado de la curva de ruta</strong></td>
<td>Seleccionar elementos únicos y de varias cantidades con selección parcial y simple y, en su lugar, recoger (con ensayo)</td>
<td></td>
</tr>
<td><strong>Selección de pedido único: ruta no feliz, recogida de borde de la curva</strong></td>
<td>Seleccionar artículos de una sola y varias cantidades con selección parcial y sin acopio y acopio en el borde de la curva (con ensayo)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Pedido realizado: cancelado antes de la selección</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Pedido realizado: cancelado antes de la entrega</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Pedido colocado: buscar en módulo de pedido</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Pedido colocado: búsqueda y registro manual para la entrega</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Pedido realizado: todos los artículos no seleccionados o no disponibles marcados por el selector</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado con artículos de paquete -selección y entrega</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado - Mano desactivada con rechazo</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado - Mano cerrada con rechazo de todos los artículos</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>



## Implementación

Después de comprobar que la solución se ha configurado y probado según sus especificaciones, está listo para implementar desde el ensayo a la producción.

La implementación y las pruebas varían según la infraestructura y las capacidades.

>[!TIP]
>
>Para obtener instrucciones de implementación, listas de comprobación y prácticas recomendadas para Adobe Commerce en proyectos de infraestructura en la nube, consulte [Implementar la tienda](https://devdocs.magento.com/cloud/live/stage-prod-live.html) en la documentación para desarrolladores de Adobe Commerce.




















