---
title: Usar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado
description: Aprenda a utilizar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 261416654773470edfa3cc22058cccf92ef29cdb
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# Usar Adobe Journey Optimizer para enviar un correo electrónico de carro de compras abandonado

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) le ayuda a personalizar la experiencia de comercio para sus compradores. Por ejemplo, puede utilizar Journey Optimizer para crear y enviar campañas de marketing programadas, como promociones semanales de una tienda minorista, o generar un correo electrónico de carro de compras abandonado si un cliente agregó un producto a un carro de compras pero luego no completó el proceso de cierre de compra.

Al seguir estos pasos, puede aprender a escuchar una `checkout` generado a partir de la instancia de Commerce y responde a ese evento en Journey Optimizer para crear un correo electrónico de carro de compras abandonado.

>[!IMPORTANT]
>
>Para fines de demostración, asegúrese de que está utilizando su entorno de zona protegida de Commerce. Esto garantiza que los datos de evento de la tienda y del back office que envía al Experience Platform no diluyan los datos de evento de producción.

## Requisitos previos

Antes de comenzar con estos pasos, asegúrese de lo siguiente:

- Se le ha aprovisionado para utilizar Adobe Journey Optimizer
- Usted [configurado](connect-data.md) el conector del Experience Platform
- Usted [confirmado](connect-data.md#confirm-that-event-data-is-collected) los datos del evento de Commerce llegan al perímetro del Experience Platform

## Paso 1: Crear un usuario en el entorno de zona protegida de Commerce

Cree un usuario en el entorno de zona protegida y confirme que la información de la cuenta de usuario aparece en el Experience Platform. Asegúrese de que el correo electrónico especificado sea válido, ya que se utiliza más adelante en esta sección para enviar el correo electrónico del carro de compras abandonado.

1. Inicie sesión o cree una cuenta en su entorno de zona protegida de Commerce.

   ![Inicie sesión en su cuenta de prueba](assets/sign-in-account.png){width="700" zoomable="yes"}

   Con el conector de Experience Platform instalado y configurado, esta información de la cuenta se envía al Experience Platform como un perfil.

1. Confirme que la información de su cuenta de usuario aparece en la **[!UICONTROL Profile]** sección del Experience Platform.

   Ir a **[!UICONTROL Profiles]** en Adobe Experience Platform. Clic **[!UICONTROL Detail]** para ver el perfil que ha creado.

   ![Confirmar perfil](assets/check-event-profile.png){width="700" zoomable="yes"}

## Paso 2: Ver eventos en Journey Optimizer

En su entorno de zona protegida de Commerce, vea páginas de productos, añada artículos a un carro de compras y otras actividades que realizaría un comprador. Estas actividades almacenan en déclencheur los eventos de la tienda. Ahora puede confirmar que estos eventos fluyen a Journey Optimizer.

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Seleccionar **[!UICONTROL Profiles]**.
1. Establecer **[!UICONTROL Identity namespace]** hasta `Email`.
1. Configure las variables **[!UICONTROL Identity value]** a su dirección de correo electrónico.
1. Seleccione el perfil y, a continuación, seleccione el **[!UICONTROL Events]** pestaña.

   ![Comprobar detalles del evento](assets/check-event-details.png){width="700" zoomable="yes"}

   Busque la variable `commerce.checkouts` y examine la carga útil del evento:

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   Como puede ver, la carga útil de evento completa contiene datos de evento enriquecidos. En la siguiente sección, configurará eventos en Journey Optimizer para detectar y responder a los `commerce.checkouts` evento generado desde su tienda de Commerce.

## Paso 3: Configuración de eventos en Journey Optimizer

Configure dos eventos en Journey Optimizer: un evento escucha el `commerce.checkouts` y el otro es un evento de tiempo de espera básico que espera a que transcurra una cantidad de tiempo específica antes de activar un correo electrónico de carro de compras abandonado.

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
   1. Establecer **[!UICONTROL Schema]** a su Commerce [esquema](update-xdm.md).
   1. Seleccionar **[!UICONTROL Fields]** y en el **[!UICONTROL Fields]** , seleccione los campos que sean útiles para este evento.

      Por ejemplo, seleccione todos los campos bajo la etiqueta **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, y **[!UICONTROL Web]**.

   1. Clic **[!UICONTROL OK]** para guardar los campos seleccionados.
   1. Haga clic dentro de **[!UICONTROL Event id condition]** y cree una condición de `eventType` is equal to `commerce.checkouts` Y `personalEmail.address` es igual a la dirección de correo electrónico que utilizó al crear el perfil en la sección anterior.

      ![Journey Optimizer Establecer condición](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Haga clic **[!UICONTROL OK]**.
   1. Clic **[!UICONTROL Save]** para guardar el evento.

### Creación de un evento de tiempo de espera

1. Cree un evento en Journey Optimizer como lo hizo anteriormente.

1. En el panel de navegación derecho, configure el evento de la siguiente manera:

   1. Configure las variables **[!UICONTROL Name]** hasta: `firstname_lastname_timeout`.
   1. Establecer **[!UICONTROL Type]** hasta **[!UICONTROL Unitary]**.
   1. Establecer **[!UICONTROL Event id typ]e** hasta **[!UICONTROL Rule based]**.
   1. Establecer **[!UICONTROL Schema]** a su Commerce [esquema](update-xdm.md).
   1. Configure las variables **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, y **[!UICONTROL Event id condition]** a la misma que la anterior.
   1. Clic **[!UICONTROL Save]** para guardar el evento.

Con estos dos eventos configurados, cree un recorrido que envíe un correo electrónico del carro de compras abandonado.

## Paso 4: Crear un recorrido de cierre de compra

Cree un recorrido que escuche el `commerce.checkouts` y, a continuación, envía un correo electrónico de carro de compras abandonado después de que haya transcurrido un tiempo determinado.

1. En Journey Optimizer, seleccione **[!UICONTROL Journeys]** bajo **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Haga clic **[!UICONTROL Create Journey]**.
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

Ahora tiene un recorrido en Journey Optimizer que escucha el `commerce.checkouts` desde la tienda de Commerce y un correo electrónico del carro de compras abandonado que se envía después de que haya transcurrido un periodo de tiempo. En la siguiente sección, probará el recorrido.

## Paso 5: Déclencheur del evento de cierre de compra en tiempo real

En esta sección, probará el evento en tiempo real.

1. En Journey Optimizer, active el modo de prueba.

   ![Habilitar modo de prueba](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Para probar este recorrido en tiempo real, abra otra pestaña del explorador y vaya al sitio web de Commerce de la zona protegida.

   1. Añadir un producto al carro de compras.
   1. Vaya a la página de cierre de compra.
   1. En la página de cierre de compra, abandone el carro de compras volviendo a la página principal o cerrando la pestaña.

      El recorrido se activa. Para confirmarlo, abra la pestaña que tenga el recorrido en Journey Optimizer. Debería ver una flecha verde que muestra la ruta que siguió el usuario.

1. Busque el correo electrónico en su bandeja de entrada.
