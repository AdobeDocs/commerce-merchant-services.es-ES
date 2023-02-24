---
title: Conecte la solución de entrega de la tienda
description: Establezca las conexiones entre Adobe Commerce y la solución Store Fulfillment creando y autorizando una integración con Adobe Commerce y agregando las credenciales de la cuenta Store Fulfillment a la configuración del servicio Adobe Commerce.
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Conecte la solución de entrega de la tienda

Conecte los servicios de cumplimiento de la tienda con Adobe Commerce agregando las credenciales de autenticación y los datos de conexión necesarios al administrador de Adobe Commerce.

- **[Configurar [!DNL Commerce integration settings]](#create-the-commerce-integration)**-Cree una integración de Adobe Commerce para los servicios de entrega de la tienda y genere los tokens de acceso para autenticar las solicitudes entrantes de los servidores de entrega de la tienda.

- **[Configurar las credenciales de cuenta para los servicios de cumplimiento de la tienda](#configure-store-fulfillment-account-credentials)**-Añada sus credenciales para conectar Adobe Commerce a su cuenta de cumplimiento de la tienda.

>[!NOTE]
>
>Complete la configuración de conexión y valide la conexión correctamente antes de comenzar a realizar pruebas.

## Creación de una integración con Adobe Commerce

Para integrar Adobe Commerce con los servicios de entrega de tiendas, cree una integración de comercio y genere tokens de acceso que se puedan utilizar para autenticar solicitudes desde los servidores de entrega de tiendas.

1. Desde el administrador, cree la integración para el cumplimiento del almacén.

   - Asigne un nombre a la extensión
   - Escriba su dirección de correo electrónico
   - Escriba la contraseña de la cuenta de administrador

1. Configurar [!UICONTROL API Resource Access permissions] para la integración: seleccione `[!UICONTROL All]`

1. Genere los tokens de acceso para la autenticación guardando y activando la integración.

1. Copie y guarde los tokens de acceso en una ubicación segura y cifrada.

1. Póngase en contacto con su administrador de cuentas para completar la configuración en el lado del cumplimiento de la tienda y para autorizar la integración.


>[!NOTE]
>
>Para obtener instrucciones detalladas, consulte [Integraciones](https://docs.magento.com/user-guide/system/integrations.html) en el _Guía del usuario de Adobe Commerce_.

## Configuración de las credenciales de la cuenta de cumplimiento de la tienda

Después de completar el formulario de admisión, se crea una cuenta de Wal Store Fulfillment para usted. Recibirá las siguientes credenciales cuando estén disponibles:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (normalmente el mismo que la configuración anterior)

Estas credenciales son necesarias para configurar y utilizar el cumplimiento de la tienda.

>[!NOTE]
>
>El proceso de creación de cuentas puede tardar algún tiempo en completarse. Mientras espera las credenciales, [revisar y configurar otras configuraciones para la solución de cumplimiento de la tienda](service-config-settings-overview.md).

### Agregar credenciales para conectarse al cumplimiento de la tienda

1. Configurar [credenciales de cuenta](enable-general.md) para los entornos Producción y Sandbox.

1. Desde el administrador, vaya a **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Introduzca las credenciales de la cuenta proporcionadas para el **[!UICONTROL Production environment]**. Todos los campos son obligatorios.

1. Select **[!UICONTROL Save Config]**.

1. Pruebe la conexión seleccionando **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Si las credenciales no son válidas, compruebe que ha introducido los valores correctos para cada entorno y vuelva a validar. Póngase en contacto con su representante de cuentas si todavía tiene problemas para conectarse.
