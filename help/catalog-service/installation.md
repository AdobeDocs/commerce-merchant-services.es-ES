---
title: Integración e instalación
description: Obtenga información sobre cómo instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d7a38fc81265897615896812d49a164a21d1d84
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Integración e instalación

Consulte el tutorial del proceso del servicio de catálogo.

Parte 1:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

Parte 2:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## Requisitos previos

El proceso de incorporación para [!DNL Catalog Service] requiere acceso a la línea de comandos del servidor. Si no está familiarizado con el trabajo desde la línea de comandos, pida ayuda a un desarrollador o integrador de sistemas.

### Requisitos de software

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositor: 2.x

### Plataformas compatibles

- Adobe Commerce en infraestructura de nube: 2.4.4+
- Adobe Commerce local: 2.4.4+

## Entornos

El servicio de catálogo tiene dos entornos disponibles para la incorporación:

- Simulador para pruebas (https://catalog-service-sandbox.adobe.io/graphql): se utiliza para pruebas y validaciones antes de publicarse
- Producción (https://catalog-service.adobe.io/graphql)- se utiliza para el tráfico en directo para comerciantes de comercio y sitios web)

## Instalación y configuración

Para empezar a usar el servicio de catálogo para Adobe Commerce, se requieren los siguientes pasos:

- Instalación de las extensiones de exportación de datos
- Configuración del servicio y la exportación de datos
- Acceso al servicio

### Instalación de las extensiones de exportación de datos

El proceso de incorporación para el servicio de catálogo requiere acceso a la línea de comandos del servidor.

La extensión del servicio de catálogo se puede instalar tanto en la infraestructura de nube de Adobe Commerce como en las instancias locales.

El servicio de catálogo se instala con las claves del Compositor, que están vinculadas a la cuenta de comercio [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) proporcionado durante el proceso de suscripción. El Compositor utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que las claves del Compositor no se guardaban previamente en un entorno externo `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obtener más información sobre la obtención de claves de Composer.

#### Adobe Commerce en infraestructura en la nube

Utilice este método para instalar la extensión del servicio de catálogo para una instancia de Commerce Cloud.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la sección requerida de la siguiente manera:

```json
"require": {
  "magento/catalog-service": "^2.1.0"
}
```

1. Pruebe la nueva configuración localmente y actualice las dependencias:

```bash
composer update
```

El comando actualiza todas las dependencias.

1. Confirmar e impulsar los cambios para `composer.json` y `composer.lock`.

#### Local

Utilice este método para instalar la extensión del servicio de catálogo para una instancia local.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la sección requerida de la siguiente manera:

```json
"require": {
    "magento/catalog-service": "^2.1.0"
}
```

1. Actualice las dependencias e instale la extensión:

```bash
composer update
```

El comando actualiza todas las dependencias.

1. Actualizar Adobe Commerce:

```bash
bin/magento setup:upgrade
```

1. Borre la caché:

```bash
bin/magento cache:clean
```

### Configuración del servicio y la exportación de datos

Después de instalar el servicio de catálogo, debe configurar la variable [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) especificando las claves de API y seleccionando un espacio de datos SaaS.

Una vez completada la configuración de SaaS, realice una sincronización de datos inicial siguiendo la [Sincronización del catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guía.

Para asegurarse de que la exportación del catálogo se esté ejecutando correctamente:

- Confirme que los trabajos de cron se están ejecutando.
- Compruebe que los indexadores se estén ejecutando.
- Asegúrese de que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`y `Product Variant Feed` los indexadores se establecen en &quot;Actualizar por programa&quot;.

La sincronización inicial puede tardar de unos minutos a horas, dependiendo del tamaño del catálogo. Después de la sincronización inicial, el Catálogo exporta los datos de producto del servidor de Commerce a los servicios de Commerce de forma continua para mantener los servicios actualizados.

### Acceso al servicio

Se puede acceder a la API del servicio de catálogo mediante comandos de POST a través de HTTPS.

Para obtener la clave de api, vaya al área de Commerce Service Connector en el administrador y copie la clave de API pública.

Lea el [Documentación de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) para comprender cómo consultar y enviar los encabezados necesarios para generar solicitudes de API.

## Servicio de catálogo y red de API

La variable [Mesh de API para Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe IO.

Consulte la  [Servicio de catálogo y red de API](mesh.md) tema para detalles de instalación y configuración.
