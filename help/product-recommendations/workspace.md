---
title: '[!DNL Product Recommendations] Workspace'
description: Obtenga información sobre cómo configurar, administrar y supervisar el rendimiento de recomendaciones de productos.
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 25d5321b6f29bab5d8cf329170f3644f35100438
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

El [!DNL Product Recommendations] workspace muestra una lista de las recomendaciones configuradas anteriormente con métricas que le ayudan a realizar un seguimiento del éxito de cada recomendación. La lista se puede configurar para calcular las métricas del último día, semana o mes. Puede utilizar las métricas para crear perspectivas procesables en función de la frecuencia con la que se ve o se hace clic en una unidad de recomendación, o para analizar el rendimiento de sus recomendaciones.

![Recommendations Workspace](assets/workspace.png)
_Recommendations Workspace_

## Establecer el ámbito

Inicialmente, la variable [ámbito](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) de todas las configuraciones de recomendaciones se establece en `Default Store View`. Si la instalación de Commerce incluye varias vistas de tiendas, establezca **Ámbito** a la [vista de tienda](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) donde se aplican las recomendaciones.

## Definir intervalo de fechas de métricas

1. Haga clic en **Calendario** ![Selector de calendario](assets/icon-calendar.png) control.

1. Elija una de las siguientes opciones:

   - Últimas 24 horas
   - Últimos 7 días
   - Últimos 30 días

   Los valores calculados en las columnas de métricas cambian para reflejar el intervalo de fechas actual.

## Mostrar u ocultar columnas

1. En la esquina superior izquierda, haga clic en **Mostrar/ocultar** ![Selector de columna](assets/icon-show-hide-columns.png) columnas.

   Las columnas visibles tienen una marca de verificación azul.

1. En el menú, realice una de las acciones siguientes:

   - Para mostrar una columna oculta, haga clic en cualquier nombre de columna sin marca de verificación.
   - Para ocultar una columna visible, haga clic en cualquier nombre de columna con una marca de verificación.

   La tabla se actualiza para incluir solo las columnas seleccionadas.

   ![Recommendations Workspace](assets/workspace-select-columns.png)
   _Mostrar u ocultar columnas_

## Configuración

La configuración determina el espacio de datos SaaS que proporciona los datos de comportamiento de recomendación.

- Para cambiar la ubicación en la que se originan los datos de comportamiento de recomendación, elija un espacio de datos de SaaS diferente.

- Para configurar un nuevo espacio de datos SaaS, haga clic en **Editar configuración**. Para obtener más información, consulte [Configuración](settings.md).

![Configuración de Recommendations](assets/settings.png)
_Configuración de Recommendations_

## Ver detalles

1. En la tabla, haga clic en la recomendación que desee examinar.

   ![Recommendations Workspace](assets/recommendation-detail.png)
   _Detalle de tasa de conversión de página de inicio_

1. Para cambiar el estado de la recomendación, haga clic en **Activar** o **Desactivar**.

## Editar recomendación

En la página de detalles de la recomendación, haga clic en **Editar**. Para obtener más información, vaya a [Editar Recommendations](edit.md).

## Crear recomendación

En la página de detalles de la recomendación, haga clic en **Crear**. Para obtener más información, vaya a [Crear Recommendations](create.md).

## Controles de Workspace

| Control | Descripción |
|---|---|
| ![Selector de calendario](assets/icon-calendar.png) | Determina el intervalo de tiempo que se utiliza para los cálculos de métricas. Opciones: 24 horas / 7 días / 30 días |
| ![Selector de columna](assets/icon-show-hide-columns.png) | Determina las columnas que aparecen en [!DNL Product Recommendations] tabla. |
| Configuración | Determina el espacio de datos SaaS donde se recuperan los datos de comportamiento de recomendación y también habilita el tipo de recomendación de similitud visual. |
| Crear recomendación | Abre el [Crear nueva recomendación](create.md) página. |

## Descripciones de columna

| Columna | Descripción |
|---|---|
| Nombre | El nombre de la recomendación. |
| Página | Página en la que aparece la recomendación. |
| Tipo | El tipo de recomendación. |
| Estado | El estado de la recomendación. Opciones: Inactivo/Activo/Borrador |
| Creado | La fecha en la que se creó la recomendación. |
| Última edición | Fecha en la que se editó la recomendación por última vez. |
| Impresiones | El número de veces que se carga y procesa una unidad de recomendación en una página. En la página se representa una unidad de recomendación que está por debajo del pliegue de la ventanilla del explorador, pero el comprador no la ve. En este caso, la unidad procesada se cuenta como una impresión, pero una vista solo se cuenta si el usuario desplaza la unidad a la vista. |
| vImpresiones | (Impresiones visibles) El número de unidades de recomendación que registran al menos una vista. |
| Vistas | El número de unidades de recomendación que aparecen en la ventanilla móvil del explorador del comprador. Este evento se puede activar varias veces en una página. |
| Clics | La suma del número de veces que un comprador hace clic en un elemento de la unidad de recomendación y el número de veces que el comprador hace clic en el elemento **Añadir al carro de compras** botón en la unidad de recomendación |
| Ingresos | Ingresos impulsados por la recomendación para el intervalo de tiempo actual. |
| Ingresos Lt | (Ingresos de por vida) Ingresos de por vida impulsados por una recomendación. |
| Visibilidad | Porcentaje de unidades de recomendación que se registran para la vista. |
| Ctr | (Tasa de pulsaciones) El porcentaje de impresiones unitarias de la recomendación que registra un clic. |
| vCtr | (Tasa de clics visibles) El porcentaje de impresiones visibles para la unidad de recomendación que registra un clic. |
