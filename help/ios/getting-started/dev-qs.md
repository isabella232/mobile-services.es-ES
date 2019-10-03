---
description: Esta información le ayuda a implementar la biblioteca iOS y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.
seo-description: Esta información le ayuda a implementar la biblioteca iOS y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.
seo-title: Implementación principal y ciclo vital
solution: Marketing Cloud,Analytics
title: Implementación principal y ciclo vital
topic: Desarrollador e implementación
uuid: 96d06325-e424-4770-8659-4b5431318ee3
translation-type: tm+mt
source-git-commit: 4db9781e6e1e75a04d9715a41c5a32c10ede1bf4

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Esta información le ayuda a implementar la biblioteca iOS y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.

## Descargar el SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**Requisitos previos**

Antes de descargar el SDK, complete los pasos en *Crear un grupo* de informes en la implementación [principal y el ciclo vital](/help/ios/getting-started/requirements.md) para configurar un grupo de informes de desarrollo y descargar una versión previamente rellenada del archivo de configuración.

Para descargar el SDK:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`, el archivo de encabezado Objective-C empleado para llamadas iOS AppMeasurement.
   * `ADBMobileConfig.json`, que es el archivo de configuración del SDK personalizado para su aplicación.
   * `AdobeMobileLibrary.a`, un binario multiarquitectura habilitado para código de bits que contiene las compilaciones de biblioteca para los simuladores (i386, x86_64) y dispositivos iOS (armv7, armv7s, arm64).

      Este binario multiarquitectura se debe vincular cuando el destino se dirija a una aplicación iOS.

   * `AdobeMobileLibrary_Extension.a`, un binario multiarquitectura habilitado para código de bits que contiene las compilaciones de biblioteca para los simuladores (i386, x86_64) y dispositivos iOS (armv7, armv7s, arm64).

      Este binario multiarquitectura se debe vincular cuando el destino se dirija a una extensión iOS.

   * `AdobeMobileLibrary_Watch.a`, un binario multiarquitectura habilitado para código de bits que contiene las compilaciones de biblioteca para los simuladores (i386, x86_64) y dispositivos Apple Watch (armv7k).

      Este binario multiarquitectura se debe vincular cuando el destino se dirija a una aplicación de extensión Apple Watch (watchOS 2).

   * `AdobeMobileLibrary_TV.a`, un binario multiarquitectura habilitado para código de bits que contiene las compilaciones de biblioteca para el simulador (x86_64) y los dispositivos Apple TV (arm64) nuevos.

      Este binario multiarquitectura se debe vincular cuando el destino se dirija a una aplicación Apple TV (tvOS).

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Inicie el IDE de Xcode y abra la aplicación.
1. En Navegador de proyectos, arrastre el directorio `AdobeMobileLibrary` y suéltelo debajo de su proyecto.
1. Compruebe lo siguiente:

   * La casilla de verificación **[!UICONTROL Copiar elementos si es necesario]está seleccionada.**
   * **[!UICONTROL Crear grupos]** está seleccionado.
   * Ninguna de las casillas de verificación en la sección **[!UICONTROL Agregar a destinos]está seleccionada.**
   ![](assets/step_3.png)

1. Haga clic en **[!UICONTROL Finalizar]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. Haga clic en su aplicación.
   1. En la ficha **[!UICONTROL General]**, seleccione sus destinos y vincule los marcos y bibliotecas necesarios en las secciones **[!UICONTROL Marcos vinculados]** y bibliotecas **.**
   * **Destinos de aplicaciones iOS**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
      * `CoreLocation.framework` (optional, but required for geo-tracking capabilities)
   * **Extensión iOS Target**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch (watchOS 2) Target**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV (tvOS) Target**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. Confirme que la aplicación se compila sin errores.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

Add a /  call in :`collectLifecycleData``collectLifecycleDataWithAdditionalData``application:didFinishLaunchingWithOptions`

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### Incluir datos adicionales con llamadas al ciclo vital

Para incluir datos adicionales en las llamadas al ciclo vital, utilice `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. El SDK elimina del parámetro `NSDictionary` los valores que no pertenezcan a los tipos `NSString` o `NSNumber`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

El valor de los datos de contexto adicionales que se envían con `collectLifecycleDataWithAdditionalData` debe asignarse a variables personalizadas en Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

Otras métricas del ciclo vital se recopilan automáticamente. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

## Qué hacer a continuación {#section_A24DC703359D4B5C8F493D6421306FD3}

Complete las siguientes tareas:

* [Seguimiento de estados de aplicaciones](/help/ios/analytics-main/states.md)
* [Seguimiento de acciones de aplicaciones](/help/ios/analytics-main/actions.md)
