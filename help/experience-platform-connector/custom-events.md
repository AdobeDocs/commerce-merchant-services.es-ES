---
title: Crear eventos personalizados
description: Aprenda a crear eventos personalizados para conectar los datos de Adobe Commerce a otros productos DX de Adobe.
source-git-commit: 1dd8f94e632bb98666ad252badf8420a014260fb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Crear eventos personalizados

Puede ampliar el [plataforma de eventos](events.md) creando sus propios eventos de tienda para recopilar datos exclusivos de su industria. Cuando se crea y configura un evento personalizado, se envía a la variable [Recopilador de eventos de tienda de Magento](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Administrar eventos personalizados

Los eventos personalizados solo son compatibles con Adobe Experience Platform. Los datos personalizados no se reenvían a los paneles de Adobe Commerce ni a los rastreadores de métricas.

Para cualquier `custom` , el recolector agrega un `personId` (`ecid`) a `customContext` y ajusta un `xdm` antes de reenviar a Edge.

Ejemplo:

Evento personalizado publicado mediante el SDK de MSE:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

En el borde del Experience Platform:

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

## Gestión de anulaciones de eventos (atributos personalizados)

Las anulaciones de atributos para eventos estándar solo se admiten para el Experience Platform. Los datos personalizados no se reenvían a los paneles de comercio ni a los rastreadores de métricas.

Para cualquier evento con un conjunto `customContext`, el selector anula `personId` y los contadores de Adobe Analytics y reenvía todos los demás atributos definidos en `customContext`.

Ejemplos:

Vista de producto con anulaciones publicadas mediante el SDK de MSE:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

En el borde del Experience Platform:

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

Vista de producto con anulaciones de Adobe Commerce publicadas mediante el SDK de MSE:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

En el borde del Experience Platform:

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
> La anulación de eventos con atributos personalizados puede afectar a los informes predeterminados de Adobe Analytics.
