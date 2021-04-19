---
description: Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-description: Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-title: Métodos SDK
solution: Experience Cloud,Analytics
title: Métodos SDK
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 50%

---

# Métodos SDK {#sdk-methods}

Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.

>[!TIP]
>
>Cuando consume métodos `winmd` de winJS (JavaScript), la primera letra de todos los métodos se hace minúscula automáticamente.

* **GetVersion (winJS: getVersion)**

   Devuelve la versión actual de la biblioteca de Adobe Mobile.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` : Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (entonces se envían las visitas) u excluido (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      El valor predeterminado se establece en el archivo [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md).

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Estos son ejemplos de código para este método:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Establece el estado de privacidad del usuario actual como `status`. Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` : Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (entonces se envían las visitas) u excluido (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Este es un ejemplo de código para este método:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es 0.

   * Esta es la sintaxis para este método:

      ```csharp
      static float GetLifetimeValue();
      ```

   * Este es un ejemplo de código para este método:

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Devuelve el identificador de usuario personalizado si se ha establecido. Devuelve null si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID anterior (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es `null` hasta que se establece.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Establece el identificador de usuario como `identifier`.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **GetDebugLogging (winJS: getDebugLogging)**

   Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `false`.

   * Esta es la sintaxis para este método:

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Establece la preferencia de registro de depuración en `debugLogging`. El registro de depuración solo funciona cuando se utiliza la versión de depuración de la biblioteca, la versión de la versión ignora esta configuración.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoque este método en el método `onResume()` de cada actividad dentro de la aplicación, como se muestra en el siguiente ejemplo. También se recomienda pasar la actividad o el servicio como el objeto de contexto en lugar del contexto de aplicación global.

   * Esta es la sintaxis para este método:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS: pauseCollecting &#x200B; LifecycleData)**

   Indica al SDK que la aplicación está en pausa, para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, en pausa recopila una marca de tiempo para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo vital sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoque este método en los métodos `onPause()` de cada actividad dentro de su aplicación, como se muestra en el ejemplo. También se recomienda pasar la actividad o el servicio como el objeto de contexto en lugar del contexto de aplicación global.

   * Esta es la sintaxis para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
