---
title: Configuración de usuario
description: Configure las fuentes Inventory management mejoradas como tiendas comerciales para admitir la solución de entrega de tiendas para Adobe Commerce.
role: User, Admin
level: Intermediate
exl-id: eb735bef-c339-4d0b-b3e7-10328915725b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Configuración de usuario

Los usuarios de la aplicación de asistencia de la tienda se administran en Adobe Commerce. Sin embargo, estos usuarios no interactúan directamente con Adobe Commerce. La administración de usuarios está configurada en Adobe Commerce para habilitar conexiones seguras entre Adobe Commerce y la aplicación.

El modelo de usuario de la aplicación de cumplimiento de la tienda está separado de otros modelos de usuario de Adobe Commerce. La aplicación mantiene su propio modelo de permisos mediante funciones de usuario y usuarios que se pueden asignar a todas las ubicaciones o a ubicaciones específicas. Se admiten los siguientes permisos: Orden de selección, orden de entrega y reducción de cantidad de artículos (y cancelación).

>[!TIP]
>
>Para obtener los mejores resultados, [configurar la conexión](connect-set-up-service.md) antes de agregar usuarios y permisos para Store Associates que usan la aplicación Store Assist.

## Aplicación de asistencia de tienda: funciones de usuario

Durante la configuración inicial del usuario para la aplicación de ayuda de la tienda, cree funciones de usuario para personalizar los permisos de usuario en la aplicación de asistencia de la tienda. Por ejemplo, puede crear diferentes funciones para administradores de almacén y asociados de almacén y asignar diferentes recursos de rol para administrar permisos para cada tipo de usuario.

Configurar funciones de usuario desde **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Información de función

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Habilite o deshabilite el usuario. | Global | Sí |

### Recursos de rol

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Lista de los grupos de permisos disponibles que se pueden asignar a una función de usuario. En este momento, la solución de cumplimiento de almacenamiento no tiene diferentes niveles de permisos definidos para las funciones de recursos. Todas las funciones de usuario tienen el mismo acceso a los recursos. | Global | Sí |

## Asistencia de la tienda: información del usuario

Administre los perfiles de usuario de la aplicación de asistencia de la tienda desde la configuración del sistema de administración:  **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Habilite o deshabilite el usuario. | Global | Sí |
| **[!UICONTROL User Name]** | Nombre de usuario asociado al usuario | Global | Sí |
| **[!UICONTROL First Name]** | Nombre asociado al usuario | Global | No |
| **[!UICONTROL Last Name]** | Apellidos asociados al usuario | Global | No |
| **[!UICONTROL Role]** | Función asociada al usuario | Global | No |
| **[!UICONTROL Access to all locations]** | Asigne a los usuarios acceso a todas las tiendas o seleccione las tiendas individualmente. | Global | No |
| **Configuración regional de la interfaz** | Si su tienda tiene varios idiomas, establezca la configuración regional de la interfaz en el idioma que se utilizará para la interfaz de administración. | Global | No |
| **Activo desde** | Para establecer una fecha de inicio, seleccione el icono de calendario. | Global | No |
| **Activo a** | Establezca la Fecha de caducidad seleccionando el icono del calendario. La configuración de una fecha de caducidad es útil para configurar asignaciones temporales de usuarios o funciones. Después de la fecha de caducidad, el estado de la cuenta de usuario cambia a `Inactive`, pero la cuenta se puede actualizar si es necesario. | Global | No |
