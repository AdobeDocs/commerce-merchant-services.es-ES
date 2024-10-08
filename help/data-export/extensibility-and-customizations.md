---
title: Ampliación y personalización de los datos de exportación de fuentes de SaaS
description: Obtenga información sobre cómo ampliar y personalizar los datos de la fuente  [!DNL SaaS Data Export] .
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Ampliación y personalización de los datos de exportación de fuentes de SaaS

La extensión [!DNL Commerce Data Export] proporciona una forma de exportar datos desde la aplicación [!DNL Commerce] a servicios de Commerce como Live Search, Servicio de catálogo y Recommendations de productos. Si es necesario, puede ampliar y personalizar los datos de fuente para incluir datos adicionales o modificar los datos recopilados actualizando el módulo `Magento\CatalogDataExporter`.

>[!NOTE]
>
>Añadir nuevos datos a la fuente o modificar los datos existentes puede afectar al rendimiento de la recopilación de fuentes y causar problemas en la lógica de procesamiento en el lado de Adobe Commerce. Asegúrese de probar el código personalizado antes de combinarlo con un entorno de producción.

## Ampliar datos de atributos en la fuente de productos

La fuente Products incluye atributos predeterminados necesarios para el procesamiento del producto o que suelen utilizar los consumidores. Puede incluir atributos del sistema adicionales en la fuente de productos añadiéndolos a la fuente.

Para completar esta tarea, actualice el módulo `magento/catalog-data-exporter` para agregar los atributos de sistema adicionales al [archivo de configuración de inyección de dependencia](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`). Agregue los atributos a la consulta de atributos del producto (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

**Ejemplo**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
