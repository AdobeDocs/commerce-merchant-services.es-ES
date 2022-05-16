---
title: '"Notas técnicas de la regla"'
description: '"Notas técnicas sobre el uso de [!DNL Live Search] reglas".'
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Notas técnicas de la regla

[!DNL Live Search] las reglas déclencheur acciones basadas en una variedad de condiciones de consulta y permiten a los comerciantes modelar la experiencia de búsqueda para distintos escenarios.

La versión actual de [!DNL Live Search] Las reglas se basan en la cadena de consulta introducida por el comprador, no en el conjunto de resultados devueltos. Una cadena de consulta puede incluir caracteres alfanuméricos y se ignora la mayúsculas. Al igual que con las facetas y los sinónimos, las reglas se almacenan en `protobuf dynamo`. En el momento de la consulta, el servicio de búsqueda recupera las reglas mediante `grpc` llamadas a `search-admin-service`.
