---
title: Configuración
description: Aprenda a cambiar la fuente de su [!DNL Product Recommendations] y cómo habilitar recomendaciones visuales.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 6d0c7c749fe90c7c204afe47446f3483d8668b53
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuración

Cuando [configuración de un espacio de datos SaaS](https://docs.magento.com/user-guide/configuration/services/saas.html) para Recommendations, el espacio de datos SaaS recopila datos de catálogo y datos de comportamiento de tienda. [Adobe Sensei](https://www.adobe.com/sensei.html) analiza esos datos y calcula las asociaciones de productos utilizadas para servir Product Recommendations.

Los entornos que no son de producción para pruebas o ensayos no suelen tener la cantidad o calidad de datos de comportamiento de tienda para ofrecer recomendaciones de productos realistas. El comportamiento real del comprador a escala solo se puede capturar en un entorno de producción. Para resolver este problema, Adobe Commerce le permite utilizar las recomendaciones de productos de su entorno de producción con otros espacios de datos SaaS que no sean de producción. El uso de datos reales de tienda en un entorno que no sea de producción le permite obtener una vista previa de las recomendaciones que ven los compradores y experimentar con diferentes tipos de recomendaciones y ubicaciones. Los compradores pueden obtener una vista previa de Recommendations desde otro espacio de datos SaaS, pero no hacer clic en él.

## Elija el origen de las recomendaciones

Para cambiar el origen de los datos de recomendaciones de productos, elija el espacio de datos SaaS con los datos de comportamiento que desee utilizar. Antes de empezar, asegúrese de que:

- La recopilación de datos de tienda debe ser [configurado y habilitado](install-configure.md) para su entorno de producción y [verificado](verify.md) los datos de comportamiento se envían a Adobe Commerce.
- El catálogo de entornos que no son de producción debe ser esencialmente el mismo que el catálogo de producción. El uso de catálogos similares garantiza que las unidades de recomendación del producto devueltas imiten de cerca a las de producción.

1. Inicie sesión en el administrador de su entorno de Adobe Commerce que no sea de producción.

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Recommendations de producto**.

1. Haga clic en **Configuración**.

   ![configuración de recomendaciones del producto](assets/settings.png)
   _Configuración_

1. En el _Fuente de Recommendations_ , habilite **Recuperar recomendaciones de un espacio de datos SaaS diferente** . La variable _Fuente de Recommendations_ solo aparece en un entorno que no sea de producción.

   Una lista de _Espacios de datos SaaS disponibles_ aparece.

   ![configuración de recomendaciones del producto](assets/settings-select-saas.png)
   _Configuración_

1. Seleccione el espacio de datos SaaS que tiene datos de comprador que desee utilizar.

1. Haga clic en **Guardar cambios**.

   Adobe Commerce ahora obtiene recomendaciones del espacio de datos seleccionado.

   >[!NOTE]
   >
   > Aunque puede ver las recomendaciones recuperadas de otro espacio de datos SaaS en la tienda que no sea de producción, no puede hacer clic en las recomendaciones.

### Configuración de un nuevo espacio de datos SaaS

1. En la sección Recommendations source , haga clic en **Editar configuración**.

1. Siga las instrucciones para configurar un [[!DNL Commerce] service](/help/landing/saas.md).

## Habilitar recomendaciones visuales

Si la variable [Recommendations de productos visuales](install-configure.md) está instalado, debe habilitar Visual Recommendations para que use el [Similitud visual](type.md#visualsim) tipo de recomendación.

En el _Visual Recommendations_ sección, establecer **Habilitar Visual Recommendations** a la posición activa.
