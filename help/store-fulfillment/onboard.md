---
title: Información general sobre la incorporación
description: '"Conecte su [!DNL Commerce] a la instancia de [!DNL Store Fulfillment Manager] completando algunos pasos de integración".'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Información general sobre la incorporación

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

## Requisitos

Debe cumplir los siguientes requisitos para instalar, implementar y utilizar la solución.

* **Información de la cuenta de comercio**-Instalación [!DNL Channel Manager] requiere un [Cuenta de comercio](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Necesita un ID de cuenta y credenciales con acceso de propietario o administrador a la variable [!DNL Adobe Commerce] instancia.

* Para [!DNL Adobe Commerce] en los proyectos de infraestructura de nube, los instaladores de software deben tener acceso de administrador al proyecto de Cloud. Consulte [Administrar el acceso de los usuarios](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Acceso al cumplimiento de la tienda por medio del archivo de software Walmart Technologies (archivo .zip) para instalar la solución Store Fulfillment**-Durante el proceso de incorporación y activación, el representante de cuentas de cliente proporcionará acceso de descarga al archivo de instalación.

* **Experiencia con el Compositor y el[!DNL Commerce CLI]**—Consulte [Instalación general de CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obtener información sobre el uso de estas herramientas para instalar y administrar extensiones en [!DNL Adobe Commerce] y [!DNL Magento Open Source] plataformas.

* [!DNL Inventory Management] extensión para Adobe Commerce y Magento Open Source

   Debe tener la extensión de Inventory management instalada y habilitada en la instancia de Adobe Commerce y Magento Open Source. Normalmente, esta extensión está instalada y habilitada de forma predeterminada en Adobe Commerce 2.3.x y posteriores. Para obtener más información, consulte [Instalación de Inventory management](https://devdocs.magento.com/extensions/inventory-management/) en la documentación para desarrolladores de Adobe Commerce.

## Requisitos de plataforma y versión

La variable [!DNL Store Fulfillment] está disponible para los clientes de Adobe Commerce en las siguientes plataformas.

* Adobe Commerce en infraestructura de nube (ECE)
* Adobe Commerce local (EE)

La solución Store Fulfillment es compatible con las siguientes versiones de software.

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

* Solo empresas basadas en EE. UU.

* Minoristas de B2C, fabricantes de CPG que venden D2C o distribuidores que venden D2C o a pequeñas empresas

* Al menos un almacén físico o almacén

* Administrar el inventario de productos con Inventory management para Adobe Commerce (era MSI)

* Capacidad de sindicación de inventario de comerciantes

* Almacene la disponibilidad de Wi-Fi en todas las ubicaciones que admitan la solución Store Fulfillment

* Los asociados de almacén y almacén tienen acceso a dispositivos móviles iOS o Android durante sus turnos, ya sea personales o proporcionados por el comerciante

* Los productos que se administran mediante la solución Store Fulfillment deben tener atributos de producto que incluyan un SKU o código de producto UPC
