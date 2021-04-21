---
description: A partir de WatchOS 2, las extensiones WatchKit se ejecutarán en un dispositivo Apple Watch. Las aplicaciones que se ejecutan en este entorno requieren que el marco WatchConnectivity comparta datos con la aplicación iOS contenedora.
seo-description: A partir de WatchOS 2, las extensiones WatchKit se ejecutarán en un dispositivo Apple Watch. Las aplicaciones que se ejecutan en este entorno requieren que el marco WatchConnectivity comparta datos con la aplicación iOS contenedora.
seo-title: Implementación de Apple Watch con WatchOS 2
solution: Experience Cloud,Analytics
title: Implementación de Apple Watch con WatchOS 2
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 100%

---

# Implementación de Apple Watch con WatchOS 2 {#apple-watch-implementation-with-watchos}

A partir de WatchOS 2, las extensiones WatchKit se pueden ejecutar en un Apple Watch. Las aplicaciones que se ejecutan en este entorno requieren que el marco `WatchConnectivity` comparta datos con la aplicación iOS contenedora.

>[!TIP]
>
>A partir de `AdobeMobileLibrary` 4.6.0, se admite `WatchConnectivity`.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Primeros pasos {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Asegúrese de que tiene un proyecto con al menos los siguientes destinatarios:
>
>* La aplicación contenedora
>* La aplicación WatchKit
>* La extensión de WatchKit
>



Para obtener más información sobre el desarrollo de aplicaciones WatchKit, consulte [La arquitectura de las aplicaciones Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configurar la aplicación contenedora {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Complete los siguientes pasos en su proyecto Xcode:

1. Arrastre la carpeta `AdobeMobileLibrary` a su proyecto.
1. Asegúrese de que el archivo `ADBMobileConfig.json` pertenece al destino de la aplicación contendora.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación contenedora, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

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

1. Antes de realizar una llamada a la biblioteca `ADBMobile`, configure `application:didFinishLaunchingWithOptions:` en el método `WCSession`: del delegado de la aplicación.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. En el delegado de la aplicación, implemente los métodos `session:didReceiveMessage:` y `session:didReceiveUserInfo:`.

   `syncSettings:` recibe una llamada en la biblioteca `ADBMobile` y devuelve un valor booleano que indica si el diccionario estaba destinado al consumo por parte de la biblioteca `ADBMobile`. Si devuelve el valor `No`, el mensaje no se inició desde el SDK de Adobe.

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

1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino de la extensión WatchKit.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su extensión WatchKit, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. En la clase que implementa el protocolo `WKExtensionDelegate`, importe `WatchConnectivity` y agregue el protocolo `WCSessionDelegate`.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. En el archivo de implementación de la clase delegada de la extensión, importe `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. En el método `applicationDidFinishLaunching` del delegado de la extensión, configure `WCSession` antes de realizar ninguna llamada a la biblioteca `ADBMobile`.

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

1. En el delegado de la extensión, implemente los métodos `session:didReceiveMessage:` y `session:didReceiveUserInfo:`.

   `syncSettings:` recibe una llamada en la biblioteca `ADBMobile` y devuelve un valor booleano que indica si el diccionario estaba destinado al consumo por parte de la biblioteca `ADBMobile`. Si devuelve el valor `NO`, el mensaje no se inició desde el SDK de Adobe.

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

* Para aplicaciones WatchKit, `a.RunMode` se establece en `Extension`.
* Como las aplicaciones WatchKit se ejecutan en el reloj, comunican correctamente sus nombres en `a.AppID`.
* En las aplicaciones WatchOS2 no se activa ninguna llamada de ciclo vital.
