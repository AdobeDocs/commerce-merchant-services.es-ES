---
title: "[!DNL SaaS Data Export Guide]"
description: '"Obtenga información acerca del uso de [!DNL data export] extensión para servicios SaaS de Adobe Commerce que sincroniza datos entre Adobe Commerce y los servicios de Commerce conectados".'
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Guía de [!DNL SaaS Data Export]

[!DNL SaaS data export] mejora el rendimiento del front-end al optimizar la sincronización de datos entre una instancia de Adobe Commerce y los servicios de Commerce conectados. Al agregar Live Search, Product Recommendations o el servicio de catálogo a una instalación de Adobe Commerce, la variable [!DNL Data export] La extensión de se instala automáticamente.

La exportación de datos de SaaS recopila y exporta varios tipos de datos, denominados _fuentes_, que agregan tipos específicos de información. Según los servicios de Commerce que estén instalados, las fuentes de exportación de datos SaaS incluyen:

- **Fuentes de entidades de catálogo** datos de producto agregados. Los datos incluyen productos, atributos de productos, precios de productos, variaciones de productos, categorías, permisos de categorías y permisos de productos.
- El **Fuente de ámbitos** agrega datos para grupos de clientes, sitios web, tiendas y vistas de tiendas.
- El **Fuente de pedidos de ventas** agrega datos de pedidos, incluidas sus entidades relacionadas, como facturas, envíos, notas de abono, etc.
- El **Fuente de inventario de varias fuentes** agrega datos sobre los artículos de estado de stock de inventario.

La extensión de exportación de datos admite varios métodos para iniciar y administrar el proceso de sincronización de datos.

- **Sincronización manual desde Admin o la línea de comandos**

   - El [Panel de administración de datos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) en el Administrador de Commerce proporciona una vista gráfica del estado de sincronización. Puede utilizar el tablero para realizar una resincronización completa (_sincronización completa_) de todas las fuentes. Sin embargo, Adobe solo recomienda realizar una sincronización completa la primera vez que conecte Adobe Commerce a un servicio de Commerce. Consulte [Proceso de sincronización](data-synchronization.md).

   - El [Herramienta de línea de comandos de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) proporciona comandos para sincronizar fuentes específicas e incluye opciones adicionales para personalizar el procesamiento de fuentes.

- **Sincronización automatizada con trabajos cron**

   - [Sincronización parcial de datos](data-synchronization.md#partial-synchronization-with-cron-jobs): los trabajos de Cron almacenan en déclencheur una sincronización de datos parcial cuando un usuario administrador de Commerce actualiza una entidad. El proceso de exportación de datos envía solamente estas actualizaciones a los servicios de Commerce conectados. El proceso de sincronización parcial se basa en el mecanismo MView y no requiere acciones por parte del usuario administrador o del integrador de sistemas.

   - [Reintento automático de errores de sincronización](data-synchronization.md#failed-items-sync-for-error-recovery): los trabajos Cron déclencheur el reintento automático del proceso de sincronización cuando se producen errores durante el proceso de sincronización de datos.

- **Exportar programación y rendimiento**

   - Los desarrolladores e integradores de sistemas pueden calcular el tiempo necesario para que la exportación de datos SaaS sincronice los datos entre Adobe Commerce y los servicios conectados. Esta estimación puede ayudar a programar el procesamiento de exportación de datos para evitar interrupciones en el sitio. Consulte [Estimar el volumen de datos y el tiempo de transmisión](estimate-data-volume-sync-time.md).

   - En los casos en los que la sincronización debe realizarse más rápidamente, la exportación de datos SaaS proporciona opciones de personalización para mejorar el rendimiento del procesamiento de exportación. Consulte [Mejora del rendimiento de exportación de datos](customize-export-processing.md).

- **Seguimiento y solución de problemas de actividades de exportación de datos**: utilice los registros de exportación de datos y exportación de saas para revisar el estado de sincronización y las cargas útiles de alimentación durante el proceso de sincronización e indexación. Consulte [Registro y solución de problemas](troubleshooting-logging.md).



