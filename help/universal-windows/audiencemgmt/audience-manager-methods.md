---
description: Lista de métodos de Audience Manager provistos por la biblioteca de la Plataforma universal de Windows.
seo-description: Lista de métodos de Audience Manager provistos por la biblioteca de la Plataforma universal de Windows.
seo-title: Métodos de Audience Manager
solution: Marketing Cloud, Analytics
title: Métodos de Audience Manager
topic: Desarrollador e implementación
uuid: efbe 8 f 33-7 f 53-40 a 6-b 7 aa-a 36 ac 718 c 047
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods{#audience-manager-methods}

Lista de métodos de Audience Manager provistos por la biblioteca de la Plataforma universal de Windows.

Actualmente, el SDK ofrece compatibilidad con varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

Si Audience Manager está configurado en su archivo JSON, se envía una señal que contiene métricas del ciclo vital junto con su visita de ciclo vital.

* **Getvisitorprofile (winjs: Getvisitorprofile)**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Devuelve `null` si todavía no se ha enviado ninguna señal. El perfil del visitante está guardado en `SharedPreferences` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

   Envía a la gestión de público una señal con características y obtiene una devolución de los segmentos coincidentes en una llamada de retorno a block.

   * Esta es la sintaxis para este método:

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      