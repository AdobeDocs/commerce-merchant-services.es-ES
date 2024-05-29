---
title: Usar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado
description: Aprenda a utilizar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: a94f75dfab1f88f02e217b0e021cc2dfc94244c7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 0%

---

# Usar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado

Obtenga información sobre cómo enviar un correo electrónico de renovación de la participación personalizado o una notificación si se ha abandonado una sesión del carro de compras o del explorador. En este artículo, se utilizan datos generados a partir de clientes que han visto una serie de productos y categorías, que han interactuado con un producto o que han invertido tiempo en una página.

## ¿Qué datos debo considerar al usar?

Cree un carro de compras abandonado, examine el correo electrónico o las notificaciones con datos de eventos de tienda y back office.

| Tipos de datos | Datos De Tienda (Eventos De Comportamiento) | Datos del back office (eventos del lado del servidor) |
|---|---|---|
| **Definición** | Clics o acciones que los clientes realizan en el sitio. | Información sobre el ciclo de vida y detalles de cada pedido (anterior y actual). |
| **Eventos capturados por Adobe Commerce** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlayed](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[Historial de pedidos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### ¿Qué puedo hacer con solo Adobe Commerce?

Usar Adobe [!DNL Commerce] para configurar recordatorios de correo electrónico basados en reglas, que pueden servir como correos electrónicos de abandono del carro de compras o del explorador. Descubra cómo aquí.

### Qué puedo hacer con el Adobe [!DNL Commerce] ¿y Experience Cloud?

- **Adobe [!DNL Commerce] con Adobe Journey Optimizer** - Uso del Adobe [!DNL Commerce] con Adobe Journey Optimizer permite utilizar [!DNL Commerce] datos como déclencheur para un recorrido de abandono omnicanal. Puede personalizar ese recorrido en función de los atributos del cliente, los artículos que abandonó, otros comportamientos de compra y los comportamientos de compra anteriores.

- **Adobe Commerce, Adobe Journey Optimizer y Adobe Real-Time CDP** - Añadir Real-Time CDP le permite refinar aún más las campañas de abandono en función de perfiles de clientes unificados y audiencias centralizadas basadas en reglas o potenciadas por IA. Por ejemplo, puede crear lo siguiente:

   - Una audiencia de &quot;convertidores potentes&quot; con una tasa de abandono baja
   - Una audiencia de &quot;alta consideración&quot; que ha vuelto a visitar determinadas categorías varias veces
   - Una audiencia de &quot;alto potencial&quot; con alto gasto y lealtad, pero que ha abandonado recientemente

### ¿Qué han conseguido otros clientes?

Adobe [!DNL Commerce] Los clientes de han logrado un impacto comercial significativo mediante la implementación de campañas de abandono personalizadas con Adobe [!DNL Commerce], ADOBE [!DNL Journey Optimizer], y ADOBE [!DNL Real-Time CDP].

Un minorista de ropa global y multimarca logró:

- Conversión 1.9x al hacer clic desde nuevas campañas
- Aumento del 57 % en los ingresos procedentes de los recorridos de abandono omnicanal
- Aumento del 41 % en la tasa de conversión de las campañas de renovación de la participación
- Más de 1000 nuevos compradores comprometidos por semana

Una compañía global de bebidas logró:

- Tasas de apertura de correo electrónico de renovación de participación del 36 %
- Aumento del 21 % en las tasas de clics
- Aumento del 8,5 % en la tasa de conversión
- El 89% de los abandonadores que vuelven a comprometerse convierten

## Vamos a empezar.

Este caso de uso en particular se centra en la creación de un correo electrónico de carro de compras abandonado mediante los datos de su [!DNL Commerce] y enviándola al Adobe [!DNL Journey Optimizer].

### ¿Qué es Adobe Journey Optimizer?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) le ayuda a personalizar la experiencia de comercio para sus compradores. Por ejemplo, puede utilizar Journey Optimizer para crear y enviar campañas de marketing programadas, como promociones semanales de una tienda minorista, o generar un correo electrónico de carro de compras abandonado si un cliente agregó un producto a un carro de compras pero luego no completó el proceso de cierre de compra.

En este tema, aprenderá a crear un correo electrónico de carro de compras abandonado escuchando un `checkout` evento generado a partir de su [!DNL Commerce] y responder a ese evento en Journey Optimizer.

>[!IMPORTANT]
>
>Para fines de demostración, utilice su [!DNL Commerce] entorno limitado para que no diluya los datos del evento de producción con los datos de evento de tienda y back office que envía a Experience Platform.

### Requisitos previos

Antes de comenzar con estos pasos, asegúrese de lo siguiente:

- Se le ha aprovisionado para utilizar el Adobe [!DNL Journey Optimizer]. Si no está seguro, póngase en contacto con el integrador de sistemas o con el equipo de desarrollo que administra los proyectos y entornos.
- Usted [instalado](install.md) y [configurado](connect-data.md) el [!DNL Data Connection] extensión en [!DNL Commerce].
- Usted [confirmado](connect-data.md#confirm-that-event-data-is-collected) que su [!DNL Commerce] los datos de evento llegan al perímetro del Experience Platform.

## Paso 1: Crear un usuario en su [!DNL Commerce] entorno de zona protegida

Cree un usuario en el entorno de zona protegida y confirme que la información de la cuenta de usuario aparece en el Experience Platform. Asegúrese de que el correo electrónico especificado sea válido, ya que se utiliza más adelante en esta sección para enviar el correo electrónico del carro de compras abandonado.

1. Inicie sesión o cree una cuenta en su [!DNL Commerce] entorno de zona protegida.

   ![Inicie sesión en su cuenta de prueba](assets/sign-in-account.png){width="700" zoomable="yes"}

   Con el [!DNL Data Connection] extensión instalada y configurada, esta información de la cuenta se envía al Experience Platform como un perfil.

1. Confirme que la información de su cuenta de usuario aparece en la **[!UICONTROL Profile]** sección del Experience Platform.

   Ir a **[!UICONTROL Profiles]** en Adobe Experience Platform. Clic **[!UICONTROL Detail]** para ver el perfil que ha creado.

   ![Confirmar perfil](assets/check-event-profile.png){width="700" zoomable="yes"}

## Paso 2: Ver eventos en Journey Optimizer

En su [!DNL Commerce] entorno de zona protegida, déclencheur eventos en la tienda mediante la visualización de páginas de productos, la adición de artículos a un carro de compras y la finalización de otras actividades que realizaría un comprador. A continuación, confirme que estos eventos fluyen a Journey Optimizer.

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Seleccionar **[!UICONTROL Profiles]**.
1. Establecer **[!UICONTROL Identity namespace]** hasta `Email`.
1. Configure las variables **[!UICONTROL Identity value]** a su dirección de correo electrónico.
1. Seleccione el perfil y, a continuación, seleccione el **[!UICONTROL Events]** pestaña.

   ![Comprobar detalles del evento](assets/check-event-details.png){width="700" zoomable="yes"}

   Busque la variable `commerce.checkouts` y examine la carga útil del evento:

       &quot;json
       &quot;personID&quot;: &quot;84281643067178465783746543501073369488&quot;,
       &quot;eventType&quot;: &quot;commerce.checkouts&quot;,
       &quot;_id&quot;: &quot;4b41703f-e42e-485b-8d63-7001e3580856-0&quot;,
       &quot;commerce&quot;: {
       &quot;carrito&quot;: {},
       &quot;cierres de compra&quot;: {
       &quot;valor&quot;: 1
       }
       &quot;
   
   Como puede ver, la carga útil de evento completa contiene datos de evento enriquecidos. En la siguiente sección, configurará eventos en Journey Optimizer para detectar y responder a los `commerce.checkouts` evento generado a partir de su [!DNL Commerce] tienda.

## Paso 3: Configuración de eventos en Journey Optimizer

Configure dos eventos en Journey Optimizer: un evento escucha el `commerce.checkouts` Commerce y el otro es un evento de tiempo de espera básico que espera a que transcurra un tiempo específico antes de activar un correo electrónico de carro de compras abandonado.

### Crear un evento de escucha

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Clic **[!UICONTROL Configurations]** en el **[!UICONTROL Administration]** del panel izquierdo.

1. En el **[!UICONTROL Events]** mosaico, haga clic en **[!UICONTROL Manage]**.

   ![Configuración de eventos de Journey Optimizer](assets/ajo-config.png){width="700" zoomable="yes"}

1. En el **[!UICONTROL Events]** página, haga clic en **[!UICONTROL Create Event]**.

1. En el panel de navegación derecho, configure el evento de la siguiente manera:

   1. Configure las variables **[!UICONTROL Name]** hasta: `firstname_lastname_checkout`.
   1. Establecer **[!UICONTROL Type]** hasta **[!UICONTROL Unitary]**.
   1. Establecer **[!UICONTROL Event id typ]e** hasta **[!UICONTROL Rule based]**.
   1. Establecer **[!UICONTROL Schema]** a su [!DNL Commerce] [esquema](update-xdm.md).
   1. Seleccionar **[!UICONTROL Fields]** para abrir **[!UICONTROL Fields]** página. A continuación, seleccione los campos útiles para este evento. Por ejemplo, seleccione todos los campos bajo la etiqueta **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, y **[!UICONTROL Web]**.
   1. Clic **[!UICONTROL OK]** para guardar los campos seleccionados.
   1. Haga clic dentro de **[!UICONTROL Event id condition]** field. A continuación, cree una condición: `eventType` is equal to `commerce.checkouts` Y `personalEmail.address` es igual a la dirección de correo electrónico que utilizó al crear el perfil en la sección anterior.

      ![Journey Optimizer Establecer condición](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Clic **[!UICONTROL OK]**.
   1. Clic **[!UICONTROL Save]** para guardar el evento.

### Creación de un evento de tiempo de espera

1. Cree un evento en Journey Optimizer como lo hizo anteriormente.

1. En el panel de navegación derecho, configure el evento de la siguiente manera:

   1. Configure las variables **[!UICONTROL Name]** hasta: `firstname_lastname_timeout`.
   1. Establecer **[!UICONTROL Type]** hasta **[!UICONTROL Unitary]**.
   1. Establecer **[!UICONTROL Event id type]** hasta **[!UICONTROL Rule based]**.
   1. Establecer **[!UICONTROL Schema]** a su [!DNL Commerce] [esquema](update-xdm.md).
   1. Configure las variables **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, y **[!UICONTROL Event id condition]** a la misma que la anterior.
   1. Clic **[!UICONTROL Save]** para guardar el evento.

Con estos dos eventos configurados, cree un recorrido que envíe un correo electrónico del carro de compras abandonado.

## Paso 4: Crear un recorrido de cierre de compra

Cree un recorrido que escuche el `commerce.checkouts` y, a continuación, envía un correo electrónico de carro de compras abandonado después de que haya transcurrido un tiempo determinado.

1. En Journey Optimizer, seleccione **[!UICONTROL Journeys]** bajo **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Clic **[!UICONTROL Create Journey]**.
1. Especifique el nombre del recorrido.
1. Clic **[!UICONTROL OK]** para guardar el recorrido.
1. En el panel de navegación izquierdo, debajo de **[!UICONTROL EVENTS]** , busque el evento de cierre de compra que creó anteriormente: `firstname_lastname_checkout` y arrástrelo y suéltelo en el lienzo.

   >[!TIP]
   >
   >Al hacer doble clic en el evento, se agrega automáticamente al lienzo.

1. Busque el evento de tiempo de espera y añádalo al lienzo.
1. Haga doble clic en el evento de tiempo de espera.

   1. En el **[!UICONTROL Timeout]** , seleccione la **[!UICONTROL Define the event time]** casilla de verificación
   1. En el **[!UICONTROL Wait for]** field enter `1` y `Minute`.
   1. Seleccione el **[!UICONTROL Set a timeout path]** casilla de verificación

   Con esta configuración de tiempo de espera, un comprador que realiza un cierre de compra pero no completa el pedido en un minuto déclencheur esta rama de tiempo de espera. En un entorno de producción real, establecería esto para un período más largo, como de 24 horas.

1. En el panel de navegación izquierdo, debajo de **[!UICONTROL ACTIONS]**, añada el **[!UICONTROL Email]** acción a la rama de tiempo de espera. El recorrido debería tener el siguiente aspecto:

   ![Lienzo de Journey Optimizer](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Crear un correo electrónico de carro de compras abandonado

Cree un correo electrónico de carro de compras abandonado que se enviará cuando se detecte un carro de compras abandonado.

1. En el recorrido que ha creado anteriormente, haga doble clic en **[!UICONTROL Email]** en el lienzo.

1. Siga las [pasos](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) en la guía de Journey Optimizer para crear el correo electrónico del carro de compras abandonado.

Ahora tiene un recorrido en Journey Optimizer que escucha el `commerce.checkouts` evento de su [!DNL Commerce] y un correo electrónico del carro de compras abandonado que se envía después de que haya transcurrido un período de tiempo. La siguiente sección muestra cómo probar el recorrido.

## Paso 5: Déclencheur del evento de cierre de compra en tiempo real

En esta sección, probará el evento en tiempo real.

1. En Journey Optimizer, active el modo de prueba.

   ![Habilitar modo de prueba](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Para probar este recorrido en tiempo real, abra otra pestaña del explorador y vaya a [!DNL Commerce] en su entorno de zona protegida.

   1. Añadir un producto al carro de compras.
   1. Vaya a la página de cierre de compra.
   1. En la página de cierre de compra, abandone el carro de compras volviendo a la página principal o cerrando la pestaña.

      El recorrido se activa. Para confirmarlo, abra la pestaña que tenga el recorrido en Journey Optimizer. Debería ver una flecha verde que muestra la ruta que siguió el usuario.

1. Busque el correo electrónico en su bandeja de entrada.
