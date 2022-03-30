---
description: Artículo de inicio rápido para desarrolladores
solution: Experience Cloud Services,Analytics
title: Inicio rápido para desarrolladores
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Inicio rápido para desarrolladores {#developer-quick-start}

Necesitará Visual Studio 2013 o posterior para implementar el SDK.

## Obtención del SDK   {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir el [Descarga de SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), tendrá una carpeta independiente para cada combinación de arquitectura y plataforma admitida. También tendrá un `ADBMobileConfig.json` que se explica más adelante en esta guía.

## Seleccione la versión correcta {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` se proporcionan archivos para cada plataforma de destino (Windows 8.1, Windows Phone 8.1) y arquitectura compatible (x86, x64, ARM). Los archivos se separan en una estructura de carpetas según lo siguiente:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. La variable `.winmd` contiene solo metadatos y, como tal, tendrá un número de versión de `255.255.255.255` que es un comportamiento aceptado de acuerdo con Microsoft (consulte [¿Cómo puedo agregar información de ensamblaje para un archivo dll de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión de la `ADBMobile.dll` archivo.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca Universal App Store para Windows 8.1 se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía están en WinJS (JavaScript) y es posible que deban modificarse si utiliza un idioma distinto. Tenga en cuenta que cuando consume métodos winmd desde winJS (JavaScript), la primera letra de todos los métodos se hace minúscula automáticamente.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto.

Además, cuando utilice el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Agregar la biblioteca y el archivo de configuración al proyecto: C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el **Explorador de soluciones**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque las `ADBMobile.winmd` archivo.

   Para obtener más información, consulte la *Seleccione la versión correcta* a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` se selecciona en la variable **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Omita este paso si también tiene un proyecto C++ en la solución.

1. En el **Windows** a la izquierda, seleccione **[!UICONTROL Extensiones]** y, a continuación, seleccione y agregue **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Agregue la siguiente línea a la clase:

   ```
   using ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a su `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambiar **[!UICONTROL Acción de compilación]** a **[!UICONTROL Contenido]**.

## Agregar la biblioteca y el archivo de configuración al proyecto - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho del ratón en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y, a continuación, agregue una referencia a la `ADBMobile.winmd` archivo.

   Para obtener más información, consulte la *Seleccione la versión correcta* a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. En el **[!UICONTROL Administrador de referencias]** , compruebe que `ADBMobile.winmd` está seleccionado y haga clic en **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. Agregue la siguiente línea a la clase:

   ```
   using namespace ADMS::Measurement;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a la `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. En el **[!UICONTROL General]** pestaña, cambiar **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL OK]**.

## Agregar la biblioteca y el archivo de configuración a su proyecto: WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.
1. En el **Explorador de soluciones**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Para obtener más información, consulte *Seleccione la versión correcta* a continuación.

1. Seleccione la versión correcta de la biblioteca y, a continuación, busque la `ADBMobile.winmd` archivo.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` está marcado en la variable **[!UICONTROL Administrador de referencias]** y haga clic en **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionar `ADBMobile.winmd`, cambie el filtro de archivo predeterminado de **[!UICONTROL Archivos de componente]** a **Todos los archivos**.

1. En el **[!UICONTROL Explorador de soluciones]**, haga clic con el botón derecho **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Agregar referencia]**.

   Omita este paso si también tiene un proyecto C++ en la solución.

1. En el **[!UICONTROL Windows]** a la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Haga clic con el botón derecho del ratón en el proyecto y seleccione **[!UICONTROL Agregar]** > **[!UICONTROL Elemento existente]**.

1. Vaya a la `ADBMobileConfig.json` y haga clic en **[!UICONTROL Agregar]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json]` en la solución y seleccione **[!UICONTROL Propiedades]**.

1. con **[!UICONTROL Propiedades del archivo]** seleccionado, asegúrese **[!UICONTROL Acción del paquete]** está configurado como **[!UICONTROL Contenido]**.

   Para proyectos JavaScript, el archivo se establece en **[!UICONTROL Contenido]** de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

La variable `ADBMobileConfig.json` contiene la configuración global de SDK y se encuentra en la raíz del proyecto después de completar los pasos del *Agregar la biblioteca y el archivo de configuración a su proyecto* para obtener más información. Si su `ADBMobileConfig.json` Adobe Mobile Services no lo preconfiguró, por lo que deberá actualizar algunos valores para comenzar.

El siguiente es un ejemplo de `ADBMobileConfig.json` archivo:

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

* **Analytics**: `rsids` y `server`
* **Target**: `clientCode`
* **Audience Manager**: `server`

Para obtener más información, consulte [Configuración de ADBMobileConfig.json](/help/windows-appstore/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Cuando desea habilitar la depuración para el SDK, debe llamar a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones C Sharp y JS, debe habilitar la depuración de código nativa completando los siguientes pasos (la depuración de código nativa es la configuración predeterminada para las aplicaciones C++):

### C

Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Propiedades]** > **[!UICONTROL Ficha Depuración]**. En la lista desplegable Debugger , seleccione **[!UICONTROL Solo nativo]**.

### JS

Haga clic con el botón derecho en el proyecto y seleccione  **[!UICONTROL Propiedades]** > **[!UICONTROL Propiedades de configuración]** > **[!UICONTROL Ficha Depuración]**. Cambie la lista desplegable de tipo depurador a **Solo nativo**.

¡Ya está! Ya está listo para implementar Analytics, Target y Gestión de público en su aplicación Universal App Store para Windows 8.1.
