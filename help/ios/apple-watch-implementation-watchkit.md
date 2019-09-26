---
description: A partir de WatchOS 2, las extensiones WatchKit se pueden ejecutar en un dispositivo Apple Watch. Las aplicaciones que se ejecutan en este entorno requieren que el marco WatchConnectivity comparta datos con la aplicación iOS contenedora.
seo-description: A partir de WatchOS 2, las extensiones WatchKit se pueden ejecutar en un dispositivo Apple Watch. Las aplicaciones que se ejecutan en este entorno requieren que el marco WatchConnectivity comparta datos con la aplicación iOS contenedora.
seo-title: Implementación de Apple Watch con WatchOS 2
solution: Marketing Cloud,Analytics
title: Implementación de Apple Watch con WatchOS 2
topic: Desarrollador e implementación
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

A partir de WatchOS 2, las extensiones WatchKit se pueden ejecutar en Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>Se admite a partir de `AdobeMobileLibrary` v4.6.0 `WatchConnectivity` .

## Nueva versión del SDK de Adobe Experience Platform Mobile

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Primeros pasos {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Asegúrese de que tiene un proyecto con al menos los siguientes objetivos:
>
>* La aplicación contenedora
>* La aplicación WatchKit
>* La extensión WatchKit
>



Para obtener más información acerca del desarrollo de aplicaciones WatchKit, consulte [La arquitectura de la aplicación Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurar la aplicación contenedora {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Complete los siguientes pasos en su proyecto Xcode:

1. Arrastre la carpeta `AdobeMobileLibrary` a su proyecto.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación contenedora, expanda la sección **Vincular binario con bibliotecas]y agregue las bibliotecas siguientes:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. En la clase que implementa el protocolo `UIApplicationDelegate`, agregue el protocolo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. En el archivo de implementación de la clase delegada de la aplicación, importe `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` is called in the  library, which returns a bool that indicates whether the dictionary was meant for consumption by the  library. `ADBMobile``ADBMobile` Si devuelve el valor `No`, el mensaje no se inició desde el SDK de Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Configuración de la extensión WatchKit {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su extensión WatchKit, expanda la sección **Vincular binario con bibliotecas]y agregue las bibliotecas siguientes:[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. En el archivo de implementación de la clase delegada de la extensión, importe `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. En el método `applicationDidFinishLaunching` del delegado de la extensión, inicialice la aplicación del reloj para el SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` se llama en la `ADBMobile` biblioteca, que devuelve un bool que indica si el diccionario estaba destinado al consumo en la `ADBMobile` biblioteca. Si devuelve el valor `NO`, el mensaje no se inició desde el SDK de Adobe.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Información adicional {#section_7BCDB5CF0D424DCA97883753D1881233}

Recuerde la información siguiente:

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* Como las aplicaciones WatchKit se ejecutan en el reloj, comunican correctamente sus nombres en `a.AppID`.
* En las aplicaciones WatchOS2 no se activa ninguna llamada de ciclo vital.

