---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Métodos adbmobile. cs
solution: Marketing Cloud, Desarrollador
title: Métodos adbmobile. cs
uuid: af 504934-febd -45 d 9-81 e 2-2 a 310 f 4 c 65 dc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## Métodos de configuración

* **CollectLifecycleData**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void CollectLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.CollectLifecycleData(); 
      ```

* **EnableLocalNotifications (solo iOS)**

   Activa las notificaciones locales en la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.EnableLocalNotifications(); 
      ```

* **GetDebugLogging**

   Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `false`.

   * Esta es la sintaxis para este método:

      ```java
      public static bool GetDebugLogging();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Devuelve el valor de duración del usuario actual.

   * Esta es la sintaxis para este método:

      ```java
      public static double GetLifetimeValue();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Las visitas se envían inmediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Las visitas se descartan.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas).

      Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in. El valor predeterminado se establece en el archivo [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Esta es la sintaxis para este método:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Devuelve el identificador del usuario si se ha establecido un identificador personalizado. Devuelve vacío si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

   * Esta es la sintaxis para este método:

      ```java
      public static string GetUserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var userId = ADBMobile.GetUserIdentifier(); 
      ```

* **GetVersion**

   Obtiene la versión de la biblioteca.

   * Esta es la sintaxis para este método:

      ```java
      public static string GetVersion();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (solo iOS)**

   Indica al SDK que la siguiente reanudación desde segundo plano no debe iniciar una nueva sesión, independientemente del valor del tiempo de espera de sesión del ciclo vital en el archivo de configuración.

   >[!TIP]
   >
   >Este método está pensado para utilizarse en aplicaciones que realizan un registro de notificaciones mientras se encuentran en segundo plano y solo debería invocarse desde el código que se ejecuta mientras la aplicación está en segundo plano.

   * Esta es la sintaxis para este método:

      ```java
      public static void KeepLifecycleSessionAlive(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.KeepLifecycleSessionAlive(); 
      ```

* **PauseCollectingLifecycleData (solo Android)**

   Indica al SDK que la aplicación está en pausa para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, cuando está en pausa, recopila un registro de fecha y hora para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo de vida sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.PauseCollectingLifecycleData(); 
      ```

* **SetContext (solo Android)**

   Indica al SDK que debe establecer su contexto de aplicación desde la actividad actual de unityplayer.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetContext();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.SetContext(); 
      ```

* **SetDebugLogging**

   Establece la preferencia de registro de depuración como activado.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetDebugLogging (bool enabled); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.SetDebugLogging(true); 
      ```

* **Setprivacystatus**

   Establece el estado de privacidad del usuario actual como estado. Establezca uno de los siguientes valores:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Las visitas se envían inmediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Las visitas se descartan.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus); 
      ```

   * Esta es la muestra de código para esta sintaxis:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Establece el identificador de usuario como userId.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetUserIdentifier(string userId); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId"); 
      ```

## Métodos de Analytics

* **GetTrackingIdentifier**

   Recupera el identificador de seguimiento analítico.

   * Esta es la sintaxis para este método:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier(); 
      ```

* **TrackState**

   Realiza un seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas que están disponibles en la aplicación, como “pantalla de título”, “nivel 1” o “pausa”, entre otros. Estos estados son similares a las páginas de un sitio web y las llamadas `TrackState` incrementan las visualizaciones de página.

   If state is empty, it displays as *`app name app version (build)`* in reports. Si observa este valor en los informes, asegúrese de que está estableciendo state en todas las llamadas a `TrackState`.

   >[!TIP]
   >
   >Es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var contextData = new Dictionary<string, object>); 
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Realiza un seguimiento de una acción en la aplicación. Las acciones son lo que sucede en la aplicación que desea medir, como “muertes”, “subida de nivel”, “suscripciones a la fuente”, entre otras métricas.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (solo iOS)**

   Realiza un seguimiento de una acción que ocurre en segundo plano. Esto impide que los eventos del ciclo vital se activen en ciertos escenarios.

   >[!TIP]
   >
   >Este método solo debe invocarse en el código que se ejecuta mientras la aplicación está en segundo plano.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envía las coordenadas de latitud y longitud actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada TrackLocation.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null); 
      ```

* **TrackBeacon**

   Realiza un seguimiento cuando un usuario accede a la proximidad de una señalización.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata); 
      ```

* **TrackingClearCurrentBeacon**

   Borra los datos de señalizaciones una vez el usuario haya abandonado la proximidad de la señalización.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackingClearCurrentBeacon(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Incrementa el valor del ciclo de vida del usuario.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Inicia una acción temporizada con acción de nombre. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Pasa datos para actualizar los datos de contexto asociados a la acción determinada. Los datos que se pasan se añaden a los datos existentes de esa acción determinada y se sobrescriben si ya se ha definido esa clave para una acción.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var contextData = new Dictionary<string, object>; 
      contextData.Add("checkpoint", "1:32"); 
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Finaliza una acción temporizada.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackTimedActionEnd(string action); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackTimedActionEnd("level2"); 
      ```

* **TrackingTimedActionExists**

   Devuelve si la acción temporizada está en progreso o no.

   * Esta es la sintaxis para este método:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2"); 
      ```

* **TrackingSendQueuedHits**

   Fuerza la biblioteca a enviar todas las visitas en la cola sin conexión, sin importar cuántas haya en la cola.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Borra todas las visitas de la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackingClearQueue();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackingClearQueue(); 
      ```

* **TrackingGetQueueSize**

   Recupera el número de visitas que hay actualmente en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Métodos de ID de Experience Cloud

* **GetMarketingCloudID**

   Recupera el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      public static string GetMarketingCloudID(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Con el ID de Experience Cloud, puede configurar ID de cliente adicionales para asociarlos a cada visitante. La API de visitante acepta varios ID de cliente para el mismo visitante, además de un identificador de tipo de cliente para separar el ámbito de los distintos ID de cliente. Este método corresponde a setCustomerIDs en la biblioteca JavaScript.

   * Esta es la sintaxis para este método:

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      var ids = new Dictionary<string, object> (); 
      ids.Add ("player1", "jimbob"); 
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

