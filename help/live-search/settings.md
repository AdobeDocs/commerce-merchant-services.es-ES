---
title: Configuración de búsqueda en directo
description: Configure intervalos y rangos de facetas de precios para facetas de búsqueda activa.
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Configuración

Utilice la variable *Configuración* para configurar los intervalos y los intervalos de facetas de precio que están disponibles como filtros de búsqueda en la tienda. La configuración de facetas de precios es estática en lugar de dinámica y no se basa en los resultados de búsqueda.
Puede especificar el número de grupos de intervalos de precios y cómo se distribuyen entre ellos los valores de precios. Cada rango de precios se superpone en uno al grupo anterior. Por ejemplo, cinco grupos con un intervalo de veinte crean los siguientes intervalos de precios: 0-20, 20-40, 40-60, 60-80 y >80. Si no hay suficientes productos en el catálogo para rellenar todos los intervalos definidos, la visualización de los grupos disponibles se ajusta en consecuencia. Por ejemplo: 0-20, 60-80, >80.

![Configuración](assets/settings.png)

## Configurar agrupaciones de facetas de precio

1. En el Administrador, vaya a **Marketing** > *SEO y búsqueda* > **Live Search**.
1. En el **Configuración** ficha *Facetas de precios*, haga lo siguiente:
   * Introduzca la variable **Número de selecciones**, o agrupaciones de precios que estarán disponibles. Se pueden definir hasta 50 agrupaciones de precios.
   * Introduzca la variable **Valor de intervalo** o rango de precios para cada grupo. El valor máximo es 10 000.
1. Haga clic en **Guardar**.
La configuración actualizada tarda unos quince minutos en estar disponible en la tienda.

## Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Número de selecciones | Especifica el número de agrupaciones de rango de precios que se pueden usar como filtros de búsqueda en la tienda. Valor predeterminado: 8, Valor máximo: 50 |
| Valor de intervalo | Especifica el intervalo de intervalo de precios para cada grupo. Por ejemplo, cinco selecciones con un valor de intervalo de veinte crea cinco agrupaciones de 0 a 20, 20 a 40, 40 a 60, 60 a 80 y >80. Valor predeterminado: 5, Valor máximo: 10 000 |
