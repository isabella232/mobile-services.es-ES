---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Marketing Cloud,Analytics
title: Inicio rápido para desarrolladores
topic: Desarrollador e implementación
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

Necesitará Visual Studio 2013 o posterior para implementar el SDK.

## Obtención del SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir la [descarga del SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), tendrá una carpeta independiente para cada combinación compatible de arquitectura y plataforma. También tendrá un archivo `ADBMobileConfig.json` que se explica más adelante en esta guía.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). Estos archivos se organizan en una estructura de carpetas del siguiente modo:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca Universal App Store para Windows 8.1 se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía corresponden a WinJS (JavaScript) y puede que deban modificarse si emplea un lenguaje distinto. Tenga en cuenta que, cuando consume métodos winmd desde winJS (JavaScript), la primera letra de todos los métodos se hace minúscula automáticamente.

La diferencia principal entre las implementaciones radica en la estructura de datos usada para los datos de contexto.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UIUCONTROL Agregar referencia]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   Para obtener más información, consulte la sección *Seleccionar la versión* correcta a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Omita este paso si también tiene un proyecto de C++ en la solución.

1. En la ficha **Windows** de la izquierda, seleccione **[!UICONTROL Extensiones]** y, a continuación, seleccione y agregue Paquete de tiempo de ejecución de **[!UICONTROL Microsoft Visual C++ 2013 para Windows]**.

1. Agregue la siguiente línea a la clase:

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Agregar]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Cambie **[!UICONTROL Acción de compilación]** a **[!UICONTROL Contenido]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   Para obtener más información, consulte la sección *Seleccionar la versión* correcta a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. En la ventana Administrador **[!UICONTROL de]** referencias, verifique que `ADBMobile.winmd` esté seleccionado y haga clic en **[!UICONTROL Aceptar]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. Agregue la siguiente línea a la clase:

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   Para obtener más información, consulte *Seleccionar la sección Versión* correcta más abajo.

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Verifique que `ADBMobile.winmd` esté marcado en la ventana **Administrador de referencias** y haga clic en **[!UICONTROL Aceptar]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Omita este paso si también tiene un proyecto de C++ en la solución.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue Paquete de tiempo de ejecución de **[!UICONTROL Microsoft Visual C++ 2013 para Windows]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. Una vez seleccionadas las propiedades **** del archivo, asegúrese de que la acción **[!UICONTROL de]** paquete está establecida en **[!UICONTROL Contenido]**.

   Para proyectos JavaScript, el archivo se establece en **[!UICONTROL Contenido]** de forma predeterminada.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

Esto es un ejemplo de archivo `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Como mínimo, actualice los siguientes valores en función de las soluciones que utilice:

* **Analytics**: `rsids` y `server`
* **Target**: `clientCode`
* **Gestión de público**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Cuando quiera activar la depuración para el SDK, tendrá que realizar una llamada a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones de C Sharp y JS, debe activar la depuración de código nativo completando los siguientes pasos (la depuración de código nativo es la configuración predeterminada para las aplicaciones de C++):

### C

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. En la lista desplegable del depurador, seleccione Solo **[!UICONTROL nativo]**.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. Cambie el menú desplegable de tipo de depurador a **Solo nativo**.

¡Ya está! Ya está preparado para implementar Analytics, Target y Gestión de público en su aplicación Universal App Store para Windows 8.1.
