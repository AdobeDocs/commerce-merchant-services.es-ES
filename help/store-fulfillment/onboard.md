---
title: Información general sobre la incorporación para los servicios de entrega de la tienda
description: '"[!DNL Live Search] flujo de incorporación, requisitos del sistema, límites y limitaciones"'
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Información general sobre la incorporación para el cumplimiento de la tienda

Introducción a [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] configurando, configurando y habilitando los siguientes componentes:

- **Extensión de entrega de tiendas**-Instale y configure esta extensión de terceros en la instancia de Adobe Commerce. Después de la instalación, puede configurar y administrar la solución Store Fulfillment desde el Administrador para que sea compatible [!DNL buy online, pickup in store] escenarios (BOPIS) en la tienda de comercio.

   ![[!DNL Store Fulfillment Service] configuración en la vista Administración](assets/store-fulfillment-admin-home.png)

- **Cuenta de entrega de la tienda**-Durante el proceso de activación, un administrador de cuentas crea su cuenta de cumplimiento de almacenamiento y le proporciona la información de la cuenta y las credenciales. Estas credenciales son necesarias para habilitar la conexión entre Adobe Commerce y la solución Store Fulfillment.

- **Aplicación de asistencia de la tienda**: proporciona a los asociados de almacén un flujo de trabajo completo de cumplimiento de almacenamiento para administrar los pedidos BOPIS desde dispositivos móviles. Store Associates puede descargar e instalar el [!DNL Store Assist] para dispositivos iOS y Android. El proceso de incorporación a la aplicación lo gestiona el Centro de clientes de tecnología de comercio Walmart como un proceso independiente. Sin embargo, [algunos ajustes de configuración de la aplicación](user-setup.md) se completan desde el administrador de Adobe Commerce.

   | Aplicación de asistencia de tienda: vista de introducción | Aplicación de asistencia de la tienda: vista de módulos |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] visualización en dispositivos móviles](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] en dispositivo móvil](assets/store-assist-orders-small.png) |




## Pasos de aprovisionamiento

- **Regístrese para[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**-Complete el formulario de registro en [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)o póngase en contacto con el administrador de cuentas de Adobe Commerce para obtener ayuda.

- **Inicio de la solicitud de aprovisionamiento para el cumplimiento de la tienda**-Complete el formulario de admisión proporcionado por su Administrador de cuentas para proporcionar la información necesaria para iniciar el proceso de aprovisionamiento.

- **Obtenga las credenciales de la cuenta de cumplimiento de la tienda**-Una vez creada la cuenta de satisfacción de la tienda para usted, recibirá las credenciales necesarias para integrar la solución de cumplimiento de la tienda con Adobe Commerce.

- **[Descargue el código fuente para instalar el [!DNL Store Fulfillment] Extensión](install.md)**

## Pasos de incorporación

1. [Instalación de la extensión Store Fulfillment para Adobe Commerce](install.md).

1. Desde el administrador, [habilitar la solución](enable-general.md).

1. [Configurar la extensión de cumplimiento de la tienda desde el administrador de Adobe Commerce](service-config-settings-overview.md).

1. [Conecte el [!DNL Store Fulfillment] utilizando las credenciales de cumplimiento de la tienda que se le han proporcionado.](connect-set-up-service.md)

1. [Crear usuarios y funciones para la aplicación de ayuda de la tienda](user-setup.md)

1. [Descargar Walmart [!DNL Store Assist] al dispositivo deseado. La aplicación está disponible tanto en la tienda de aplicaciones (iOS) como en la de reproducción (Android)](app-setup.md)

Una vez que haya instalado, configurado, completado la integración correctamente y tenga acceso al [!DNL Store Assist] aplicación, puede [comenzar a crear pedidos y pruebas](test-and-deploy.md).


