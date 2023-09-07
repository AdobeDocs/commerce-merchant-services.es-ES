---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Notas de la versión'
description: "Revise las notas de la versión para obtener información acerca de todos los [!DNL Store Fulfillment by Walmart Commerce Technologies] Versiones de."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Notas de la versión

Estas notas de la versión describen la versión inicial de [!DNL Store Fulfillment Services by Walmart Commerce Technologies] e incluir:

![Nuevo](../assets/new.svg) Nuevas funciones
![Problema corregido](../assets/fix.svg) Correcciones y mejoras
![Problema conocido](../assets/bug.svg) Problemas conocidos

Consulte [Próximas versiones](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para obtener más información sobre las programaciones de versiones y la compatibilidad.

Consulte [Disponibilidad del producto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) para saber qué versiones de Adobe Commerce admiten esta extensión.

## v1.5.0

*3 de agosto de 2023*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}[Adobe Commerce 2.4.4 a 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), incluidas las versiones de parches de seguridad 2.4.6-p1, 2.4.5-p3 y 2.4.4-p4

Esta versión incluye las siguientes actualizaciones:

![Nuevo](../assets/fix.svg) Se ha actualizado la extensión para que admita [Versiones de parches de seguridad de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 y 2.4.4-p4.

![Nuevo](../assets/new.svg)<!-- WMTP-918 --> Se ha agregado compatibilidad con [Envío asincrónico](sales-emails.md) opción de configuración para correos electrónicos de ventas. Los comerciantes que actualicen a la versión 1.5.0 tienen la opción de enviar correos electrónicos inmediatamente (predeterminado) o de forma asíncrona.

![Nuevo](../assets/new.svg)<!-- WMTP-916--> Se ha actualizado el [Configuración de orígenes](merchant-store-configuration.md) para admitir formatos de número de teléfono internacional.

![Nuevo](../assets/new.svg) Se ha añadido una lógica para evitar que los importes de devolución superen el importe restante o facturado.

![Nuevo](../assets/new.svg)<!-- WMTP-882 --> Reemplazado `google.map.LatLng` con literales JSON para admitir la compatibilidad con versiones anteriores de [!DNL Google Maps].

![Problema corregido](../assets/fix.svg)<!-- WMTP- --> Se ha actualizado el script que crea el `[!DNL Available for Store Pickup]` y `[!DNL Available for Home Delivery]` atributos de producto para evitar conflictos de categoría de atributos.

![Problema corregido](../assets/fix.svg)<!-- WMTP-915 --> Se ha corregido un problema de compatibilidad que provocaba un bucle interminable al cargar y guardar algunas entidades.

![Problema corregido](../assets/fix.svg)<!-- WMTP-921 --> Se ha corregido un problema que impedía [!DNL Ship to Store] La validación de presupuestos se activa cuando se añade un artículo al carro de compras desde una página de detalles del producto (PDP).

![Problema corregido](../assets/fix.svg)<!-- WMTP- 932 --> Se ha corregido un problema de cierre de compra que permitía a los clientes seleccionar el método de envío a domicilio para los artículos que no cumplen los requisitos para este tipo de envío.

![Problema corregido](../assets/fix.svg) Actualizaciones de instalación:

- <!-- WMTP-880--> Se ha corregido un problema que provocaba que se devolviera un código de sitio web incorrecto al instalar el [!DNL Store Fulfillment] extensión.

- <!-- WMTP-878--> Se ha corregido un problema con los números enteros de SKU que requería que el tipo de datos se convirtiera en tipo de cadena durante la instalación.

![Problema corregido](../assets/fix.svg)<!-- WMTP-915--> Se ha corregido un error debido a la falta de un código de error de protección.

![Problema corregido](../assets/fix.svg)<!-- WMTP-932 --> Se ha corregido un error relacionado con el rechazo parcial durante las operaciones de dispensación.

![Nuevo](../assets/new.svg)<!-- WMTP-953 --> Se ha actualizado el extremo de la API Cancel para que consuma el parámetro de estado como un objeto opcional.

![Nuevo](../assets/new.svg)<!-- WMTP-960 --> Se han mejorado los detalles de registro para el extremo de API Dispense.

## v1.4.0

*13 de abril de 2023*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

![Nuevo](../assets/fix.svg) [!DNL Store Fulfillment] es ahora [compatible con [!DNL Adobe Commerce] De 2.4.4 a 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 de febrero de 2023*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

Esta versión incluye la siguiente actualización:

![Nuevo](../assets/fix.svg)<!-- WMTP-795 --> Se ha añadido la capacidad de deshabilitar la solución Store Fulfillment para un sitio específico cambiando el ámbito predeterminado de la configuración del sistema de sitio web a global.

## v1.2.0

*27 de septiembre de 2022*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

Esta versión incluye la siguiente actualización:

![Nuevo](../assets/fix.svg) [!DNL Store Fulfillment] es ahora [compatible con [!DNL Adobe Commerce] 2.4.4 a 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 de julio de 2022*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

Estabilidad: disponibilidad general

![Nuevo](../assets/fix.svg)<!-- WMTP-731 --> Simplificación de la [Configuración de la experiencia de registro](check-in-experience-setup.md) para la aplicación Store Assist, añadiendo selecciones predeterminadas de modelo y marca de coche. En la versión anterior, los comerciantes tenían que configurar manualmente la marca del coche y las selecciones del modelo.

## v1.0.0

*4 de marzo de 2022*

[!BADGE Admitido]{type=Informative tooltip="Admitido"}

Estabilidad: disponibilidad general

## Aplicación Store Assist

Para obtener información sobre las nuevas versiones de la aplicación Store Assist, consulte la información de la aplicación en la [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
