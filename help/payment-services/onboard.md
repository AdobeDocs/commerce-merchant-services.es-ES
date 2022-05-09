---
title: Incorporado [!DNL Payment Services]
description: Conecte la instancia con [!DNL Payment Services] completando algunos pasos de integración.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Incorporado [!DNL Payment Services]

Para empezar a usar [!DNL Payment Services] para [!DNL Adobe Commerce] y [!DNL Magento Open Source], debe completar algunos pasos de incorporación para conectar su instancia con la funcionalidad de pagos.

## Flujo de incorporación

![Flujo de incorporación](assets/onboarding-diagram.svg)

Este diagrama de flujo de incorporación muestra el proceso general de incorporación [!DNL Payment Services].

Después de completar la incorporación para el entorno limitado o los pagos en directo, se puede acceder a los informes financieros desde [!DNL Payment Services] en el menú

Si tanto el simulador para pruebas como los pagos activos están incorporados y habilitados, puede cambiar fácilmente entre esos modos desde el [!DNL Payment Services] Hogar.

## Requisitos previos

Para usar [!DNL Payment Services], debe tener lo siguiente disponible para su instancia:

* Módulo Conector de servicios
* Módulo de ID de servicios
* Claves de API

Los módulos Services Connector y Services ID se instalan automáticamente durante la [instalación de [!DNL Payment Services]](install.md). Cuando se complete la instalación, podrá ver una nueva sección en los ajustes de configuración (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) al expandir **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Para obtener información sobre cómo crear o acceder a las claves de API, consulte [Credenciales de API](#obtain-api-credentials).

## Pasos de incorporación

1. [Instale el [!DNL Payment Services] Extensión](install.md#get-payment-services).
1. [Obtener credenciales de API](connect.md#obtain-api-credentials).
1. [Conecte la instancia](connect.md#configure-commerce-services) a Commerce Services. Esta conexión debe completarse solo una vez por cada instancia de Commerce.
1. [Configuración del servicio de entorno limitado](sandbox.md#enable-sandbox-testing) (o, alternativamente, proceder a [activación de pagos en directo](sandbox.md#enable-live-payments) si ha probado la funcionalidad en otro entorno) con una cuenta de procesamiento de pagos PayPal de prueba.
1. [Establezca [!DNL Payment Services] como método de pago](production.md#set-payment-services-as-payment-method), en el modo de entorno limitado, para iniciar el procesamiento de los pagos de prueba.
1. [Solicitud de derechos de pago](production.md#request-payments-entitlement-from-adobe) para activar la incorporación.
1. [Integración completa del comerciante](production.md#complete-merchant-onboarding) para habilitar los pagos en directo para sus sitios web de Commerce.
1. [Obtenga su [!DNL Payment Services] ID del comerciante](production.md#configure-pricing-tier) y envíelo a Ventas para configurar el nivel de precios correcto.
1. [Habilitar [!DNL Payment Services] en modo Activo](production.md#enable-live-payments) para empezar a procesar los pagos en directo.
1. Pagos de prueba, en ambos [entorno limitado](sandbox.md#test-in-sandbox-environment) y [producción](production.md#test-in-production) entornos.

>[!NOTE]
>
>Si no configura los servicios de comercio en Admin (paso 3), no podrá configurar entornos limitados ni pagos activos.

## Resolución de problemas

* [Resolución de problemas [!DNL Payment Services] instalación](https://support.magento.com/hc/en-us/articles/4406603542541)
* [Cuenta de espacio aislado de PayPal no verificada](https://support.magento.com/hc/en-us/articles/4406954952461)
* [Retrasado [!DNL Payment Services] datos del informe](https://support.magento.com/hc/en-us/articles/4406114741517)
* [La tarjeta de crédito de prueba falla con PayPal cuando se procesan pagos en un entorno Sandbox](https://support.magento.com/hc/en-us/articles/5201041963917)
