---
description: Lista de métodos de Audience Manager proporcionados por la biblioteca Universal App Store para Windows 8.1.
solution: Experience Cloud Services,Analytics
title: Métodos de Audience Manager
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Métodos de Audience Manager {#audience-manager-methods}

Lista de métodos de Audience Manager proporcionados por la biblioteca Universal App Store para Windows 8.1.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Los métodos de Audience Manager llevan el prefijo &quot;AudienceManager&quot;.

>[!NOTE]
>
>Cuando consume métodos winmd desde winJS (JavaScript), la primera letra de todos los métodos se hace minúscula automáticamente.

Si Audience Manager está configurado en su archivo JSON, junto a su visita de ciclo vital se envía una señal que contiene métricas del ciclo vital.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Devuelve `null` si todavía no se ha enviado ninguna señal. El perfil del visitante se guarda en `SharedPreferences` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

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

* **GetDpuuid (winJS: getDpuuid)**

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

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Establece el DPID y el DPUUID. Si se establecen DPID y DPUUID, se enviarán con cada señal.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Envía al Audience Manager una señal con características y obtiene una devolución de los segmentos coincidentes en una llamada de retorno de bloque.

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
