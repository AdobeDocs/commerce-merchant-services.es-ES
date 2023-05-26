---
title: Incorporación e instalación
description: Obtenga información sobre cómo instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 742af84407943e7df47f986717b6dc31dc067863
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Incorporación e instalación

Consulte una introducción al proceso Servicio de catálogo.

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

- Adobe Commerce en infraestructura en la nube: 2.4.4+
- Adobe Commerce local: 2.4.4+

## Entornos

El servicio de catálogo tiene dos entornos disponibles para la incorporación:

- Espacio aislado (https://catalog-service-sandbox.adobe.io/graphql): se utiliza para pruebas y validación antes de activarse
- Producción (https://catalog-service.adobe.io/graphql)-) utilizada para el tráfico en directo de comerciantes y sitios web de Commerce

## Instalación y configuración

Para empezar a utilizar el servicio de catálogo para Adobe Commerce, se requieren los siguientes pasos:

- Instalación de las extensiones de exportación de datos
- Configuración del servicio y la exportación de datos
- Acceso al servicio

### Instalación de las extensiones de exportación de datos

El proceso de incorporación del servicio de catálogo requiere acceso a la línea de comandos del servidor.

La extensión del Servicio de catálogo se puede instalar tanto en la infraestructura de nube de Adobe Commerce como en instancias locales.

El servicio de catálogo se instala con claves de Compositor, que están vinculadas a la cuenta de Commerce [mageide](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) durante el proceso de suscripción. Composer utiliza estas claves durante la instalación inicial de Adobe Commerce o en situaciones en las que las claves de Composer no se han guardado previamente en un repositorio externo `auth.json` archivo.

Consulte [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obtener más información sobre cómo obtener claves de Composer.

#### Adobe Commerce en la infraestructura en la nube

Utilice este método para instalar la extensión del servicio de catálogo para una instancia de Commerce Cloud.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la sección requerida de la siguiente manera:

```json
"require": {
  "magento/catalog-service": "^2.2.0"
}
```

1. Pruebe la nueva configuración localmente y actualice las dependencias:

```bash
composer update
```

El comando actualiza todas las dependencias.

1. Confirme e inserte los cambios para `composer.json` y `composer.lock`.

#### On-Premise

Utilice este método para instalar la extensión del servicio de catálogo para una instancia local.

1. Abra el `<Commerce_root>/composer.json` en un editor de texto y actualice la sección requerida de la siguiente manera:

```json
"require": {
    "magento/catalog-service": "^2.2.0"
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

Después de instalar el servicio de catálogo, debe configurar la variable [Conector de Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) especificando las claves API y seleccionando un espacio de datos SaaS.

Una vez completada la configuración de SaaS, realice una sincronización de datos inicial siguiendo el [Sincronización de catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guía.

Para asegurarse de que la exportación del catálogo se ejecuta correctamente:

- Confirme que los trabajos cron se están ejecutando.
- Compruebe que los indexadores se están ejecutando.
- Asegúrese de que la variable `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, y `Product Variant Feed` Los indexadores se definen como &quot;Actualizar por programación&quot;.

La sincronización inicial puede tardar entre unos minutos y horas, según el tamaño del catálogo. Después de la sincronización inicial, el catálogo exporta datos de producto del servidor de Commerce a los servicios de Commerce de forma continua para mantener los servicios actualizados.

### Acceso al servicio

Se puede acceder a la API del servicio de catálogo mediante comandos del POST a través de HTTPS.

Para obtener la clave API, vaya al área del conector de Commerce Service en el administrador y copie la clave API pública.

Lea el [Documentación de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) para comprender cómo consultar y enviar los encabezados necesarios para generar solicitudes de API.

## Servicio de catálogo y malla de API

El [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite a los desarrolladores integrar API privadas o de terceros y otras interfaces con productos de Adobe mediante Adobe IO.

Consulte la  [Servicio de catálogo y malla de API](mesh.md) tema para obtener detalles de instalación y configuración.
