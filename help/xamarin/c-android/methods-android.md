---
description: Métodos Android para el SDK de los componentes Xamarin para soluciones de Experience Cloud 4.x.
keywords: Xamarin
seo-description: Métodos Android para el SDK de los componentes Xamarin para soluciones de Experience Cloud 4.x.
seo-title: Métodos Android
solution: Marketing Cloud, Desarrollador
title: Métodos Android
uuid: 860 af 1 c 4-f 57 e -4 bcb -8308-4 e 316 da 9 a 27 b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

Métodos Android para el SDK de los componentes Xamarin para soluciones de Experience Cloud 4.x.

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **Debuglogging**

   Devuelve la preferencia de registro de depuración actual y el valor predeterminado es false.

   * Esta es la sintaxis para este método:

      ```java
      public static Boolean DebugLogging;
      ```

   * Este es un ejemplo de código para este método:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   Devuelve el valor de duración del usuario actual.

   * Esta es la sintaxis para este método:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Este es un ejemplo de código para este método:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.
   * `ADBMobilePrivacyStatus.OptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatus.OptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatus.Unknown` - si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.
   El valor predeterminado se establece en el archivo [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md).

   * Esta es la sintaxis para este método:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Si se ha establecido un identificador personalizado, devuelve este identificador. Si no se establece un identificador personalizado, devuelve null. El valor predeterminado es `null`.

   * Esta es la sintaxis para este método:

      ```java
      public static UserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Versión**

   Obtiene la versión de la biblioteca.

   * Esta es la sintaxis para este método:

      ```java
      public static string Version;
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Indica al SDK que la aplicación está en pausa para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, cuando está en pausa, recopila un registro de fecha y hora para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo de vida sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity actividad)**

   (4.2 o posterior) Indica al SDK que se deben recopilar los datos del ciclo de vida para su uso en todas las soluciones del SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity actividad)**

   (4.2 o posterior) Indica al SDK que se deben recopilar los datos del ciclo de vida para su uso en todas las soluciones del SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Este es un ejemplo de código para este método:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. Se utiliza la configuración distinta hasta que se cierre la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 o posterior) Establece el icono grande que se utiliza para las notificaciones creadas por el SDK. Este icono es la imagen principal que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 o posterior) Establece el icono pequeño que se utiliza para las notificaciones creadas por el SDK. Este icono se muestra en la barra de estado y es la imagen secundaria que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Devuelve el ID generado de forma automática para Analytics. Se trata de un ID exclusivo de aplicación que se genera durante el primer inicio y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación y se elimina durante la desinstalación.

   * Esta es la sintaxis para este método:

      ```java
      public static string TrackingIdentifier;
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. `States`son las vistas que están disponibles en la aplicación, como "pantalla de título", "nivel 1" o "pausa", entre otros. Estos estados son similares a las páginas de un sitio web y las llamadas `TrackState` incrementan las visualizaciones de página. Si el estado está vacío, se muestra como "nombre_aplicación versión_aplicación (compilación)" en los informes. Si observa este valor en los informes, asegúrese de que está estableciendo state en todas las llamadas a `TrackState`.

   >[!TIP]
   >
   >Es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Realiza un seguimiento de una acción en la aplicación. Las acciones son lo que sucede en la aplicación que desea medir, como “muertes”, “subida de nivel”, “suscripciones a la fuente”, entre otras métricas.

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Envía las coordenadas de latitud y longitud actuales. Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `TrackLocation`.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Realiza un seguimiento cuando un usuario accede a la proximidad de una señalización.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Borra los datos de señalizaciones una vez el usuario haya abandonado la proximidad de la señalización.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   Agrega una cantidad al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Inicia una acción temporizada con acción de nombre. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   > Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Pasa datos para actualizar los datos de contexto asociados a la acción determinada. Los datos que se pasan se añaden a los datos existentes de esa acción determinada y se sobrescriben si ya se ha definido esa clave para una acción.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Finaliza una acción temporizada.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Devuelve si la acción temporizada está en progreso o no.

   * Esta es la sintaxis para este método:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Fuerza a la biblioteca a enviar todas las visitas en la cola sin conexión, independientemente de cuántas visitas haya en cola.

   * Esta es la sintaxis para este método:

      ```java
      public static void SendQueuedHits();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Borra todas las visitas de la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      public static void ClearQueue(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Recupera el número de visitas que se encuentran actualmente en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      public static long QueueSize(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Recupera el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      public static string MarketingCloudId;
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Con el ID de Experience Cloud, puede configurar ID de cliente adicionales para asociarlos a cada visitante. La API de visitante acepta varios identificadores de cliente para el mismo visitante, con un identificador de tipo de cliente para separar el ámbito de los distintos identificadores de cliente. Este método corresponde a `setCustomerIDs` en la biblioteca de JavaScript.

   * Esta es la sintaxis para este método:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Métodos de Target {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

   * Esta es la sintaxis para este método:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Constructor de conveniencia para crear un objeto `ADBTargetLocationRequest` con los parámetros determinados.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Crea `ADBTargetLocationRequest`un.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Borra las cookies de Target de la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static void ClearCookies(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Devuelve cero si todavía no se ha enviado ninguna señal. El perfil del visitante está guardado en `NSUserDefaults` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * Esta es la sintaxis para este método:

      ```java
      public static string Dpuuid; 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * Esta es la sintaxis para este método:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Establece el `dpid` y `dpuuid`. If `dpid` and `dpuuid` are set, they are sent with each signal.

   * Esta es la sintaxis para este método:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

   * Esta es la sintaxis para este método:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Restaurar**

   Restaura el administrador de audiencia `UUID` y elimina el perfil del visitante actual.

   * Esta es la sintaxis para este método:

      ```java
      public static void Reset ();
      ```

   * Este es un ejemplo de código para este método:

      ```java
       AudienceManager.Reset ();
      ```

## Vídeo {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Para obtener más información acerca de Video Analytics, consulte [Análisis de vídeo](/help/android/analytics-main/video-qs.md).

* **MediaSettings**

   Devuelve un objeto `MediaSettings` con parámetros específicos.

   * Esta es la sintaxis para este método:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Este es un ejemplo de código para este método:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Devuelve un objeto `MediaSettings` para su uso con el seguimiento de un vídeo de anuncio.

   * Esta es la sintaxis para este método:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Abrir**

   Abre un objeto `ADBMediaSettings` para su seguimiento.

   * Esta es la sintaxis para este método:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Cierre**

   Cierra el elemento de medios denominado.

   * Esta es la sintaxis para este método:

      ```java
      public static void Close(string name);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Close (settings.Name); 
      ```

* **Reproducir**

   Reproduce el elemento de medios denominado en el desplazamiento determinado (en segundos).

   * Esta es la sintaxis para este método:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Completado**

   Marca de forma manual como completo el elemento de medios en el desplazamiento proporcionado (en segundos).

   * Esta es la sintaxis para este método:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el desplazamiento determinado.

   * Esta es la sintaxis para este método:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Haga clic**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Rastrear**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.Track (settings.Name, null); 
      ```