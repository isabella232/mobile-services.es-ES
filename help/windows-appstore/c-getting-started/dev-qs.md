---
description: 'null'
seo-description: 'null'
seo-title: Inicio rápido para desarrolladores
solution: Experience Cloud,Analytics
title: Inicio rápido para desarrolladores
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---


# Inicio rápido para desarrolladores {#developer-quick-start}

Necesitará Visual Studio 2013 o posterior para implementar el SDK.

## Obtención del SDK   {#section_99FE1A17A36D4A2C943939023CF6265C}

Después de descomprimir la descarga [del](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)SDK, dispondrá de una carpeta independiente para cada combinación de arquitectura y plataforma admitida. También tendrá un `ADBMobileConfig.json` archivo que se explicará más adelante en esta guía.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Se proporcionan diferentes archivos `.dll`/ `.winmd` para cada plataforma de destinatario (Windows 8.1, Windows Phone 8.1) y arquitectura compatible (x86, x64, ARM). Los archivos se separan en una estructura de carpetas de acuerdo con lo siguiente:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>La versión de `ADBMobile.winmd` no refleja la versión de la biblioteca. El `.winmd` archivo solo contiene metadatos y, como tal, tendrá un número de versión `255.255.255.255` cuyo comportamiento aceptado según Microsoft (consulte [¿Cómo agrego información de ensamblado para un archivo DLL de componente WinRT C++ / CX?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Para comprobar la versión de la biblioteca que está utilizando, compruebe la versión del `ADBMobile.dll` archivo subyacente.

## Diferencias de sintaxis {#section_A02DE120B6D240F5AFFE7509755C4F14}

La biblioteca Universal App Store para Windows 8.1 se puede utilizar en varios lenguajes de programación. Los ejemplos de esta guía están en WinJS (JavaScript) y es posible que deban modificarse si utiliza un idioma diferente. Tenga en cuenta que cuando consume métodos winmd de winJS (JavaScript), todos los métodos automáticamente tienen su primera letra minúscula.

La principal diferencia entre las implementaciones es la estructura de datos utilizada para los datos de contexto.

Además, al utilizar el SDK en un proyecto WinJS, utilice una cadena vacía ( `""` o `''`) en lugar de `null` para valores de cadena vacíos.

## Añadir la biblioteca y el archivo de configuración al proyecto: C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie Visual Studio y abra la solución.
1. En el Explorador **de** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

1. Seleccione la versión correcta de la biblioteca y busque el `ADBMobile.winmd` archivo asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión* correcta a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` esté seleccionado en la ventana Administrador **[!UICONTROL de]** referencias y haga clic en **[!UICONTROL Aceptar]**.

   >[!NOTE]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

   Omita este paso si también tiene un proyecto de C++ en la solución.

1. En la ficha **Windows** de la izquierda, seleccione **[!UICONTROL Extensiones]** y, a continuación, seleccione y agregue Paquete de tiempo de ejecución de **[!UICONTROL Microsoft Visual C++ 2013 para Windows]**.

1. Añada la línea siguiente en la clase:

   ```
   using ADBMobile;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > Elemento **** existente.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. Cambie **[!UICONTROL Acción]** de compilación por **[!UICONTROL Contenido]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Inicie Visual Studio y abra la solución.
1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > **[!UICONTROL Referencias]**.

1. Seleccione la versión correcta de la biblioteca y, a continuación, agregue una referencia al `ADBMobile.winmd` archivo asociado.

   Para obtener más información, consulte la sección *Seleccionar la versión* correcta a continuación.

1. Haga clic en **[!UICONTROL Agregar]**.

1. En la ventana Administrador **[!UICONTROL de]** referencias, verifique que `ADBMobile.winmd` esté seleccionado y haga clic en **[!UICONTROL Aceptar]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. Añada la línea siguiente en la clase:

   ```
   using namespace ADMS::Measurement;
   ```

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > Elemento **** existente.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. En la ficha **[!UICONTROL General]** , cambie **[!UICONTROL Contenido]** a **[!UICONTROL Sí]** y haga clic en **[!UICONTROL Aceptar]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Inicie Visual Studio y abra la solución.
1. En el Explorador **de** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

   Para obtener más información, consulte *Seleccionar la sección Versión* correcta más abajo.

1. Seleccione la versión correcta de la biblioteca y, a continuación, busque el `ADBMobile.winmd` archivo asociado.

1. Haga clic en **[!UICONTROL Agregar]**.

1. Compruebe que `ADBMobile.winmd` está marcado en la ventana Administrador **[!UICONTROL de]** referencias y haga clic en **[!UICONTROL Aceptar]**.

   >[!TIP]
   >
   >Al agregar una referencia a una aplicación de Windows Phone, para seleccionarla `ADBMobile.winmd`, cambie el filtro de archivos predeterminado de Archivos **[!UICONTROL de]** componentes a **Todos los archivos**.

1. En el Explorador **[!UICONTROL de]** soluciones, haga clic con el botón derecho en **[!UICONTROL Referencias]** y seleccione **[!UICONTROL Añadir referencia]**.

   Omita este paso si también tiene un proyecto de C++ en la solución.

1. En la ficha **[!UICONTROL Windows]** de la izquierda, seleccione **[!UICONTROL Extensiones]** y seleccione y agregue Paquete de tiempo de ejecución de **[!UICONTROL Microsoft Visual C++ 2013 para Windows]**.

1. Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Añadir]** > Elemento **** existente.

1. Vaya al `ADBMobileConfig.json` archivo y haga clic en **[!UICONTROL Añadir]**.

1. Haga clic con el botón derecho en el `ADBMobileConfig.json]` archivo de la solución y seleccione **[!UICONTROL Propiedades]**.

1. Una vez seleccionadas las propiedades **** del archivo, asegúrese de que la acción **[!UICONTROL de]** paquete está establecida en **[!UICONTROL Contenido]**.

   Para proyectos JavaScript, el archivo se establece en **[!UICONTROL Contenido]** de forma predeterminada.

## Actualizar el archivo de configuración ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

El `ADBMobileConfig.json` archivo contiene la configuración global del SDK y se encuentra en la raíz del proyecto después de completar los pasos en la sección *Añadir la biblioteca y el archivo de configuración a su proyecto* . Si Adobe Mobile Services no ha preconfigurado el `ADBMobileConfig.json` archivo, deberá actualizar algunos valores para empezar.

The following is an example of an `ADBMobileConfig.json` file:

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

* **Analytics**: `rsids` y `server`
* **Target**: `clientCode`
* **Audience Manager**: `server`

Para obtener más información, consulte [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Depuración {#section_3A10376A60394A15BEE483323E0CD4AA}

Cuando desee habilitar la depuración para el SDK, debe llamar a `ADBMobile.Config.setDebugLogging(true);`.

Para las aplicaciones de C Sharp y JS, debe activar la depuración de código nativo completando los siguientes pasos (la depuración de código nativo es la configuración predeterminada para las aplicaciones de C++):

### C Sharp

Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Propiedades]** > ficha **[!UICONTROL Depurar]**. En la lista desplegable del depurador, seleccione Solo **[!UICONTROL nativo]**.

### JS

Haga clic con el botón derecho en el proyecto y seleccione **[!UICONTROL Propiedades]** > Propiedades **** de configuración > ficha **** Depuración. Cambie la lista desplegable de tipo de depurador a Solo **nativo**.

¡Ya está! Ya está listo para implementar Analytics, Destinatario y administración de Audiencias en la aplicación Universal App Store para Windows 8.1.
