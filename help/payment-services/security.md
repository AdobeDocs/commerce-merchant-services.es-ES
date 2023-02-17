---
title: Seguridad y cumplimiento
description: Revise los requisitos de seguridad y cumplimiento para su sitio.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: 17ba23192fed6cd219411420c5d56b42c94af0f5
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# Seguridad y cumplimiento

La seguridad es de suma preocupación en [!DNL Payment Services] y no se pasa ninguna información regulada privada o de la Industria de Tarjetas de Pago (PCI) a través de su [!DNL Payment Services].

## Seguridad comercial

[!DNL Adobe Commerce] y [!DNL Magento Open Source] incluye compatibilidad con varias funciones de seguridad.

Consulte [Seguridad](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} en la guía del usuario principal para revisar las prácticas recomendadas de seguridad, y aprender a administrar sesiones de administración y credenciales, implementar CAPTCHA y administrar las restricciones del sitio web.

## Cumplimiento de PCI

La Industria de Tarjetas de Pago (PCI) estableció un conjunto de requisitos para las empresas que aceptan pagos con tarjeta de crédito a través de Internet. Además de mantener un entorno seguro, los comerciantes que manejan la información de las tarjetas de crédito de los clientes son responsables de cumplir algunas directrices estándar.

Consulte [Directrices de cumplimiento de PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} para obtener más información.

Los comerciantes pueden completar un [cuestionario de autoevaluación (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, que es una herramienta de autovalidación para evaluar la seguridad de los datos del titular de la tarjeta.

### Campos de tarjeta de crédito

Con los campos de la tarjeta de crédito, no se pasan datos regulados por PCI a través de los servicios. No es necesario que almacene o mantenga esos datos, lo que reduce enormemente las preocupaciones de cumplimiento de PCI.

### 3DS

PCI 3-D Secure (3DS) permite la autenticación del comprador con el emisor de su tarjeta de crédito al realizar compras con tarjeta de crédito en línea. Esta capa adicional de seguridad ayuda a prevenir el fraude en línea y es necesaria como parte de las regulaciones de cumplimiento de la Unión Europea (UE).

[!UICONTROL Payment Services] proporciona funcionalidad 3DS para permitir a los comerciantes cumplir con las regulaciones de la UE y proteger a los clientes y comerciantes de actividades fraudulentas en sus tiendas.

Si usted es un comerciante dentro de la UE o Gran Bretaña donde se requiere el cumplimiento de 3DS, debe activar manualmente 3DS (es `Off` de forma predeterminada) en [Configuración](settings.md#credit-card-fields).

Los pedidos realizados para el comprador por el personal del comerciante/tienda no están configurados con medidas de cumplimiento 3DS.

Consulte [3DS en Configuración](settings.md#3ds) para obtener más información.

### Bóveda de tarjetas

Cuando un comprador [vaults (o &quot;guarda&quot;): la información de su tarjeta de crédito](vaulting.md) para futuras compras en sus tiendas, la información mínima de la tarjeta de crédito se comparte con el comprador (los últimos cuatro dígitos, la fecha de caducidad de la tarjeta y la marca de la tarjeta). La información de la tarjeta de crédito se almacena en el proveedor de pagos. Cuando una tarjeta caduca o ya no necesita la información guardada, puede eliminarla para que el proveedor de pagos ya no almacene la información.

Consulte [Bóveda de tarjetas de crédito](vaulting.md) para obtener más información.

### Botones inteligentes PayPal

Con los botones inteligentes PayPal, no se pasan datos regulados por PCI a través de sus servicios. No es necesario que almacene o mantenga esos datos, lo que reduce enormemente las preocupaciones de cumplimiento de PCI.

Por razones de seguridad, PayPal no pasa la dirección de facturación durante el cierre de compra (país, correo electrónico y nombre) es la única información de facturación utilizada. Si lo desea, puede habilitar el cierre de compra de PayPal de su sitio para que devuelva la dirección de facturación completa contactando con PayPal y completando un proceso de verificación.

PayPal también cuenta con una protección integrada contra el fraude que utiliza el aprendizaje automático para luchar contra el fraude. Consulte la [Documentación de protección del vendedor](https://www.paypal.com/us/webapps/mpp/security/seller-protection) para obtener más información.
