---
title: Creación de eventos personalizados
description: Aprenda a crear eventos personalizados para conectar los datos de Adobe Commerce a otros productos DX de Adobe.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Creación de eventos personalizados

Puede ampliar el [plataforma de eventos](events.md) creando sus propios eventos de tienda para recopilar datos exclusivos de su sector. Al crear y configurar un evento personalizado, se envía a la variable [Recopilador de eventos de Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## Gestión de eventos personalizados

Los eventos personalizados solo son compatibles con Adobe Experience Platform. Los datos personalizados no se reenvían a los paneles de Adobe Commerce ni a los rastreadores de métricas.

Para cualquier `custom` evento, el recopilador añade un `personId` (`ecid`) a `customContext` y envuelve un `xdm` objeto que lo rodea antes de reenviarlo a Edge.

Ejemplo:

Evento personalizado publicado mediante el SDK de eventos de Adobe Commerce:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

En Experience Platform Edge:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> El uso de eventos personalizados puede afectar a los informes predeterminados de Adobe Analytics.

## Controlar anulaciones de eventos (atributos personalizados)

Las anulaciones de atributos para eventos estándar solo se admiten para el Experience Platform. Los datos personalizados no se reenvían a los paneles y rastreadores de métricas de Commerce.

Para cualquier evento con un conjunto `customContext`, el recolector anula `personId` y Adobe Analytics, y reenvía todos los demás atributos establecidos en `customContext`.

Ejemplos:

Vista de producto con invalidaciones publicadas mediante el SDK de eventos de Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

En Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

La vista de producto con invalidaciones de Adobe Commerce publicadas mediante el SDK de eventos de Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

En Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Anular los eventos con atributos personalizados puede afectar a los informes predeterminados de Adobe Analytics.
