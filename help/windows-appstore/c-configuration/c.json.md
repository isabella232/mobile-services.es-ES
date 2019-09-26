---
description: Información para ayudarle a utilizar el archivo de configuración ADBMobile JSON.
seo-description: Información para ayudarle a utilizar el archivo de configuración ADBMobile JSON.
seo-title: Archivo de configuración ADBMobileConfig.json
solution: Marketing Cloud,Analytics
title: Archivo de configuración ADBMobileConfig.json
topic: Desarrollador e implementación
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` archivo config {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

Actualmente, el SDK ofrece compatibilidad con varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. El prefijo de los métodos de configuración es “Config”.

* **rsids**

   (Necesario para Analytics). Uno o más grupos de informes para recibir datos de Analytics. Los ID de grupos de informes deben separarse con comas, sin espacios intermedios.

   * Estos son los ejemplos de código para esta variable:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Necesario para Analytics y Gestión de público). Servidor de Analytics o Gestión de público, basado en el nodo principal. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. El prefijo de protocolo lo gestiona automáticamente la biblioteca basándose en la variable `ssl`.

   Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos que se envían a Analytics. El charset se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). El valor predeterminado es `false`.

* **offlineEnabled**

   Cuando está activado (true), las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde, cuando el dispositivo se conecta. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false. Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo, póngase en contacto Servicio de atención al cliente. Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite establecer un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp`.

* **lifecycleTimeout**

   Especifica la duración, en segundos, que debe transcurrir entre cada inicio de aplicación antes de que el inicio se considere como una nueva sesión. Este tiempo de espera también se aplica cuando su aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación permanece en segundo plano no se incluye en la duración de la sesión. El valor predeterminado es 300 segundos.

* **batchLimit**

   Envía las visitas en lotes. Por ejemplo, si se establece en 50, las visitas se ponen en cola hasta que se acumulan 50 y entonces se envían todas. Requiere `offlineEnabled=true`. El valor predeterminado es `0` (sin lotes).

* **privacyDefault**

   * `optedin` - las visitas se envían inmediatamente.
   * `optedout` - las visitas se descartarán.
   * `optunknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

      El valor predeterminado es `optedin`.

      >[!TIP]
      >
      >Esto sólo establece el valor predeterminado. Si este valor se llega a establecer o cambiar en el código, se guarda en el almacenamiento local y se utiliza en adelante hasta que se cambia de nuevo, o hasta que la aplicación se desinstale y se vuelva a instalar.

* **poi**

   Cada matriz de punto de interés (POI) guarda su nombre, latitud, longitud y radio del área (en metros). El nombre del punto puede ser cualquier cadena. Cuando se envía una llamada a `trackLocation`, si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto que se envía junto con la llamada a `trackLocation`.

   * Este es el ejemplo de código para esta variable:

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Determina cuánto tiempo espera Target una respuesta.

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
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

