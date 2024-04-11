---
title: Incorporación e instalación
description: "Aprenda a instalar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---

# Incorporación e instalación

Los siguientes vídeos le guían a través de [!DNL Catalog Service] proceso.

**Parte 1**: Incorporación e instalación

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Parte 2**: uso del [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## Requisitos previos

El proceso de incorporación para [!DNL Catalog Service] requiere acceso a la línea de comandos del servidor. Si no está familiarizado con el trabajo desde la línea de comandos, pida ayuda a un desarrollador o integrador de sistemas.

**Requisitos de software**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositor: 2.x

**Plataformas compatibles**

- Adobe Commerce en infraestructura en la nube: 2.4.4+
- Adobe Commerce local: 2.4.4+

>[!ENDSHADEBOX]

## Extremos

[!DNL Catalog Service] tiene dos extremos disponibles para la incorporación:

- Zona protegida (`https://catalog-service-sandbox.adobe.io/graphql`): se utiliza para pruebas y validación antes de activarse
- Producción (`https://catalog-service.adobe.io/graphql`): se utiliza para el tráfico en directo de comerciantes y sitios web de Commerce.

Todas las instancias de prueba de Commerce deben utilizar el extremo de zona protegida.

Las pruebas de carga solo deben realizarse en el extremo de la zona protegida. Se recomienda que una [Ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) se abrirá durante la prueba de carga para que el equipo de servicios pueda anticipar el tráfico adicional del servidor.

## Instalación y configuración

Para empezar con [!DNL Catalog Service] para Adobe Commerce, se requieren los siguientes pasos:

- Instalación de las extensiones de exportación de datos
- Configuración del servicio y la exportación de datos
- Acceso al servicio

### Instalación de las extensiones de exportación de datos

El proceso de incorporación para [!DNL Catalog Service] requiere acceso a la línea de comandos del servidor.

El [!DNL Catalog Service] La extensión de se puede instalar tanto en la infraestructura de nube de Adobe Commerce como en instancias locales.

El [!DNL Catalog Service] se instala con las claves del Compositor, que están vinculadas a la cuenta de Commerce [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) durante el proceso de suscripción. Composer utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que las claves de Composer no se han guardado previamente en un repositorio externo `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obtener más información sobre cómo obtener claves de Composer.

#### Adobe Commerce en la infraestructura en la nube

Utilice este método para instalar [!DNL Catalog Service] para una instancia de Commerce Cloud.

1. En la estación de trabajo local, cambie al directorio del proyecto.
1. Añada el módulo Servicio de catálogo.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Actualizar dependencias del paquete.

   ```bash
   composer update
   ```

1. Confirmar y enviar cambios de código para el `composer.json` y `composer.lock` archivos.

#### On-Premise

Utilice este método para instalar [!DNL Catalog Service] extensión para una instancia local.

1. Use Compositor para agregar el módulo Servicio de catálogo a su proyecto:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update
   ```

1. Actualizar Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

### Configuración del servicio y la exportación de datos

Después de la instalación [!DNL Catalog Service], debe configurar la variable [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) especificando las claves API y seleccionando un espacio de datos SaaS.

Una vez completada la configuración de SaaS, realice una sincronización de datos inicial utilizando [Tablero de administración de datos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Puede utilizar este panel para monitorizar el estado de sincronización de los datos de producto transferidos desde la base de datos de Commerce a los servicios SaaS de Commerce.

Para asegurarse de que la exportación del catálogo se ejecuta correctamente:

- Confirme que los trabajos cron se están ejecutando.
- Compruebe que los indexadores se están ejecutando.
- Asegúrese de que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, y `Product Variant Feed` Los indexadores se definen como &quot;Actualizar por programación&quot;.

La sincronización inicial puede tardar entre unos minutos y horas, según el tamaño del catálogo. Después de la sincronización inicial, el catálogo exporta datos de productos del servidor de Commerce a los servicios de Commerce de forma continua para mantener los servicios actualizados. Para monitorizar el estado de la sincronización, consulte la [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### Acceso al servicio

El [!DNL Catalog Service] Se puede acceder a la API mediante comandos del POST a través de HTTPS.

Para obtener la clave API, vaya al área de Commerce Service Connector en el administrador y copie la clave API pública.

Lea el [Documentación de GraphQL](https://developer.adobe.com/commerce/services/graphql/) para comprender cómo consultar y enviar los encabezados necesarios para generar solicitudes de API.

Para permitir [!DNL Catalog Service] a través de un cortafuegos, añada `commerce.adobe.io` a la lista de permitidos.

## Servicio de catálogo y malla de API

El [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe IO.

Consulte la  [[!DNL Catalog Service] y API Mesh](mesh.md) tema para obtener detalles de instalación y configuración.

## Tablero de administración de datos

Los usuarios pueden consultar la [Tablero de administración de datos](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) para obtener más datos acerca de [!DNL Catalog Service] sincronización de datos.
