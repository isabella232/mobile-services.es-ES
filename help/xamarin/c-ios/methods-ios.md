---
description: Métodos iOS para el SDK de componentes Xamarin para soluciones Experience Cloud 4.x.
keywords: Xamarin
seo-description: Métodos iOS para el SDK de componentes Xamarin para soluciones Experience Cloud 4.x.
seo-title: Métodos de iOS
solution: Experience Cloud
title: Métodos de iOS
uuid: d6a056db-80c1-44d0-970f-c961ad01b0bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 70%

---


# Métodos de iOS{#ios-methods}

Métodos iOS para el SDK de componentes Xamarin para soluciones Experience Cloud 4.x.

## Métodos de configuración {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **DebugLogging**

   Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `false`.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Establece la preferencia de registro de depuración en enabled.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void SetDebugLogging(bool enabled);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      ```

* **LifetimeValue**

   Devuelve el valor de duración del usuario actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static double LifetimeValue();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue();
      ```

* **PrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.
   * `ADBMobilePrivacyStatus.OptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatus.OptOut`: las visitas se descartarán.
   * ADBMobilePrivacyStatus.Unknown: si el seguimiento sin conexión está activado, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento sin conexión está deshabilitado, las visitas se descartan hasta que el estado de privacidad cambie para adhesión.

   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Esta es la sintaxis para este método:

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var privacyStatus = ADBMobile.PrivacyStatus();
      ```


* **SetPrivacyStatus**

   Establece el estado de privacidad del usuario actual en estado. Establezca uno de los siguientes valores:
   * `ADBMobilePrivacyStatus.OptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatus.OptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatus.Unknown`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Devuelve el identificador de usuario personalizado si se ha establecido un identificador personalizado. Devuelve null si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Devuelve el identificador de usuario personalizado si se ha establecido un identificador personalizado. Devuelve null si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string UserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Obtiene la versión de la biblioteca.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string Version();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (solo iOS)**

   Indica al SDK que la siguiente reanudación desde segundo plano no debe iniciar una nueva sesión, independientemente del valor del tiempo de espera de sesión del ciclo vital en el archivo de configuración.

   >[!TIP]
   >
   >Este método está diseñado para utilizarse en aplicaciones que se registran para recibir notificaciones en segundo plano y solo debe invocarse desde el código que se ejecuta mientras la aplicación está en segundo plano.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void KeepLifecycleSessionAlive();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Métodos de Analytics {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Recupera el identificador de seguimiento analítico.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas disponibles en la aplicación, como &quot;pantalla de título&quot;, &quot;nivel 1&quot;, &quot;pausa&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas incrementan las vistas de página.Si el estado está vacío, se muestra como &quot;nombre de aplicación versión de la aplicación (compilación)&quot; en los informes. `TrackState` If you see this value in reports, make sure you are setting state in each `TrackState` call.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que desea medir, como &quot;muertes&quot;, &quot;nivel ganado&quot;, &quot;suscripciones de fuentes&quot; y otras métricas.

   >[!TIP]
   >
   >Si cuenta con un código que podría estar ejecutándose mientras la aplicación se encuentra en segundo plano (por ejemplo, recuperación de datos en segundo plano), utilice `trackActionFromBackground` en su lugar.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (solo iOS)**

   Rastrea una acción que se produjo en el fondo. Esto evita que los eventos del ciclo vital se activen en determinados escenarios.

   >[!TIP]
   >
   > Este método solo debería invocarse en el código que se ejecuta mientras la aplicación se encuentra en segundo plano.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envía las coordenadas de latitud y longitud actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `TrackLocation`.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Realiza un seguimiento cuando un usuario accede a la proximidad de una señalización.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Borra los datos de señalizaciones una vez el usuario haya abandonado la proximidad de la señalización.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Añade la cantidad al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      public nbsp;static void TrackLifetimeValueIncrease(cantidad de doble, datos NSDictionary);

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Inicia una acción temporizada con acción de nombre. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Pasa datos para actualizar los datos de contexto asociados con la acción determinada. Los datos pasados se anexan a los datos existentes para la acción dada y se sobrescriben si la misma clave ya está definida para action.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Finaliza una acción temporizada.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      });
      ```

* **TrackingTimedActionExists**

   Devuelve si una acción temporizada está (o no) en curso.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Fuerza la biblioteca a enviar todas las visitas en la cola sin conexión, sin importar cuántas haya en la cola.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Borra todas las visitas de la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Recupera el número de visitas que hay actualmente en la cola sin conexión.

   * Este es un ejemplo de código para este método:

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Recupera el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Con el ID de Experience Cloud, puede establecer ID de cliente adicionales para asociarlos a cada visitante. La API de Visitante acepta varios ID de cliente para el mismo visitante, junto con un identificador de tipo de cliente para separar el ámbito de los distintos ID de cliente. Este método corresponde a setCustomerIDs en la biblioteca JavaScript.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
      ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Métodos de Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sends request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
      Console.WriteLine  (context); 
      });
      ```

* **TargetCreateRequest**

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Crea un `ADBTargetLocationRequest`.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Borra cualquier cookie objetivo de la aplicación.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Devuelve nil si todavía no se ha enviado ninguna señal. Visitor profile is saved in `NSUserDefaults` for easy access across multiple launches of your app.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Devuelve el DPID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Devuelve el DPUUID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Establece el dpid y el dpuuid. Si dpid y dpuuid están establecidos, se enviarán con cada señal.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Restaura el UUID de Audience Manager y elimina el perfil del visitante actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void AudienceReset ();
      ```

   * Esta es la sintaxis para este método:

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Vídeo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Para obtener más información, consulte Análisis [de vídeo](/help/ios/getting-started/dev-qs.md).

* **MediaCreateSettings**

   Devuelve un objeto `ADBMediaSettings` con parámetros específicos.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Devuelve un objeto `ADBMediaSettings` para su uso con el seguimiento de un vídeo de anuncio.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Abre un objeto `ADBMediaSettings` para su seguimiento.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Cierra el elemento de medios llamado nombre.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Reproduce el elemento de medios llamado name con un desplazamiento offset dado (en segundos).

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Marca de forma manual como completado el elemento de medios en el offset indicado (en segundos).

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el offset indicado.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```
