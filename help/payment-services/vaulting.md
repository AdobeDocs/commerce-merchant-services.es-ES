---
title: Validación de tarjetas de crédito
description: Los compradores pueden almacenar (guardar) los datos de sus tarjetas de crédito para futuras compras.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Validación de tarjetas de crédito

Convierta a los clientes únicos en compradores fieles con bóvedas de tarjetas de crédito. Los compradores pueden guardar (o &quot;bóveda&quot;) sus credenciales de tarjeta de crédito durante el cierre de compra para usarlas en una compra posterior para la misma cuenta o para otra tienda dentro de la misma cuenta de comerciante.

![Almacene su tarjeta de crédito para uso posterior](assets/save-card-for-later.png)

Los compradores utilizan el token almacenado para realizar un cierre de compra futuro con la información guardada de su tarjeta de crédito.

![Usar credenciales almacenadas para compras futuras](assets/use-stored-card.png)

También pueden eliminar fácilmente sus tarjetas de crédito abovedadas de [Métodos de pago almacenados](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) en su Mi cuenta.

![Métodos de pago almacenados en mi cuenta](assets/stored-payment-methods.png)

## Habilitar bóveda

Puede habilitar la bóveda de tarjetas de crédito para clientes _y_ comerciantes en Admin: para sus tiendas en [!DNL Payment Services] [Configuración](settings.md#card-vaulting).

## Usar la bóveda en el administrador

Si un cliente tiene una tarjeta de crédito anteriormente abovedada, un comerciante puede crear un pedido subsiguiente para ese cliente en el Administrador mediante sus métodos de pago en blanco.

Solo puede utilizar tarjetas abovedadas en el Administrador si el cliente tiene una cuenta existente y un token válido almacenados en el sistema desde un pago completado anteriormente.

Para crear un pedido en el Administrador de un cliente con su tarjeta de crédito abovedada:

1. [Crear un pedido y agregar productos](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. En _[!UICONTROL Payment & Shipping Information]_, seleccione **[!UICONTROL Stored Cards]**como método de pago.
1. Seleccione el método de pago de tarjeta de crédito con bóveda que desee.
1. Después de completar cualquier otro paso necesario para la solicitud, [enviarlo](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Uso de la tarjeta de crédito abovedada en Admin para clientes](assets/admin-vaultedcard.png)

## Seguridad

La información mínima de la tarjeta de crédito se comparte con el comprador; solo ven los cuatro últimos dígitos, la fecha de caducidad y la marca de su tarjeta de crédito abovedada. La información de la tarjeta de crédito se almacena con el proveedor de pagos para satisfacer [PCI](security.md#PCI-compliance) estándares de cumplimiento.
