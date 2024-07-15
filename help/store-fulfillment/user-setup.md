---
title: Configuración de usuario
description: Configure fuentes de Inventory management mejoradas como tiendas comerciales para admitir la solución Store Fulfillment para Adobe Commerce.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, User Account, Tools and External Services
exl-id: eb735bef-c339-4d0b-b3e7-10328915725b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Configuración de usuario

Los usuarios de la aplicación Store Assist se administran en Adobe Commerce. Sin embargo, estos usuarios no interactúan directamente con Adobe Commerce. La administración de usuarios está configurada en Adobe Commerce para habilitar conexiones seguras entre Adobe Commerce y la aplicación.

El modelo de usuario de aplicación Store Fulfillment está separado de otros modelos de usuario de Adobe Commerce. La aplicación mantiene su propio modelo de permisos a través de las funciones de usuario y los usuarios que se pueden asignar a todas las ubicaciones o a ubicaciones específicas. Se admiten los siguientes permisos: orden de acopio, orden de distribución y reducción de la cantidad de artículos (y cancelación).

>[!TIP]
>
>Para obtener los mejores resultados, [configura tu conexión](connect-set-up-service.md) antes de agregar usuarios y permisos para los asociados de la tienda que usan la aplicación Store Assist.

## Aplicación de asistencia de tienda: funciones de usuario

Durante la configuración inicial del usuario para la aplicación Store Assist, cree funciones de usuario para personalizar los permisos de usuario para la aplicación Store Assist. Por ejemplo, puede crear diferentes funciones para administradores de tiendas y asociados de tiendas, y asignar diferentes recursos de funciones para administrar permisos para cada tipo de usuario.

Configurar roles de usuario de **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Información de rol

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Habilitar o deshabilitar el usuario. | Global | Sí |

### Recursos de rol

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Enumerar los grupos de permisos disponibles que se pueden asignar a una función de usuario. En este momento, la solución Store Fulfillment no tiene niveles de permisos diferentes definidos para las funciones de recursos. Todos los roles de usuario tienen el mismo acceso a los recursos. | Global | Sí |

## Asistencia de tienda: información del usuario

Administrar perfiles de usuario de aplicaciones de asistencia de tienda desde la configuración del sistema de administración: **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Habilitar o deshabilitar el usuario. | Global | Sí |
| **[!UICONTROL User Name]** | Nombre de usuario asociado con el usuario | Global | Sí |
| **[!UICONTROL First Name]** | Nombre asociado con el usuario | Global | No |
| **[!UICONTROL Last Name]** | Apellidos asociados con el usuario | Global | No |
| **[!UICONTROL Role]** | Función asociada al usuario | Global | No |
| **[!UICONTROL Access to all locations]** | Asigne a los usuarios acceso a todas las tiendas o seleccione las tiendas individualmente. | Global | No |
| **Configuración regional de la interfaz** | Si la tienda tiene varios idiomas, establezca la Configuración regional de la interfaz en el idioma que se utilizará en la interfaz de administración. | Global | No |
| **Activo Desde** | Para definir una fecha de inicio, seleccione el icono de calendario. | Global | No |
| **Activo Para** | Establezca la Fecha de caducidad seleccionando el icono del calendario. La configuración de una fecha de caducidad es útil para configurar asignaciones temporales de usuarios o roles. Después de la fecha de caducidad, el estado de la cuenta de usuario cambia a `Inactive`, pero la cuenta se puede actualizar si es necesario. | Global | No |
