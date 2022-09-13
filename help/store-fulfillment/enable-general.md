---
title: Configuración general
description: Configure las opciones generales para habilitar [!DNL Store Fulfillment] para su tienda. Configure las extensiones globales, los ajustes del sistema para el registro, la sincronización de datos y la seguridad. Proporcione datos clave para permitir la integración entre Adobe Commerce y los servicios de cumplimiento de la tienda.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: fda4620f57aa7aa9fb930b10f5717fee98983378
workflow-type: tm+mt
source-wordcount: '2518'
ht-degree: 0%

---

# Configuración de servicio y ventas de tiendas

Configurar[!DNL Store Fulfillment] para habilitar la extensión, especifique la configuración de la extensión, configure los ajustes de seguridad para los usuarios de la aplicación Store Assist y establezca las opciones para los métodos de envío.

>[!IMPORTANT]
>
>La configuración del servicio Store Fulfillment se aplica solo después de conectar la instancia de Adobe Commerce y la variable [!DNL Store Fulfillment] aplicación. Consulte [Conectar el cumplimiento de la tienda](connect-set-up-service.md).

Configure los servicios de cumplimiento de almacenamiento en el menú Configuración de almacén de administración de Adobe Commerce.

Acceda a la configuración para habilitar la extensión, configurar la configuración global y especificar las opciones de seguridad para las conexiones de usuario y cuentas de la aplicación Store Assist seleccionando **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

![Configuración de los servicios de la tienda de administración para el cumplimiento de la tienda](assets/store-services-admin-sf-config.png)

Acceda a la configuración para configurar los métodos de envío seleccionando **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

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
<td>Mensaje que se muestra cuando un cliente selecciona la recogida en la tienda, pero el método de entrega no está disponible. Si es necesario, puede personalizar el texto predeterminado.
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
<td>Habilite o deshabilite la solución. Cuando esté habilitado, configure y use las funcionalidades de cumplimiento de la tienda y establezca la conexión entre su tienda Adobe Commerce y los servicios de cumplimiento de la tienda. Cuando está desactivado, todas las funciones de entrega de la tienda están deshabilitadas y no hay comunicación entre Adobe Commerce y los servicios de entrega de la tienda. La información del pedido no se puede procesar ni recibir.</td>
<td>Global</td>
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
<td>Seleccione: <i>Sandbox</i> o <i>Producción</i><br></br> Sandbox se comunica con los servicios de cumplimiento en una prueba.La producción se comunica con un entorno interactivo. Uso <strong>only</strong> en producción.<br></br>Se le asigna un conjunto de credenciales para cada entorno y puede administrar ambos conjuntos en la misma instalación. <br></br>Guarde las credenciales antes de validar la conexión.</td>
<td>Global</td>
<td>Sí</td>
    </tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Dirección URL del extremo de la API de cumplimiento de Walmart Store. Debe ser la URL completa que se le proporcione durante el proceso de incorporación. Los clientes de satisfacción de la tienda reciben tanto un Simulador para pruebas como una URL de producción. Asegúrese de copiar/pegar la dirección URL completa, incluida la barra diagonal "/".</td>
<td>Global</td>
<td>Sí</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Dirección URL del extremo de autenticación de cumplimiento de Walmart Store. El valor debe ser la dirección URL completa que se le proporcione durante el proceso de incorporación. Recibirá un Simulador para pruebas y una URL de producción. Asegúrese de copiar/pegar la dirección URL completa, incluida la barra diagonal "/".</td>
<td>Global</td>
<td>Sí</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Su ID de comerciante único (inquilino) que se le proporcionó durante el proceso de incorporación. Su ID se utiliza para enrutar sus pedidos y garantiza que sus tiendas comerciales los reciban.</td>
<td>Global</td>
<td>Sí</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>Su ID de integración único. Se proporciona durante el proceso de incorporación. No cambia. Se utiliza para autenticar toda comunicación con los servicios de cumplimiento.</td>
<td>Global</td>
<td>Sí</td>
    </tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>La clave de integración única. Se proporciona durante el proceso de incorporación. Se utiliza para autenticar toda comunicación con los servicios de cumplimiento.</td>
<td>Global</td>
<td>Sí</td>
    </tr>
</table>

Después de configurar las credenciales de la cuenta, seleccione <strong>[!UICONTROL Validate Credentials]</strong> para verificar y establecer una conexión con el servicio web de cumplimiento por primera vez.

## Configurar el registro

Cuando el registro está habilitado, el archivo de registro se puede expandir rápidamente. Para evitar problemas de tiempo de respuesta en entornos de producción, asegúrese de habilitar el registro y habilite solo durante un breve periodo de tiempo cuando sea necesario.

Solicite al administrador del sistema que configure los entornos para permitir la gestión de excepciones de modo que las excepciones relacionadas con la API puedan capturarse a través del cortafuegos o la caché. También puede pedir al administrador del sistema que configure la rotación de registros en este archivo para minimizar el tamaño.

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
<td>El modo de depuración se utiliza para aumentar la actividad registrada dentro de la integración. Cuando está desactivado, no se registra ninguna información de depuración. Cuando está habilitada, se registra toda la información de depuración. Todos los datos registrados se encuentran en el archivo : `var/log/walmart-bopis.log`</td>
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
<td>Determina si se requiere un cambio de contraseña de usuario.<br></br>"Sí": Requiere que el usuario cambie su contraseña después de configurar la cuenta."No": Recomienda que el usuario cambie su contraseña después de configurar la cuenta.</td>
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

### Autenticación de dos factores

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
<td><strong>[!UICONTROL APP User 2FA]</strong></td>
<td>Habilite o deshabilite la autenticación de dos factores para asociados de tiendas. Cuando se habilita, se solicita a la asociada de almacén que proporcione una contraseña única generada por un proveedor de autenticación.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL APP 2FA Policy]</strong></td>
<td>Establece la directiva de aplicación para la autenticación de dos factores.<br></br><strong>[!UICONTROL Optional]</strong>: La asociada de tienda puede evitar la autenticación de dos factores si no hay ningún proveedor establecido.<br></br><strong>[!UICONTROL Mandatory]</strong>: El asociado de tienda es necesario para completar la autenticación de dos factores.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL 2FA Providers]</strong></td>
<td>Seleccione uno o varios servicios de proveedor de autenticación para ofrecer asociados de almacén. Para configurar la autenticación y la autenticación de dos factores, los asociados de la tienda deben instalar la aplicación de autenticación de uno de los proveedores disponibles instalados en sus dispositivos móviles.</td>
<td>Global</td>
<td>No</td>
</tr>
</tbody>
</table>

## Métodos de envío

El cumplimiento de la tienda funciona ampliando el Adobe Commerce nativo [!DNL In-Store Delivery] capacidades.
Después de instalar la extensión, hay disponibles opciones de configuración de administración adicionales para los métodos de envío en la tienda. Configure estas opciones adicionales en Administración seleccionando <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

En la configuración de cumplimiento de la tienda, puede configurar los siguientes métodos de envío para los pedidos de recogida en la tienda.

- **Selección en la tienda**: opciones de oferta para la entrega en la tienda durante el proceso de cierre de compra. Este es el escenario de entrega más común para los pedidos de BOPIS.

- **Toma de la curva**-Opciones de oferta para que los clientes se estacionen en una ubicación de tienda y que su pedido les sea entregado por un asociado de tienda.

>[!NOTE]
>
>Para obtener información adicional sobre la configuración de las opciones de envío en la tienda, consulte [Entrega en la tienda](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) en la Guía del usuario de Adobe Commerce.


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
<td>Especifica el título que se mostrará para la opción Entrega en casa en las áreas de producto, carro y cierre de compra. La entrega a domicilio se refiere a las funciones de envío estándar de Adobe Commerce, desde un almacén, por un operador o directamente a la dirección de envío proporcionada por el cliente.</br></br>Esta etiqueta no afecta al transportista de envío seleccionado ni a sus etiquetas de método de envío disponibles.</td>
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
<td>Cuando se presentan opciones de envío a un cliente y está disponible la recogida en la tienda, se muestra esta etiqueta.</br></br>Puede personalizar esta etiqueta, que se muestra en las áreas de producto, carro y cierre de compra.</td>
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
<td>Cuando un pedido está listo para ser recogido en sus tiendas minoristas, se notifica al cliente por correo electrónico. Si el cliente ha seleccionado [!DNL In-Store Pickup] durante el cierre de compra, puede personalizar las instrucciones de recogida aquí.</br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar las instrucciones en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Instrucciones de extracción en Curbside</strong></td>
<td>Especifica instrucciones de recogida de pedidos personalizadas para incluir en las notificaciones de correo electrónico del cliente las solicitudes de recogida de la parte de la curva.</br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar las instrucciones en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Tiempo de espera estimado</strong></td>
<td>Número de minutos necesarios para recibir, completar y preparar la recepción de un pedido. Esta información se muestra al cliente al seleccionar una ubicación de tienda minorista para la opción de entrega de Recogida de tiendas .</br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar el tiempo de espera en el nivel de ubicación de la tienda minorista.</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
<tr>
<td><strong>Etiqueta de tiempo de recogida estimada</strong></td>
<td>Muestra el tiempo estimado hasta que un pedido esté disponible para la recogida de clientes. Esta información se muestra a los clientes cuando seleccionan una ubicación de tienda minorista para la opción de entrega de Recogida de tiendas .</br></br>Al personalizar esta etiqueta, puede utilizar el código <code>%1</code> para insertar el <strong>Tiempo de espera estimado</strong>.Por ejemplo:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Se trata de una configuración global que se aplica a todas las ubicaciones de tiendas minoristas. También puede personalizar el tiempo de espera en el nivel de ubicación de la tienda minorista.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
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
<td><strong>n-Stock</strong></td>
<td>Cuando un cliente utiliza el localizador de tienda minorista, se muestra la disponibilidad de inventario para artículos actuales o no para la mayoría de las ubicaciones.</br></br>Aquí puede personalizar la etiqueta de estado "en existencias".</td>
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
<td>Cuando un cliente utiliza el localizador de tienda minorista, se muestra la disponibilidad de inventario para cualquier artículo actual en cada ubicación.</br></br>Aquí puede personalizar la etiqueta de estado "parcialmente en existencias".</td>
<td>Vista de la tienda</td>
<td>No</td>
</tr>
</tbody></table>
