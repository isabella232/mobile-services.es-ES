---
description: Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-description: Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-title: Métodos de SDK
solution: Marketing Cloud, Analytics
title: Métodos de SDK
topic: Desarrollador e implementación
uuid: 0 f 558 ff 4-73 d 3-4439-9 d 51-62 fbd 74 d 2 cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Clases y métodos proporcionados por la biblioteca Universal App Store para Windows 8.1.

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
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Estos son los ejemplos de código de este método:

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

* **Setprivacystatus (winjs: Setprivacystatus)**

   Sets the privacy status for the current user to `status`. Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

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

* **Getlifetimevalue (winjs: Getlifetimevalue)**

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

* **Getuseridentifier (winjs: Getuseridentifier)**

   Devuelve el identificador del usuario si se ha establecido un identificador personalizado. Devuelve vacío si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3. x al 4. x de Experience Cloud, el ID previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. De este modo, se preservan los datos de visitante tras actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es `null` hasta que se establece.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```js
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

      ```js
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

      ```js
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

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. También recomendamos pasar la actividad o servicio como el objeto de contexto en lugar de como el contexto de la aplicación.

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

   Indica al SDK que la aplicación está en pausa para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, cuando está en pausa, recopila un registro de fecha y hora para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo de vida sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. También recomendamos pasar la actividad o servicio como el objeto de contexto en lugar de como el contexto de la aplicación.

   * Esta es la sintaxis para este método:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
