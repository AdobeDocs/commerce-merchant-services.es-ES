---
title: "Configuración de configuraciones de Commerce y [!DNL Live Search] "
description: '"Describe las opciones de configuración de Adobe Commerce que [!DNL Live Search] puedo leer".'
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# [!DNL Live Search] Ajustes de configuración de Adobe Commerce y

Hay opciones de configuración de Commerce que [!DNL Live Search] admite. En este tema se enumeran estos valores de configuración.

## Valores de configuración admitidos

| Ajuste de configuración de Commerce | Compatible con Popover | Admitido por el adaptador |
|---|---|---|
| Tiendas -> Configuración -> Catálogo -> Catálogo -> Búsqueda en el catálogo -> Longitud mínima de la consulta | Sí | Sí |
| Tiendas -> Configuración -> Catálogo -> Inventario -> Mostrar productos sin existencias | Sí con versión 2.0.4 o posterior | Sí con versión 2.0.4 o posterior |
| Tiendas -> Configuración -> General -> Configuración de divisa -> Opciones de divisa -> Moneda base | Sí | Sí |

## Valores de configuración no admitidos

[!DNL Live Search] no se pueden leer todos los valores de configuración. Esta tabla enumera los valores que pueden ser de mayor interés para los desarrolladores.

| Configuración del Magento | Notas |
|---|---|
| Tiendas -> Configuración -> Catálogo -> Tienda -> Modo de lista | Se representa correctamente, pero los eventos no se envían para algunas interacciones de página |
| Tiendas -> Configuración -> Catálogo -> Tienda -> Permitir todos los productos por página | No implementado; envía una solicitud al servicio de búsqueda sin tamaño de página y [!DNL Live Search] devuelve un tamaño de página predeterminado de 20 |
| Tiendas -> Configuración -> Catálogo -> Catálogo -> Búsqueda en el catálogo -> Longitud máxima de la consulta | No implementado; los servicios de búsqueda aceptan hasta 255 caracteres |
| Tiendas -> Configuración -> General -> Configuración de divisa -> Opciones de divisa -> Moneda de visualización predeterminada | No implementado; [!DNL Live Search] solo tiene acceso a la moneda base |
| Configuración -> Ventas -> Impuestos -> Configuración De Visualización De Precios -> Mostrar Precios De Productos En El Catálogo |  |
