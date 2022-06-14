---
title: Configuración de la aplicación
description: '"Configure el [!DNL Store Assist] aplicación para administrar los flujos de trabajo y procesos de cumplimiento de la tienda end-to-end para la compra en línea, realizar pedidos en la tienda". '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Configuración de la aplicación

Store Assist es una aplicación de plataforma de cumplimiento como servicio (FaaS) basada en Walmart Commerce Technologies. La aplicación proporciona funciones de cumplimiento en la tienda para gestionar [!DNL buy online], [!DNL pick up in store] (BOPIS) órdenes.

La aplicación recibe toda la información sobre pedidos y clientes, desde los detalles de pedidos hasta los tiempos de recogida, y pone los datos a disposición de los asociados en línea, a través de dispositivos móviles. Con el asistente de tienda, los asociados de almacén pueden ver qué artículos pidieron los clientes, recogen los artículos correctos con mayor rapidez y configuran los pedidos completados para el envío de recogida en tienda o en el lado del límite a los clientes.

Store Associates utiliza el Store Assist [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]y [!UICONTROL Orders] para completar el siguiente proceso de administración de entrega y entrega:

- Asignación de fechas y horas de entrega de pedidos
- Reciba notificaciones de los clientes cuando lleguen a la tienda para que realicen la recogida
- Etapa de pedidos para entrega a clientes
- Seguimiento del estado de pedidos para todos los pedidos en las ubicaciones de tiendas asignadas

Consulte [Flujos de trabajo de cumplimiento de Store Assist](store-assist-modules.md) para obtener más información sobre la aplicación Store Assist.


## Configurar la aplicación de ayuda de la tienda

La aplicación de ayuda de la tienda requiere dos tipos de configuración:

- Configuración de administración de Adobe Commerce para [Administre cuentas de usuario, funciones de usuario y permisos de recursos desde la configuración del sistema de administración de Adobe Commerce](user-setup.md).

- Los ajustes de configuración de front-end para personalizar la interfaz de aplicación de Store Assist y otros ajustes, entre ellos:

   - **Marca de la aplicación de ayuda de la tienda**: personalice la interfaz de usuario de la aplicación con el logotipo y los colores de su empresa.

   - **Actualizar las instrucciones predeterminadas**: personalice las instrucciones que se muestran en las interfaces de Store Assist para los módulos Pick, Stage, Handoff y Order para que sus asociados sepan exactamente qué hacer durante cada paso del proceso de cumplimiento.

   - **Localización**: seleccione el idioma disponible para la aplicación, elija el formato de fecha y hora, seleccione las unidades de medida predeterminadas y la moneda predeterminada.

   - **Tiempo de inactividad**: especifique la cantidad de tiempo que la aplicación debe estar inactiva para que cierre la sesión.

   - **Cancelación de la tienda**: especifique si se pueden cancelar pedidos de la tienda y qué funciones tienen permisos de cancelación

   - **Ventana de limpieza de pedidos**: especifique cuánto tiempo ha pasado el tiempo de recogida programado que un pedido seleccionado permanece en el ensayo antes de ser rebloqueado, por ejemplo, tres días.

   - Personalizar todo en las instrucciones de la aplicación (selección, ensayo, desactivación)

   - **Recogida de notificaciones**-Configuración si desea que las notificaciones push comiencen a surtir una vez realizado el pedido

   - **Comprobar notificaciones**-Configurar si desea recibir notificaciones push una vez que un cliente haya iniciado sesión o esté esperando X minutos o no haya ninguna notificación

   - **Proceso de apagado manual**: habilite la firma del cliente, habilite una solicitud para comprobar el ID del cliente antes de transferir el pedido.

   - **Habilitar rechazo de elemento al realizar el envío**

   Trabaje con el equipo de Servicios al cliente de Walmart Commerce Technologies para completar la configuración de Frontend para la aplicación de ayuda al almacén.

## Descarga e instalación de aplicaciones

Una vez completada la configuración de la aplicación de asistencia de tienda, Store Associates puede descargar e instalar la aplicación de asistencia de tienda en sus dispositivos móviles e iniciar sesión.

- Descargue la aplicación de ayuda de la tienda desde la [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) o la tienda de Google Play.

- Store Associates requiere la siguiente información para iniciar sesión:

   - El nombre de la empresa asociado a su cuenta de Store Assist

   - Credenciales de cuenta de Store Assist: credenciales de nombre de usuario y contraseña para su cuenta.
   Un administrador de Adobe Commerce puede crear cuentas de usuario de la aplicación de ayuda de tienda para las ubicaciones de tiendas que tengan [Recogida en la tienda](merchant-store-configuration.md#pickup-location-configuration) activada en la configuración de las tiendas de administración.

