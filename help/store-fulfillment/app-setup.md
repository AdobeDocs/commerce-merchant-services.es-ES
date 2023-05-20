---
title: Configuración de aplicación
description: Configure las variables [!DNL Store Assist] aplicación para administrar los flujos de trabajo y procesos de cumplimiento de tiendas de extremo a extremo para comprar en línea y recoger pedidos en tiendas.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Configuración de aplicación

Store Assist es una aplicación de plataforma de cumplimiento como servicio (FaaS) con tecnología de Walmart Commerce Technologies. La aplicación proporciona funciones de cumplimiento en la tienda para gestionar [!DNL buy online, pick up in store] (BOPIS) pedidos. Con la asistencia de tienda, los socios de tienda pueden ver qué artículos pidieron los clientes, recoger los artículos correctos más rápido y configurar pedidos satisfechos para la entrega de recogida en tienda o en la zona de la calle a los clientes.

La aplicación Store Assist recibe toda la información de pedidos y clientes (desde los detalles del pedido hasta las horas de recogida) y pone los datos a disposición de los asociados del almacén en línea, a través de dispositivos móviles. La aplicación incluye [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], y [!UICONTROL Orders] para ayudar a Almacenar se asocia con actividades de cumplimiento como las siguientes:

- Asignar fechas y horas de entrega de pedidos.
- Reciba notificaciones de clientes cuando lleguen para recoger el pedido.
- Realizar pedidos de entrega a los clientes.
- Rastree el estado de los pedidos de todos los pedidos en sus ubicaciones de tiendas asignadas.

>[!NOTE]
>
>Consulte [Flujos de trabajo de asistencia de almacenamiento](store-assist-modules.md) para obtener más información sobre la aplicación Store Assist.

## Configuración de la aplicación de asistencia de tienda

La aplicación Store Assist requiere dos tipos de configuración:

- Configuración del sistema de administración de Adobe Commerce para [administrar cuentas de usuario, funciones de usuario y permisos de recursos](user-setup.md), y [las selecciones de modelos y marcas de automóviles disponibles para los clientes durante el proceso de check-in](check-in-experience-setup.md).

- Ajustes de configuración de front-end para personalizar la interfaz de la aplicación Store Assist y otros ajustes, como:

   - **Crear una marca para la aplicación Store Assist**: personalice la interfaz de usuario de la aplicación con el logotipo y los colores de su empresa.

   - **Actualizar las instrucciones predeterminadas**: permite personalizar las instrucciones de los módulos Asistencia en tienda, Selección, Ensayo, Entrega y Pedido para guiar a los asociados de tienda en cada paso del flujo de trabajo de cumplimiento de la empresa.

   - **Localización**: seleccione el idioma disponible para la aplicación. Elija el formato de fecha y hora y seleccione las unidades de medida y la moneda predeterminadas.

   - **Tiempo de inactividad**: especifique la cantidad de tiempo que la aplicación debe estar inactiva antes de cerrar la sesión.

   - **Cancelación de la tienda**: permite especificar si los pedidos se pueden cancelar desde el almacén y qué funciones tienen permisos de cancelación

   - **Ventana Limpieza de Pedidos**: permite especificar cuánto tiempo debe transcurrir el [Tiempo de espera de recogida estimado](enable-general.md#delivery-method-title-configuration) Asegúrese de que un pedido seleccionado permanece en el entorno de ensayo antes de volver a estar disponible, por ejemplo, tres días. El valor predeterminado es de siete días. Si esta configuración está activada, la solicitud se cancela automáticamente cuando caduca este tiempo. Los artículos son repuestos y el comerciante recibe un correo electrónico de cancelación.

   - Personalice todas las instrucciones de la aplicación (picking, ensayo, entrega).

   - **Selección de notificaciones**: permite especificar si se debe enviar una notificación push para iniciar el proceso de picking después de que un cliente realice una solicitud.

   - **Registrar notificaciones**: especifique si desea enviar una notificación push durante el proceso de registro para las recogidas de pedidos después del registro, después de que el tiempo de espera del cliente exceda un período de tiempo especificado. O bien, deshabilite la notificación.

   - **Proceso de entrega**: permite activar procesos opcionales cuando el asociado de tienda envía el pedido al cliente; por ejemplo, para solicitar la firma de un cliente o pedir al asociado que compruebe el ID del cliente.

   - **Habilitar rechazo de elemento al entregar**: permite a los clientes devolver o cancelar artículos de pedido durante el traspaso de pedidos.
   Trabaje con el equipo de servicios al cliente de Walmart Commerce Technologies para completar la configuración de front-end de la aplicación Store Assist.

## Descarga e instalación de aplicaciones

Una vez configurada y configurada la aplicación Store Assist, Store Associates puede descargar, instalar e iniciar sesión en la aplicación Store Assist desde sus dispositivos móviles.

- Compruebe que el dispositivo móvil cumple los requisitos [requisitos de hardware y software](solution-requirements.md#store-assist-app-requirements) para la solución Store Fulfillment.

- Descargue la aplicación Store Assist desde el [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Store Associates necesita la siguiente información para iniciar sesión:

   - **[!UICONTROL Company name]** asociado a la cuenta de asistencia de tienda

   - **Credenciales de cuenta de asistencia de tienda**: credenciales de nombre de usuario y contraseña para su cuenta.
   Un administrador de Adobe Commerce puede crear y administrar [!DNL Store Assist app] cuentas de usuario para todas las ubicaciones de tiendas que tengan [Recogida en tienda](merchant-store-configuration.md#pickup-location-configuration) Habilitado en la configuración de las tiendas de administración.
