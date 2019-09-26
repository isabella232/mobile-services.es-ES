---
description: Información para ayudarle a utilizar el archivo de configuración ADBMobile JSON.
seo-description: Información para ayudarle a utilizar el archivo de configuración ADBMobile JSON.
seo-title: Configuración de ADBMobileConfig.json
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json config
topic: Desarrollador e implementación
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Archivo de configuración ADBMobileConfig.json {#adbmobileconfig-json-config}

Información para ayudarle a utilizar el archivo de configuración ADBMobile JSON.

Actualmente, el SDK ofrece compatibilidad con varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. El prefijo de los métodos de configuración es “Config”.

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. Los ID de grupos de informes deben separarse con comas, sin espacios intermedios.

   * Esta es la sintaxis para este método:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Necesario para Analytics y Gestión de público**). Servidor de Analytics o Gestión de público, basado en el nodo principal. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. El prefijo de protocolo lo gestiona automáticamente la biblioteca basándose en la variable `ssl`.

   Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos que se envían a Analytics. El charset se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). El valor predeterminado es `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor `false`.

   Si esta configuración no se realiza correctamente, se perderán datos. If you are unsure whether a report suite is timestamp enabled, contact Customer Care. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   El valor predeterminado es `false`.

* **lifecycleTimeout**

   Especifica la duración, en segundos, que debe transcurrir entre cada inicio de aplicación antes de que el inicio se considere como una nueva sesión. Este tiempo de espera también se aplica cuando su aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación permanece en segundo plano no se incluye en la duración de la sesión.

   El valor predeterminado es 300 segundos.

* **batchLimit**

   Envía las visitas en lotes.

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Requiere `offlineEnabled=true`y el valor predeterminado es `0` (sin lotes).

* **privacyDefault**

   The options are:

   * `optedin` - las visitas se envían inmediatamente.
   * `optedout` - las visitas se descartarán.
   * `optunknown`: si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a inclusión (entonces se envían las visitas) o exclusión (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a inclusión.

      Esto sólo establece el valor predeterminado. Si este valor se llega a establecer o cambiar en el código, se guarda en el almacenamiento local y se utiliza en adelante hasta que se cambia de nuevo, o hasta que la aplicación se desinstale y se vuelva a instalar.

      El valor predeterminado es `optedin`.

* **poi**

   Cada matriz de punto de interés (POI) guarda su nombre, latitud, longitud y radio del área (en metros). El nombre del punto puede ser cualquier cadena. Cuando se envía una llamada a `trackLocation`, si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto que se envía junto con la llamada a `trackLocation`.

   * Este es el ejemplo de código para esta variable:

      ```js
       "poi" [ 
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
