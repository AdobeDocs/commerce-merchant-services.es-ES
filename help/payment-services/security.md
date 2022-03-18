---
title: Seguridad y cumplimiento
description: Revise los requisitos de seguridad y cumplimiento para su sitio.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Seguridad y cumplimiento

La seguridad es de suma preocupación en [!DNL Payment Services] y no se pasa ninguna información regulada privada o de la Industria de Tarjetas de Pago (PCI) a través de su [!DNL Payment Services].

## Seguridad comercial

Adobe Commerce y Magento Open Source son compatibles con varias funciones de seguridad.

Consulte [Seguridad](https://docs.magento.com/user-guide/stores/security.html){target=&quot;_blank&quot;} en la guía del usuario principal para revisar las prácticas recomendadas de seguridad, y aprender a administrar sesiones de administración y credenciales, implementar CAPTCHA y administrar las restricciones del sitio web.

## Cumplimiento de PCI

La Industria de Tarjetas de Pago (PCI) estableció un conjunto de requisitos para las empresas que aceptan pagos con tarjeta de crédito a través de Internet. Además de mantener un entorno seguro, los comerciantes que manejan la información de las tarjetas de crédito de los clientes son responsables de cumplir algunas directrices estándar.

Consulte [Directrices de cumplimiento de PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;} para obtener más información.

Los comerciantes pueden completar un [cuestionario de autoevaluación (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}, que es una herramienta de autovalidación para evaluar la seguridad de los datos del titular de la tarjeta.

### Campos de tarjeta de crédito

Con los campos de la tarjeta de crédito, no se pasan datos regulados por PCI a través de los servicios. No es necesario que almacene o mantenga esos datos, lo que reduce enormemente las preocupaciones de cumplimiento de PCI.

### Botones inteligentes PayPal

Con los botones inteligentes PayPal, no se pasan datos regulados por PCI a través de sus servicios. No es necesario que almacene o mantenga esos datos, lo que reduce enormemente las preocupaciones de cumplimiento de PCI.

Por razones de seguridad, PayPal no pasa la dirección de facturación durante el cierre de compra (país, correo electrónico y nombre) es la única información de facturación utilizada. Si lo desea, puede habilitar el cierre de compra de PayPal de su sitio para que devuelva la dirección de facturación completa contactando con PayPal y completando un proceso de verificación.

PayPal también cuenta con una protección integrada contra el fraude que utiliza el aprendizaje automático para luchar contra el fraude. Consulte la [Documentación de protección del vendedor](https://www.paypal.com/us/webapps/mpp/security/seller-protection) para obtener más información.
