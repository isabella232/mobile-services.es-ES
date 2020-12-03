---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Experience Cloud,Analytics
title: Inicio rápido para desarrolladores
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
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

Después de descomprimir el archivo de descarga [del](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) SDK, dispondrá de una carpeta independiente para cada combinación de arquitectura y plataforma admitida. También tendrá un `ADBMobileConfig.json` archivo. Para obtener más información sobre este archivo, consulte [Archivo](/help/universal-windows/c-configuration/c.json.md)de configuración ADBMobileConfig.json.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Se proporcionan diferentes `.dll/.winmd` archivos para cada arquitectura admitida (x86, x64, ARM).

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. El `.winmd` archivo solo contiene metadatos y tiene un número de versión de `255.255.255.255`, que es un comportamiento aceptado según Microsoft. Para obtener más información, consulte [¿Cómo agrego información de ensamblado para un archivo DLL de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión del `ADBMobile.dll` archivo subyacente.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca de la Plataforma universal de Windows se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía están en WinJS (JavaScript), si utiliza un lenguaje diferente, puede que sea necesario modificarlos. Cuando se consumen métodos winmd de winJS, se reduce automáticamente la primera letra de todos los métodos.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto. Además, al utilizar el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de la versión* correcta en esta página.

1. Haga clic en **Agregar**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la ventana Administrador **[!UICONTROL de]** referencias y haga clic en **[!UICONTROL Aceptar]**.

1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

   Si también tiene un proyecto de C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]**, seleccione y agregue Tiempo de ejecución de **[!UICONTROL Visual C++ 2015 para aplicaciones]** de la Plataforma universal de Windows.

1. Añada la línea siguiente en la clase:

   ```csharp
   using ADBMobile;
   ```

1. Haga clic con el botón secundario en el proyecto y haga clic en **[!UICONTROL Añadir]** > Elemento **** existente.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambie **[!UICONTROL Acción]** de compilación por **[!UICONTROL Contenido]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y agregue una referencia al archivo ADBMobile.winmd asociado.

   Para obtener más información, consulte *Seleccionar la sección de la versión* correcta en esta página.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` está marcado en la ventana Administrador **[!UICONTROL de]** referencias y haga clic en **[!UICONTROL Aceptar]**.

1. Añada la línea siguiente en la clase:

   ```c++
   using namespace ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > Elemento **** existente.

1. Busque `ADBMobileConfig.json` el archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. En la ficha **[!UICONTROL General]** , cambie **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL Aceptar]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.

1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo ADBMobile.winmd asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que el archivo ADBMobile.winmd esté marcado en la ventana Administrador **[!UICONTROL de]** referencias y haga clic en **[!UICONTROL Aceptar]**.

1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

   Si también tiene un proyecto de C++ en la solución, omita este paso.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue Tiempo de ejecución de **[!UICONTROL Visual C++ 2015 para aplicaciones]** de la Plataforma universal de Windows.

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > Elemento **** existente.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. Una vez seleccionadas las propiedades **** del archivo, asegúrese de que la acción **[!UICONTROL de]** paquete está establecida en **[!UICONTROL Contenido]**.

   Para proyectos JavaScript, el archivo se establece en Contenido de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

El `ADBMobileConfig.json` archivo contiene la configuración global del SDK y se encuentra en la raíz del proyecto después de completar los pasos en la sección *Añadir la biblioteca y el archivo de configuración a su proyecto* . Si Adobe Mobile Services no ha preconfigurado el `ADBMobileConfig.json` archivo, deberá actualizar algunos valores para empezar.

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

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Para habilitar la depuración para el SDK, llame a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones de C Sharp y JavaScript, debe activar la depuración de código nativo completando los siguientes pasos (la depuración de código nativo es la configuración predeterminada para las aplicaciones de C++):

### C Sharp

1. Haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **[!UICONTROL Propiedades]** > ficha **[!UICONTROL Depurar]**.

1. Cambie la lista desplegable de tipo de depurador a Solo **nativo**.

### JavaScript

1. Haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **[!UICONTROL Propiedades]** > Propiedades **** de configuración > ficha **** Depuración.

1. Cambie la lista desplegable de tipo de depurador a Solo **[!UICONTROL nativo]**.

¡Ya está! Ya está listo para implementar Analytics, Destinatario y administración de Audiencias en la aplicación de la Plataforma universal de Windows.

