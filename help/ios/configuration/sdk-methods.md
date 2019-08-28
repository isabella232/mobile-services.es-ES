---
description: Esta es una lista de métodos que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos que proporciona la biblioteca iOS.
seo-title: Métodos de configuración
solution: Marketing Cloud, Analytics
title: Métodos de configuración
topic: Desarrollador e implementación
uuid: 623 c 7 b 07-fbb 3-4 d 39-a 5 c 4-e 64 faec 4 ca 29
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuration methods {#configuration-methods}

Esta es una lista de métodos que proporciona la biblioteca iOS.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de identidad de Adobe Experience Platform.

* **setAppExtensionType**

   Configura el SDK de Adobe Mobile para determinar qué clase de extensión se está ejecutando.

   Establezca uno de los siguientes valores:
   * `ADBMobileAppExtensionTypeRegular` - la extensión se incluye con una aplicación contenedora.
   * `ADBMobileAppExtensionTypeStandAlone` - la extensión no está empaquetada con una aplicación contenedora.
   >[!TIP]
   >
   >This method should **only** be used if your app has an extension or is a stand-alone extension. For more information, see *ADBMobileAppExtensionType* below.

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

   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` - si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.
El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* Método **setPrivacyStatus**

   Sets the privacy status for the current user to `status`.

   Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` - si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.

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

   Devuelve el identificador de visitante generado automáticamente. Se trata de un identificador de visitante exclusivo y específico para la aplicación que generan los servidores de Adobe. Si los servidores de Adobe no están disponibles en el momento de la generación, el ID se genera empleando el CFUUID de Apple. El valor se genera durante el primer inicio y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación, se guarda y se restaura durante el proceso estándar de copia de seguridad de la aplicación y se elimina al desinstalarla.

   >[!TIP]
   >
   >Si la aplicación se actualiza de Experience Cloud 3. x al SDK 4. x, el ID de visitante previo personalizado o generado automáticamente se recupera y se almacena como identificador de usuario personalizado. Para obtener más información, consulte abajo la fila `userIdentifier`. Esto preserva los datos de visitante al actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario tiene el valor `nil` y se utiliza el identificador de seguimiento.

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
   >Si la aplicación se actualiza del SDK 3. x al 4. x de Experience Cloud, el ID de visitante previo personalizado o generado automáticamente se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK.

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
   >Este método está pensado para utilizarse en aplicaciones que realizan un registro de notificaciones mientras se encuentran en segundo plano y solo debería invocarse desde el código que se ejecuta mientras la aplicación está en segundo plano.

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
   >The preferred location to invoke this method is in `application:didFinishLaunchingWithOptions:`.

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

   Se debe llamar a este método desde el punto de entrada de la aplicación. Where applicable, this may include one or both of the methods `application:didFinishLaunchingWithOptions:` and/or `applicationWillEnterForeground:` in your AppDelegate class.

   >[!IMPORTANT]
   >
   >Data that is passed to the SDK via `collectLifecycleDataWithAdditionalData:` will be persisted by the SDK in `NSUserDefaults`. El SDK elimina cualquier valor del parámetro `NSDictionary` que no sea del tipo `NSString` o `NSNumber`. To use  `collectLifecycleDataWithAdditionalData:`, you must have SDK **version 4.4** or later.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **overrideConfigPath**

   Le permite cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación. Se utiliza la configuración distinta hasta que se cierre la aplicación.

   >[!IMPORTANT]
   >
   >To use `overrideConfigPath`, you must have SDK version 4.2 or later.

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
   >This method should only be used in the  `application:didRegisterForRemoteNotificationsWithDeviceToken:` method.

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

   Establece el IDFA en el SDK. Si el IDFA se ha establecido en el SDK, el IDFA se enviará en el ciclo vital. También se puede acceder a él en Señales (Postbacks).

   >[!TIP]
   >
   >Retrieve the IDFA from Apple APIs **only** if you are using an ad service. Si recupera el IDFA y no lo utiliza de forma apropiada, podría rechazarse la aplicación.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
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

