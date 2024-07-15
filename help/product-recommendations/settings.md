---
title: Configuración
description: Aprenda a cambiar el origen de sus  [!DNL Product Recommendations] datos y a habilitar las recomendaciones visuales.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Configuración

Al [configurar un espacio de datos SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) para Recommendations, el espacio de datos SaaS recopila datos de catálogo y datos de comportamiento de tienda. [Adobe Sensei](https://www.adobe.com/sensei.html) analiza esos datos y calcula las asociaciones de productos que se usan para usar Product Recommendations.

Los entornos que no son de producción para pruebas o ensayo generalmente no tienen la cantidad o calidad de los datos de comportamiento de la tienda para ofrecer recomendaciones de productos realistas. El comportamiento real del comprador a escala solo se puede capturar en un entorno de producción. Para solucionar este problema, Adobe Commerce le permite utilizar recomendaciones de productos de su entorno de producción con otros espacios de datos de SaaS que no sean de producción. El uso de datos reales de la tienda en un entorno que no sea de producción le permite obtener una vista previa de las recomendaciones que ven los compradores y experimentar con diferentes tipos de recomendaciones y ubicaciones. Los compradores pueden obtener una vista previa de Recommendations desde un espacio de datos de SaaS diferente, pero no hacer clic en él.

Los pedidos de ensayo se registran usando el ensayo `environmentId`. No afecta a los datos de producción. Los datos de producción se recuperaron usando `alternateEnvironmentId`.

>[!NOTE]
>
>Al usar Product Recommendations mediante REST, el parámetro `alternateEnvironmentId` se puede usar para especificar otros espacios de datos. Este parámetro no está disponible cuando se utiliza Product Recommendations mediante GraphQL.

## Elija la fuente de las recomendaciones

Para cambiar la fuente de los datos de recomendaciones de productos, elija el espacio de datos SaaS con los datos de comportamiento que desee utilizar. Antes de empezar, asegúrese de que:

- La recopilación de datos de la tienda debe estar [configurada y habilitada](install-configure.md) para su entorno de producción y [verificada](verify.md) que los datos de comportamiento se están enviando a Adobe Commerce.
- El catálogo de entornos de no producción debe ser esencialmente el mismo que el catálogo de producción. El uso de catálogos similares garantiza que las unidades de recomendación de productos devueltas imiten de cerca las de la producción.

1. Inicie sesión en el administrador del entorno de Adobe Commerce que no sea de producción.

1. En la barra lateral de _Admin_, ve a **Marketing** > _Promociones_ > **Product Recommendations**.

1. Haga clic en **Configuración**.

   ![configuración de recomendaciones de productos](assets/settings.png)
   _Configuración_

1. En la sección _Origen de Recommendations_, habilite la opción **Recuperar recomendaciones desde un espacio de datos SaaS diferente**. La sección _Origen de Recommendations_ solo aparece en un entorno que no sea de producción.

   Aparecerá una lista de _espacios de datos SaaS disponibles_.

   ![configuración de recomendaciones de productos](assets/settings-select-saas.png)
   _Configuración_

1. Seleccione el espacio de datos SaaS que tenga los datos de comprador que desee utilizar.

1. Haga clic en **Guardar cambios**.

   Adobe Commerce ahora obtiene recomendaciones del espacio de datos seleccionado.

   >[!NOTE]
   >
   > Aunque puede ver las recomendaciones recuperadas de otro espacio de datos de SaaS en la tienda que no sea de producción, no puede hacer clic en las recomendaciones.

### Configuración de un nuevo espacio de datos SaaS

1. En la sección Origen de Recommendations, haga clic en **Editar configuración**.

1. Siga las instrucciones para configurar un nuevo [[!DNL Commerce] servicio](/help/landing/saas.md).

## Habilitar recomendaciones visuales

Si el módulo [Visual Product Recommendations](install-configure.md) está instalado, debe habilitar Visual Recommendations para que utilice el tipo de recomendación [Similitud visual](type.md#visualsim).

En la sección _Visual Recommendations_, establezca **Habilitar Visual Recommendations** en la posición activa.
