---
description: Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.
keywords: phonegap
seo-description: Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.
seo-title: Complemento PhoneGap
solution: Marketing Cloud,Analytics
title: Complemento PhoneGap
topic: Desarrollador e implementación
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# PhoneGap plug-in{#phonegap-plug-in}

Este complemento le permite enviar llamadas iOS AppMeasurement desde el proyecto PhoneGap.

## Nueva versión del SDK de Adobe Experience Platform Mobile

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Creación de un proyecto de PhoneGap

To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Instalación del complemento utilizando npm: {#section_43229E57C16944C0B51531CB92089189}

1. Ejecute el siguiente comando:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Instalación manual del complemento {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Incluir la biblioteca AppMeasurement

Para incluir AppMeasurement:

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. Complete la siguiente configuración:

   1. Seleccione **[!UICONTROL Copiar elementos a la carpeta del grupo de destino (si es necesario)]**.
   1. Seleccione los objetivos en los que quiere usar el código AppMeasurement.

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Agregar permisos de aplicación

La biblioteca AppMeasurement requiere lo siguiente:

1. Inicie el IDE de Xcode y abra la aplicación.
1. Arrastre la carpeta **[!UICONTROL Adobe Mobile]al proyecto de Xcode y complete la siguiente configuración:**

   1. Seleccione **[!UICONTROL Copiar elementos a la carpeta del grupo de destino (si es necesario)]**.
   1. Seleccione **[!UICONTROL Crear grupos para todas las carpetas agregadas]**.
   1. Seleccione los destinos en los que quiere usar el código AppMeasurement y haga clic en **[!UICONTROL Finalizar]**.
   ![](assets/xcode-settings.png){width="672"}

1. En la ficha **[!UICONTROL Fases de compilación]** del destino del proyecto, expanda la sección **Vincular binario con bibliotecas]y agregue las bibliotecas siguientes:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Confirme que la aplicación se compila sin errores inesperados.

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

