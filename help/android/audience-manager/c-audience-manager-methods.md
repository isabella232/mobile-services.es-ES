---
description: Esta es una lista de métodos de Audience Manager que proporciona la biblioteca Android.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Esta es una lista de métodos de Audience Manager que proporciona la biblioteca Android.
seo-title: Métodos de Audience Manager
solution: Experience Cloud,Analytics
title: Métodos de Audience Manager
topic: Desarrollador e implementación
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Métodos de Audience Manager{#audience-manager-methods}

Esta es una lista de métodos de Audience Manager que proporciona la biblioteca Android.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform. Los métodos tienen un prefijo de acuerdo con la solución. Por ejemplo, los métodos de Experience Cloud ID llevan el prefijo `audience manager`.

Si Audience Manager está configurado en su archivo JSON, junto a su visita de ciclo vital se envía una señal que contiene métricas del ciclo vital.

* **getVisitorProfile**

   Devuelve el perfil del visitante que se obtuvo más recientemente. Si no se ha enviado ninguna señal, devuelve el valor `null`. El perfil del visitante está guardado en `SharedPreferences` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Devuelve el DPID actual.

   * Esta es la sintaxis para este método:

      ```java
      public static void getDpid(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Devuelve el DPUUID actual.

   * Esta es la sintaxis para este método:

      ```java
      public static void getDpuuid(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Establece el DPID y el DPUUID, y estos valores se envían con cada señal.

   Si el valor DPUUID enviado al método contiene caracteres que no sean seguros para la URL, los clientes deberán cifrar el parámetro antes de enviarlo al SDK.

   * Esta es la sintaxis para este método:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Envía a la gestión de público una señal con las características y obtiene una devolución de los segmentos coincidentes en una llamada de retorno de bloques.

   * Esta es la sintaxis para este método:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
