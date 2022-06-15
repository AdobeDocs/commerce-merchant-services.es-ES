---
title: Configuración de la aplicación
description: '"Configure el [!DNL Store Assist] aplicación para administrar los flujos de trabajo y procesos de cumplimiento de la tienda end-to-end para la compra en línea, realizar pedidos en la tienda". '
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Configuración de la aplicación

Store Assist es una aplicación de plataforma de cumplimiento como servicio (FaaS) basada en Walmart Commerce Technologies. La aplicación proporciona funciones de cumplimiento en la tienda para gestionar [!DNL buy online], [!DNL pick up in store] (BOPIS) órdenes.  Con el asistente de tienda, los asociados de almacén pueden ver qué artículos pidieron los clientes, recogen los artículos correctos con mayor rapidez y configuran los pedidos completados para el envío de recogida en tienda o en el lado del límite a los clientes.

La aplicación de asistencia de la tienda recibe toda la información sobre pedidos y clientes, desde los detalles de pedidos hasta los tiempos de recogida, y pone los datos a disposición de los asociados en línea, a través de dispositivos móviles. La aplicación incluye [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]y [!UICONTROL Orders] módulos para ayudar a Store Associates con actividades de cumplimiento como las siguientes:

- Asigne fechas y horas de entrega del pedido.
- Reciba notificaciones de los clientes cuando lleguen para la recogida de pedidos.
- Etapa los pedidos para su entrega a los clientes.
- Rastree el estado de los pedidos de todas las ubicaciones de tiendas asignadas.

>[!NOTE]
>
>Consulte [Flujos de trabajo de cumplimiento de Store Assist](store-assist-modules.md) para obtener más información sobre la aplicación Store Assist.

## Configurar la aplicación de ayuda de la tienda

La aplicación de ayuda de la tienda requiere dos tipos de configuración:

- Configuración de administración de Adobe Commerce para [administrar cuentas de usuario, funciones de usuario y permisos de recursos desde la configuración del sistema de administración de Adobe Commerce](user-setup.md).

- Los ajustes de configuración de front-end para personalizar la interfaz de aplicación de Store Assist y otros ajustes, entre ellos:

   - **Marca de la aplicación de ayuda de la tienda**: personalice la interfaz de usuario de la aplicación con el logotipo y los colores de su empresa.

   - **Actualizar las instrucciones predeterminadas**: personalice las instrucciones de las interfaces de Store Assist para los módulos Pick, Stage, Handoff y Order para cumplir con las políticas y procedimientos de su empresa, y guíe Store Associates a través de cada paso del flujo de trabajo de cumplimiento.

   - **Localización**: seleccione el idioma disponible para la aplicación. Elija el formato de fecha y hora y seleccione las unidades de medida predeterminadas y la moneda predeterminada.

   - **Tiempo de inactividad**: especifique la cantidad de tiempo que la aplicación debe estar inactiva antes de cerrar la sesión.

   - **Cancelación de la tienda**: especifique si se pueden cancelar pedidos de la tienda y qué funciones tienen permisos de cancelación

   - **Ventana de limpieza de pedidos**: especifique cuánto tiempo ha pasado el tiempo de recogida programado que un pedido seleccionado permanece en el ensayo antes de ser rebloqueado, por ejemplo, tres días.

   - Personalice todo en las instrucciones de la aplicación (selección, ensayo, desactivación).

   - **Recogida de notificaciones**-Especifique si desea enviar una notificación push para iniciar el proceso de selección después de que un cliente realice un pedido.

   - **Comprobar notificaciones**-Especifique si se debe enviar una notificación push durante el proceso de registro para los pedidos después de la facturación, después de que el tiempo de espera del cliente exceda un período de tiempo especificado. O bien, desactive la notificación.

   - **Proceso de apagado manual**: habilite procesos opcionales cuando Store Associate envía pedidos al cliente, por ejemplo, requiera una firma del cliente o solicite a la asociada que compruebe el ID del cliente.

   - **Habilitar rechazo de elemento al realizar el envío**-Permitir que los clientes devuelvan o cancelen artículos de pedido durante la entrega del pedido.

   Trabaje con el equipo de Servicios al cliente de Walmart Commerce Technologies para completar la configuración de front-end para la aplicación de asistencia al almacén.

## Descarga e instalación de aplicaciones

Una vez completada la configuración de la aplicación de asistencia de tienda, Store Associates puede descargar, instalar e iniciar sesión en la aplicación de asistencia de tienda desde sus dispositivos móviles.

- Descargue la aplicación de ayuda de la tienda desde la [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) o la tienda de Google Play.

- Store Associates requiere la siguiente información para iniciar sesión:

   - El nombre de empresa asociado a su cuenta de asistente de tienda

   - Credenciales de cuenta de Store Assist: credenciales de nombre de usuario y contraseña para su cuenta.
   Un administrador de Adobe Commerce puede crear una cuenta de usuario y establecer permisos para las cuentas de usuario de la aplicación de asistencia de tienda para las ubicaciones de tiendas que tengan [Recogida en la tienda](merchant-store-configuration.md#pickup-location-configuration) activada en la configuración de las tiendas de administración.

