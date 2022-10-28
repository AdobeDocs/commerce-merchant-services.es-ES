---
title: Gestión de restricciones de cookies
description: Descubra cómo las recomendaciones de productos administran las restricciones de cookies.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Gestión de restricciones de cookies

Tanto Adobe Commerce como el Magento Open Source piden el consentimiento antes de que los datos se almacenen en las cookies del explorador. Para obtener más información, consulte [Modo de restricción de cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

Al implementar la variable `magento/product-recommendations` para la producción, comienza a recopilar eventos de interacción del comprador en su tienda. Dado que los datos de estos eventos se pueden almacenar en cookies del explorador o en almacenamiento local, la función admite el modo de restricción de cookies al no recopilar eventos hasta que el comprador haya dado su consentimiento a la cookie.

Es posible que esto no funcione con soluciones de consentimiento de cookies de terceros. Cada comerciante tiene la responsabilidad de garantizar que la recopilación de datos no se produzca antes de que se haya dado el consentimiento de las cookies, como suele exigir la ley. Si administra el consentimiento de las cookies con código personalizado, puede utilizar una cookie que no rastrea llamada `mg_dnt` para restringir la recopilación de datos.

- Nombre de la cookie:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- Establezca la cookie no rastrear para deshabilitar la recopilación de datos:

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- Para borrar la cookie cuando el usuario ha aceptado las cookies:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
