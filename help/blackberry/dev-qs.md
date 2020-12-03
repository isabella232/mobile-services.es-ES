---
title: Inicio rápido para desarrolladores
seo-title: Inicio rápido para desarrolladores de BlackBerry para Adobe Mobile Services
description: La Guía de Inicio rápido para desarrolladores de BlackBerry le ayuda a comprender el proceso de implementación de la biblioteca de BlackBerry para Adobe Mobile Services.
seo-description: La Guía de Inicio rápido para desarrolladores de BlackBerry le ayuda a comprender el proceso de implementación de la biblioteca de BlackBerry para Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 2%

---


# Inicio rápido para desarrolladores

Esta información le ayuda a comprender el proceso de implementación de la biblioteca BlackBerry.

## Obtención del SDK  

**El SDK requiere BlackBerry 10 o posterior.**

Después de descomprimir el SDK descargado, compruebe que los siguientes archivos existen en una `AdobeMobile` carpeta:

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

## Añadir los SDK en el proyecto

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Configurar]** > **[!UICONTROL Añadir biblioteca]**.
1. Seleccione Biblioteca **** externa y haga clic en **[!UICONTROL Siguiente]**.
1. Haga clic en **[!UICONTROL Examinar]** junto al campo Biblioteca **[!UICONTROL de]** dispositivos.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. En la `Device-Debug` carpeta, seleccione `libADBMobileShared.so` y haga clic en **[!UICONTROL Abrir]**.
1. Haga clic en **[!UICONTROL Examinar]** junto al campo Biblioteca **[!UICONTROL del]** simulador.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. En la `Device-Debug` carpeta, seleccione `libADBMobileShared.so` y haga clic en **[!UICONTROL Abrir]**.
1. Haga clic en **[!UICONTROL Añadir]** junto al campo **[!UICONTROL Incluir carpetas]** .
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Añada la `public` carpeta a sus inclusiones.
1. En la `ADBMobile-4.0.0BETA-BlackBerry` carpeta, hay un archivo `.json` de configuración denominado `ADBMobileConfig.json`.

   Copie ese archivo en la raíz del proyecto.
1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Actualizar]**.

   El `.json` archivo debe estar visible en el Explorador **[!UICONTROL de proyectos]**.
1. Abra el `bar-descriptor.xml` archivo del proyecto.
1. En la parte inferior de la ventana, seleccione la ficha **[!UICONTROL Recursos]** .
1. Confirme que **[!UICONTROL (Todas las configuraciones)]** está seleccionada y, a continuación, haga clic en **[!UICONTROL Añadir archivos]** en la sección **[!UICONTROL Recursos]** de la ventana.
   >[!TIP]
   >
   >Hay un error en el IDE de QNX Momentics que a veces evita que esos botones sean visibles. Si no puede ver los botones, cambie el tamaño de las ventanas hasta que aparezcan.

1. Haga clic en **[!UICONTROL Espacio de trabajo]**.
1. Busque el `ADBMobileConfig.json` archivo en el proyecto y haga clic en **[!UICONTROL Aceptar]**.

La aplicación puede importar las clases e interfaces de la `adobeMobileLibrary.jar` biblioteca mediante `#include <ADBMobile.hpp>`.

## Añadir permisos de aplicaciones

En `bar-descriptor.xml` el directorio del proyecto, agregue la línea `<permission>access_internet</permission>`o, en el IDE de QNX Momentics, seleccione el cuadro de **[!UICONTROL Internet]** en la sección Permisos de la ficha **[!UICONTROL Aplicación]** .

## Actualizar el archivo `ADBMobileConfig.json` de configuración

El `ADBMobileConfig.json` archivo contiene la configuración global del SDK. Debe actualizar algunos valores para empezar.

The following is an example of an `ADBMobileConfig.json` file:

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

Al menos debe actualizar los parámetros `rsids` y `server` . Para obtener más información, consulte Referencia [de métodos y clases de](/help/blackberry/methods.md)Adobe Mobile.

Ahora puede implementar Analytics en la aplicación BlackBerry 10.
