---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Experience Cloud,Analytics
title: Inicio rápido para desarrolladores
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# Inicio rápido para desarrolladores{#developer-quick-start}

A continuación encontrará información sobre cómo implementar la biblioteca de la Plataforma universal de Windows.

>[!IMPORTANT]
>
>Para implementar el SDK, necesita Visual Studio 2013 o posterior.

## Obtención del SDK   {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir el archivo [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), tendrá una carpeta independiente para cada combinación compatible de arquitectura y plataforma. También tendrá un archivo `ADBMobileConfig.json`. Para obtener más información sobre este archivo, consulte [Archivo de configuración ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Seleccione la versión correcta {#section_E53C5AA7D5474824A89BB32C003865A1}

Se proporcionan diferentes archivos `.dll/.winmd` para cada arquitectura admitida (x86, x64, ARM).

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. El archivo `.winmd` solo contiene metadatos y tiene un número de versión de `255.255.255.255`, que se acepta según Microsoft. Para obtener más información, consulte [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión del archivo `ADBMobile.dll` subyacente.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca de la Plataforma universal de Windows se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía se encuentran en WinJS (JavaScript); si utiliza un idioma diferente, puede que sea necesario modificarlos. Cuando consume métodos winmd desde winJS, la primera letra de todos los métodos se hace minúscula automáticamente.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto. Además, cuando utilice el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Agregar la biblioteca y el archivo de configuración a su proyecto - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión correcta* en esta página.

1. Haga clic en **Agregar**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la ventana **[!UICONTROL Reference Manager]** y haga clic en **[!UICONTROL OK]**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Si también tiene un proyecto C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]**, seleccione y añada **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Agregue la siguiente línea a la clase:

   ```csharp
   using ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y haga clic en **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json` de la solución y seleccione **[!UICONTROL Properties]**.

1. Cambie **[!UICONTROL Acción de compilación]** por **[!UICONTROL Contenido]**.

## Agregar la biblioteca y el archivo de configuración al proyecto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y añada una referencia al archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión correcta* en esta página.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` esté marcado en la ventana **[!UICONTROL Reference Manager]** y haga clic en **[!UICONTROL OK]**.

1. Agregue la siguiente línea a la clase:

   ```c++
   using namespace ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json` de la solución y seleccione **[!UICONTROL Properties]**.

1. En la pestaña **[!UICONTROL General]**, cambie **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL Aceptar]**.

## Agregar la biblioteca y el archivo de configuración a su proyecto: WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la ventana **[!UICONTROL Reference Manager]** y haga clic en **[!UICONTROL OK]**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Si también tiene un proyecto C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y añada **[!UICONTROL Tiempo de ejecución de Visual C++ 2015 para aplicaciones de la Plataforma universal de Windows]**.

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json` de la solución y seleccione **[!UICONTROL Properties]**.

1. Con **[!UICONTROL Propiedades del archivo]** seleccionado, asegúrese de que **[!UICONTROL Acción del paquete]** esté configurado como **[!UICONTROL Contenido]**.

   Para los proyectos JavaScript, el archivo se establece en Contenido de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

El archivo `ADBMobileConfig.json` contiene la configuración global del SDK y se encuentra en la raíz del proyecto después de completar los pasos de la sección *Add the library and config file to your project* . Si Adobe Mobile Services no ha preconfigurado el archivo `ADBMobileConfig.json`, debe actualizar algunos valores para empezar.

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

* **Adobe Analytics**:  `rsids` y  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Para obtener más información, consulte [Métodos SDK](/help/universal-windows/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Para habilitar la depuración para el SDK, llame a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones C Sharp y JavaScript, debe habilitar la depuración de código nativa completando los siguientes pasos (la depuración de código nativa es la configuración predeterminada para las aplicaciones C++):

### C

1. Haga clic con el botón derecho en el proyecto y haga clic en **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**.

1. Cambie la lista desplegable de tipo depurador a **Solo nativo**.

### JavaScript

1. Haga clic con el botón derecho en el proyecto y haga clic en **[!UICONTROL Propiedades]** > **[!UICONTROL Propiedades de configuración]** > **[!UICONTROL pestaña Depuración]**.

1. Cambie la lista desplegable de tipo depurador a **[!UICONTROL Solo nativo]**.

¡Ya está! Ya está listo para implementar Analytics, Target y Gestión de público en la aplicación de la Plataforma universal de Windows.
