---
title: Incorporación
description: Conozca los requisitos y las plataformas compatibles en [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Incorporación

El proceso de incorporación para [!DNL Product Recommendations] requiere acceso a la línea de comandos del servidor y consta de los siguientes pasos. Si no está familiarizado con el trabajo desde la línea de comandos, pida ayuda a un desarrollador o integrador de sistemas.

- [Flujo de trabajo de implementación](implementation-workflow.md)
- [Instalar y configurar](install-configure.md)
- [Configuración](settings.md)
- [Verificar](verify.md)
- [Entorno de ensayo](staging-environment.md)

## Requisitos

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4 / 8.1
- Compositor

### Plataformas compatibles

- Adobe Commerce local (EE) : 2.4.x
- Adobe Commerce on Cloud (ECE) : 2.4.x

### Compatibilidad con Page Builder

[!DNL Product Recommendations] se puede agregar a una página como tipo de contenido de Page Builder . Para añadir la compatibilidad de Page Builder a Product Recommendations, consulte [Instalar y configurar](install-configure.md).

Consulte [[!DNL Page Builder] Integración](page-builder.md) para obtener instrucciones sobre cómo agregar [!DNL Product Recommendations] into [!DNL Page Builder] contenido.

### Compatibilidad con B2B {#b2bsupport}

Las tiendas B2B suelen requerir lógica compleja que dicta la visibilidad y los precios del producto para cada comprador o grupo de clientes. [!DNL Product Recommendations] now [support](release-notes.md) esta funcionalidad respetándola [permisos de categoría](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [catálogos compartidos](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)y [precios específicos del grupo de clientes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Por ejemplo, si ha ocultado ciertas categorías del segmento de clientes minoristas, no se mostrarán recomendaciones para productos de esas categorías a un comprador de ese segmento. Además, cuando define un catálogo compartido para grupos de clientes y empresas específicos, dichos compradores ven las recomendaciones solo para los productos a los que pueden acceder. Todos los productos recomendados reflejan un precio correcto específico del grupo de clientes en función del grupo de clientes de cada comprador.
