---
description: Lista de métodos de Audience Manager que proporciona la biblioteca Universal App Store para Windows 8.1.
seo-description: Lista de métodos de Audience Manager que proporciona la biblioteca Universal App Store para Windows 8.1.
seo-title: Métodos de Audience Manager
solution: Marketing Cloud, Analytics
title: Métodos de Audience Manager
topic: Desarrollador e implementación
uuid: e 39 c 9 c 3 e-fd 53-4 b 46-8 fff -88101 a 064 a 9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Lista de métodos de Audience Manager que proporciona la biblioteca Universal App Store para Windows 8.1.

Actualmente, el SDK ofrece compatibilidad con varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. El prefijo de los métodos de Audience Manager es “AudienceManager”.

>[!NOTE]
>
>Cuando consume métodos winmd desde winjs (JavaScript), todos los métodos tienen automáticamente su primera letra minúscula.

Si Audience Manager está configurado en su archivo JSON, junto a su visita de ciclo vital se envía una señal que contiene métricas del ciclo vital.

* **Getvisitorprofile (winjs: Getvisitorprofile)**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Devuelve `null` si todavía no se ha enviado ninguna señal. El perfil del visitante está guardado en `SharedPreferences` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **Getdpid (winjs: Getdpid)**

   Devuelve el DPID actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **Getdpuuid (winjs: Getdpuuid)**

   Devuelve el DPUUID actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **Setdpidanddpuuid (winjs: Setdpidanddpuuid)**

   Establece el DPID y el DPUUID. Si DPID y DPUUID se han establecido, se envían con cada señal.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **Signalwithdata (winjs: Signalwithdata)**

   Envía a Audience Manager una señal con características y obtiene una devolución de los segmentos coincidentes en una llamada de retorno de block.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

