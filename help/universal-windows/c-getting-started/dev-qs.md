---
description: 'null'
seo-description: 'null'
seo-title: Developer quick start
solution: Marketing Cloud,Analytics
title: Developer quick start
topic: Desarrollador e implementación
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

A continuación encontrará información sobre cómo implementar la biblioteca de la Plataforma universal de Windows.

>[!IMPORTANT]
>
>Para implementar el SDK, necesita Visual Studio 2013 o posterior.

## Obtención del SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. También tendrá un `ADBMobileConfig.json` archivo. Para obtener más información sobre este archivo, consulte [Archivo](/help/universal-windows/c-configuration/c.json.md)de configuración ADBMobileConfig.json.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. El `.winmd` archivo solo contiene metadatos y tiene un número de versión de `255.255.255.255`, que es un comportamiento aceptado según Microsoft. Para obtener más información, consulte [¿Cómo agrego información de ensamblado para un archivo DLL de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Diferencias sintácticas {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca de la Plataforma universal de Windows se puede emplear en varios lenguajes de programación. Los ejemplos de esta guía están en WinJS (JavaScript), si utiliza un lenguaje diferente, puede que sea necesario modificarlos. When you consume winmd methods from winJS, all methods automatically have their first letter lowercased.

La diferencia principal entre las implementaciones radica en la estructura de datos usada para los datos de contexto. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de la versión* correcta en esta página.

1. Haga clic en **Agregar**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si también tiene un proyecto de C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]**, seleccione y agregue Tiempo de ejecución de **[!UICONTROL Visual C++ 2015 para aplicaciones]** de la Plataforma universal de Windows.

1. Agregue la siguiente línea a la clase:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambie **[!UICONTROL Acción de compilación]** a **[!UICONTROL Contenido]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Seleccione la versión correcta de la biblioteca y agregue una referencia al archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de la versión* correcta en esta página.

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

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Si también tiene un proyecto de C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue Tiempo de ejecución de **[!UICONTROL Visual C++ 2015 para aplicaciones]** de la Plataforma universal de Windows.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Una vez seleccionadas las propiedades **** del archivo, asegúrese de que la acción **[!UICONTROL de]** paquete está establecida en **[!UICONTROL Contenido]**.

   Para proyectos JavaScript, el archivo se establece en Contenido de forma predeterminada.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

Como mínimo, actualice los siguientes valores para las soluciones que está utilizando:

* **Adobe Analytics**: `rsids` y `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Para obtener más información, consulte Métodos [SDK](/help/universal-windows/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Para habilitar la depuración para el SDK, llame `ADBMobile.Config.setDebugLogging(true);`.

For C Sharp and JavaScript apps, you need to enable native code debugging by completing the following steps (native code debugging is the default setting for C++ apps):

### C

1. Right-click the project, click  Properties &gt; Debug tab.********

1. Cambie el menú desplegable de tipo de depurador a **Solo nativo**.

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Cambie el menú desplegable de tipo de depurador a **[!UICONTROL Solo nativo]**.

¡Ya está! Ya está todo listo para implementar Analytics, Target y Gestión de público en la aplicación de la Plataforma universal de Windows.

