---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Experience Cloud,Analytics
title: Inicio rápido para desarrolladores
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---

# Inicio rápido para desarrolladores {#developer-quick-start}

Necesitará Visual Studio 2013 o posterior para implementar el SDK.

## Obtención del SDK   {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir la [descarga del SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), tendrá una carpeta independiente para cada combinación compatible de arquitectura y plataforma. También tendrá un archivo `ADBMobileConfig.json` que se explica más adelante en esta guía.

## Seleccione la versión correcta {#section_E53C5AA7D5474824A89BB32C003865A1}

Se proporcionan diferentes archivos `.dll`/ `.winmd` para cada plataforma de destino (Windows 8.1, Windows Phone 8.1) y arquitectura compatible (x86, x64, ARM). Los archivos se separan en una estructura de carpetas según lo siguiente:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. El archivo `.winmd` solo contiene metadatos y, como tal, tendrá un número de versión de `255.255.255.255` que es comportamiento aceptado según Microsoft (consulte [¿Cómo puedo agregar información de ensamblado para un archivo dll de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión del archivo `ADBMobile.dll` subyacente.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca Universal App Store para Windows 8.1 se puede usar en varios lenguajes de programación. Los ejemplos de esta guía están en WinJS (JavaScript) y es posible que deban modificarse si utiliza un idioma distinto. Tenga en cuenta que cuando consume métodos winmd desde winJS (JavaScript), la primera letra de todos los métodos se hace minúscula automáticamente.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto.

Además, cuando utilice el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Agregar la biblioteca y el archivo de configuración al proyecto - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el archivo `ADBMobile.winmd` asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión correcta* a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` esté seleccionado en la ventana **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL Aceptar]**.

   >[!NOTE]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Omita este paso si también tiene un proyecto C++ en la solución.

1. En la ficha **Windows** de la izquierda, seleccione **[!UICONTROL Extensiones]** y, a continuación, seleccione y añada **[!UICONTROL Paquete de tiempo de ejecución de Microsoft Visual C++ 2013 para Windows]**.

1. Agregue la siguiente línea a la clase:

   ```
   using ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json` de la solución y seleccione **[!UICONTROL Properties]**.

1. Cambie **[!UICONTROL Acción de compilación]** por **[!UICONTROL Contenido]**.

## Agregar la biblioteca y el archivo de configuración al proyecto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y, a continuación, agregue una referencia al archivo `ADBMobile.winmd` asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión correcta* a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. En la ventana **[!UICONTROL Reference Manager]**, verifique que `ADBMobile.winmd` esté seleccionado y haga clic en **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. Agregue la siguiente línea a la clase:

   ```
   using namespace ADMS::Measurement;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json` de la solución y seleccione **[!UICONTROL Properties]**.

1. En la pestaña **[!UICONTROL General]**, cambie **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL Aceptar]**.

## Agregar la biblioteca y el archivo de configuración a su proyecto: WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.
1. En el **Explorador de soluciones**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Para obtener más información, consulte la sección *Seleccionar la versión correcta* a continuación.

1. Seleccione la versión correcta de la biblioteca y, a continuación, busque el archivo `ADBMobile.winmd` asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` esté marcado en la ventana **[!UICONTROL Reference Manager]** y haga clic en **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Omita este paso si también tiene un proyecto C++ en la solución.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y añada **[!UICONTROL Paquete de tiempo de ejecución de Microsoft Visual C++ 2013 para Windows]**.

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Vaya al archivo `ADBMobileConfig.json` y haga clic en **[!UICONTROL Add]**.

1. Haga clic con el botón derecho en el archivo `ADBMobileConfig.json]` de la solución y seleccione **[!UICONTROL Properties]**.

1. Con **[!UICONTROL Propiedades del archivo]** seleccionado, asegúrese de que **[!UICONTROL Acción del paquete]** esté configurado como **[!UICONTROL Contenido]**.

   Para los proyectos JavaScript, el archivo se establece en **[!UICONTROL Content]** de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

El archivo `ADBMobileConfig.json` contiene la configuración global del SDK y se encuentra en la raíz del proyecto después de completar los pasos de la sección *Agregar la biblioteca y el archivo de configuración a su proyecto*. Si Adobe Mobile Services no ha preconfigurado el archivo `ADBMobileConfig.json`, debe actualizar algunos valores para empezar.

El siguiente es un ejemplo de archivo `ADBMobileConfig.json`:

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

* **Analytics**:  `rsids` y  `server`
* **Target**: `clientCode`
* **Audience Manager**: `server`

Para obtener más información, consulte [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Cuando desea habilitar la depuración para el SDK, debe llamar a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones C Sharp y JS, debe habilitar la depuración de código nativa completando los siguientes pasos (la depuración de código nativa es la configuración predeterminada para las aplicaciones C++):

### C

Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**. En la lista desplegable del depurador, seleccione **[!UICONTROL Solo nativo]**.

### JS

Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**. Cambie la lista desplegable de tipo depurador a **Solo nativo**.

¡Ya está! Ya está listo para implementar Analytics, Target y Gestión de público en su aplicación Universal App Store para Windows 8.1.
