---
description: Información para ayudarle a utilizar el SDK Universal App Store para Windows 8.1 con Adobe Analytics.
seo-description: Información para ayudarle a utilizar el SDK Universal App Store para Windows 8.1 con Adobe Analytics.
seo-title: Métodos de Analytics
solution: Marketing Cloud, Analytics
title: Métodos de Analytics
topic: Desarrollador e implementación
uuid: 79 db 105 c -216 c -4061-97 f 3-a 55954995 e 67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Información para ayudarle a utilizar el SDK Universal App Store para Windows 8.1 con Adobe Analytics.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud], incluidas Analytics], Target] y Audience Manager]. Los métodos tienen un prefijo que depende de la solución. El prefijo de los métodos de Analytics es “Analytics”.

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs: Trackstate)**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las visualizaciones disponibles en su aplicación, como “tablero de inicio”, “configuración de la aplicación”, “carrito”, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `TrackState` incrementan las visualizaciones de página. Si `state` está vacío, en los informes se muestra “app name app version (build)”. Si observa este valor en los informes, asegúrese de que está estableciendo `state` en todas las llamadas a `TrackState`.

   >[!TIP]
   >
   >Es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs: Trackaction)**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, “inicios de sesión”, “toques en banners”, “suscripciones a fuentes” y otras métricas.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **Gettrackingidentifierasync (winjs: Gettrackingidentifierasync)**

   Devuelve el identificador de usuario generado de forma automática para Analytics. Se trata de un identificador de visitante exclusivo y específico para la aplicación que se genera durante el lanzamiento inicial, que después se almacena y utiliza a partir de ese momento. Esta ID se conserva entre las actualizaciones de la aplicación y se elimina al desinstalarla.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **Tracklocation (winjs: Tracklocation)**

   Envía las coordenadas x e y actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **Tracklifetimevalueincrease (winjs: Tracklifetimevalueincrease)**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **Tracktimedactionstart (winjs: Tracktimedactionstart)**

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
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **Tracktimedactionupdate (winjs: Tracktimedactionupdate)**

   Pasa `contextData` para actualizar los datos de contexto asociados a `action` en cuestión. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **Tracktimedactionexistsasync (winjs: Tracktimedactionexistsasync)**

   Devuelve true si la acción temporizada dada existe, y false si no es así.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs: Tracktimedactionend)**

   Finaliza una acción temporizada.

   * Esta es la sintaxis para este método:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs: Cleartrackingqueue)**

   Borra todas las visitas almacenadas de la cola de seguimiento de Analytics.

   * Esta es la sintaxis para este mensaje:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Este es el ejemplo de código:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs: Getqueuesizeasync)**

   Devuelve el número de visitas almacenadas en la cola de Analytics.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
