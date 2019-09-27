---
description: Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS efectuando reemplazos directos en los archivos .xml. Designe áreas de su página que se reemplazarán con contenido de Target empleando el elemento XML personalizado ADBTarget.
seo-description: Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS efectuando reemplazos directos en los archivos .xml. Designe áreas de su página que se reemplazarán con contenido de Target empleando el elemento XML personalizado ADBTarget.
seo-title: Adobe Target para TVML/TVJS
title: Adobe Target para TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target para TVML/TVJS{#adobe-target-for-tvml-tvjs}

Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS efectuando reemplazos directos en los archivos .xml. Designe áreas de su página que se reemplazarán con contenido de Target empleando el elemento XML personalizado ADBTarget.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. Para obtener más información, consulte Implementación de [Apple TV con tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Primeros pasos {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>You should plan what you want to replace accordingly.

Su caso de uso podría ser tan sencillo como sustituir un valor de cadena en una etiqueta, o tan complejo como reemplazar una página entera.

## Configure your ADBTarget element {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

En el elemento `ADBTarget`, debe proporcionar el nombre de en la propiedad `mbox`mbox. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Nombre de su ubicación Mbox.

   * Tipo de propiedad: Cadena
   * Esta propiedad es obligatoria.

* **`id`**

   ID del pedido.

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.

* **`total`**

   El total del pedido.

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.

* **`purchasedProductIds`**

   Una lista separada por comas del ID de los productos adquiridos en este pedido.

   * Este es el ejemplo de código de esta propiedad:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.

* **`mboxParameters`**

   Una lista de pares clave-valor para `mboxParameters`. Each entry in this string is separated by a semicolon, and key-values are separated by a colon.

   * Here is the code sample for this property:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.

* **`customParameterName`**

   El valor de esta propiedad es `customParameterValue`.

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.


## Ejemplos {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Ejemplo 1

El siguiente ejemplo utiliza un elemento `ADBTarget` en la página `LandingPage.xml.js` para reemplazar el contenido de una alerta:

#### Configure Target

Suponga que tiene una ubicación Mbox llamada `landingPage` y que el contenido de la oferta se establece del siguiente modo:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### Configure landingPage.xml.js

* Esta es la configuración para landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Si la solicitud a Target se realiza correctamente y se devuelve el contenido de la oferta, su página resultará así:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Si el servidor de Target no está disponible o se excede el tiempo de la solicitud, su página resultará así:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Ejemplo 2

El siguiente ejemplo ilustra cómo se agregan datos personalizados al elemento `ADBTarget`. Este método le permite crear experiencias condicionales y ofrecer contenido para esta ubicación Mbox en Target:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
