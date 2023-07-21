---
title: Configuración
description: Aprenda a cambiar el origen de su [!DNL Product Recommendations] datos y cómo habilitar las recomendaciones visuales.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 48e350167611a2737d79bf5decccd7f6f24c714c
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Configuración

Cuando usted [configuración de un espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) para Recommendations, el espacio de datos SaaS recopila datos de catálogo y datos de comportamiento de tienda. [Adobe Sensei](https://www.adobe.com/sensei.html) analiza esos datos y calcula las asociaciones de productos que se usan para usar Product Recommendations.

Los entornos que no son de producción para pruebas o ensayo generalmente no tienen la cantidad o calidad de los datos de comportamiento de la tienda para ofrecer recomendaciones de productos realistas. El comportamiento real del comprador a escala solo se puede capturar en un entorno de producción. Para solucionar este problema, Adobe Commerce le permite utilizar recomendaciones de productos de su entorno de producción con otros espacios de datos de SaaS que no sean de producción. El uso de datos reales de la tienda en un entorno que no sea de producción le permite obtener una vista previa de las recomendaciones que ven los compradores y experimentar con diferentes tipos de recomendaciones y ubicaciones. Los compradores pueden obtener una vista previa de Recommendations desde un espacio de datos de SaaS diferente, pero no hacer clic en él.

>[!NOTE]
>
>Cuando se utiliza Product Recommendations mediante REST, la variable `alternateEnvironmentId` se puede utilizar para especificar otros espacios de datos. Este parámetro no está disponible cuando se utiliza Product Recommendations mediante GraphQL.

## Elija la fuente de las recomendaciones

Para cambiar la fuente de los datos de recomendaciones de productos, elija el espacio de datos SaaS con los datos de comportamiento que desee utilizar. Antes de empezar, asegúrese de que:

- La recopilación de datos de la tienda debe ser [configurado y habilitado](install-configure.md) para su entorno de producción y [verificado](verify.md) que los datos de comportamiento se están enviando a Adobe Commerce.
- El catálogo de entornos de no producción debe ser esencialmente el mismo que el catálogo de producción. El uso de catálogos similares garantiza que las unidades de recomendación de productos devueltas imiten de cerca las de la producción.

1. Inicie sesión en el administrador del entorno de Adobe Commerce que no sea de producción.

1. En el _Administrador_ barra lateral, vaya a **Marketing** > _Promociones_ > **Product Recommendations**.

1. Clic **Configuración**.

   ![configuración de recomendaciones de productos](assets/settings.png)
   _Configuración_

1. En el _fuente de Recommendations_ , habilite la sección **Obtener recomendaciones de un espacio de datos de SaaS diferente** opción. El _fuente de Recommendations_ solo aparece en un entorno que no sea de producción.

   Una lista de _Espacios de datos SaaS disponibles_ aparece.

   ![configuración de recomendaciones de productos](assets/settings-select-saas.png)
   _Configuración_

1. Seleccione el espacio de datos SaaS que tenga los datos de comprador que desee utilizar.

1. Clic **Guardar cambios**.

   Adobe Commerce ahora obtiene recomendaciones del espacio de datos seleccionado.

   >[!NOTE]
   >
   > Aunque puede ver las recomendaciones recuperadas de otro espacio de datos de SaaS en la tienda que no sea de producción, no puede hacer clic en las recomendaciones.

### Configuración de un nuevo espacio de datos SaaS

1. En la sección Origen de Recommendations, haga clic en **Editar configuración**.

1. Siga las instrucciones para configurar una nueva [[!DNL Commerce] servicio](/help/landing/saas.md).

## Habilitar recomendaciones visuales

Si la variable [Visual Product Recommendations](install-configure.md) está instalado, debe habilitar Visual Recommendations para que utilice el [Similitud visual](type.md#visualsim) tipo de recomendación.

En el _Visual Recommendations_ sección, conjunto **Habilitar Visual Recommendations** a la posición activa.
