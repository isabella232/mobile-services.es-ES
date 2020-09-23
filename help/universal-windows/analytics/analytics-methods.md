---
description: Información útil para utilizar el SDK de la Plataforma universal de Windows con Adobe Analytics.
seo-description: Información útil para utilizar el SDK de la Plataforma universal de Windows con Adobe Analytics.
seo-title: Métodos de Analytics
solution: Experience Cloud,Analytics
title: Métodos de Analytics
topic: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 57%

---


# Métodos de Analytics {#analytics-methods}

Información útil para utilizar el SDK de la Plataforma universal de Windows con Adobe Analytics.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Destinatario y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Los métodos de Analytics llevan el prefijo &quot;Analytics&quot;.

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

>[!TIP]
>
>Cuando se consumen `winmd` métodos de winJS (JavaScript), se reduce automáticamente la primera letra de todos los métodos.

* **TrackState (winJS: trackState)**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas disponibles en la aplicación, como &quot;panel principal&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `TrackState` incrementan las visualizaciones de página.
If `state` is empty, it displays as &quot;app name app version (build)&quot; in reports. If you see this value in reports, make sure you are setting `state` in each `TrackState` call.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que desea medir, como &quot;inicios de sesión&quot;, &quot;toques en banners&quot;, &quot;suscripciones de fuentes&quot; y otras métricas.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Devuelve el ID de visitante generado automáticamente para Analytics. Se trata de un ID de visitante exclusivo y específico para la aplicación que se genera durante el primer inicio y que luego se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación y se elimina al desinstalarla.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Envía las coordenadas x e y actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Inicia una acción temporizada llamada `action`. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Pasa `contextData` para actualizar los datos de contexto asociados a `action` en cuestión. Los `data` que se pasan se agregan a los datos existentes de esa acción y los sobrescriben si ya se ha definido la misma clave para `action`.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Devuelve true si la acción temporizada dada existe y false si no existe.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS: trackTimed &#x200B; ActionEnd)**

   Finaliza una acción temporizada.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Borra todas las visitas almacenadas de la cola de seguimiento de Analytics.

   * Esta es la sintaxis para este método:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Devuelve el número de visitas almacenadas actualmente en la cola de Analytics.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
