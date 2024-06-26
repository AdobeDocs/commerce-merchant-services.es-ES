---
title: "Configuración"
description: "Configure las opciones de [!DNL Live Search] servicio."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: ba7e92d5b3aaabe6a8c71f86b0e4eab38aec9adf
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Configuración

Utilice el *Configuración* workspace para configurar los intervalos y rangos de facetas de precios y el idioma predeterminado para el índice.

Facetado de precios especifica el número de grupos de intervalos de precios y cómo se distribuyen los valores de precios entre ellos.

La configuración Idioma indica a [!DNL Live Search] indica qué idioma esperar al escribir el índice.

![Configuración](assets/settings.png)

## Facetado de precios

Puede especificar el número de grupos de intervalos de precios y cómo se distribuyen los valores de precios entre ellos. Cada rango de precios se superpone con el grupo anterior por uno. Por ejemplo, cinco grupos con un intervalo de 20 crean los siguientes intervalos de precios: 0-20, 20-40, 40-60, 60-80 y >80. Si no hay suficientes productos en el catálogo para rellenar todos los intervalos definidos, la visualización de los grupos disponibles se ajusta en consecuencia. Por ejemplo: 0-20, 60-80, >80.

1. En el Administrador, vaya a **Marketing** > *SEO y búsqueda* > **[!DNL Live Search]**.
1. En el **Configuración** workspace en *Facetado de precios*, haga lo siguiente:
   * Introduzca el **Número de selecciones** o que haya agrupaciones de precios disponibles. Se pueden definir hasta 50 agrupaciones de precios.
   * Introduzca el **Valor de intervalo**, o rango de precios para cada grupo. El valor máximo es 10 000.
1. Clic **Guardar**.

   La configuración actualizada tarda unos 15 minutos en estar disponible en la tienda.

### Descripciones de campos

| Campo | Descripción |
|--- |--- |
| Número de selecciones | Especifica el número de agrupaciones de intervalos de precios que se pueden usar como filtros de búsqueda en la tienda. Valor predeterminado: 8, Valor máximo: 50 |
| Valor de intervalo | Especifica el intervalo de rango de precios para cada grupo. Por ejemplo, cinco selecciones con un valor de intervalo de 20 crean cinco agrupaciones de 0-20, 20-40, 40-60, 60-80 y >80. Valor predeterminado: 5, Valor máximo: 10 000 |

## Idioma

La configuración de idioma indica [!DNL Live Search] qué idioma esperar al leer el catálogo y escribir el índice.

Los idiomas tienen diferentes conjuntos de reglas gramaticales: cómo se separan las palabras, tiempos verbales y formas de palabras, por ejemplo.
La configuración Idioma garantiza que se aplique el conjunto correcto de reglas al mecanismo de indexación.

Establezca la configuración Idioma en el idioma principal del catálogo. Al cambiar el idioma del índice, puede tardar entre 5 y 60 minutos en reflejar el cambio en la tienda, según el tamaño y la complejidad del catálogo.

| Idioma | Código |
|----|----|
| Árabe | ar |
| Armenio | hy |
| Vasco | eu |
| Bengalí | bn |
| brasileño | pt-br |
| Búlgaro | bg |
| Catalán | ca |
| Chino (simplificado) | zh-cn |
| Chino (tradicional) | zh-tw |
| Checo | cs |
| Danés | da |
| Neerlandés | nl |
| Inglés | en |
| Estonio | et |
| Finés | fi |
| francés | fr |
| Gallego | gl |
| Alemán | de |
| Griego | el |
| Hindi | hola |
| Húngaro | hu |
| Indonesio | id |
| Irlandés | ga |
| Italiano | it |
| Japonés (Katakana) | ja |
| Coreano | ko |
| Letón | lv |
| Lituano | lt |
| Noruego | no |
| persa | fa |
| Portugués | pt |
| Rumano | ro |
| Ruso | ru |
| Sorani | ku |
| Español | es |
| Sueco | sv |
| Turco | tr |
| Tailandés | th |
