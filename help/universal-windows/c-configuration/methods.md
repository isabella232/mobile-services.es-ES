---
description: Clases y métodos proporcionados por la biblioteca de la Plataforma universal de Windows.
seo-description: Clases y métodos proporcionados por la biblioteca de la Plataforma universal de Windows.
seo-title: Métodos SDK
solution: Marketing Cloud,Analytics
title: Métodos SDK
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 66%

---


# SDK methods {#sdk-methods}

Clases y métodos proporcionados por la biblioteca de la Plataforma universal de Windows.

>[!TIP]
>
>Cuando se consumen `winmd` métodos de winJS (JavaScript), se reduce automáticamente la primera letra de todos los métodos.

* **GetVersion (winJS: getVersion)**

   Devuelve la versión actual de la biblioteca de Adobe Mobile.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * `ADBMobilePrivacyStatusOptIn` - Las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - Se descartan las visitas.
   * `ADBMobilePrivacyStatusUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      The default value is set in the `ADBMobileConfig.json` config file. Para obtener más información, consulte [Archivo](/help/universal-windows/c-configuration/c.json.md)de configuración ADBMobileConfig.json.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Estos son ejemplos de código para este método:

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Establece el estado de privacidad del usuario actual como `status`. Establezca uno de los siguientes valores:
   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `DBMobilePrivacyStatusUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan. Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      * Esta es la sintaxis para este método:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Estos son ejemplos de código para este método:

         **Engranaje en C**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es `0`.

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

   Devuelve el identificador de usuario personalizado si se ha establecido un identificador personalizado. Returns `null` if a custom identifier is not set.
El valor predeterminado es `null`.

   >[!IMPORTANT]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el servicio de ID anterior (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es `null` hasta que se establece.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Este es un ejemplo de código para este método:

      ```csharp
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

      ```javascript
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

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Establece la preferencia de registro de depuración en `debugLogging`. El registro de depuración solo funciona cuando se utiliza la versión de depuración de la biblioteca, la versión de lanzamiento omite esta configuración.

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

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/universal-windows/metrics.md).

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

   Indica al SDK que la aplicación está en pausa, para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, al pausar recopila una marca de tiempo para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo vital sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/universal-windows/metrics.md).

   * Esta es la sintaxis para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
