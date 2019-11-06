---
description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.
seo-title: Métodos de Analytics
solution: Experience Cloud,Analytics
title: Métodos de Analytics
topic: Desarrollador e implementación
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Métodos de Analytics {#analytics-methods}

Esta es una lista de métodos de Adobe Analytics que proporciona la biblioteca Android.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform. Los métodos tienen un prefijo de acuerdo con la solución. Por ejemplo, los métodos de Experience Cloud ID llevan el prefijo `analytics`.

Los siguientes métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics:

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas que están disponibles en la aplicación, como `home dashboard`, `app settings` o `cart`, entre otros. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

   Si el `state` está vacío, en los informes se muestra `app name app version (build)`. Si observa este valor en los informes, asegúrese de que establece un `state` en cada llamada `trackState`.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction**
Realiza el seguimiento de una acción en la aplicación.

   Acciones que le interesará medir, como `logons`, `banner taps`, `feed subscriptions` y otras métricas que se producen en la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier**
Devuelve el identificador de usuario generado de forma automática para Analytics.

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

   Envía la latitud, longitud y ubicación actuales en un determinado punto de interés. Para obtener más información, consulte [Geolocalización y puntos de interés](/help/android/location/geo-poi.md).

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

   Pasa `contextData` para actualizar los datos de contexto asociados con `action`. Los `data` que se pasan se anexan a los ya existentes para la acción. Si la misma clave ya está definida para `action`, los datos se sobrescriben.

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

   Finaliza una acción temporizada. Si proporciona un valor para `block`, puede acceder a los valores de tiempo finales y manipular los `data` antes de enviar la visita final.

   >[!TIP]
   >
   >Si proporciona `block`, debe devolver `true` para enviar una visita. Pasar el valor `null` para `block` envía la visita final.

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