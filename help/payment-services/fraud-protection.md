---
title: Protección contra el fraude significativo
description: Habilitar la protección contra fraudes automatizada para [!DNL Payment Services] con Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Protección contra fraudes significativa

Puede habilitar la protección contra fraudes automatizada para [!DNL Payment Services] con el [Extensión significativa](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce es compatible con las versiones 5.4.0 y posteriores de Signifyd. [!DNL Payment Services] admite flujos Signifyd anteriores y posteriores a la autenticación.

Signifyd/[!DNL Payment Services] La integración de proporciona cobertura para tarjetas de crédito, tarjetas de débito, tarjetas abovedadas, pagos a través del administrador y métodos de pago mediante PayPal y Apple Pay. Aunque algunos detalles de las transacciones no se comparten entre los Servicios de pago y Signifyd, Signifyd proporciona una cobertura de riesgo integral para todos los métodos de pago, asegurando la máxima protección.

Consulte [Documentación significativa](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) para obtener más información sobre la instalación y configuración de la extensión de.

## Incorporación

Debe comunicarse directamente con Signifyd para incorporar la extensión y utilizarla con [!DNL Payment Services]—no hay [!DNL Payment Services] se necesita configuración. Puede configurar la extensión Signifyd en el Administrador una vez instalada. Cualquier compatibilidad relacionada con esta extensión será administrada por Signifyd.

Al incorporar Signifyd, debe:

1. Póngase en contacto con Signifyd para configurar una nueva cuenta.
1. De forma predeterminada, Signifyd es [incluido en la lista de permitidos](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) para asegurarse de que Signifyd no da su déclencheur para otras opciones de pago que actualmente no admite. Si quieres prohibir una forma de pago en particular, debes hacer cambios.
1. Confirme con Signifyd que PayPal no rechazará pedidos, a través de la configuración de protección contra fraude del comerciante en Paypal, que Signifyd pueda aprobar.
1. Habilite la extensión Signify para que sea compatible con [!DNL Payment Services]:
   * Al utilizar [!DNL Payment Services] in _Activo_ modo, Signifyd debe estar en modo de producción.
   * Al utilizar [!DNL Payment Services] in _Sandbox_ modo, Signifyd debe estar en modo de prueba.

## Configuración

Debido a que Signifyd realiza alguna acción sobre sus pedidos, es necesario configurar la extensión para que se comporte de forma adecuada en función de la acción de pago configurada para [!DNL Payment Services].

Estas opciones de configuración no son compatibles con Payment Services ni con la integración de Signifyd:

* Cuándo [!DNL Payment Services] está configurado con la variable `Authorize` acción de pago _y_ Signifyd está en `PostAuth` con el _[!UICONTROL Decline Guarantees]_opción establecida en **Crear nota de crédito**.

  Razón: [!DNL Payment Services] crea una transacción de autorización que Signify intenta devolver.


* [!DNL Payment Services] está configurado con la variable `Authorize and Capture` acción de pago _y_ Signifyd está en `PostAuth` con el _[!UICONTROL Decline Guarantees]_opción establecida en **Cancelar pedido**.

  Razón: [!DNL Payment Services] crea una transacción de captura que Signifyd intenta anular.


Consulte la documentación de Signifyd para obtener información sobre [configuración de la extensión](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Consulte la documentación identificada para [más información sobre los flujos de trabajo de pedidos](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
