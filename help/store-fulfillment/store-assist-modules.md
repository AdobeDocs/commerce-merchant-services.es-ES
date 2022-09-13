---
title: Flujos de trabajo de cumplimiento de Store Assist
description: Obtenga información sobre los módulos Pick, Stage, Hand-Off y Orders disponibles en la aplicación de asistencia de tienda. Estos módulos habilitan el flujo de trabajo completo de cumplimiento de la tienda para los pedidos de BOPIS. Store Associates utiliza estos módulos para administrar y entregar pedidos de recogida de tiendas a los clientes.
role: User
level: Intermediate
exl-id: a8414f19-5489-41e9-84d6-39d2e61c2b08
source-git-commit: fda4620f57aa7aa9fb930b10f5717fee98983378
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# Flujos de trabajo de cumplimiento de Store Assist

La aplicación Store Assist proporciona a Store Associates cuatro módulos para administrar el proceso de cumplimiento en la tienda para la compra en línea y la recogida en pedidos de la tienda:

- **[Seleccionar](#pick-module)**: obtenga una visibilidad completa de todos los elementos pedidos y las herramientas para asegurarse de que se seleccionan los elementos adecuados y las cantidades correctas. Los asociados del almacén pueden seleccionar uno o varios pedidos simultáneamente para obtener una buena eficacia.

- **[Prueba](#stage-module)**: introduzca una ubicación en la que se realizan los pedidos mientras los clientes viajan a la tienda, de modo que Store Associates pueda encontrarlos fácilmente para realizar la entrega de los pedidos.

- **[Desactivar mano](#hand-off-module)**: obtenga notificaciones en tiempo real después de que los clientes lleguen a la tienda para minimizar el tiempo de espera y los pedidos de entrega sin problemas.

- **[Pedidos](#orders-module)**: permite ver una lista de todos los pedidos realizados para un almacén, de modo que todos sepan el número de pedidos y el estado de cada pedido.

>[!NOTE]
>
>Antes de que Store Associates pueda usar la aplicación Store Assist, un administrador debe completar la [proceso de configuración de la aplicación](app-setup.md).

## Seleccionar módulo

El módulo Pick ayuda a los asociados de la tienda a buscar y analizar los artículos pedidos por el cliente y sacarlos para que los recojan. Se puede ver cuántos pedidos tienen que haberse hecho antes y empezar a recogerlos de inmediato. También puede elegir otros pedidos para elegir primero. Los pedidos se ordenan por tiempo de entrega con pedidos vencidos primero. Los asociados del almacén pueden seleccionar los pedidos que desean seleccionar en el orden que requieran sus operaciones.

Los asociados también pueden elegir elegir elegir entre un pedido a la vez o varios pedidos al mismo tiempo.

Al realizar la selección, los asociados de la tienda verán una lista de todos los artículos que se seleccionarán para cada pedido, sus cantidades, su precio y la descripción del producto del catálogo. Se muestra una barra de progreso para ayudarles a navegar dentro del asistente de almacenamiento mientras seleccionan los pedidos.

Una vez que los asociados empiezan a seleccionar y seleccionan los artículos que se van a elegir, se les presenta toda la información del artículo relevante, como: tamaño, color, cantidad, precio, descripción, ajuste y SKU/UPC. Los asociados tienen dos acciones disponibles al seleccionar pedidos:

- Indique que no se encuentra el artículo y asígnele un déclencheur de reembolso.
- Analizar el código de barras en el elemento. El propósito del análisis es verificar que han seleccionado el elemento correcto. En los casos en que la cámara no pueda leer el código de barras, los asociados de la tienda deben introducir manualmente el SKU del elemento que hayan seleccionado.

Si los asociados no pueden encontrar un elemento, pueden omitirlo y volver a él más tarde.  El reembolso mencionado anteriormente se emite solamente una vez que completan su etapa de recolección en la orden.

## Módulo de ensayo

El módulo Stage muestra dónde se realiza el pedido registrado hasta que el cliente llega a recogerlo. La configuración de esta ubicación es un paso clave para evitar pedidos perdidos cuando los asociados de la tienda terminan su turno antes de que llegue el cliente o si tiene muchos pedidos. En cualquier caso, esto está diseñado para ayudarle a encontrar rápidamente el orden correcto con toda la información relevante sobre él.

Puede utilizar una barra de texto de forma libre para indicar dónde se coloca el orden: en el mostrador, en la sala trasera o en la ubicación B3 - todo basado en sus operaciones.

También puede actualizar fácilmente la ubicación de ensayo en la aplicación si sus asociados necesitan colocarla en otro lugar.

## Módulo de desactivación de mano

La variable [!UICONTROL Hand Off] muestra qué clientes han registrado para recoger sus pedidos y dónde se han realizado sus pedidos y esperan a ellos. Los clientes pueden recoger pedidos en la tienda o en el aparcamiento exterior/costado. La información sobre su ubicación exacta se presenta en este módulo una vez que se han registrado.

Una vez que seleccione en un pedido que esté listo para la entrega del cliente. Todos pueden ver la información del pedido, incluidos los artículos que no se han encontrado, la ubicación de espera del cliente, el tiempo de espera, la ubicación en la que se ha realizado el pedido y el número de teléfono del cliente, si está disponible.

Es posible que el cliente haya elegido una persona alternativa para recoger el pedido. En este caso, verá el nombre y la información de contacto de la persona que se supone que debe elegir el pedido.

Al entregar el pedido al cliente, el Asociado de Tiendas debe aceptar el pedido o rechazar ciertos artículos. Una vez que el cliente esté satisfecho, debe firmar el pedido en el dispositivo de su asociado, si una firma de su empresa requiere una firma.

Si los clientes llegan sin registrarse, sus asociados pueden comprobarlo manualmente.

## Módulo Pedidos

El módulo Pedidos muestra todos los pedidos existentes y su estado. Cuando un cliente llama para comprobar su pedido, Store Associates puede encontrar la información rápidamente buscando el número o buscando en el módulo Pedidos.

Store Associates también puede cancelar pedidos desde la página Pedidos de la aplicación Store Assist.
