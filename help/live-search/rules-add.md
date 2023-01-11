---
title: "Agregar reglas"
description: '"Aprenda a crear [!DNL Live Search] reglas".'
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Agregar reglas

Para generar una regla, el primer paso es utilizar el editor de reglas para definir las condiciones en el texto de consulta del comprador que déclencheur los eventos asociados. A continuación, complete los detalles de la regla, pruebe los resultados y publique la regla.

## Paso 1: Agregar una regla

1. En el Administrador, vaya a **Marketing** > SEO y Búsqueda > **Live Search**.
1. Configure las variables **Ámbito** para identificar el [vista de tienda](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) donde se aplica la regla.
1. Haga clic en el **Reglas** pestaña .
1. Haga clic en **Agregar regla** para iniciar el editor de reglas.

   ![Espacio de trabajo de reglas](assets/rules-workspace-add-rule.png)

## Paso 2: Describir las condiciones

Las condiciones son los requisitos para almacenar en déclencheur un evento. Una regla puede tener hasta diez condiciones y 25 eventos.

![Regla: genere su regla](assets/rules-add-workspace.png)

### Condición única

1. En *Crear una regla*, seleccione **Condición** para cumplir, y siga las instrucciones para completar la declaración.

   * La consulta de búsqueda contiene : introduzca la cadena de texto que debe estar en la consulta del comprador. La configuración Coincidencia determina el grado en que la consulta del comprador coincide con el catálogo. Opciones:<br /> Cualquiera : cualquier parte del texto de consulta del comprador puede coincidir con la condición.<br />Todo : todas las consultas del comprador deben coincidir con la condición.
   * La consulta de búsqueda es : introduzca una cadena de texto que coincida exactamente con la consulta del comprador. Por ejemplo: &quot;pantalones de yoga&quot;. Reglas con `Search query is` y Coincidir `All` solo puede tener una condición.
   * La consulta de búsqueda comienza por : introduzca un carácter o una cadena de texto que debe estar al principio de la consulta del comprador.
   * La consulta de búsqueda termina con : introduzca un carácter o una cadena de texto que debe estar al final de la consulta del comprador.

   Los resultados aparecen inmediatamente en la variable *Probar la regla* y se numeran por prioridad. Puede usar la variable *Resultados por fila* en la parte superior derecha para cambiar el número de productos en cada fila.

   ![Regla: simple](assets/rule-simple-test.png)

1. Para probar otras consultas, cambie el texto de la consulta en la *Probar la regla* cuadro de búsqueda y pulse **Devuelve**.
Inicialmente, el panel de prueba procesa la consulta desde el cuadro de búsqueda Condiciones . Pero ahora está procesando la consulta desde el cuadro de consulta de prueba. El panel de prueba solo procesa una consulta a la vez.

   ![Regla: actualizar prueba](assets/rule-update-test.png)

1. Si le gusta el resultado, actualice el texto en la *Condiciones* cuadro de búsqueda. A continuación, haga clic en cualquier lugar de la página para actualizar los resultados en el panel de prueba.
1. Para crear una regla sencilla con una condición, vaya al paso 3: [Añadir eventos](#events).

### Varias condiciones

1. Para generar una regla con varias condiciones, haga clic en **Añadir condición**.
Una regla puede tener hasta diez condiciones. El operador lógico que une dos condiciones se basa en la *Coincidencia* configuración. De forma predeterminada, *Coincidencia* es `All` y el operador lógico es `AND`.

   ![Reglas - La consulta de búsqueda contiene](assets/rules-search-query-contains-and.png)

1. Seleccione la segunda condición e introduzca el texto de consulta requerido.

   ![Condiciones de regla](assets/rules-add-condition.png)

1. Para cambiar la lógica de la regla, cambie la variable **Coincidencia** para determinar la proximidad de los criterios de búsqueda del comprador a la condición de consulta. Establezca **Coincidencia** a uno de los siguientes:

   * Cualquiera - (predeterminado) Todos los operadores lógicos de la regla están definidos como `OR` y los resultados aparecen en el panel de prueba.
   * Todo : todos los operadores lógicos de la regla se establecen en `AND` y los resultados aparecen en el panel de prueba.

   La variable *Coincidencia* determina el operador lógico que se utiliza para unir varias condiciones. Cambio de la variable *Coincidencia* cambia todos los operadores lógicos de la regla. No es posible combinar `AND` y `OR` en la misma regla.

   En este ejemplo, en lugar de buscar &quot;pantalones de yoga&quot;, hay dos consultas separadas que buscan &quot;yoga&quot; o &quot;pantalones&quot;. Esta regla es menos específica y se activa con mayor frecuencia en la tienda que en la otra.

   ![Reglas - Coincidencia](assets/rules-match.png)

1. Para añadir otra condición, haga clic en **Añadir condición** y repita el proceso.

## Paso 3: Añadir eventos

los eventos son acciones que cambian los resultados de la búsqueda cuando se cumplen las condiciones. Una sola regla puede tener hasta 25 eventos.

1. En *Eventos*, elija el **Evento** cuando se cumplan las condiciones asociadas.

   Por ejemplo, elija `Pin a product`. A continuación, introduzca el nombre del producto que desea fijar. Si necesita ayuda, puede encontrar el nombre en el panel de prueba.
A continuación, introduzca la variable *Posición* donde aparecerá el producto anclado. El producto se mueve a la nueva posición del panel de prueba y se marca con una *Anclado* distintivo de vista previa.

   ![Reglas - Coincidencia](assets/rule-event-pin-product.png)

1. Para varios eventos, elija cualquier otro que desee almacenar en déclencheur cuando se cumplan las condiciones.

   * Ampliación : seleccione Ampliar. A continuación, introduzca el nombre o SKU del producto que desea mover más arriba en los resultados de búsqueda. En el panel de prueba, cada producto potenciado tiene un *Ampliado* distintivo de vista previa.
   * Bury : mueve un SKU más bajo en los resultados de búsqueda. Cada SKU está marcado con un *Enterrado* distintivo de vista previa en el panel de prueba.
   * Incrustar un producto: introduzca el nombre o SKU del producto. A continuación, seleccione la opción Posición en los resultados de búsqueda donde debe aparecer el producto. El producto está marcado con un *Anclado* distintivo de vista previa en el panel de prueba.
   * Ocultar un producto: excluye un SKU de los resultados de búsqueda.

## Paso 4: Complete los detalles

La información que se introduce aquí aparece en la [Detalles de regla](rules-workspace.md) panel.

1. En *Detalles*, introduzca un **Nombre** para la regla. Todos los nombres de reglas deben ser únicos.
1. Escriba un breve **Descripción** de la regla.
1. Introduzca la variable **Fecha de inicio** y **Fecha final** para que la regla esté activa o elija las fechas del calendario.

   Para seleccionar un intervalo de fechas, haga clic en la primera fecha y arrastre para seleccionarlo.

   ![Regla - Completada](assets/rule-add-details.png)

## Paso 5: Probar la regla

1. Examine los resultados de la regla en el panel de prueba.
1. Si la regla tiene varias consultas, pruebe cada una de ellas que pueda verse afectada por la regla.

## Paso 6: Guardar y publicar

1. Cuando termine, haga clic en **Guardar y publicar**.

   La regla se agrega a la lista en el espacio de trabajo de reglas.

1. Aunque las reglas activas entren en vigor inmediatamente, es posible que tenga que esperar hasta 15 minutos para que los resultados de la consulta en caché en la tienda se actualicen.

## Descripciones de campos

### Condiciones (if)

| Condición | Descripción |
|--- |--- |
| La consulta de búsqueda contiene | Carácter o cadena de texto que se incluye en la consulta del comprador. La consulta del comprador debe coincidir con un solo carácter para cumplir esta condición. |
| La consulta de búsqueda es | Carácter o cadena de texto que coincida exactamente con la consulta del comprador. Las consultas complejas con varias condiciones no se pueden componer cuando se utiliza esta condición. |
| La consulta de búsqueda comienza con | La consulta del comprador comienza con este carácter o cadena de texto. |
| La consulta de búsqueda finaliza con | La consulta del comprador termina con este carácter o cadena de texto. |

### Operadores lógicos

| Operador | Descripción |
|--- |--- |
| O | (Predeterminado) El operador lógico `OR` compara dos condiciones y cumple los requisitos para almacenar en déclencheur un evento si al menos una condición es verdadera. |
| Y | El operador lógico `AND` compara dos condiciones y cumple los requisitos para almacenar en déclencheur un evento si ambas condiciones son verdaderas. |

### Coincidir con operadores

| Operador | Descripción |
|--- |--- |
| Cualquiera | Cambia todos los operadores lógicos de la regla a `OR` y devuelve el conjunto de productos coincidentes. |
| Todo | Cambia todos los operadores lógicos de la regla a `AND` y devuelve el conjunto de productos coincidentes. |

### Eventos

| Evento | Descripción |
|--- |--- |
| Aumento | Mueve un SKU o un rango de SKU más alto en los resultados de búsqueda. Cada uno de ellos está marcado con un distintivo de vista previa &quot;potenciado&quot; en los resultados de búsqueda de prueba. |
| Bury | Mueve un SKU o rango de SKU más abajo en los resultados de búsqueda. Cada uno de ellos está marcado con un distintivo de vista previa &quot;enterrado&quot; en los resultados de búsqueda de prueba. |
| Incrustar un producto | Adjunta un único SKU a una posición específica en los resultados de búsqueda. El producto se marca con un distintivo de vista previa &quot;anclado&quot; en los resultados de búsqueda de prueba. |
| Ocultar un producto | Excluye un SKU o rango de SKU de los resultados de búsqueda. |

### Detalles

| Campo | Descripción |
|--- |--- |
| Nombre | Nombre de la regla. Los nombres de las reglas deben ser únicos. |
| Fecha de inicio | La fecha de inicio de la regla, si está programada. |
| Fecha final | La fecha de finalización de la regla, si está programada. |
| Descripción | Una breve descripción de la regla. |
