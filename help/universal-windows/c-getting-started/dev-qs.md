---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Marketing Cloud, Analytics
title: Inicio rápido para desarrolladores
topic: Desarrollador e implementación
uuid: 11 c 06 fcf-d 5 e 4-4858-9 a 4 e -3 bf 66 cdd 2 a 48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Aquí tiene información sobre cómo implementar la biblioteca de la Plataforma universal de Windows.

>[!IMPORTANT]
>
>Para implementar el SDK, necesita Visual Studio 2013 o posterior.

## Obtención del SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. También tendrá un `ADBMobileConfig.json` archivo. Para obtener más información sobre este archivo, consulte [Archivo de configuración adbmobileconfig. json](/help/universal-windows/c-configuration/c.json.md).

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` El archivo solo contiene metadatos y tiene un número de versión de `255.255.255.255`, que se acepta de acuerdo con Microsoft. Para obtener más información, consulte [¿Cómo agrego información de ensamblado para un DLL de componente winrt C + +/CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Diferencias sintácticas {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca de la Plataforma universal de Windows se puede emplear en varios lenguajes de programación. Los ejemplos de esta guía están en winjs (JavaScript) si está utilizando un idioma diferente, es posible que deba modificarse. Cuando consume métodos winmd desde winjs, todos los métodos tienen automáticamente su primera letra minúscula.

La diferencia principal entre las implementaciones radica en la estructura de datos usada para los datos de contexto. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo adbmobile. winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de versión* correcta en esta página.

1. Haga clic en **Agregar**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si también tiene un proyecto de C + + en su solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]**, seleccione y agregue Tiempo de ejecución **[!UICONTROL de Visual C + + 2015 para las aplicaciones de la Plataforma universal de Windows]**.

1. Agregue la siguiente línea a la clase:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en `ADBMobileConfig.json` el archivo de su solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambie **[!UICONTROL Acción de compilación]** a **[!UICONTROL Contenido]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Seleccione la versión correcta de la biblioteca y agregue una referencia al archivo adbmobile. winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de versión* correcta en esta página.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Verifique que `ADBMobile.winmd` esté marcado en la ventana **Administrador de referencias** y haga clic en **[!UICONTROL Aceptar]**.

1. Agregue la siguiente línea a la clase:

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo adbmobile. winmd asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si también tiene un proyecto de C + + en su solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue Tiempo de ejecución **[!UICONTROL de Visual C + + 2015 para las aplicaciones de la Plataforma universal de Windows]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Con las Propiedades **[!UICONTROL de archivo]** seleccionadas, asegúrese de que **[!UICONTROL Acción de paquete]** está configurada en **[!UICONTROL Contenido]**.

   En el caso de proyectos de JavaScript, el archivo se establece en Contenido de forma predeterminada.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` El archivo contiene la configuración global del SDK y se encuentra en la raíz del proyecto después de completar los pasos de *la* sección Agregar la biblioteca y configuración a su proyecto. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

Este es un ejemplo de archivo `ADBMobileConfig.json`:

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

Como mínimo, actualice los siguientes valores para las soluciones que utilice:

* **Adobe Analytics**: `rsids` y `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Para obtener más información, consulte [Métodos SDK](/help/universal-windows/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Para habilitar la depuración para el SDK, realice una llamada `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones C Sharp y JavaScript, debe habilitar la depuración de código nativo completando los pasos siguientes (la depuración de código nativo es la configuración predeterminada para las aplicaciones de C + +):

### C Sharp

1. Haga clic con el botón secundario en el proyecto y haga clic **[!UICONTROL en Propiedades]** &gt; **[!UICONTROL ficha Depuración]**.

1. Cambie el menú desplegable de tipo de depurador a **Solo nativo**.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Cambie el menú desplegable de tipo de depurador a **[!UICONTROL Solo nativo]**.

¡Ya está! Ya está todo listo para implementar Analytics, Target y Gestión de público en la aplicación de la Plataforma universal de Windows.

