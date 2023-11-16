---
title: Creación de eventos personalizados
description: Aprenda a crear eventos personalizados para conectar los datos de Adobe Commerce a otros productos DX de Adobe.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Creación de eventos personalizados

Puede ampliar el [plataforma de eventos](events.md) creando sus propios eventos de tienda para recopilar datos exclusivos de su sector. Al crear y configurar un evento personalizado, se envía a la variable [Recopilador de eventos de Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## Gestión de eventos personalizados

Los eventos personalizados solo son compatibles con Adobe Experience Platform. Los datos personalizados no se reenvían a los paneles de Adobe Commerce ni a los rastreadores de métricas.

Para cualquier `custom` evento, el recolector:

- Agrega `identityMap` con `ECID` como identidad principal
- Incluye `email` in `identityMap` como identidad secundaria _if_ `personalEmail.address` se establece en el evento
- Envuelve el evento completo dentro de un `xdm` antes de reenviar a Edge

Ejemplo:

Evento personalizado publicado mediante el SDK de eventos de Adobe Commerce:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

En Experience Platform Edge:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> El uso de eventos personalizados puede afectar a los informes predeterminados de Adobe Analytics.

## Controlar anulaciones de eventos (atributos personalizados)

Las anulaciones de atributos para eventos estándar solo se admiten para el Experience Platform. Los datos personalizados no se reenvían a los paneles y rastreadores de métricas de Commerce.

Para cualquier evento con `customContext`, el selector anula los campos de unión establecidos en los contextos relevantes con campos en `customContext`. El caso de uso de las invalidaciones es cuando un desarrollador desea reutilizar y ampliar contextos establecidos por otras partes de la página en eventos ya admitidos.

>[!NOTE]
>
>Al anular los eventos personalizados, el reenvío de eventos al Experience Platform debe desactivarse para ese tipo de evento para evitar el recuento doble.

Ejemplos:

Vista de producto con invalidaciones publicadas mediante el SDK de eventos de Adobe Commerce:

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

En Experience Platform Edge:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Anular los eventos con atributos personalizados puede afectar a los informes predeterminados de Adobe Analytics.
