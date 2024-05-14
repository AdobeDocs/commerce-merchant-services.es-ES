---
title: Incorporación e instalación
description: "Aprenda a instalar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c33ec5a10f9f2570e971e968efd1524e0d384ecd
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Incorporación e instalación

Instale el servicio de catálogo para solicitar y recibir datos de producto de una instancia de Commerce mediante [API de GraphQL del servicio de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/).

>[!NOTE]
>
>Si la instancia de Commerce utiliza Live Search o Product Recommendations, el servicio de catálogo se instala o actualiza automáticamente al incorporar o actualizar esos servicios. Para obtener más información, consulte las instrucciones de instalación de [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) y [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).

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

Todas las instancias de prueba de Commerce utilizan el extremo de zona protegida.

Realice todas las pruebas de carga en el extremo de la zona protegida. Antes de comenzar la prueba de carga, envíe un [Ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para que el equipo de servicios pueda anticipar el tráfico adicional del servidor.

## Instalación y configuración

Para empezar con [!DNL Catalog Service] para Adobe Commerce, se requieren los siguientes pasos:

- Instalación de las extensiones de exportación de datos
- Configuración del servicio y la exportación de datos
- Acceso al servicio

### Instalación de las extensiones de exportación de datos

Debe tener acceso a la línea de comandos del servidor para completar el [!DNL Catalog Service] proceso de incorporación.

El [!DNL Catalog Service] se instala con las claves del Compositor, que están vinculadas a la cuenta de Commerce [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) durante el proceso de suscripción. Composer utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que las claves de Composer no se han guardado previamente en un repositorio externo `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obtener más información sobre cómo obtener claves de Composer.

El [!DNL Catalog Service] La extensión de se puede instalar tanto en la infraestructura de nube de Adobe Commerce como en instancias locales.

>[!BEGINTABS]

>[!TAB Infraestructura en nube]

Utilice este método para instalar [!DNL Catalog Service] para una instancia de Commerce Cloud.

1. En la estación de trabajo local, cambie al directorio del proyecto para su proyecto de Adobe Commerce en la nube.

   >[!NOTE]
   >
   >Para obtener información sobre la administración local de entornos de proyecto de Commerce, consulte [Administración de ramas con CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) en el _Guía del usuario de Adobe Commerce sobre infraestructura en la nube_.

1. Consulte la rama de entorno para actualizar con la CLI de Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Añada el módulo Servicio de catálogo.

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. Actualizar dependencias del paquete.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Confirmar y enviar cambios de código para el `composer.json` y `composer.lock` archivos.

1. Añada, confirme e inserte los cambios de código para el `composer.json` y `composer.lock` al entorno de nube.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Al insertar las actualizaciones, se inicia el [Proceso de implementación de Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) para aplicar los cambios. Compruebe el estado de implementación desde el [implementar registro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB On-Premise]

Utilice este método para instalar [!DNL Catalog Service] extensión para una instancia local.

1. Use Compositor para agregar el módulo Servicio de catálogo a su proyecto:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. Actualice las dependencias e instale la extensión:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Actualizar Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Borre la caché:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >En algunos casos, especialmente al implementar en producción, puede que desee evitar borrar el código compilado, ya que puede tardar algún tiempo. Asegúrese de realizar una copia de seguridad del sistema antes de realizar cualquier cambio.

>[!ENDTABS]

### Configuración del servicio y la exportación de datos

Después de instalar el [!DNL Catalog Service], complete las siguientes tareas para integrar el servicio de catálogo con la instancia de Adobe Commerce. Esta integración permite la sincronización de datos y la comunicación entre la instancia de Commerce, el servicio de catálogo y otros servicios de soporte.

1. Configure las variables [Conector de Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) especificando las claves API y seleccionando un espacio de datos SaaS.

   La configuración del Conector de servicios de Commerce es un proceso único necesario para utilizar servicios de Adobe Commerce como el Servicio de catálogo, Live Search y Recommendations de productos. Si ya ha configurado el conector para otro servicio, omita este paso.

1. Realice una sincronización de datos inicial desde el [Tablero de administración de datos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   La sincronización inicial puede tardar entre unos minutos y horas, según el tamaño del catálogo. Puede monitorizar el estado de sincronización desde el panel de control de Data Management. Después de la sincronización inicial, el catálogo exporta datos de productos de forma continua para mantener los servicios actualizados.

Para asegurarse de que la exportación del catálogo se ejecuta correctamente:

- [Confirme que los trabajos cron se están ejecutando.](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Compruebe que los indexadores se están ejecutando desde el [Administrador](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) o utilizando el comando CLI de Commerce `bin/magento indexer:info`.
- Compruebe que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, y `Product Variant Feed` los indexadores se establecen en `Update by Schedule`.

### Acceso al servicio

El [!DNL Catalog Service] La API de GraphQL es accesible desde ` https://catalog-service.adobe.io/graphql` extremo que utiliza comandos del POST a través de HTTPS.

En las consultas de GraphQL, debe especificar varios encabezados HTTP, incluida la clave de API pública que agregó a la configuración del Conector de servicios de Adobe Commerce en Admin. Para obtener más información, consulte la [GraphQL de servicios de tienda](https://developer.adobe.com/commerce/services/graphql/) documentación.

### Configuración del cortafuegos

Para permitir [!DNL Catalog Service] a través de un cortafuegos, añada `commerce.adobe.io` a la lista de permitidos.

## Servicio de catálogo y malla de API

El [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe IO.

Consulte la [[!DNL Catalog Service] y API Mesh](mesh.md) tema para obtener detalles de instalación y configuración.

## Tablero de administración de datos

Para obtener más información acerca de [!DNL Catalog Service] sincronización de datos, consulte la [Tablero de administración de datos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
