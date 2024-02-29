---
title: Registros de perfil
description: Descubra qué datos captura un registro de perfil.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# [!DNL Data Connection] Registros de perfil

A continuación se describen los datos de registro de perfil de Commerce que están disponibles al instalar el [!DNL Data Connection] extensión. Los datos de los registros de perfil se envían a Adobe Experience Platform.

## Registro de perfil

Las actualizaciones de registros de perfil están disponibles en el Experience Platform cuando se crea, actualiza o elimina un perfil nuevo.

### Datos recopilados del registro de perfil

A continuación se describen los datos capturados para un registro de perfil.

| Campo | Descripción |
|---|---|
| `channel` | Contiene información sobre el origen de los datos. Ambos `_id` y `_type` contain [valores de espacio de nombres](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | El identificador único del canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica el origen de los datos del canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Contiene información sobre el cliente. |
| `person.name` | Contiene información sobre el nombre del cliente. |
| `person.name.firstName` | Contiene el nombre del cliente. |
| `person.name.lastName` | Contiene los apellidos del cliente. |
| `person.birthDate` | Fecha de nacimiento del comprador. |
| `personalEmail` | Una dirección de correo electrónico personal. |
| `personalEmail.address` | La dirección técnica, por ejemplo, `name@domain.com` como se define comúnmente en RFC2822 y estándares subsiguientes. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.startDate` | La fecha en la que se creó el perfil por primera vez. |

>[!NOTE]
>
>Cada registro de perfil también incluye el [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que incluye la dirección de correo electrónico del comprador, cuando está disponible, y ECID.

Obtenga información sobre cómo [crear un esquema específico de registro de perfil](profile-data.md) que pueden introducir los datos de sus registros de perfil.
