---
description: Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS realizando reemplazos directos en sus archivos .xml. Designe las áreas de la página que se reemplazarán por contenido de Destinatario mediante el elemento XML personalizado ADBTarget.
seo-description: Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS realizando reemplazos directos en sus archivos .xml. Designe las áreas de la página que se reemplazarán por contenido de Destinatario mediante el elemento XML personalizado ADBTarget.
seo-title: Adobe Target para TVML/TVJS
title: Adobe Target para TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 70%

---


# Adobe Target para TVML/TVJS{#adobe-target-for-tvml-tvjs}

Puede aprovechar Adobe Target en sus aplicaciones TVML/TVJS realizando reemplazos directos en sus archivos .xml. Designe las áreas de la página que se reemplazarán por contenido de Destinatario mediante el elemento XML personalizado ADBTarget.

>[!IMPORTANT]
>
>Antes de usar el elemento `ADBTarget` en sus páginas TVML, debe configurar la aplicación TVML/TVJS para que utilice el SDK para tvOS. Para obtener más información, consulte [Implementación de Apple TV con tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Primeros pasos {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identifique el archivo `.xml` en el que quiere utilizar su ubicación de Target.
1. Agregue un elemento `ADBTarget` al archivo como secundario del elemento `<document>`.
1. Si Target no encuentra su ubicación Mbox o si se excede el tiempo de respuesta, el valor entre las etiquetas `<ADBTarget>`y `</ADBTarget>` se utiliza como contenido predeterminado.

## Configuración de Mbox en Target {#section_F2DA140C34B0421D976046F825B23123}

El contenido devuelto desde Target reemplaza todo el contenido entre `<ADBTarget>` y `</ADBTarget>`, incluidas ambas etiquetas `ADBTarget`.

>[!TIP]
>
>Debe planificar en consecuencia qué desea reemplazar.

Su caso de uso podría ser tan sencillo como sustituir un valor de cadena en una etiqueta, o tan complejo como reemplazar una página entera.

## Configurar el elemento ADBTarget {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

En el elemento `ADBTarget`, debe proporcionar el nombre de en la propiedad `mbox`mbox. Si lo desea, puede agregar propiedades personalizadas a la solicitud con el formato `customParameterName="customParameterValue"`.

* **`mbox`**

   Nombre de su ubicación Mbox.

   * Tipo de propiedad: Cadena
   * Esta es una propiedad obligatoria.

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

   * Este es un ejemplo de código para esta propiedad:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Tipo de propiedad: Cadena
   * Esta propiedad **no es** obligatoria.

* **`mboxParameters`**

   Una lista de pares clave-valor para `mboxParameters`. Cada entrada en la cadena se separa con un punto y coma, mientras que los elementos clave-valor se separan con dos puntos.

   * Este es un ejemplo de código para esta propiedad:

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

* Esta es la configuración de landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Si la solicitud de Destinatario se realiza correctamente y se devuelve el contenido de la oferta, la página resultará con:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Si no se puede acceder al servidor de Destinatario o se agota el tiempo de espera de la solicitud, la página resultará en:

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
