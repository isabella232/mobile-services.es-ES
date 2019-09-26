---
title: Inicio rápido para desarrolladores
seo-title: BlackBerry Developer Quick Start for Adobe Mobile Services
description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
seo-description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Inicio rápido para desarrolladores

Esta información le ayudará a comprender el proceso de implementación de la biblioteca de BlackBerry.

## Obtención del SDK

**Requisito del SDK: BlackBerry 10 o versiones posteriores.**

Tras descomprimir el SDK descargado, verifique que los siguientes archivos estén en la carpeta `AdobeMobile`:

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

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Seleccione **[!UICONTROL Biblioteca externa]** y haga clic en **[!UICONTROL Siguiente]**.
1. Haga clic en **[!UICONTROL Examinar]** junto al campo **Biblioteca de dispositivo[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Haga clic en **[!UICONTROL Examinar]** junto al campo **Biblioteca de simulador[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Haga clic en **[!UICONTROL Añadir]** junto al campo **Incluir carpetas[!UICONTROL .]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Añada la carpeta `public` a las incluidas.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   Copie ese archivo en la raíz del proyecto.
1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Actualizar]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Abra el archivo `bar-descriptor.xml` del proyecto.
1. En la parte inferior de la ventana, seleccione la pestaña **[!UICONTROL Activos].**
1. Confirme que la opción **[!UICONTROL (Todas las configuraciones)]** esté seleccionada y, a continuación, haga clic en **[!UICONTROL Añadir archivos], en la sección** Activos] de la ventana.**[!UICONTROL **
   >[!TIP]
   >
   >Hay un error en el IDE de QNX Momentics que a veces evita que esos botones sean visibles. Si no puede verlos, cambie el tamaño de las ventanas hasta que aparezcan.

1. Click Workspace.****
1. Busque el archivo `ADBMobileConfig.json`**en el proyecto y haga clic en[!UICONTROL Aceptar]**.

La aplicación puede importar las clases e interfaces de la biblioteca `adobeMobileLibrary.jar` mediante `#include <ADBMobile.hpp>`.

## Agregar permisos de aplicación

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

El archivo `ADBMobileConfig.json` contiene opciones de configuración globales del SDK. Debe actualizar una serie de valores para empezar.

Esto es un ejemplo de archivo `ADBMobileConfig.json`:

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

You must at least update the `rsids` and `server` parameters. Para obtener más información, consulte Referencia [](/help/blackberry/methods.md)de clases y métodos de Adobe Mobile.

Ya puede implementar Analytics en su aplicación de BlackBerry 10.
