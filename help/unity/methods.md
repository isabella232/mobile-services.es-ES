---
description: Métodos de configuración de ADBMobile.cs
keywords: Unity
solution: Experience Cloud
title: Métodos ADBMobile.cs
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
exl-id: d12c16f1-c25c-4698-8943-a660d9c08faf
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 70%

---

# Métodos ADBMobile.cs {#adbmobile-cs-methods}

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

   Habilite las notificaciones locales en la aplicación.

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
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Se descartan las visitas.
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

   Devuelve el identificador de usuario personalizado si se ha establecido. Devuelve null si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

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
   >El propósito de este método es que se utilice en aplicaciones que realizan un registro de notificaciones mientras se encuentran en segundo plano, y solo debería invocarse desde el código que se está ejecutando cuando la aplicación esté en segundo plano.

   * Esta es la sintaxis para este método:

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (solo Android)**

   Indica al SDK que la aplicación está en pausa, para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, en pausa recopila una marca de tiempo para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo vital sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (solo Android)**

   Indica al SDK que debe establecer su contexto de aplicación desde la actividad actual de UnityPlayer.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetContext();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Establece la preferencia de registro de depuración como habilitada.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Establece el estado de privacidad del usuario actual en estado . Establezca uno de los siguientes valores:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Las visitas se envían inmediatamente.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Se descartan las visitas.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: si está activado el seguimiento en línea, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambia a opt-in.

   * Esta es la sintaxis para este método:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Este es un ejemplo de código para esta sintaxis:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Establece el identificador de usuario en userId.

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

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas que están disponibles en la aplicación, como &quot;pantalla de título&quot;, &quot;nivel 1&quot;, &quot;pausa&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `TrackState` incrementan las visualizaciones de página.

   Si el estado está vacío, en los informes se muestra *`app name app version (build)`*. Si observa este valor en los informes, asegúrese de que está estableciendo un estado en cada llamada `TrackState` .

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

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

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, &quot;muertes&quot;, &quot;aumento de nivel&quot;, &quot;suscripciones a fuentes&quot; y otras métricas.

   >[!TIP]
   >
   >Si cuenta con un código que podría estar ejecutándose mientras la aplicación se encuentra en segundo plano (por ejemplo, recuperación de datos en segundo plano), utilice `trackActionFromBackground` en su lugar.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (solo iOS)**

   Rastrea una acción que se produjo en el fondo. Esto evita que los eventos del ciclo vital se activen en determinados escenarios.

   >[!TIP]
   >
   >Este método solo debería invocarse en el código que se ejecuta mientras la aplicación se encuentra en segundo plano.

   * Esta es la sintaxis para este método:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Envía las coordenadas de latitud y longitud actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada TrackLocation .

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

   Agrega una cantidad al valor de duración del usuario.

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

   Pasa datos para actualizar los datos de contexto asociados a la acción determinada. Los datos que se pasan se anexan a los ya existentes para la acción determinada y se sobrescriben si ya se ha definido la misma clave para la acción.

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

## Métodos de adquisición 

* **ProcessGooglePlayInstallReferrerUrl** *(solo Android)*

   Pase la URL del referente devuelta por una llamada a la API del referente de instalación de Google Play a este método.

   * Esta es la sintaxis para este método:

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
