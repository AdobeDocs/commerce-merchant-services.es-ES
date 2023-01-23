---
title: Cargar perfiles del comprador a Adobe Experience Platform
description: Obtenga información sobre cómo cargar perfiles de comprador en Adobe Experience Platform.
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
source-git-commit: 9bf28159fdac3a7237956a536f6a522b4e2918fe
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Cargar el perfil del comprador a Adobe Experience Platform

Los comerciantes de Adobe Commerce pueden cargar datos de perfil de cliente en [Perfil del cliente en tiempo real](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), que forma parte de Adobe Experience Platform. Profile le permite consolidar los datos de sus clientes en una vista unificada, ofreciendo una cuenta procesable y con marca de tiempo de cada interacción con los clientes.

>[!NOTE]
>
> Los datos de perfil deben incluir una dirección de correo electrónico, ya que así es como se crea el vínculo entre un comprador y sus datos de comportamiento de tienda.

Después de cargar los perfiles del comprador, los datos de evento asociados con cualquier interacción que realicen los compradores en el sitio se envían a Perfil a través del conector del Experience Platform y se vinculan al perfil de ese comprador.

>[!NOTE]
>
> La variable `createAccount` [evento de tienda](events.md) no crea automáticamente un perfil de cliente en Perfil. Esto está restringido por razones de seguridad y es intencional.

En este tema, aprenderá a cargar sus perfiles de cliente de Adobe Commerce en Perfil del cliente en tiempo real en Experience Platform.

1. Determine dónde almacena los datos del cliente. Para algunos comerciantes, estos datos se almacenan en Adobe Commerce y se pueden [exportado](https://docs.magento.com/user-guide/system/data-export.html) como archivo CSV. Para otros, puede estar en un sistema de administración de la relación con los clientes (CRM) independiente.

1. Después de determinar dónde almacena los datos de sus clientes, busque los datos adecuados [conector de origen](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) en función de dónde se almacenen los datos de sus clientes. Si no ve un conector de origen apropiado, utilice el [carga de archivos locales](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) conector e importe los perfiles del comprador de un archivo CSV.

   >[!NOTE]
   >
   > Si utiliza el conector de carga de archivos local, debe habilitar la variable **Conjunto de datos del perfil** cuando [definición del conjunto de datos](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). Esto identifica el conjunto de datos como datos de perfil.

Después de crear los perfiles del comprador en Perfil, todos los datos de tienda asociados a ese comprador se vincularán a su perfil.

## Cargar perfiles con frecuencia

Para garantizar una experiencia de comprador mejorada, debe importar los datos de perfil periódicamente. Algunos conectores de origen permiten importar datos de perfil según una programación.
