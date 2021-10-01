---
title: Inicio rápido para desarrolladores
description: La Guía de inicio rápido para desarrolladores de BlackBerry le ayuda a comprender el proceso de implementación de la biblioteca de BlackBerry para Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# Inicio rápido para desarrolladores

Esta información le ayuda a comprender el proceso de implementación de la biblioteca de BlackBerry.

## Obtención del SDK  

**El SDK requiere BlackBerry 10 o posterior.**

Después de descomprimir el SDK descargado, compruebe que los siguientes archivos existan en una carpeta `AdobeMobile`:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## Añadir los SDK al proyecto

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Configurar]** > **[!UICONTROL Agregar biblioteca]**.
1. Seleccione **[!UICONTROL External library]** y haga clic en **[!UICONTROL Next]**.
1. Haga clic en **[!UICONTROL Browse]** junto al campo **[!UICONTROL Device library]**.
1. Vaya a la carpeta `ADBMobile-4.0.0BETA-BlackBerry` .
1. En la carpeta `Device-Debug`, seleccione `libADBMobileShared.so` y haga clic en **[!UICONTROL Abrir]**.
1. Haga clic en **[!UICONTROL Browse]** junto al campo **[!UICONTROL Simulator library]**.
1. Vaya a la carpeta `ADBMobile-4.0.0BETA-BlackBerry` .
1. En la carpeta `Device-Debug`, seleccione `libADBMobileShared.so` y haga clic en **[!UICONTROL Abrir]**.
1. Haga clic en **[!UICONTROL Add]** junto al campo **[!UICONTROL Include folders]**.
1. Vaya a la carpeta `ADBMobile-4.0.0BETA-BlackBerry` .
1. Añada la carpeta `public` a las inclusiones.
1. En la carpeta `ADBMobile-4.0.0BETA-BlackBerry` hay un archivo de configuración `.json` llamado `ADBMobileConfig.json`.

   Copie ese archivo en la raíz del proyecto.
1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Refresh]**.

   El archivo `.json` debe estar visible en el **[!UICONTROL Explorador del proyecto]**.
1. Abra el archivo `bar-descriptor.xml` del proyecto.
1. En la parte inferior de la ventana, seleccione la pestaña **[!UICONTROL Assets]**.
1. Confirme que **[!UICONTROL (Todas las configuraciones)]** está seleccionado y haga clic en **[!UICONTROL Agregar archivos]** en la sección **[!UICONTROL Recursos]** de la ventana.
   >[!TIP]
   >
   >Hay un error en el IDE de QNX Momentics que a veces evita que esos botones sean visibles. Si no puede ver los botones, cambie el tamaño de las ventanas hasta que aparezcan.

1. Haga clic en **[!UICONTROL Workspace]**.
1. Busque el archivo `ADBMobileConfig.json` en el proyecto y haga clic en **[!UICONTROL OK]**.

La aplicación puede importar las clases e interfaces de la biblioteca `adobeMobileLibrary.jar` utilizando `#include <ADBMobile.hpp>`.

## Añadir permisos de aplicaciones

En `bar-descriptor.xml` en el directorio del proyecto, añada la línea `<permission>access_internet</permission>` o, en el IDE de QNX Momentics, seleccione el cuadro **[!UICONTROL Internet]** en la sección de permisos de la pestaña **[!UICONTROL Application]**.

## Actualizar el archivo de configuración `ADBMobileConfig.json`

El archivo `ADBMobileConfig.json` contiene la configuración global del SDK. Debe actualizar algunos valores para empezar.

El siguiente es un ejemplo de archivo `ADBMobileConfig.json`:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

Debe actualizar al menos los parámetros `rsids` y `server`. Para obtener más información, consulte [Referencia de métodos y clases móviles de Adobe](/help/blackberry/methods.md).

Ahora puede implementar Analytics en su aplicación de BlackBerry 10.
