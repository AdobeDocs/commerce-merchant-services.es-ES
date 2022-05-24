---
title: Incorporado "[!DNL Store Fulfillment]"
description: Conecte la instancia de Commerce a la [!DNL Store Fulfillment Manager] completando algunos pasos de integración.
role: User, Admin
level: Intermediate
source-git-commit: 24639b75d3c629856fbb8fc74e7eb072d4197815
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---


# Cumplimiento de las tiendas integradas por Walmart Technologies

Complemento de la tienda integrada instalando la extensión en su instancia de comercio y configurando las conexiones de API. Estas conexiones permiten la comunicación y la sincronización de datos entre la instancia de Commerce, los sistemas de terceros para la administración de inventario y la aplicación Store Assist.

Después de completar la incorporación, configure y administre la solución desde el administrador de comercio

![[!DNL Store Fulfillment Service] configuración en la vista Administración](assets/store-fulfillment-admin-home.png)

## Información general sobre la incorporación

1. Instale la extensión Store Fulfillment by Walmart Technologies para Adobe Commerce.

1. Desde el administrador, habilite la solución y complete la configuración general para la integración, sus funciones activas y complete el formulario de incorporación para conectarse a los servicios de cumplimiento.

1. Configure los métodos de envío.

1. Configure las fuentes como tiendas físicas y los productos en el catálogo.

1. Seleccione y configure las plantillas de correo electrónico para administrar la comunicación con el cliente para comprar en línea y recoger transacciones en la tienda (BOPIS).

1. Cree usuarios y funciones para la aplicación de ayuda de la tienda.

1. Configure las programaciones de los procesos en segundo plano para sincronizar los datos con el servicio de cumplimiento.

## Requisitos previos

* **Información de la cuenta de comercio**-Descarga e instalación [!DNL Channel Manager] requiere un [Cuenta de comercio](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Necesita un ID de cuenta y credenciales con acceso de propietario o administrador a la variable [!DNL Adobe Commerce] o [!DNL Magento Open Source] instancia.

* Para [!DNL Adobe Commerce] en proyectos de infraestructura en la nube, los instaladores de software deben tener el siguiente acceso a la variable [!DNL Commerce] instancia:

   * Acceso de superusuario al proyecto de Cloud
   * Acceso de administrador a un entorno específico
   * Un [!DNL Adobe Commerce] o [!DNL Magento Open Source] cuenta con permisos para acceder al repositorio del Compositor

      Consulte [Administrar el acceso de los usuarios](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Acceso al cumplimiento de la tienda mediante el archivo de software de Walmart Technologies para instalar la solución de cumplimiento de almacenamiento en su instancia de Adobe Commerce**-El representante de cuentas del cliente puede proporcionar acceso al archivo de instalación de la extensión.

* **Experiencia con el Compositor y el[!DNL Commerce CLI]** -Consulte [Instalación general de CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obtener información sobre el uso de estas herramientas para instalar y administrar extensiones en [!DNL Adobe Commerce] y [!DNL Magento Open Source] plataformas.

* [!DNL Inventory Management] extensión para Adobe Commerce y Magento Open Source

   Debe tener la extensión de Inventory management instalada y habilitada en la instancia de Adobe Commerce y Magento Open Source. Normalmente, esta extensión está instalada y habilitada de forma predeterminada en Adobe Commerce y Magento Open Source 2.3.x y posteriores. Para obtener más información, consulte [Instalación de Inventory management](https://devdocs.magento.com/extensions/inventory-management/) en la documentación para desarrolladores de Adobe Commerce.

## Requisitos

La solución Store Fulfillment está disponible para los clientes de Adobe Commerce y Magento Open Source. Debe satisfacer los siguientes requisitos del sistema y de la empresa para instalar, implementar y utilizar la solución.

### Requisitos del sistema

La extensión Store Fulfillment de Walmart Technologies se ha probado para comprobar la compatibilidad con las siguientes versiones de software.

**Compatibilidad del software**

| **Software** | **Versión mínima** | **Versión máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| Compositor | 1.x | 2.x |
| MariaDB | 10,2 | 10,4 |
| MySQL | 5,7 | 8,0 |
| PHP | 7,4 | 8,1 |

Para conocer los requisitos detallados, consulte Adobe Commerce . [Requisitos del sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) en la documentación para desarrolladores.

### Requisitos empresariales

Su empresa debe cumplir los siguientes criterios mínimos para implementar la solución de cumplimiento de almacenamiento.

* Negocios basados en EE. UU.

* Minoristas de B2C, fabricantes de CPG que venden D2C o distribuidores que venden D2C o a pequeñas empresas

* Al menos un almacén físico o almacén

* Administrar el inventario de productos con Inventory management for Commerce (era MSI)

* Capacidad de sindicación de inventario de comerciantes

* Almacene la disponibilidad de Wi-Fi en todas las ubicaciones que admitan la solución Store Fulfillment

* Los asociados de almacén y almacén tienen acceso a dispositivos móviles iOS o Android durante sus turnos, ya sea personales o proporcionados por el comerciante

* Los productos que se administran mediante la solución Store Fulfillment deben tener atributos de producto que incluyan un SKU o producto UPC.

### Plataformas compatibles

* Adobe Commerce on Cloud (ECE) : 2.4.x
* Adobe Commerce local (EE) : 2.4.x
* Magento Open Source 2.4.x
