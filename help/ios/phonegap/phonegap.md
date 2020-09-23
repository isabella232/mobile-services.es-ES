---
description: Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.
keywords: phonegap
seo-description: Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.
seo-title: Complemento PhoneGap
solution: Experience Cloud,Analytics
title: Complemento PhoneGap
topic: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 98%

---


# Complemento PhoneGap{#phonegap-plug-in}

Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Creación de un proyecto de PhoneGap

Para crear un proyecto de PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/es/experience-manager/6-4/mobile/using/phonegap.html).

## Instalación del complemento utilizando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Ejecute el siguiente comando:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Instalación manual del complemento {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Incluir la biblioteca de AppMeasurement

Para incluir AppMeasurement:

1. Arrastre `ADBMobile_PhoneGap.h` y `ADBMobile_PhoneGap.m` a la carpeta **[!UICONTROL Plugins]** de su proyecto Xcode.
1. Complete la siguiente configuración:

   1. Seleccione **[!UICONTROL Copiar elementos a la carpeta del grupo de destino (si es necesario)]**.
   1. Seleccione los objetivos en los que quiere usar el código AppMeasurement.

1. Arrastre `ADB_Helper.js` a la carpeta `www` del proyecto.
1. En la carpeta `res/xml`, abra `config.xml` y registre un nuevo complemento agregando lo siguiente:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Añadir permisos de aplicaciones

La biblioteca AppMeasurement requiere lo siguiente:

1. Inicie el IDE de Xcode y abra la aplicación.
1. Arrastre la carpeta **[!UICONTROL Adobe Mobile]** al proyecto de Xcode y complete la siguiente configuración:

   1. Seleccione **[!UICONTROL Copiar elementos a la carpeta del grupo de destino (si es necesario)]**.
   1. Seleccione **[!UICONTROL Crear grupos para todas las carpetas agregadas]**.
   1. Seleccione los destinos en los que quiere usar el código AppMeasurement y haga clic en **[!UICONTROL Finalizar]**.

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. En la ficha **[!UICONTROL Fases de compilación]** del destino del proyecto, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Confirme que la aplicación se compila sin errores inesperados.

## Implementación del seguimiento personalizado {#section_FD102B3CDAA4492FB04E56BF17E28663}

Cuando quiera utilizar el seguimiento en archivos `html`, agregue lo siguiente a la etiqueta `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

