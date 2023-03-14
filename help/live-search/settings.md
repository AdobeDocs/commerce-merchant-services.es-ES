---
title: "[!DNL Live Search] Configuración"
description: '"Configurar intervalos y rangos de facetas de precios para [!DNL Live Search] facetas".'
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Configuración

Utilice el *Configuración* para configurar los intervalos y rangos de facetas de precio que están disponibles como filtros de búsqueda en la tienda. La configuración de la faceta de precio es estática en lugar de dinámica y no se basa en los resultados de búsqueda.

Puede especificar el número de grupos de intervalos de precios y cómo se distribuyen los valores de precios entre ellos. Cada rango de precios se superpone con el grupo anterior por uno. Por ejemplo, cinco grupos con un intervalo de veinte crean los siguientes intervalos de precios: 0-20, 20-40, 40-60, 60-80 y >80. Si no hay suficientes productos en el catálogo para rellenar todos los intervalos definidos, la visualización de los grupos disponibles se ajusta en consecuencia. Por ejemplo: 0-20, 60-80, >80.

![Configuración](assets/settings.png)

## Configurar agrupaciones de facetas de precios

1. En el Administrador, vaya a **Marketing** > *SEO y búsqueda* > **[!DNL Live Search]**.
1. En el **Configuración** pestaña debajo de *Facetado de precios*, haga lo siguiente:
   * Introduzca el **Número de selecciones** o que haya agrupaciones de precios disponibles. Se pueden definir hasta 50 agrupaciones de precios.
   * Introduzca el **Valor de intervalo**, o rango de precios para cada grupo. El valor máximo es 10 000.
1. Clic **Guardar**.

   La configuración actualizada tarda unos 15 minutos en estar disponible en la tienda.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Número de selecciones | Especifica el número de agrupaciones de intervalos de precios que se pueden usar como filtros de búsqueda en la tienda. Valor predeterminado: 8, Valor máximo: 50 |
| Valor de intervalo | Especifica el intervalo de rango de precios para cada grupo. Por ejemplo, cinco selecciones con un valor de intervalo de veinte crean cinco agrupaciones de 0-20, 20-40, 40-60, 60-80 y >80. Valor predeterminado: 5, Valor máximo: 10 000 |
