---
description: Clases y métodos proporcionados por la biblioteca de BlackBerry.
seo-description: Clases y métodos proporcionados por la biblioteca de BlackBerry.
seo-title: Referencia de métodos y clases móviles de Adobe Mobile
title: Referencia de métodos y clases móviles de Adobe Mobile
uuid: 1 e 42 d 759-be 43-4 bb 3-ac 1 a-c 7 d 64133 d 61 c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

Clases y métodos proporcionados por la biblioteca de BlackBerry.

Actualmente, el SDK admite Adobe Analytics y los métodos están en clases independientes basadas en la solución.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * ADBMobilePrivacyStatusOptIn: las visitas se envían inmediatamente.
   * ADBMobilePrivacyStatusOptOut: las visitas se descartan.
   * ADBMobilePrivacyStatusUnknown: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

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

   Sets the privacy status for the current user to `status`. Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn` - las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut` - las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

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

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Estos métodos se emplean para enviar datos a su grupo de informes de Adobe Analytics.

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las visualizaciones disponibles en su aplicación, como “tablero de inicio”, “configuración de la aplicación”, “carrito”, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

   >[!TIP]
   >
   >Es la única llamada de seguimiento que incrementa las vistas de página.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, “inicios de sesión”, “toques en banners”, “suscripciones a fuentes” y otras métricas.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envía las coordenadas x e y actuales. Sustituya el evento por el que se reciba del suscriptor a BPS.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` referencia del archivo de configuración {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

`ADBMobileConfig.json` El archivo debe colocarse en la carpeta *assets* .

* **rsids**

   (Requerido). Uno o más grupos de informes para recibir datos de Analytics. Los ID de grupos de informes deben separarse con comas, sin espacios intermedios.

   Esta es la muestra de código para esta variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Requerido). Servidor de Analytics. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. El prefijo de protocolo lo gestiona automáticamente la biblioteca basándose en la variable `ssl`. Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos que se envían a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). El valor predeterminado es `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false. Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo, póngase en contacto [Asistencia para empresas](https://helpx.adobe.com/contact/enterprise-support.ec.html).

   Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite establecer un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp`.

   El valor predeterminado es `false`.

* **lifecycleTimeout**

   Especifica la duración, en segundos, que debe transcurrir entre cada inicio de aplicación antes de que el inicio se considere como una nueva sesión. Este tiempo de espera también se aplica cuando su aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación permanece en segundo plano no se incluye en la duración de la sesión.

   El valor predeterminado es 300 segundos.

* **batchLimit**

   Número máximo de visitas sin conexión almacenadas en la cola. El valor predeterminado es 0 (Sin límite).

* **privacyDefault**

   * `optedin` - las visitas se envían inmediatamente.
   * `optedout` - las visitas se descartarán.
   * `optunknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). 

      Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.
   Esta variable define únicamente el valor inicial. Si este valor se establece o se cambia en el código en algún momento, se utiliza el valor nuevo en adelante hasta que se vuelva a cambiar, o hasta que la aplicación se desinstale y reinstale.

   El valor predeterminado es `optedin`.

Esto es un ejemplo de archivo `ADBMobileConfig.json`:

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
