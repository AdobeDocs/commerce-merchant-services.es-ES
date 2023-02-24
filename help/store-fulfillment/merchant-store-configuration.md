---
title: Configuración de tiendas de mercante
description: Configure las fuentes de Inventory management mejoradas como tiendas de productos.
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Configuración de tiendas de comerciantes (origen)

Esta solución mejora las capacidades nativas de Inventory management al ampliar las fuentes de existencias con funciones orientadas a las operaciones para los comerciantes.

- Añadir coordenadas geográficas para la ubicación de la tienda
- Designe el origen como un [!DNL Store Pickup Location] y especificar las capacidades de envío disponibles (Enviar a tienda, Enviar desde tienda)
- Especifique las opciones de recogida disponibles (en la tienda o en la malla), las instrucciones de recogida personalizadas y otra información para comunicar los detalles de la recogida y las instrucciones a los clientes

Los términos _source_ y _ubicación de la tienda de mercaderes_ se utilizan de forma intercambiable. Todos los registros son fuentes de inventario, pero las fuentes también pueden ser ubicaciones de tiendas comerciales, según los ajustes de configuración.

Administre la configuración de las tiendas de mercadotecnia desde el administrador: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>Durante el proceso de configuración, puede ser necesario vaciar la caché después de crear fuentes o actualizar fuentes existentes.

## **General**

<table>
<tbody>
<tr>
<th>Campo</th>
<th>Descripción</th>
<th>Ámbito</th>
<th>Requerido</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordenada latitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordenada longitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designe el origen como una ubicación de Recogida de tiendas disponible. Esta configuración determina si la fuente se sincroniza y muestra a los visitantes.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Configure las capacidades de envío a almacén en el nivel de origen. Para obtener más información, consulte la opción [General Configuration](enable-general.md) , <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordenada latitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordenada longitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación.</td>
<td>Global</td>
<td>Sí</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designe el origen como una ubicación de Recogida de tiendas disponible. Esta configuración determina si la fuente se sincroniza y muestra a los visitantes.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Configure las capacidades de envío a almacén en el nivel de origen. Para obtener más información, consulte la opción [General Configuration](enable-general.md) , <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Configure las capacidades de envío desde la tienda en el nivel de origen. Para obtener más información, consulte la opción [General Configuration](enable-general.md) , [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td>Global</td>
<td>No</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Coordenada latitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación. | Global | Sí |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Coordenada longitudinal de la ubicación de la tienda del comerciante. Esta información necesaria se utiliza en la búsqueda de ubicación y la ubicación de mapas en la experiencia de tienda. El valor debe coincidir con la dirección exacta del almacén para pasar la validación. | Global | Sí |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Designe el origen como una ubicación de Recogida de tiendas disponible. Esta configuración determina si la fuente se sincroniza y muestra a los visitantes. | Global | No |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Configure las capacidades de envío a almacén en el nivel de origen. Para obtener más información, consulte la [Configuración general](enable-general.md) , **[!UICONTROL Enable Ship To Store]**. | Global | No |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Configure las capacidades de envío desde la tienda en el nivel de origen. Para obtener más información, consulte la [Configuración general](enable-general.md) , [!UICONTROL Enable Ship From Store] | Global | No |

{style=&quot;table-layout:auto&quot;}

## Configuración de ubicación de recogida

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Una de las dos opciones de recogida. [!DNL In-Store Pickup] hace referencia a la capacidad de permitir que un cliente introduzca la ubicación de la tienda de comerciantes para recuperar su pedido. </br></br>Cuando está habilitada, esta opción se puede presentar al cliente durante el cierre de compra. </br></br>Esta opción también anula la configuración global a [!UICONTROL Enable In-store Pickup] que se configuró en la variable [!UICONTROL Delivery Method] para [!UICONTROL In-store Pickup] | Global | No |
| **Instrucciones de recogida en la tienda**</br>`Extension Attribute: store_pickup_instructions` | Un mensaje personalizable entregado al cliente en la variable **Pedido listo para recogida en tienda** notificación por correo electrónico. | Global | No |
| **Permitir lado de la curva**</br>`Extension Attribute: curbside_enabled` | Una de las dos opciones de recogida. La entrega en la curva permite al cliente estacionar su vehículo en un lugar designado en la ubicación de la tienda de mercantes. En esta situación, el pedido se entrega al cliente mediante un asociado de almacén. </br></br>Cuando está habilitada, esta opción se puede presentar al cliente durante el cierre de compra. Además, es posible que se pida al cliente que describa su vehículo y su estacionamiento durante el proceso de registro. </br></br>Esta opción también anula la configuración global a **Habilitar la selección en el lado de la curva** que se configuró en la variable **Método de entrega** para **Recogida en la tienda** | Global | No |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Un mensaje personalizable entregado al cliente en la variable [!UICONTROL Order Ready For Pickup in Store] notificación por correo electrónico. | Global | No |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Número de minutos necesarios para recibir, seleccionar y preparar la recepción de un pedido. </br></br>Esta información se utiliza para mostrar los tiempos estimados de recogida de pedidos a los clientes en el sitio web.</br></br> Al establecer esta opción, se anula la configuración global de **Tiempo de espera estimado** configurado para el **Método de entrega** en el **Recogida en la tienda** configuración. | Global | No |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Etiqueta que muestra el número de minutos hasta que un pedido está listo para ser recogido.</br></br> Al personalizar esta etiqueta, puede utilizar el código %1 para insertar su **Tiempo de espera estimado**.</br></br> Al establecer esta opción, se anula la configuración global de [!UICONTROL Estimated Pickup Time Label] configurado para el [!UICONTROL Delivery Method] en el [!UICONTROL In-store Pickup]. | Global | No |

### **Horas de apertura**

| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | Zona horaria de la ubicación de la tienda de mercantes. Para cada día, establezca las horas de apertura y cierre.</br></br>Estos ajustes se utilizan para optimizar los tiempos de recogida estimados y los informes del servicio de cumplimiento. | Global | Sí |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | Las horas de funcionamiento de la ubicación de la tienda de mercantes. </br></br>Esta información se puede utilizar para optimizar los tiempos de recogida estimados y en los informes de servicio de cumplimiento. | Global | Sí |

### Configurar las opciones de la interfaz de Experience Platform Check-in



| **Campo** | **Descripción** | **Ámbito** | **Requerido** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Especifique si la ubicación de la tienda de mercantes tiene plazas de estacionamiento designadas para la recogida en la esquina. </br></br>Cuando esté habilitado, puede configurar los aparcamientos disponibles. | Global | No |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Especifique si se requiere identificación de zona de estacionamiento para los clientes durante la experiencia de compra.</br></br>Si está activado, se pide al cliente que especifique su plaza de estacionamiento al llegar. Si está desactivado, el cliente puede omitir esta entrada. | Global | No |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Los aparcamientos disponibles en esta tienda comercial para la recogida en la cordillera. Utilice la interfaz proporcionada para asignar un nombre a cada zona.</br></br> No es necesario nombrar todos los aparcamientos, sólo los lugares destinados a la cortina. Por ejemplo, puede tener disponibles las filas A-G de estacionamiento, pero solo se designan los 8 primeros lugares de la fila A para la recogida en la esquina. En este escenario, puede definir 8 puntos; ex: A1, A2, A3, etc. | Global | No |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Cuando está habilitado, esta configuración permite al cliente describir su lugar de estacionamiento durante el registro de entrada. | Global | No |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Especifique si se admite la recopilación del color del vehículo por parte del cliente durante el registro de entrada. </br></br> Las selecciones disponibles para [!UICONTROL Car Color] están configuradas en el [configuración del sistema para la experiencia de registro](check-in-experience-setup.md). | Global | No |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Especifique si se requiere la identificación del color del vehículo para los clientes durante el registro.</br></br>Si está activado, se pide al cliente que especifique el color de su vehículo a su llegada. Si está desactivado, el cliente puede omitir esta entrada. | Global | No |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Especifique si se admite la recopilación de la marca de vehículo del cliente durante el registro de entrada.</br></br> Las selecciones disponibles para [!UICONTROL Car Make] están configuradas en el [configuración del sistema para la experiencia de registro](check-in-experience-setup.md). | Global | No |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Especifique si se requiere la identificación del vehículo para los clientes durante el registro.</br></br>Si está activado, se pide al cliente que especifique la marca de su vehículo a su llegada. Si está desactivado, el cliente puede omitir esta entrada. | Global | No |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Especifique si se admite la recopilación de información adicional del cliente durante el registro. | Global | No |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Especifique si se requiere información adicional para los clientes durante el registro. </br></br>Si está activado, se solicita al cliente que introduzca información adicional a su llegada. Si está desactivado, el cliente puede omitir esta entrada. | Global | No |
