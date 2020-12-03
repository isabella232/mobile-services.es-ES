---
description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.
seo-title: Métodos de Analytics
solution: Experience Cloud,Analytics
title: Métodos de Analytics
topic: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 100%

---


# Métodos de Analytics {#analytics-methods}

Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca iOS.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform. Los métodos tienen un prefijo de acuerdo con la solución. Los métodos de Experience Cloud ID llevan el prefijo `track`.

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

* **trackState:&#x200B;data:**

   Los estados son las vistas que están disponibles en la aplicación, como `home dashboard`, `app settings` o `cart`, entre otros. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página. Si `state` está vacío, en los informes se muestra *app name app version (build)*. Si observa este valor en los informes, asegúrese de que está estableciendo un `state` en cada llamada `trackState`.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   Realiza el seguimiento de una acción en la aplicación. Acciones que le interesará medir, como `logons`, `banner taps`, `feed subscriptions` y otras métricas que se producen en la aplicación.

   >[!TIP]
   >
   >Si cuenta con un código que podría estar ejecutándose mientras la aplicación se encuentra en segundo plano (por ejemplo, recuperación de datos en segundo plano), utilice `trackActionFromBackground` en su lugar.

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
   >Este método solo debería invocarse en el código que se ejecuta mientras la aplicación se encuentra en segundo plano.

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

   Pasa `data` para actualizar los datos de contexto asociados a `action` en cuestión. Los `data` que se pasan se anexan a los ya existentes para la acción. Si la misma clave ya está definida para `action`, los datos se sobrescriben.

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

   Finaliza una acción temporizada. Si proporciona un valor para `block`, tendrá acceso a los valores de tiempo finales y podrá manipular los `data` antes de enviar la visita final.

   >[!TIP]
   >
   >Si proporciona `block`, debe devolver `YES` para enviar una visita. Pasar el valor `nil` para `block` envía la visita final.

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

   Requiere SDK 4.1. Independientemente de cuántas visitas haya actualmente en cola, este método obliga a la biblioteca a enviar todas las visitas en la cola sin conexión.

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
   >Tenga cuidado al borrar la cola de forma manual. Este proceso no se puede revertir.

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
   >Este método no incrementa las visualizaciones de página.

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
