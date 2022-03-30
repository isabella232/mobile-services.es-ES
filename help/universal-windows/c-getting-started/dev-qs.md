---
description: Información sobre cómo implementar la biblioteca de la Plataforma universal de Windows.
solution: Experience Cloud Services,Analytics
title: Inicio rápido para desarrolladores
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# Inicio rápido para desarrolladores{#developer-quick-start}

A continuación encontrará información sobre cómo implementar la biblioteca de la Plataforma universal de Windows.

>[!IMPORTANT]
>
>Para implementar el SDK, necesita Visual Studio 2013 o posterior.

## Obtención del SDK   {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir el [Descarga de SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) tendrá una carpeta independiente para cada combinación admitida de arquitectura y plataforma. También tendrá un `ADBMobileConfig.json` archivo. Para obtener más información sobre este archivo, consulte [Archivo de configuración ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Seleccione la versión correcta {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` se proporcionan archivos para cada arquitectura admitida (x86, x64, ARM).

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. La variable `.winmd` contiene solo metadatos y tiene un número de versión `255.255.255.255`, que es un comportamiento aceptado de acuerdo con Microsoft. Para obtener más información, consulte [¿Cómo puedo agregar información de ensamblaje para un archivo dll de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión de la `ADBMobile.dll` archivo.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca de la Plataforma universal de Windows se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía se encuentran en WinJS (JavaScript); si utiliza un idioma diferente, puede que sea necesario modificarlos. Cuando consume métodos winmd desde winJS, la primera letra de todos los métodos se hace minúscula automáticamente.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto. Además, cuando utilice el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Añadir la biblioteca y el archivo de configuración a su proyecto - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccione la versión correcta* en esta página.

1. Haga clic en **Agregar**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la variable **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL OK]**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Si también tiene un proyecto C++ en la solución, omita este paso.

1. En el **[!UICONTROL Windows]** a la izquierda, seleccione **[!UICONTROL Extensiones]**, seleccione y agregue **[!UICONTROL Tiempo de ejecución de Visual C++ 2015 para aplicaciones de la Plataforma universal de Windows]**.

1. Agregue la siguiente línea a la clase:

   ```csharp
   using ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y, a continuación, haga clic en **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a la `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambiar **[!UICONTROL Acción de compilación]** a **[!UICONTROL Contenido]**.

## Agregar la biblioteca y el archivo de configuración al proyecto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho del ratón en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y añada una referencia al archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccione la versión correcta* en esta página.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` está marcado en la variable **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL OK]**.

1. Agregue la siguiente línea a la clase:

   ```c++
   using namespace ADBMobile;
   ```

1. Haga clic con el botón derecho del ratón en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. En el **[!UICONTROL General]** pestaña, cambiar **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL OK]**.

## Agregar la biblioteca y el archivo de configuración a su proyecto: WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la variable **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL OK]**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Si también tiene un proyecto C++ en la solución, omita este paso.

1. En el **[!UICONTROL Windows]** a la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue **[!UICONTROL Tiempo de ejecución de Visual C++ 2015 para aplicaciones de la Plataforma universal de Windows]**.

1. Haga clic con el botón derecho del ratón en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a la `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. con **[!UICONTROL Propiedades del archivo]** seleccionado, asegúrese **[!UICONTROL Acción del paquete]** está configurado como **[!UICONTROL Contenido]**.

   Para los proyectos JavaScript, el archivo se establece en Contenido de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

La variable `ADBMobileConfig.json` contiene la configuración global de SDK y se encuentra en la raíz del proyecto después de completar los pasos del *Agregar la biblioteca y el archivo de configuración al proyecto* para obtener más información. Si su `ADBMobileConfig.json` Adobe Mobile Services no lo preconfiguró, por lo que deberá actualizar algunos valores para comenzar.

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

Para habilitar la depuración para el SDK, llame a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones C Sharp y JavaScript, debe habilitar la depuración de código nativa completando los siguientes pasos (la depuración de código nativa es la configuración predeterminada para las aplicaciones C++):

### C

1. Haga clic con el botón derecho en el proyecto y haga clic en  **[!UICONTROL Propiedades]** > **[!UICONTROL Ficha Depuración]**.

1. Cambie la lista desplegable de tipo depurador a **Solo nativo**.

### JavaScript

1. Haga clic con el botón derecho en el proyecto y haga clic en **[!UICONTROL Propiedades]** > **[!UICONTROL Propiedades de configuración]** > **[!UICONTROL Ficha Depuración]**.

1. Cambie la lista desplegable de tipo depurador a **[!UICONTROL Solo nativo]**.

¡Ya está! Ya está listo para implementar Analytics, Target y Gestión de público en la aplicación de la Plataforma universal de Windows.
