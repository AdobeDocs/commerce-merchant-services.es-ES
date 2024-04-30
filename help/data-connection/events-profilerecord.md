---
title: Registros de perfil
description: Descubra qué datos captura un registro de perfil.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] Registros de perfil (beta)

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
| `billingAddress` | La dirección postal de facturación. |
| `billingAddress.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle. |
| `billingAddress.street2` | Segunda línea para información de dirección (opcional) |
| `billingAddress.city` | El nombre de la ciudad. |
| `billingAddress.state` | El nombre del estado. Este es un campo de forma libre. |
| `billingAddress.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `billingAddressPhone` | El número de teléfono asociado con la dirección de facturación. |
| `billingAddressPhone.number` | El número de teléfono. Tenga en cuenta que el número de teléfono es una cadena y puede incluir caracteres clave como corchetes `()`, guiones `-`o caracteres para indicar identificadores de submarcado como extensiones `x` por ejemplo,  `1-353(0)18391111` o `+613 9403600x1234`. |
| `shippingAddress` | La dirección postal de envío. |
| `shippingAddress.street1` | Información principal de la dirección postal, número de piso, número de calle y nombre de la calle. |
| `shippingAddress.street2` | Segunda línea para información de dirección (opcional) |
| `shippingAddress.city` | El nombre de la ciudad. |
| `shippingAddress.state` | El nombre del estado. Este es un campo de forma libre. |
| `shippingAddress.country` | El nombre del territorio administrado por el gobierno. Distinto a `xdm:countryCode`Sin embargo, este es un campo de forma libre que puede tener el nombre del país en cualquier idioma. |
| `shippingAddressPhone` | Número de teléfono asociado a la dirección de envío. |
| `shippingAddressPhone.number` | El número de teléfono. Tenga en cuenta que el número de teléfono es una cadena y puede incluir caracteres clave como corchetes `()`, guiones `-`o caracteres para indicar identificadores de submarcado como extensiones `x` por ejemplo,  `1-353(0)18391111` o `+613 9403600x1234`. |
| `userAccount` | Indica detalles de fidelidad, preferencias, procesos de inicio de sesión y otras preferencias de la cuenta. |
| `userAccount.startDate` | La fecha en la que se creó el perfil por primera vez. |

>[!NOTE]
>
>Cada registro de perfil también incluye el [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) , que incluye el ID de cliente de Commerce generado por el sistema como identificador principal del perfil y un ID de correo electrónico que se utiliza como identificador secundario.

Obtenga información sobre cómo [crear un esquema específico de registro de perfil](profile-data.md) que pueden introducir los datos de sus registros de perfil.
