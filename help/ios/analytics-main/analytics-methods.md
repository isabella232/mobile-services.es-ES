---
description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.
seo-title: Métodos de Analytics
solution: Marketing Cloud, Analytics
title: Métodos de Analytics
topic: Desarrollador e implementación
uuid: d 49 fe 6 de-cb 32-4 b 96-9891-c 567310 e 59 a 6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de identidad de Adobe Experience Platform. Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página. If `state` is empty, it displays as *app name app version (build)* in reports. If you see this value in reports, ensure you are setting `state` in each `trackState` call.

   >[!TIP]
   >
   >Es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   Realiza el seguimiento de una acción en la aplicación. Las acciones que desea medir, como, y otras `logons``banner taps``feed subscriptions`métricas, se producen en la aplicación.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Recupera el identificador de seguimiento analítico.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   Realiza el seguimiento de una acción que se produjo en segundo plano, lo que impide que se activen eventos de ciclo vital en determinados escenarios.

   >[!TIP]
   >
   >Este método solo debe invocarse en el código que se ejecuta mientras la aplicación está en segundo plano.

   * Esta es la sintaxis para este método:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   Envía las coordenadas x e y actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   Realiza un seguimiento cuando un usuario accede a la proximidad de una señalización.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Borra los datos de señalizaciones una vez el usuario haya abandonado la proximidad de la señalización.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   Inicia una acción temporizada llamada `action`. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   Pasa `data` para actualizar los datos de contexto asociados a `action` en cuestión. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   Finaliza una acción temporizada. If you provide `block`, you will have access to the final time values and be able to manipulate `data` prior to sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Devuelve si la acción temporizada está en progreso o no.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Requiere SDK 4.1. Independientemente de cuántas visitas haya en cola, fuerza a la biblioteca a enviar todas las visitas en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Recupera el número de visitas que hay actualmente en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Borra todas las visitas de la cola sin conexión.

   >[!CAUTION]
   >
   >Tenga cuidado al borrar la cola manualmente. Este proceso no se puede revertir.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Realiza un seguimiento de los clics en un mensaje push.

   >[!IMPORTANT]
   >
   >Este método no incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
