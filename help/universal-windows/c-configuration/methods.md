---
description: Clases y métodos provistos por la biblioteca de la Plataforma universal de Windows.
seo-description: Clases y métodos provistos por la biblioteca de la Plataforma universal de Windows.
seo-title: Métodos de SDK
solution: Marketing Cloud, Analytics
title: Métodos de SDK
topic: Desarrollador e implementación
uuid: e 3 aa 41 d 6-7 bc 0-4208-a 662-12907 c 209 a 77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Clases y métodos provistos por la biblioteca de la Plataforma universal de Windows.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs: Getversion)**

   Devuelve la versión actual de la biblioteca de Adobe Mobile.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * `ADBMobilePrivacyStatusOptIn` - Las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - Las visitas se descartan.
   * `ADBMobilePrivacyStatusUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

      The default value is set in the `ADBMobileConfig.json` config file. Para obtener más información, consulte [Archivo de configuración adbmobileconfig. json](/help/universal-windows/c-configuration/c.json.md).

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Estos son los ejemplos de código de este método:

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

* **Setprivacystatus (winjs: Setprivacystatus)**

   Sets the privacy status for the current user to `status`. Establezca uno de los siguientes valores:
   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `DBMobilePrivacyStatusUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan. Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

      * Esta es la sintaxis para este método:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Estos son los ejemplos de código de este método:

         **C-sharp**

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

* **Getlifetimevalue (winjs: Getlifetimevalue)**

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

* **Getuseridentifier (winjs: Getuseridentifier)**

   Devuelve el identificador de usuario personalizado si se ha establecido alguno. Returns `null` if a custom identifier is not set.
El valor predeterminado es `null`.

   >[!IMPORTANT]
   >
   >Si la aplicación se actualiza del SDK 3. x al 4. x de Experience Cloud, el servicio de ID previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es `null` hasta que se establece.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Este es un ejemplo de código para este método:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs: Setuseridentifier)**

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

* **Getdebuglogging (winjs: Getdebuglogging)**

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

* **Setdebuglogging (winjs: Setdebuglogging)**

   Establece la preferencia de registro de depuración en `debugLogging`. El registro de depuración solo funciona cuando se utiliza la versión de depuración de la biblioteca, la versión de lanzamiento ignora esta configuración.

   * Esta es la sintaxis para este método:

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **Collectlifecycledata (winjs: Collectlifecycledata)**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. For more information, see  [Lifecycle metrics](/help/universal-windows/metrics.md).

   * Esta es la sintaxis para este método:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **Pausecollectinglifecycledata (winjs: Pausecollectinglifecycledata)**

   Indica al SDK que la aplicación está en pausa para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, cuando está en pausa, recopila un registro de fecha y hora para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo de vida sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/universal-windows/metrics.md).

   * Esta es la sintaxis para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
