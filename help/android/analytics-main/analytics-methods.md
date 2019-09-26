---
description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.
keywords: android;biblioteca;móvil;sdk
seo-description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.
seo-title: Métodos de Analytics
solution: Marketing Cloud,Analytics
title: Métodos de Analytics
topic: Desarrollador e implementación
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.

The SDK currently supports multiple Adobe Experience Cloud Solutions], including Analytics], Target], Audience Manager], and the Adobe Experience Platform Identity Service]. Los métodos tienen un prefijo de acuerdo con la solución. Por ejemplo, los métodos de Experience Cloud ID llevan el prefijo `analytics`.

Los siguientes métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics:

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

   If `state` is empty, `app name app version (build)` is displayed in reports. Si observa este valor en los informes, asegúrese de que establece un `state` en cada llamada `trackState`.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction** Rastrea una acción en la aplicación.

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * Esta es la sintaxis para este método:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier** Devuelve el identificador de visitante generado automáticamente para Analytics.

   Se trata de un ID exclusivo y específico para la aplicación que se genera durante el primer inicio, que después se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación y se elimina al desinstalarla.

   * Esta es la sintaxis para este método:

      ```java
      public static String getTrackingIdentifier(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String trackingId = Analytics.getTrackingIdentifier(); 
      ```

* **trackLocation**

   Envía la latitud, longitud y ubicación actuales en un punto de interés definido. Para obtener más información, consulte [Ubicación geográfica y puntos de interés](/help/android/location/geo-poi.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Inicia una acción temporizada llamada `action`.

   Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:
   ```java
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Pasa `contextData` para actualizar los datos de contexto asociados con `action`. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Finaliza una acción temporizada. If you provide `block`, you can access the final time values and can manipulate `data` before sending the final hit.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

   * Esta es la sintaxis para este método:

      ```java
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
              contextData.put("price", 49.95);
              return true;
         }
      });
      ```

* **sendQueuedHits**

   **Requiere SDK 4.1.**

   Independientemente de cuántas visitas haya en cola, este método obliga a la biblioteca a enviar todas las visitas en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      voidsendQueuedHits()
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Devuelve el número de llamadas de seguimiento almacenadas en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      long getQueueSize()
      ```

   * Este es un ejemplo de código para este método:

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   Borra todas las visitas de la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```java
      voidclearQueue()
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Tenga cuidado al borrar la cola de forma manual. Este proceso no se puede revertir.