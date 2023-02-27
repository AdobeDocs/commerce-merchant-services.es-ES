---
title: Configuración general
description: Configure las opciones generales para habilitar [!DNL Store Fulfillment] para su tienda. Configure las extensiones globales, los ajustes del sistema para el registro, la sincronización de datos y la seguridad. Proporcione datos clave para permitir la integración entre Adobe Commerce y los servicios de cumplimiento de la tienda.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 0%

---

# Configuración de servicio y ventas de tienda

Configurar [!DNL Store Fulfillment] de la variable [!DNL Commerce] El administrador para habilitar la extensión, especificar la configuración de la extensión, configurar los ajustes de seguridad para los usuarios de la aplicación de Store Assist y establecer las opciones para los métodos de envío.

>[!IMPORTANT]
>
>La configuración del servicio Store Fulfillment se aplica solo después de conectar la instancia de Adobe Commerce y la variable [!DNL Store Fulfillment] aplicación. Consulte [Conectar el cumplimiento de la tienda](connect-set-up-service.md).

## Administrar la configuración de los servicios de cumplimiento de la tienda

Administre la configuración de los servicios de cumplimiento de la tienda desde el [!DNL Commerce Admin Store Configuration] para abrir el Navegador.

- Habilite la extensión, configure la configuración global y especifique las opciones de seguridad para las conexiones de usuario y cuentas de la aplicación Store Assist seleccionando **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

   ![Configuración de los servicios de la tienda de administración para el cumplimiento de la tienda](assets/store-services-admin-sf-config.png)

- Configurar métodos de entrega seleccionando **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

   ![Configuración de ventas de la tienda de administración para el cumplimiento de la tienda](assets/store-sales-admin-sf-deliver-config.png)

## Configuración básica

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>El precio que cobra al cliente por la recogida en la tienda. El valor predeterminado es cero.</td>
<td>Sitio web</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>Radio, en kilómetros, que se utilizará cuando un comprador busque una ubicación de recogida en la tienda en el cierre de compra. Los resultados de la búsqueda solo devuelven almacenes ubicados dentro del radio de búsqueda especificado.</td>
<td>Sitio web</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Mensaje que se muestra cuando un cliente selecciona la recogida en la tienda de un artículo que no está disponible para la captura en la tienda. Si es necesario, puede personalizar el texto predeterminado.
</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>La variable [!UICONTROL Search Radius] solo se usa si ha configurado la variable [configuración de ubicación y asignación de tiendas](store-location-map-provider-setup.md) para Adobe Commerce.

## Habilitar la solución de entrega de tiendas

Active la variable [!DNL Store Fulfillment] solución para añadir las funciones de recogida en tienda y en la zona de cierre de compra a las experiencias de compra y cierre de compra de su tienda de Adobe Commerce.

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Habilite o deshabilite la solución. Cuando esté habilitado, configure y use las funcionalidades de cumplimiento de la tienda y establezca la conexión entre su tienda Adobe Commerce y [!DNL Store Fulfillment] servicios. Cuando está desactivado, todas las funciones de entrega de la tienda están deshabilitadas y no hay comunicación entre Adobe Commerce y los servicios de entrega de la tienda. La información del pedido no se puede procesar ni recibir.</td>
<td>Sitio web</td>
<td>Sí</td>
</tr>
</tbody>
</table>

## Agregar credenciales de cuenta

<table>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Seleccione: <i>[!UICONTROL Sandbox]</i> o <i>[!UICONTROL Production]</i><br></br>Selección [!UICONTROL Sandbox] permite la comunicación con los servicios de cumplimiento en un entorno de prueba.<br></br>Selección [!UICONTROL Production] permite la comunicación con los servicios de realización en un entorno en directo.<br></br>Se le asigna un conjunto de credenciales para cada entorno y puede administrar ambos conjuntos en la misma instalación. <br></br>Guarde las credenciales antes de validar la conexión.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Dirección URL del extremo de la API de cumplimiento de Walmart Store. Debe ser la URL completa que se proporcione durante el proceso de incorporación. Los clientes de satisfacción de la tienda reciben tanto un Simulador para pruebas como una URL de producción. Al añadir los valores, asegúrese de copiar y pegar la dirección URL completa, incluida la barra diagonal "/".</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Dirección URL del extremo de autenticación de cumplimiento de Walmart Store. El valor debe ser la dirección URL completa que se proporcione durante el proceso de incorporación. Recibirá un Simulador para pruebas y una URL de producción. Al añadir los valores, asegúrese de copiar y pegar la dirección URL completa, incluida la barra diagonal "/".</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Su ID de comerciante único (inquilino) que se proporcionó durante el proceso de incorporación. Este ID se utiliza para enrutar los pedidos a fin de garantizar que sus tiendas comerciales los reciban.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>ID de integración único que se proporciona durante el proceso de incorporación. Este ID se utiliza para autenticar toda comunicación entre Adobe Commerce y los servicios de cumplimiento de la tienda</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>La clave de integración única proporcionada durante el proceso de incorporación. Esta clave se utiliza para autenticar toda comunicación entre Adobe Commerce y el servicio de cumplimiento de la tienda.</td>
<td>Global</td>
<td>Sí</td>
</tr>
</table>

Después de configurar la variable [!UICONTROL Account Credentials], seleccione <strong>[!UICONTROL Validate Credentials]</strong> para verificar y establecer una conexión con el servicio de cumplimiento de la tienda por primera vez.

## Configuración del registro

Los registros para los servicios de cumplimiento de la tienda están disponibles en el archivo de registro `var/log/walmart-bopis.log`.

Solicite al administrador del sistema que configure los entornos para permitir la gestión de excepciones de modo que las excepciones relacionadas con la API puedan capturarse a través del cortafuegos o la caché.

Dado que el archivo de registro de la aplicación puede crecer rápidamente, habilite el registro para la aplicación solo durante un breve periodo cuando sea necesario (por ejemplo, al solucionar problemas de cumplimiento de la tienda para un [!DNL Commerce] pedido. Esta configuración evita problemas de tiempo de respuesta en entornos de producción causados por archivos de registro grandes.

>[!TIP]
>
>Para las instalaciones locales de Adobe Commerce, pida al administrador del sistema que configure la rotación de registros para el `var/log/walmart-bopis.log` para minimizar el tamaño. Para las instalaciones locales de Adobe Commerce, consulte [Rotación de registro](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) en el _Guía de instalación de Adobe Commerce_. Para Adobe Commerce en proyectos de infraestructura en la nube, consulte [Ver y administrar registros](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>El modo de depuración se utiliza para aumentar la actividad registrada dentro de la integración. Cuando está desactivado, no se registra ninguna información de depuración. Cuando está habilitada, se registra toda la información de depuración <br></br>Todos los datos registrados se encuentran en el archivo : <pre>var/log/walmart-bopis.log</pre>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>

## Administrar sincronización de pedidos

Configure los ajustes para administrar la gestión de errores para la sincronización de pedidos, los atributos de catálogo que se utilizarán para la digitalización de códigos de barras durante la selección de pedidos y configurar los tamaños de lote de pedidos para la cola de entrega de tiendas.

Puede ver detalles sobre las operaciones de sincronización de pedidos desde el panel Administración de colas de cumplimiento de almacenamiento en el panel Administrador (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Administración de errores de sincronización

<table>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Especifica los intentos de reintento para una operación de sincronización de registros después de que se produzca un error crítico.<br></br>Los errores críticos se producen cada vez que la integración no obtiene una respuesta positiva del servicio de cumplimiento. Esto puede ocurrir cuando el servicio está inactivo o cuando hay un error en los datos de pedido que se están enviando.<br></br>Cuando se alcanza el umbral de reintentos, el elemento permanece en cola pero no se vuelve a procesar. Ver todos los elementos con errores de <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Administración en Administración. Para solucionar problemas de forma sistemática relacionados con errores, póngase en contacto con su administrador de cuentas.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Habilitar las notificaciones de error para recibir un correo electrónico cuando la variable [!UICONTROL Retry Critical Error Threshold] se alcanza para una solicitud. La notificación incluye todos los detalles disponibles sobre el error.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Una lista delimitada por comas de direcciones de correo electrónico de destinatario para notificaciones de error.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Especifica la plantilla de correo electrónico utilizada para notificar a los destinatarios los errores de sincronización de pedidos. Se proporciona una plantilla predeterminada. No admite personalización.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</table>

### Sincronización de pedidos

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>El atributo de catálogo que almacena el código analizable para los artículos correspondientes en sus ubicaciones de comercialización.<br></br>Si solo tiene una ubicación de comerciante existente, es probable que utilice códigos UPC, mientras que el canal de comercio electrónico identifica los productos por SKU. Si este es su escenario, seleccione el atributo de catálogo que contiene el código UPC.<br></br>Esta configuración garantiza que los pedidos enviados a los artículos de la lista de tiendas con el identificador correcto para que los asociados de almacén puedan analizar los artículos con precisión durante el proceso de selección.<br></br>Si no está seguro, consulte con sus asociados de cumplimiento en el departamento de envío y selección para determinar qué atributo debe enviarse. Es posible que deba agregar el atributo apropiado al conjunto de atributos del producto de Adobe Commerce si el atributo no está incluido actualmente en la base de datos.</td>
<td>Sitio web</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>El atributo de catálogo que almacena el origen del código de barras para los artículos correspondientes en las ubicaciones de los comerciantes.<br></br>Esta configuración garantiza que los pedidos enviados a sus tiendas incluyan un identificador correcto para que los asociados de almacén puedan analizar con precisión los artículos durante el proceso de selección. Las opciones incluyen: SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Precio incrustado UPC.<br></br>Si no está seguro, seleccione la opción que se parezca más a los valores contenidos en su [!UICONTROL Barcode Source] atributo. Los asociados del almacén aún pueden hacer coincidir manualmente elementos de su lista de selección.</td>
<td>Sitio web</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>El número máximo de elementos que se envían desde la cola de satisfacción de la tienda al mismo tiempo.<br></br>Los pedidos BOPIS se envían al servicio de cumplimiento en lotes, a intervalos regulares. Esta configuración le permite controlar el tamaño del lote.<br></br>El valor predeterminado es de 100 elementos. Según el volumen y la capacidad del pedido, es posible que tenga que ajustar este valor hacia arriba o hacia abajo.</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>

## Habilitar las opciones de envío de la entrega de la tienda

Configure las opciones de envío de cumplimiento de la tienda que determinan la disponibilidad de las opciones de recogida y envío a domicilio en las tiendas de Adobe Commerce.

### Enviar a almacén

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>La configuración de envío a tienda se basa en sus capacidades de envío a tienda existentes. Si utiliza Inventory management, o si puede aceptar y realizar pedidos en ubicaciones comerciales sin inventario mediante transferencias de inventario entre tiendas, establezca esta opción en "Sí".<br></br>Si no puede admitir la opción de envío a almacén o no desea ofrecerla, establezca en "No". Cuando está desactivado, los artículos del catálogo con cero inventario para un almacén de mercadotecnia o los artículos que están por debajo de la ubicación [!DNL Out of Stock Threshold], no se ofrecen con opciones de recogida en la tienda.<br></br>Se trata de una configuración global que se puede ajustar por ubicación del comerciante.</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>

### Enviar desde tienda

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Habilita o deshabilita la opción Entrega a domicilio en las tiendas de mercaderes. Cuando está habilitado, las ubicaciones de los almacenes de mercadotecnia se tienen en cuenta en conjunto con otras fuentes asignadas en las existencias asociadas al sitio web.<br></br>En los servicios estándar de Inventory management, la variable [!DNL Ship from Store] es inherente y no se puede desactivar. Con la solución Store Fulfillment, puede activarla o desactivarla.<br></br>Este es un entorno global. También puede ajustar esta configuración por ubicación y producto del comerciante.</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>


## Administrar aplicaciones de cumplimiento de tiendas usar cuentas y permisos

Configure los ajustes de la cuenta de usuario y la seguridad de contraseña de la aplicación de cumplimiento de almacenamiento y la autenticación de dos factores.

### Seguridad de la aplicación

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>El intervalo de tiempo, en segundos, que una sesión de usuario asociado de tienda permanece activa antes del cierre de sesión automático. Los valores válidos van del 60 al 31536000.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Especifica el número de intentos de inicio de sesión fallidos permitidos antes de que una asociación de almacén se bloquee fuera de su cuenta.<br></br>Para desactivar el bloqueo de cuenta, establezca el valor en 0.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Número de minutos para bloquear una cuenta después de un error de inicio de sesión.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Requiere que el usuario cambie su contraseña después de configurar la cuenta.<br></br><em>[!UICONTROL No]</em>: Recomienda que el usuario cambie su contraseña después de configurar la cuenta.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Número de días que una contraseña sigue siendo válida antes de un cambio de contraseña requerido. Deje esta opción en blanco.</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>

## Métodos de envío

El cumplimiento de la tienda funciona ampliando el Adobe Commerce nativo [!DNL In-Store Delivery] capacidades. Después de instalar la extensión, puede configurar los métodos de envío en la tienda utilizando la siguiente configuración ampliada que se añade al administrador.

- **Selección en la tienda**: opciones de oferta para la entrega en la tienda durante el proceso de cierre de compra. Este es el escenario de entrega más común para los pedidos de BOPIS.

- **[!UICONTROL Curbside pick up]**-Opciones de oferta para que los clientes se estacionen en una ubicación de tienda y que su pedido les sea entregado por un asociado de tienda.

Configure estas opciones en Administración seleccionando <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>Para obtener información adicional sobre la configuración de las opciones de envío en la tienda, consulte [Entrega en la tienda](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) en el _Guía del usuario de Adobe Commerce_.


### Configuración de métodos de entrega

Con el método de entrega en la tienda, el cliente puede seleccionar un origen para utilizarlo como ubicación de recogida durante el cierre de compra.

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descripción</strong></td>
<td><strong>Ámbito</strong></td>
<td><strong>Requerido</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Habilite o deshabilite la opción de recogida en la tienda disponible durante el cierre de compra para los clientes que elijan la recogida en la tienda. Cuando la opción de recogida en la tienda está desactivada, no se muestra.<br></br>Esta configuración global se aplica a todas las ubicaciones de tiendas minoristas. Cuando está habilitado, puede desactivarlo de forma selectiva en la ubicación de la tienda minorista.</td>
<td>Sitio web</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Habilite o deshabilite la opción de recogida en la parte superior durante el proceso de cierre de compra para los clientes que elijan la opción de recogida en la tienda.<br></br>Esta configuración global se aplica a todas las ubicaciones de tiendas minoristas. Cuando está habilitado, puede desactivarlo de forma selectiva en la ubicación de la tienda minorista.</td>
<td>Sitio web</td>
<td>No</td>
</tr>
</tbody>
</table>

### Configuración del título del método de entrega

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
<td><strong>Título de la entrega a domicilio</strong></td>
<td>Especifica el título que se mostrará para la opción Entrega en casa en las áreas de producto, carro y cierre de compra. La entrega a domicilio se refiere a las funciones de envío estándar de Adobe Commerce, desde un almacén, por un operador o directamente a la dirección de envío proporcionada por el cliente. </br></br>Esta etiqueta no afecta a las etiquetas del método de envío para el transportista seleccionado.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Descripción de la entrega a casa</strong></td>
<td>Descripción opcional que se muestra siempre que se muestra a los clientes el Título de la entrega a domicilio. La mayoría de las veces, la descripción es un mensaje estático para comunicar las promesas de entrega. Algunos ejemplos:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Título de la colección de tiendas</strong></td>
<td>Cuando se presentan opciones de envío a un cliente y está disponible la recogida en la tienda, se muestra esta etiqueta. </br></br>Puede personalizar esta etiqueta, que se muestra en las áreas de producto, carro y cierre de compra.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<td><strong>Descripción de la colección de tiendas</strong></td>
<td>Donde quiera que se muestre el título de la colección de tiendas, puede incluir una descripción. Este mensaje estático ayuda a mejorar las comunicaciones de los clientes relacionadas con la experiencia de recogida de tiendas. Algunos ejemplos:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Título de colección en la tienda</strong></td>
<td>Cuando la opción de envío de almacenamiento está activada, este título se muestra a los clientes como opción de envío de recogida de almacenamiento. Puede personalizar su etiqueta.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<tr>
<td><strong>Título de colección de curvas</strong></td>
<td>Cuando la opción Recogida en Curbside está habilitada, los clientes ven la opción como un tipo de opción de envío de Recogida de tiendas. Puede personalizar su etiqueta aquí.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Instrucciones de recogida en la tienda</strong></td>
<td>Cuando un pedido está listo para ser recogido en sus tiendas minoristas, se notifica al cliente por correo electrónico. Si el cliente ha seleccionado [!DNL In-Store Pickup] durante el cierre de compra, puede personalizar las instrucciones de recogida aquí. </br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar las instrucciones en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Instrucciones de extracción en Curbside</strong></td>
<td>Especifica instrucciones de captura de pedidos personalizadas para incluir en las notificaciones de correo electrónico del cliente las solicitudes de recogida en la parte de la curva. </br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar las instrucciones en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Tiempo de espera estimado</strong></td>
<td>Número de minutos necesarios para recibir, completar y preparar la recepción de un pedido. Esta información se muestra al cliente al seleccionar una ubicación de tienda minorista para la opción de entrega de Recogida de tiendas . Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar el tiempo de espera en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Etiqueta de tiempo de recogida estimada</strong></td>
<td>Muestra el tiempo estimado hasta que un pedido esté disponible para la recogida de clientes. Esta información se muestra a los clientes cuando seleccionan una ubicación de tienda minorista para la variable [!DNL In-Store Pickup] opción de envío. </br></br>Al personalizar esta etiqueta, puede utilizar el código <code>%1</code> para insertar el <strong>Tiempo de espera estimado</strong>. Por ejemplo:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar el tiempo de espera en el nivel de ubicación de la tienda minorista.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Vista de la tienda</td>
<td>No</td>
<tr>
<td><strong>Renuncia de responsabilidad por el tiempo de recogida</strong></td>
<td>Contenido mostrado en la página del producto en la información del objeto que indica las horas de almacenamiento, las vacaciones, los cierres inesperados, etc.</td>
<td>Vista de la tienda
</td>
<td>No
</td>
</tr>
</tbody></table>

### Configuración de títulos de disponibilidad de stock

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
<td><strong>En existencias</strong></td>
<td>Cuando un cliente utiliza el localizador de tienda minorista, se muestra la disponibilidad del inventario para los artículos actuales para cada ubicación. </br></br>Puede personalizar el <em>[!UICONTROL in-stock]</em> etiqueta de estado aquí.</br></br></td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Fuera de existencias</strong></td>
<td>Cuando un cliente utiliza el localizador de tienda minorista, se muestra la disponibilidad de inventario de cualquier artículo actual para cada ubicación.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Parcialmente en existencias</strong></td>
<td>Cuando un cliente utiliza el localizador de tienda minorista, se muestra la disponibilidad de inventario para cualquier artículo actual en cada ubicación. </br></br>Puede personalizar el <em>[!UICONTROL partially in-stock]</em> etiqueta de estado aquí.</br></br></td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>

