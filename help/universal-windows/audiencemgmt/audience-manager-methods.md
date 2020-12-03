---
description: Lista de los métodos de Audience Manager proporcionados por la biblioteca de la Plataforma universal de Windows.
seo-description: Lista de los métodos de Audience Manager proporcionados por la biblioteca de la Plataforma universal de Windows.
seo-title: Métodos de Audience Manager
solution: Experience Cloud,Analytics
title: Métodos de Audience Manager
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---


# Métodos de Audience Manager {#audience-manager-methods}

Lista de los métodos de Audience Manager proporcionados por la biblioteca de la Plataforma universal de Windows.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Destinatario y Audience Manager. Methods are prefixed according to the solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>Cuando se consumen `winmd` métodos de winJS (JavaScript), se reduce automáticamente la primera letra de todos los métodos.

Si el administrador de audiencias está configurado en el archivo JSON, se envía una señal que contiene métricas del ciclo vital junto con la visita del ciclo vital.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Devuelve el perfil del visitante que se haya obtenido más recientemente. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

   Envía a la administración de audiencias una señal con características y obtiene la devolución de los segmentos coincidentes en una llamada de retorno de bloque.

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
      ```
