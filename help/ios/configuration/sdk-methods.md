---
description: Esta es una lista de métodos que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos que proporciona la biblioteca iOS.
seo-title: Métodos de configuración
solution: Experience Cloud,Analytics
title: Métodos de configuración
topic: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 100%

---


# Métodos de configuración {#configuration-methods}

Esta es una lista de métodos que proporciona la biblioteca iOS.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform.

* **setAppExtensionType**

   Configura los ajustes del SDK de Adobe Mobile para determinar qué tipo de extensión se está ejecutando.

   Establezca uno de los siguientes valores:
   * `ADBMobileAppExtensionTypeRegular`: La extensión está empaquetada con una aplicación contenedora.
   * `ADBMobileAppExtensionTypeStandAlone`: La extensión no está empaquetada con una aplicación contenedora.

   >[!TIP]
   >
   >Este método **solo** debe usarse si la aplicación tiene una extensión o es una extensión independiente. Para obtener más información, consulte *ADBMobileAppExtensionType*, más adelante.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Devuelve la versión actual de la biblioteca de Adobe Mobile.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(NSString*) version;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual:

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.
El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Establece el estado de privacidad del usuario actual como `status`.

   Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es `0`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Devuelve el identificador de visitante generado automáticamente. Se trata de un ID de visitante exclusivo y específico para la aplicación que generan los servidores de Adobe. Si no se puede acceder a los servidores de Adobe en el momento de la generación, el ID se genera mediante la CFUUID de Apple. El valor se genera en el primer inicio y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación, se guarda y se restaura durante el proceso de copia de seguridad de la aplicación estándar y se elimina al desinstalar.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. Para obtener más información, consulte abajo la fila `userIdentifier`. Esto preserva los datos de visitante al actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario tiene el valor `nil` y se utiliza el identificador de seguimiento.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Si se ha establecido un identificador personalizado, se devuelve el identificador de usuario. Si no se ha definido un identificador personalizado, se devuelve `nil`. El valor predeterminado es `nil`.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK.

   Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es `nil` hasta que se establece.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Establece el identificador de usuario como `identifier`.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `NO`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Establece la preferencia de registro de depuración en `debug`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Indica al SDK que la siguiente reanudación desde segundo plano no debe iniciar una nueva sesión, independientemente del valor del tiempo de espera de sesión del ciclo vital en el archivo de configuración.

   >[!TIP]
   >
   >El propósito de este método es que se utilice en aplicaciones que realizan un registro de notificaciones mientras se encuentran en segundo plano, y solo debería invocarse desde el código que se está ejecutando cuando la aplicación está en segundo plano.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

   >[!TIP]
   >
   >La ubicación preferida para invocar este método es `application:didFinishLaunchingWithOptions:`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Le permite pasar datos adicionales al recopilar métricas del ciclo vital.

   Se debe llamar a este método desde el punto de entrada de la aplicación. Donde sea aplicable, esto puede incluir en su clase AppDelegate uno de estos dos métodos, o ambos: `application:didFinishLaunchingWithOptions:` o `applicationWillEnterForeground:`.

   >[!IMPORTANT]
   >
   >Los datos pasados al SDK mediante `collectLifecycleDataWithAdditionalData:`: serán guardados por el SDK en `NSUserDefaults`. El SDK elimina cualquier valor del parámetro `NSDictionary` que no sea del tipo `NSString` o `NSNumber`. Para utilizar `collectLifecycleDataWithAdditionalData:` necesita la **versión 4.4 o posterior del SDK**.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Utilice esta API para pausar la recopilación de datos del ciclo vital. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

   >[!IMPORTANT]
   >
   >En el método delegado `applicationDidEnterBackground` primero debe invocar el método `pauseCollectingLifecycleData`.
   >
   >La API se proporciona para mitigar el problema en dispositivos iPhone 7/7s o anteriores con iOS 13, donde la métrica de duración de la sesión se volvió anormal. Esto se debe a algunos cambios desconocidos que se han producido en iOS 13, en los que iOS no deja tiempo suficiente para que la tarea en segundo plano finalice cuando no se utiliza la aplicación en primer plano.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Le permite cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación. Se utiliza la configuración distinta hasta que se cierre la aplicación.

   >[!IMPORTANT]
   >
   >Para utilizar `overrideConfigPath` necesita la versión 4.2 o posterior del SDK.

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Establece el token del dispositivo para notificaciones push.

   >[!IMPORTANT]
   >
   >Este método solo debe utilizarse en el método `application:didRegisterForRemoteNotificationsWithDeviceToken:`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Establece el IDFA en el SDK. Si el IDFA se ha establecido en el SDK, el IDFA se enviará en el ciclo vital. También se puede acceder en Señales (Postbacks).

   >[!TIP]
   >
   >Recupere el IDFA desde las API de Apple **solo** si está utilizando un servicio publicitario. Si recupera el IDFA y no lo utiliza de forma apropiada, podría rechazarse la aplicación.
   >
   >Si la aplicación requiere IDFA, consulte la [documentación de Apple](https://developer.apple.com/documentation/adsupport) para averiguar las preferencias del usuario sobre el seguimiento de anuncios y recuperar el valor IDFA.
   >
   >Para iOS 14+, es necesario implementar el nuevo [marco de transparencia de seguimiento de aplicaciones](https://developer.apple.com/documentation/apptrackingtransparency) para recuperar correctamente el valor IDFA.
   * Esta es la sintaxis para este método:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *idfa = // retrieve IDFA using AdSupport (before iOS 14.0) and/or AppTrackingTransparency (iOS 14.0+)
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```

