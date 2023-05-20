---
title: Verificar colección de eventos
description: Obtenga información sobre cómo comprobar que los datos de comportamiento se envían a Adobe Commerce.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Verificar colección de eventos

Después de usted [instalar y configurar](install-configure.md) el `magento/product-recommendations` , puede verificar que los datos de comportamiento se envían a Adobe Commerce. Puede utilizar las herramientas para desarrolladores disponibles en Chrome o instalar la extensión Snowplow Chrome. Si necesita ayuda adicional, consulte [Solucionar problemas [!DNL Product Recommendations] módulo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) en la Base de conocimiento de asistencia.

## Verificación mediante herramientas para desarrolladores en Chrome

Para asegurarse de que el archivo JS del recopilador de eventos se está cargando en todas las páginas del sitio:

1. En Chrome, elija **Personalización y control de Google Chrome** luego seleccione **Más herramientas** > **Herramientas para desarrolladores**.
1. Elija la **Red** y luego seleccione la pestaña **JS** escriba.
1. Filtrar por `ds.`
1. Vuelva a cargar la página.
1. Debería ver `ds.js` o `ds.min.js` en el **Nombre** columna.

![Recopilador de eventos JS](assets/filter-ds.png)
_Recopilador de eventos JS_

Para asegurarse de que los eventos se activan en las páginas de su sitio (inicio, producto, cierre de compra, etc.):

1. Asegúrese de desactivar cualquier bloqueador de anuncios en su navegador y aceptar las cookies en el sitio.
1. En Chrome, elija **Personalización y control de Google Chrome** (los tres puntos verticales de la esquina superior derecha del explorador) y seleccione **Más herramientas** > **Herramientas para desarrolladores**.
1. Elija la **Red** pestaña y filtro para `tp2`.
1. Vuelva a cargar la página.
1. Debería ver las llamadas en `tp2` en el **Nombre** columna.

![Activación de eventos](assets/filter-tp2.png)
_Verificar que se estén activando eventos_

## Verificar con la extensión Snowplow Chrome

Instale el [Extensión de Snowplow Analytics Debugger para Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Esta extensión muestra los eventos que se recopilan y envían a Adobe Commerce.

1. Asegúrese de desactivar cualquier bloqueador de anuncios en su navegador y aceptar las cookies en el sitio.

1. En Chrome, elija **Personalización y control de Google Chrome** (los tres puntos verticales de la esquina superior derecha del explorador) y seleccione **Más herramientas** > **Herramientas para desarrolladores**.

1. Elija la **Snowplow Analytics Debugger** pestaña.

1. En el **Evento** columna, seleccione **Evento estructurado**.

1. Desplácese hacia abajo hasta que vea **Datos de contexto _n_**. Busque la instancia de tienda en la **Esquema**.

1. Compruebe que la variable [ID del espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) está configurado correctamente.

![Snowplow, filtro](assets/snowplow-filter.png)
_Filtro de quitanieves_

>[!NOTE]
>
> Un valor de `Data validity : NOT FOUND` en el depurador indica un esquema interno. El complemento Snowplow Chrome no puede validar los eventos con un esquema interno. Esto no afecta a la funcionalidad real.

## Compruebe que los eventos se activan correctamente

Para comprobar que los eventos utilizados para las métricas se activan correctamente, busque `impression-render`, `view`, y `rec-click` eventos en Snowplow Analytics Debugger. Consulte la [lista completa de eventos](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [Modo de restricción de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) está activada, Adobe Commerce no recopila datos de comportamiento hasta que el comprador da su consentimiento. Si el modo de restricción de cookies está desactivado, los datos de comportamiento se recopilan de forma predeterminada.
