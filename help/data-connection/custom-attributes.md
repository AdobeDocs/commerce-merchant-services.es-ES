---
title: Añadir atributos de pedido personalizados
description: Aprenda a añadir atributos de pedido personalizados a los datos de back office y a enviarlos al Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Añadir atributos de pedido personalizados

En este artículo, aprenderá a añadir atributos personalizados a los eventos de back office. Con los atributos personalizados, puede capturar perspectivas de datos enriquecidas para mejorar los análisis y crear experiencias personalizadas para sus compradores.

Los atributos personalizados se admiten en dos niveles:

- Nivel de pedido
- Nivel de artículo de pedido

>[!NOTE]
>
>El Adobe [!DNL Commerce] admite atributos personalizados que tienen un tipo de datos de cadena, booleano o fecha.

Añadir atributos personalizados a eventos de back office requiere lo siguiente:

1. Cree un proyecto en su instalación de [!DNL Commerce].
1. Actualice el esquema para que los nuevos atributos personalizados se puedan introducir correctamente en Experience Platform.
1. En el Administrador, confirme que los atributos personalizados se capturan y se envían al Experience Platform.

>[!IMPORTANT]
>
>La estructura de directorios y los ejemplos de código siguientes ilustran cómo se pueden implementar atributos personalizados. La estructura de directorios real y el código requerido dependen de la configuración de la tienda y del entorno.

## Paso 1: Crear la estructura de directorios

1. Vaya al directorio `app/code` de la instalación de [!DNL Commerce] y cree un directorio de módulos. Por ejemplo: `Magento/AepCustomAttributes`. Este directorio contiene los archivos necesarios para los atributos personalizados.
1. En el directorio del módulo, cree un subdirectorio llamado `etc`. El directorio `etc` contiene los archivos `module.xml`, `query.xml`, `di.xml` y `et_schema.xml`.

## Paso 2: Definir las dependencias y la versión de instalación

Cree un archivo `module.xml` que defina las dependencias y la versión de instalación. Por ejemplo:

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## Paso 3: Recuperar datos de pedidos de ventas

Crear un archivo `query.xml` que recupere datos de pedidos de ventas. Por ejemplo:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Paso 4: Configurar la inyección de dependencia

Cree un archivo `di.xml` que configure la inyección de dependencias. Por ejemplo:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## Paso 5: Defina los servicios utilizados para la inyección de dependencias

Cree un archivo `et_schema.xml` que defina los servicios utilizados para la inyección de dependencias. Por ejemplo:

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## Paso 6: Crear un directorio para los archivos PHP

En el mismo nivel que el directorio `etc`, cree un directorio llamado `Module/Provider`. Este directorio contiene los archivos PHP `OrderCustomAttributes` y `OrderItemCustomAttributes`.

## Paso 7: Definición de OrderCustomAttributes

Cree un archivo `OrderCustomAttributes.php` que defina el orden de los atributos personalizados. Por ejemplo:

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## Paso 8: Definición de OrderItemCustomAttributes

Cree un archivo `OrderItemCustomAttributes.php` que defina los atributos personalizados del elemento de pedido. Por ejemplo:

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## Paso 9: Crear un directorio para el archivo productContext

En el mismo nivel que el directorio `etc`, cree un directorio llamado `Plugin/Module`. Este directorio contiene el archivo `ProductContext.php`.

## Paso 10: Definir la clase ProductContext

Cree un archivo denominado `ProductContext.php` que defina la clase `ProductContext`. Por ejemplo:

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## Paso 11: Registrar el módulo

En el mismo nivel que el directorio `etc`, cree un archivo `registration.php` que registre el módulo. Por ejemplo:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Paso 12: Ampliar el esquema XDM existente

Para asegurarse de que el esquema [!DNL Commerce] del Experience Platform puede introducir los nuevos atributos de pedido personalizados, debe extender el esquema para incluir estos campos personalizados.

Para obtener información sobre cómo ampliar un esquema XDM existente para incluir estos campos personalizados, consulte el artículo [Crear y editar esquemas en la interfaz de usuario](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) en la documentación de Experience Platform. El campo ID de inquilino se genera dinámicamente; sin embargo, la estructura del campo debe ser similar al ejemplo proporcionado en la documentación del Experience Platform.

>[!IMPORTANT]
>
>Los atributos personalizados de XDM deben coincidir con los atributos enviados desde [!DNL Commerce].

Para `commerce.order`, agregue un campo para el nivel de pedido:

![Nivel de pedido](assets/order-level.png)

Para `productListItems`, agregue campos para el nivel de elemento de pedido:

![Nivel de elemento de pedido](assets/order-item-level.png)

## Paso 12: Confirmar que se están capturando datos

Vea la ficha [Personalización de datos](connect-data.md#data-customization) en el administrador para confirmar que se están capturando y enviando datos de atributos personalizados al Experience Platform.

### Resolución de problemas

Si ve el mensaje `No custom order attributes found.` en la ficha **[!UICONTROL Data Customization]**, confirme lo siguiente:

1. Ha completado los requisitos previos para habilitar la [extensión del conector de datos](overview.md#prerequisites).
1. Ha configurado [atributos de pedido personalizados](#add-custom-order-attributes).
1. Se ha generado al menos un evento de pedido.
