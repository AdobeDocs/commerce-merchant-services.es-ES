---
title: Seguridad y cumplimiento
description: Revise los requisitos de seguridad y cumplimiento del sitio.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Seguridad y cumplimiento

La seguridad es de suma importancia en [!DNL Payment Services] y no se pasa información privada o regulada por la industria de tarjetas de pago (PCI) a través de su [!DNL Payment Services].

## Seguridad de Commerce

[!DNL Adobe Commerce] y [!DNL Magento Open Source] incluyen compatibilidad con varias características de seguridad.

Consulte [Seguridad](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security){target="_blank"} en la guía del usuario principal para revisar las prácticas recomendadas de seguridad, y aprender a administrar las sesiones de administración y las credenciales, implementar CAPTCHA y administrar las restricciones del sitio web.

## Conformidad con PCI

La industria de tarjetas de pago (PCI) estableció un conjunto de requisitos para las empresas que aceptan pagos con tarjeta de crédito a través de Internet. Además de mantener un entorno seguro, los comerciantes que gestionan la información de las tarjetas de crédito de los clientes son responsables de cumplir algunas directrices estándar.

Consulte [Directrices de cumplimiento de PCI](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-pci){target="_blank"} para obtener más información.

Los comerciantes pueden completar un [cuestionario de autoevaluación (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, que es una herramienta de autovalidación para evaluar la seguridad de los datos del titular de la tarjeta.

### Campos de tarjeta de crédito

Con los campos de tarjeta de crédito, no se pasan datos regulados por PCI a través de los servicios. No tiene que almacenar ni mantener esos datos, lo que reduce considerablemente los problemas de conformidad con PCI.

### 3DS

PCI 3-D Secure (3DS) permite la autenticación del comprador con el emisor de su tarjeta de crédito al realizar compras con tarjeta de crédito en línea. Este nivel adicional de seguridad ayuda a prevenir el fraude en línea y es necesario como parte de las regulaciones de cumplimiento de la Unión Europea (UE).

[!UICONTROL Payment Services] proporciona funcionalidad 3DS para permitir que los comerciantes cumplan con las regulaciones de la UE y para proteger a los clientes y comerciantes de cualquier actividad fraudulenta en sus tiendas.

Si es un comerciante de la UE o de Gran Bretaña donde se requiere el cumplimiento de 3DS, debe activar manualmente 3DS (es `Off` de forma predeterminada) en [Configuración](settings.md#credit-card-fields).

>[!NOTE]
>
>El requisito de 3DS se aplica a las transacciones en las que el banco del titular de la tarjeta y la empresa se encuentran en el [Espacio Económico Europeo](https://www.efta.int/eea) (EEE) y Gran Bretaña. Los comerciantes estadounidenses no requieren 3DS, pero pueden habilitarlo para sus transacciones si así lo desean.

Los pedidos realizados por el comerciante o el personal de la tienda para el comprador no están configurados con medidas de cumplimiento de 3DS.

Consulte [3DS en Configuración](settings.md#3ds) para obtener más información.

### Bóveda de tarjetas

Cuando un comprador [almacena o &quot;guarda&quot; la información de su tarjeta de crédito](vaulting.md) para futuras compras en sus tiendas, se comparte la información mínima de la tarjeta de crédito con el comprador (los últimos cuatro dígitos, la fecha de caducidad de la tarjeta y la marca de la tarjeta). La información de la tarjeta de crédito se almacena con el proveedor de pagos. Cuando una tarjeta caduca o ya no necesita guardar la información, puede eliminar ese token para que el proveedor de pagos ya no almacene la información.

Consulte [Avalúo de tarjetas de crédito](vaulting.md) para obtener más información.

### Botones de pago de PayPal

Con los botones de pago de PayPal, no se pasan datos regulados por PCI a través de sus servicios. No tiene que almacenar ni mantener esos datos, lo que reduce considerablemente los problemas de conformidad con PCI.

Por razones de seguridad, PayPal no pasa la dirección de facturación durante el proceso de pago: el país, el correo electrónico y el nombre son los únicos datos de facturación utilizados. Si lo desea, puede activar el proceso de pago y envío de PayPal para que se devuelva la dirección de facturación completa poniéndose en contacto con PayPal y completando un proceso de verificación de antecedentes.

PayPal también cuenta con una protección contra el fraude integrada que utiliza el aprendizaje automático para ayudarle a combatir el fraude. Consulta la [documentación sobre la protección del vendedor](https://www.paypal.com/us/webapps/mpp/security/seller-protection) de PayPal para obtener más información.

## Protección contra el fraude

Puede habilitar la protección contra fraudes automatizada para Payment Services con la [extensión Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Consulte [Protección contra fraudes significativa](fraud-protection.md) para obtener más información.

