---
title: Correos electrónicos de ventas
description: Configure las plantillas de correo electrónico transaccional para comunicarse con los clientes y almacenar administradores durante el proceso de cumplimiento de los pedidos de recogida de tiendas.
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# Correos electrónicos de ventas

El cumplimiento de la tienda ofrece un conjunto ampliado de plantillas de correo electrónico transaccional para admitir los flujos de trabajo de pedidos y cumplimiento. Ofrecen comunicación y mensajería coherentes y automatizadas en todos los canales, notificando a los clientes y a los administradores de tiendas los cambios de estado de los pedidos, las instrucciones para los pedidos de recogida en la tienda, etc.

Las plantillas de correo electrónico de cumplimiento de almacenamiento están configuradas con la mensajería y la configuración predeterminadas. Los administradores de comerciantes en Adobe Commerce pueden administrar y modificar las configuraciones, y seleccionar las plantillas de correo electrónico para comunicarse con los clientes en diferentes escenarios. Los administradores también pueden configurar y personalizar plantillas.

Configure las plantillas de correo electrónico de ventas desde el administrador: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## Correos electrónicos: configuración general

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Envío asincrónico</strong></td>
<td>Deshabilite esta función. No se admite el envío asincrónico de correo electrónico. Para obtener el tiempo de comunicación y respuesta más rápido para la recogida de tiendas, envíe correos electrónicos inmediatamente en lugar de enviarlos por lotes. </td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>

## Pedido listo para recogida en tienda

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Habilitado</strong></td>
<td>Este correo electrónico se envía al cliente cuando el asociado de la tienda ha finalizado la selección de su pedido. Configúrelo en "No" para deshabilitar la notificación por correo electrónico. Si la plantilla de correo electrónico está deshabilitada, no impide que el asociado de almacén seleccione un pedido.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Pedido Listo Para Recogida De Remitentes De Correo Electrónico</strong></td>
<td>La identidad del remitente que se utiliza al enviar la notificación por correo electrónico.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Plantilla Pedido Listo Para Recogida De Correo Electrónico</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes registrados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>Plantilla de correo electrónico de pedido listo para la recogida para invitado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes invitados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Plantilla de correo electrónico de pedido listo para recoger para contacto de recogida alternativo</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a contactos adicionales nombrados en el pedido. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar pedido listo para la copia de correo electrónico de recogida a</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Pedido Listo Para Recogida De Un Método De Copia De Correo Electrónico</strong></td>
<td>El método de correo electrónico "copia de carbono" envía para su uso.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>


## El pedido se ha recogido en la tienda

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Habilitado</strong></td>
<td>Este correo electrónico se envía al cliente para confirmar que ha recogido su pedido de la tienda. Configúrelo en "No" para deshabilitar la notificación por correo electrónico. Si la plantilla de correo electrónico está desactivada, no impide que el cliente recopile un pedido.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>El Pedido Se Ha Recopilado Para El Remitente De Correo Electrónico</strong></td>
<td>La identidad del remitente que se utiliza al enviar la notificación por correo electrónico.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>La Plantilla De Correo Electrónico Del Pedido Se Ha Recopilado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes registrados. Se proporciona una plantilla predeterminada con la integración</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>La plantilla de correo electrónico del pedido se ha recopilado para el invitado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes invitados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Se Ha Recopilado Una Copia De Correo Electrónico A</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Se Ha Recopilado El Método De Copia De Correo Electrónico</strong></td>
<td>El método de correo electrónico "copia de carbono" enviar para utilizar.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>

## Pedido retrasado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Habilitado</strong></td>
<td>Este correo electrónico se envía al cliente para avisarle de un retraso en el procesamiento o la selección de su pedido en la tienda de mercadotecnia. Configúrelo en "No" para deshabilitar la notificación por correo electrónico. Si la plantilla de correo electrónico está desactivada, la función no impide que se retrase un pedido.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Solicitar remitente de correo electrónico retrasado
</strong></td>
<td>La identidad del remitente que se utiliza al enviar la notificación por correo electrónico.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Solicitar plantilla de correo electrónico retrasada</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes registrados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>Solicitar plantilla de correo electrónico retrasada para invitado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes invitados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar copia de correo electrónico retrasada de pedido a</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Método De Copia Retrasada De Pedido</strong></td>
<td>El método de correo electrónico "copia de carbono" enviar para utilizar.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>



## Pedido cancelado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Habilitado</strong></td>
<td>Este correo electrónico se envía al cliente para notificarles que su pedido se ha cancelado en la tienda de mercadotecnia. Establecer como <code>No</code> para desactivar la notificación por correo electrónico. Si la plantilla de correo electrónico está desactivada, esta función no impide que se cancele un pedido.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Solicitar remitente de correo electrónico cancelado
</strong></td>
<td>La identidad del remitente que se utiliza al enviar la notificación por correo electrónico.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Solicitar plantilla de correo electrónico cancelada</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes registrados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>Pedido cancelado para invitado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes invitados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar copia de correo electrónico cancelada de pedido a</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Pedido Cancelado Método De Copia</strong></td>
<td>El método de correo electrónico "copia de carbono" enviar para utilizar.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>


## Pedido parcialmente cancelado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Habilitado</strong></td>
<td>Este correo electrónico se envía al cliente para notificarles que parte de su pedido se ha cancelado en la tienda de mercadotecnia. Establecer como <code>No</code> para desactivar la notificación por correo electrónico. Si la plantilla de correo electrónico está desactivada, no impide que se cancele parcialmente un pedido.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Solicitar remitente de correo electrónico parcialmente cancelado
</strong></td>
<td>La identidad del remitente que se utiliza al enviar la notificación por correo electrónico.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Plantilla de correo electrónico parcialmente cancelada de pedido</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes registrados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>Plantilla de correo electrónico parcialmente cancelada para contacto de recogida alternativo</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a contactos adicionales nombrados en el pedido. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Pedido parcialmente cancelado para invitado</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los clientes invitados. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar copia de correo electrónico parcialmente cancelada a</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Enviar Pedido Parcialmente Cancelado Método De Copia</strong></td>
<td>El método de correo electrónico "copia de carbono" enviar para utilizar.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>

## Enviar a tienda

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descripción</strong></th>
<th><strong>Ámbito</strong></th>
<th><strong>Requerido</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>El Pedido Tiene Enviar A Almacenar Productos Remitente De Correo Electrónico</strong></td>
<td>Correo electrónico enviado al personal de mercadotecnia especificado como informe agregado de todos los pedidos abiertos que no se pueden seleccionar en un almacén de mercadotecnia hasta que su inventario esté disponible. </br></br> Los comerciantes pueden utilizar este informe para iniciar y administrar las transferencias de inventario entre almacenes o la reposición. </br></br>Esta notificación solo se aplica cuando la variable [!DNL Ship-to-Store] están activadas.
</br></br>Esta etiqueta no afecta al transportista de envío seleccionado ni a sus etiquetas de método de envío disponibles.</br></br></td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Destinatarios De Correo Electrónico De Envío A Almacén</strong></td>
<td>Lista de direcciones de correo electrónico delimitada por comas para enviar una copia de cada notificación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Plantilla de correo electrónico</strong></td>
<td>La plantilla de mensaje de correo electrónico utilizada para notificar a los destinatarios. Con la integración se proporciona una plantilla predeterminada.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Si permite los pedidos anteriores, debe proporcionar una dirección de correo electrónico de administrador para recibir notificaciones sobre estos pedidos. Añada la dirección a las siguientes opciones de configuración: **[!UICONTROL Send Order Delayed Email Copy To]** en el [Retraso de pedido](#order-delayed) plantilla y [!UICONTROL Ship To Store Email Recipients] en el [Enviar a tienda](#ship-to-store) plantilla.



