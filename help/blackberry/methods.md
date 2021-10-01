---
description: Clases y métodos proporcionados por la biblioteca de BlackBerry.
title: Referencia de métodos y clases de Adobe Mobile
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
exl-id: ad73ec1d-d082-4237-b7cb-b8ec2f7595a3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 60%

---

# Referencia de métodos y clases de Adobe Mobile {#adobe-mobile-class-and-method-reference}

Clases y métodos proporcionados por la biblioteca de BlackBerry.

Actualmente, el SDK es compatible con Adobe Analytics y los métodos se encuentran en clases independientes basadas en la solución .

## Configuración del SDK {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Devuelve la representación de enumeración del estado de privacidad del usuario actual.

   * ADBMobilePrivacyStatusOptIn : las visitas se envían inmediatamente.
   * ADBMobilePrivacyStatusOptOut : las visitas se descartan.
   * ADBMobilePrivacyStatusUnknown : si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Esta es la sintaxis para este método:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Establece el estado de privacidad del usuario actual como `status`. Establezca uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn`: las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: las visitas se descartarán.
   * `ADBMobilePrivacyStatusUnknown` : Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (entonces se envían las visitas) u excluido (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Esta es la sintaxis para este método:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Devuelve el identificador del usuario si se ha establecido uno personalizado. Devuelve `null` si no se ha establecido un identificador personalizado. El valor predeterminado es `null`.

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

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las visualizaciones disponibles en su aplicación, como &quot;tablero de inicio&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

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

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, &quot;inicios de sesión&quot;, &quot;pulsaciones en banners&quot;, &quot;suscripciones a fuentes&quot; y otras métricas.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Envía las coordenadas x e y actuales. Sustituya el evento por el evento que recibe del suscriptor a BPS.

   * Esta es la sintaxis para este método:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` Referencia del archivo de configuración {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

El archivo `ADBMobileConfig.json` debe colocarse en la carpeta *assets*.

* **rsids**

   (Obligatorio) Uno o más grupos de informes para recibir datos de Analytics. Las ID de varios grupos de informes deben separarse con comas sin espacios entre ellos.

   Este es un ejemplo de código para esta variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Requerido). Servidor de Analytics. Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `https://` o `https://`. El prefijo de protocolo lo gestiona automáticamente la biblioteca en función de la variable `ssl` . Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos enviados a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes.

* **ssl**

   Habilita (`true`) o deshabilita (`false`) el envío de datos de medición a través de SSL (HTTPS). El valor predeterminado es `false`.

* **offlineEnabled**

   Cuando está habilitado (`true`), las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde, cuando el dispositivo está en línea. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   >[!TIP]
   >
   >Si las marcas de tiempo están habilitadas en el grupo de informes, la propiedad de configuración `offlineEnabled` *debe* ser `true`. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false. Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo,   póngase en contacto   [Soporte Enterprise](https://helpx.adobe.com/es/contact/enterprise-support.ec.html).

   Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite configurar un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp` .

   El valor predeterminado es `false`.

* **lifecycleTimeout**

   Especifica la duración en segundos que debe transcurrir entre el momento en que se inicia la aplicación, antes de que el inicio se considere una sesión nueva. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión.

   El valor predeterminado es 300 segundos.

* **batchLimit**

   Número máximo de visitas sin conexión almacenadas en la cola. El valor predeterminado es 0 (sin límite).

* **privacyDefault**

   * `optedin`: las visitas se envían inmediatamente.
   * `optedout`: las visitas se descartarán.
   * `optunknown` : Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (entonces se envían las visitas) u excluido (entonces se descartan las visitas).

      Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.
   Esta variable establece únicamente el valor inicial. Si este valor se establece o se cambia en el código en algún momento, se utilizará el nuevo valor en adelante hasta que se cambie, o hasta que la aplicación se desinstale y se vuelva a instalar.

   El valor predeterminado es `optedin`.

El siguiente es un ejemplo de archivo `ADBMobileConfig.json`:

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
