---
title: Agregar sinónimos
description: Agregue sinónimos de búsqueda activa para mejorar la respuesta a las solicitudes de búsqueda.
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Agregar sinónimos

Añada su propia lista depurada de [!DNL Live Search] sinónimos para mejorar la respuesta a las solicitudes de búsqueda y mantener a los clientes comprometidos.

![[!DNL Live Search] sinónimos](assets/synonym-workspace.png)

## Paso 1: Agregar un sinónimo

1. En el Administrador, vaya a **Marketing** > SEO y Búsqueda > **[!DNL Live Search]**.
1. Para varias tiendas, establezca **Ámbito** a [vista de tienda](https://docs.magento.com/user-guide/configuration/scope.html) donde se aplica la configuración de sinónimo.
1. Haga clic en el **Sinónimos** pestaña .
1. Haga clic en el **Añadir sinónimos** botón.

## Paso 2: Defina el sinónimo por tipo

Siga las instrucciones para la [tipo de sinónimo](synonyms-type.md) que desea crear.

### Sinónimo bidireccional

1. Aceptar el valor predeterminado **bidireccional** .

   ![Agregar sinónimo bidireccional](assets/synonym-add-two-way.png)


1. Introduzca la variable **Palabra clave** término o frase a comparar.
1. Introduzca la variable **Expansión** término(s) que desea agregar como sinónimos para la palabra clave. Separe varios términos con una coma.
En este ejemplo, la palabra clave que debe coincidir es &quot;pantalones&quot; y el conjunto de términos de expansión es &quot;pantalones largos, pantalones, pantalones cortos&quot;.

   ![Ejemplo de sinónimo bidireccional](assets/synonym-add-two-way-example.png)

1. Cuando termine, haga clic en **Guardar**.
El conjunto de sinónimos aparece en la lista con una flecha bidireccional entre cada término que significa que los términos son intercambiables.

   ![Sinónimo bidireccional](assets/synonym-two-way.png)

### Sinónimo unidireccional

1. Haga clic en el **Unidireccional** tipo sinónimo.

   ![Agregar sinónimo unidireccional](assets/synonym-add-one-way.png)

1. Introduzca la variable **Palabra clave** y **Expansión** término(s). Separe varios términos con una coma.

   ![Ejemplo de sinónimo unidireccional](assets/synonym-add-one-way-example.png)

   En este ejemplo, la palabra clave es &quot;pantalones&quot; y los términos de expansión unidireccional &quot;capris, pantalones de longitud de ternera, empujadores de pedales&quot; son cada uno un subconjunto de &quot;pantalones&quot;, pero con un significado específico.

1. Cuando termine, haga clic en **Guardar**.
El conjunto de sinónimos aparece en la lista con una flecha unidireccional que señala desde los términos de expansión a la palabra clave para indicar que los términos son subconjuntos de la palabra clave. Un signo más separa cada término de expansión.

   ![Sinónimo unidireccional](assets/synonym-one-way.png)

## Paso 3: Publicar cambios

1. Cuando se hayan completado los sinónimos, haga clic en **Publicar cambios**.
1. Espere hasta dos horas para que las actualizaciones estén disponibles en la tienda.

![Publicar cambios](assets/synonym-publish.png)

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| [Tipo](synonyms.md) | Determina si los sinónimos tienen el mismo significado que la palabra clave o si son un subconjunto de la palabra clave. Opciones:<br />Dos direcciones (predeterminado): términos que tienen el mismo significado que la palabra clave y devuelven los mismos resultados de búsqueda<br />De una manera: términos que son un subconjunto de la palabra clave. Los sinónimos unidireccionales devuelven una lista más limitada de productos específicos. |
| Palabra clave | Palabra que suele estar asociada a una selección de productos del catálogo. |
| Expansión | Términos adicionales que tienen el mismo significado o similar que la palabra clave. |
