---
title: A bordo [!DNL Payment Services]
description: Conecte la instancia con [!DNL Payment Services] al completar algunos pasos de incorporación.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# A bordo [!DNL Payment Services]

Para empezar a utilizar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source], debe completar algunos pasos de incorporación para conectar su instancia con la funcionalidad de pagos.

## Flujo de incorporación

![Flujo de incorporación](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

Este diagrama de flujo de incorporación muestra el proceso general de incorporación [!DNL Payment Services].

Después de completar la incorporación para los pagos en vivo o en zona protegida, los informes financieros están accesibles desde [!DNL Payment Services] en el Administrador.

Si tanto la zona protegida como los pagos activos están incorporados y habilitados, puede cambiar fácilmente entre esos modos desde el [!DNL Payment Services] Hogar.

## Requisitos previos

Para utilizar [!DNL Payment Services], debe tener lo siguiente disponible para su instancia:

* Módulo de Conector de servicios
* Módulo de ID de servicios
* Claves de API

Los módulos Conector de servicios e ID de servicios se instalan automáticamente durante la [instalación de [!DNL Payment Services]](install.md). Cuando finalice la instalación, puede ver una nueva sección en los ajustes de configuración (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) al expandir **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Para obtener información sobre cómo crear o acceder a sus claves API, consulte [Credenciales de API](#obtain-api-credentials).

## Pasos de incorporación

1. [Instale el [!DNL Payment Services] extensión](install.md#get-payment-services).
1. [Obtener credenciales de API](connect.md#obtain-api-credentials).
1. [Conecte la instancia](connect.md#configure-commerce-services) a Commerce Services. Esta conexión solo debe completarse una vez por instancia de Commerce.
1. [Configuración del servicio de zona protegida](sandbox.md#enable-sandbox-testing) (o, alternativamente, proceda a [activación de pagos activos](sandbox.md#enable-live-payments) si has probado la funcionalidad en otro entorno) con una cuenta de procesamiento de pagos PayPal de prueba.
1. [Establecer [!DNL Payment Services] como forma de pago](production.md#set-payment-services-as-payment-method), en modo de zona protegida, para iniciar el procesamiento de los pagos de prueba.
1. [Solicitar derechos de pagos](production.md#request-payments-entitlement-from-adobe) para habilitar la incorporación en directo.
1. [Incorporación completa del comerciante](production.md#complete-merchant-onboarding) para habilitar los pagos activos para sus sitios web de Commerce.
1. [Obtenga su [!DNL Payment Services] ID de comerciante](production.md#configure-pricing-tier) y envíeselo a Ventas para configurar el nivel de precios correcto.
1. [Activar [!DNL Payment Services] en modo activo](production.md#enable-live-payments) para empezar a procesar pagos activos.
1. Pagos de prueba, en ambos [espacio aislado](sandbox.md#test-in-sandbox-environment) y [producción](production.md#test-in-production) entornos.

>[!NOTE]
>
>Si no configura Commerce Services en el Admin (paso 3), no puede configurar la zona protegida ni los pagos activos.

## Resolución de problemas

* [Solucionar problemas [!DNL Payment Services] instalación](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [Cuenta de zona protegida de PayPal no verificada](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Retrasado [!DNL Payment Services] datos del informe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Probar los errores de las tarjetas de crédito con PayPal al procesar pagos en un entorno de zona protegida](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
