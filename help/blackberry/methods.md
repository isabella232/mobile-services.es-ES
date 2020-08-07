---
description: Clases y métodos proporcionados por la biblioteca BlackBerry.
seo-description: Clases y métodos proporcionados por la biblioteca BlackBerry.
seo-title: Referencia de métodos y clases de Adobe Mobile
title: Referencia de métodos y clases de Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 55%

---


# Referencia de métodos y clases de Adobe Mobile {#adobe-mobile-class-and-method-reference}

Clases y métodos proporcionados por la biblioteca BlackBerry.

Actualmente, el SDK admite Adobe Analytics y los métodos están en clases independientes basadas en la solución.

## Ajustes del SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * ADBMobilePrivacyStatusOptIn: las visitas se envían inmediatamente.
   * ADBMobilePrivacyStatusOptOut: las visitas se descartan.
   * ADBMobilePrivacyStatusUnknown: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambia a opt-in (entonces se envían las visitas) u opt-out (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Esta es la sintaxis para este método:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* Método **setPrivacyStatus**

   Establece el estado de privacidad del usuario actual como `status`. Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Esta es la sintaxis para este método:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Devuelve el identificador del usuario si se ha establecido uno personalizado. Returns `null` if a custom identifier is not set. El valor predeterminado es `null`.

   * Esta es la sintaxis para este método:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Establece el identificador de usuario como `identifier`.

   * Esta es la sintaxis para este método:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `false`.

   * Esta es la sintaxis para este método:

      ```cpp
      static bool getDebugLogging();
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Establece la preferencia de registro de depuración en `debugLogging`.

   * Esta es la sintaxis para este método:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/blackberry/metrics.md).

   * Esta es la sintaxis para este método:

      ```cpp
      static void collectLifecycleData();
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Métodos de Analytics {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las vistas disponibles en la aplicación, como &quot;panel principal&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que desea medir, como &quot;inicios de sesión&quot;, &quot;toques en banners&quot;, &quot;suscripciones de fuentes&quot; y otras métricas.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envía las coordenadas x e y actuales. Reemplazar evento por el evento recibido del suscriptor de BPS.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` Referencia del archivo de configuración {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Requerido) Uno o más grupos de informes para recibir datos de Analytics. Las ID de varios grupos de informes deben separarse con comas sin espacios entre ellos.

   Este es el ejemplo de código para esta variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Requerido). Servidor de Analytics. Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `https://` o `https://`. El prefijo de protocolo lo gestiona automáticamente la biblioteca en función de la `ssl` variable. Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos enviados a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes.

* **ssl**

   Habilita (`true`) o deshabilita (`false`) el envío de datos de medición a través de SSL (HTTPS). El valor predeterminado es `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false. Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo,  póngase en contacto  [Asistencia](https://helpx.adobe.com/es/contact/enterprise-support.ec.html)empresarial.

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   El valor predeterminado es `false`.

* **lifecycleTimeout**

   Especifica el tiempo, en segundos, que debe transcurrir entre cada inicio de la aplicación antes de que el inicio se considere una nueva sesión. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión.

   El valor predeterminado es 300 segundos.

* **batchLimit**

   Número máximo de visitas sin conexión almacenadas en la cola. El valor predeterminado es 0 (sin límite).

* **privacyDefault**

   * `optedin`: las visitas se envían inmediatamente.
   * `optedout`: las visitas se descartarán.
   * `optunknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.
   Esta variable sólo establece el valor inicial. Si este valor se establece o se cambia en el código, se utilizará el nuevo valor en adelante hasta que se modifique o la aplicación se desinstale y vuelva a instalarse.

   El valor predeterminado es `optedin`.

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
