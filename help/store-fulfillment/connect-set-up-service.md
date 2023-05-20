---
title: Conexión de la solución Store Fulfillment
description: Establezca las conexiones entre Adobe Commerce y la solución Store Fulfillment creando y autorizando una integración de Adobe Commerce y añadiendo las credenciales de la cuenta Store Fulfillment a la configuración del servicio de Adobe Commerce.
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Conexión de la solución Store Fulfillment

Conecte los servicios de cumplimiento de almacenamiento con Adobe Commerce agregando las credenciales de autenticación y los datos de conexión necesarios al administrador de Adobe Commerce.

- **[Configurar [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)**: cree una integración de Adobe Commerce para los servicios de Store Fulfillment y genere los tokens de acceso para autenticar las solicitudes entrantes de los servidores de Store Fulfillment.

- **[Configurar las credenciales de la cuenta para los servicios de Store Fulfillment](#configure-store-fulfillment-account-credentials)**-Añada sus credenciales para conectar Adobe Commerce a su cuenta de Store Fulfillment.

>[!NOTE]
>
>Complete la configuración de la conexión y valide la conexión correctamente antes de comenzar la prueba.

## Creación de una integración de Adobe Commerce

Para integrar Adobe Commerce con los servicios de Store Fulfillment, crea una integración comercial y genera tokens de acceso que se pueden utilizar para autenticar solicitudes de los servidores de Store Fulfillment. También debe actualizar Adobe Commerce [!UICONTROL Consumer Settings] opciones para evitar `The consumer isn't authorized to access %resources.` errores de respuesta en solicitudes de Adobe Commerce a [!DNL Store Fulfillment] servicios.

1. Desde Admin, cree la integración para la adquisición de tiendas.

   - Asigne un nombre a la extensión
   - Introduzca su dirección de correo electrónico
   - Introduzca la contraseña de su cuenta de administrador

1. Configurar [!UICONTROL API Resource Access permissions] para la integración: seleccione `[!UICONTROL All]`

1. Genere los tokens de acceso para la autenticación guardando y activando la integración.

1. Copie y guarde los tokens de acceso en una ubicación segura y cifrada.

1. Póngase en contacto con el administrador de cuentas para completar la configuración en el lado de Store Fulfillment y autorizar la integración.

1. Habilitar Adobe Commerce [!UICONTROL Consumer Settings] opción para [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - Desde Admin, vaya a **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Configure las variables [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] opción para **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> El token de integración es específico del entorno. Si restaura la base de datos de un entorno con los datos de origen de un entorno diferente (por ejemplo, restaurando los datos de producción de un entorno de ensayo), excluya la variable `oauth_token` de la exportación de la base de datos para que los detalles del token de integración no se sobrescriban durante la operación de restauración.


## Configurar credenciales de cuenta de Store Fulfillment

Después de completar el formulario de admisión, se crea una cuenta de cumplimiento de Walmart Store para usted. Recibirá las siguientes credenciales cuando estén disponibles:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (normalmente es la misma que la configuración anterior)

Estas credenciales son necesarias para configurar y utilizar Satisfacción de pedidos de la tienda.

>[!NOTE]
>
>El proceso de creación de la cuenta puede tardar un poco en completarse. Mientras espera las credenciales, [revise y configure otras opciones de la solución Store Fulfillment](service-config-settings-overview.md).

### Añadir credenciales para conectarse a Store Fulfillment

1. Configurar [credenciales de cuenta](enable-general.md) para los entornos Producción y Zona protegida.

1. Desde Admin, vaya a **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Introduzca las credenciales de la cuenta proporcionadas para **[!UICONTROL Production environment]**. Todos los campos son obligatorios.

1. Seleccionar **[!UICONTROL Save Config]**.

1. Pruebe la conexión seleccionando **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Si las credenciales no son válidas, compruebe que ha introducido los valores correctos para cada entorno y vuelva a validarlas. Póngase en contacto con el representante de cuentas si sigue teniendo problemas de conexión.
