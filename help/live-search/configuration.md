---
title: '''Configuración y configuración de Commerce'' [!DNL Live Search] '''
description: Describe las opciones de configuración de Adobe Commerce que [!DNL Live Search] puede leer.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: 694a1c91425f246e497de50530d02f09a3093953
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# [!DNL Live Search] Ajustes de configuración de Adobe Commerce y

Hay opciones de configuración de Commerce que [!DNL Live Search] admite. En este tema se enumeran estos valores de configuración.

## Valores de configuración admitidos

| Ajuste de configuración de Commerce | Compatible con Popover | Admitido por el adaptador |
|---|---|---|
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Permitir todos los productos por longitud de página | Sí. Máx. 500 productos | Sí. Máx. 500 productos |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Longitud mínima de la consulta | Sí | Sí |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Productos por página en la cuadrícula Valores permitidos | Sí | Sí |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Productos por página en el valor predeterminado de la cuadrícula | Sí. Máx. 500 productos | Sí. Máx. 500 productos |
| Tiendas > Configuración > Catálogo > Inventario > Mostrar productos sin existencias | Sí con versión 2.0.4 o posterior | Sí con versión 2.0.4 o posterior |
| Tiendas > Configuración > Moneda > Moneda de visualización predeterminada | Sí con 3.1.0+ | Sí con 3.1.0+ |
| Tiendas > Configuración > General > Configuración de Divisa > Opciones de Divisa > Divisa Base | Sí | Sí |

Los precios de la página Widget de Lista de Productos y de la ventana emergente ahora se convierten a la moneda de visualización predeterminada con las tasas de cambio configuradas

## Valores de configuración no admitidos

[!DNL Live Search] no se pueden leer todos los valores de configuración. Esta tabla enumera los valores que pueden ser de mayor interés para los desarrolladores.

| Ajuste de configuración de Commerce | Notas |
|---|---|
| Tiendas > Configuración > Catálogo > Tienda > Modo de lista | Se representa correctamente, pero los eventos no se envían para algunas interacciones de página |
| Tiendas > Configuración > Catálogo > Buscar en el catálogo > Longitud máxima de la consulta | No implementado; los servicios de búsqueda aceptan hasta 255 caracteres |
| Configuración > Ventas > Impuestos > Configuración De Visualización De Precios > Mostrar Precios De Productos En El Catálogo |  |
