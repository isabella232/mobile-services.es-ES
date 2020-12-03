---
description: Información útil para utilizar el archivo de configuración JSON de ADBMobile.
seo-description: Información útil para utilizar el archivo de configuración JSON de ADBMobile.
seo-title: Archivo de configuración ADBMobileConfig.json
solution: Experience Cloud,Analytics
title: Archivo de configuración ADBMobileConfig.json
topic: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 47%

---


# `ADBMobileConfig.json` archivo config {#adbmobileconfig-json-config}

Información para ayudarle a utilizar el archivo de `ADBMobile.json` configuración.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Destinatario y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Los métodos de configuración llevan el prefijo &quot;Config&quot;.

* **rsids**

   (Necesario para Analytics) Uno o varios grupos de informes para recibir datos de Analytics. Las ID de varios grupos de informes deben separarse con comas sin espacios entre ellos.

   * Estos son los ejemplos de código para esta variable:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Necesario para Analytics y Administración de Audiencias). Analytics o el servidor de administración de Audiencias, según el nodo principal. Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `https://` o `https://`. El prefijo de protocolo lo gestiona automáticamente la biblioteca en función de la `ssl` variable.

   Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos enviados a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes. Para obtener más información, consulte [s.charSet](https://docs.adobe.com/content/help/es-ES/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Habilita (`true`) o deshabilita (`false`) el envío de datos de medición a través de SSL (HTTPS). El valor predeterminado es `false`.

* **offlineEnabled**

   Cuando se habilita (true), las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde cuando el dispositivo está en línea. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false. Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo,   póngase en contacto   Servicio de atención al cliente. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

* **lifecycleTimeout**

   Especifica la duración en segundos que debe transcurrir entre el momento en que se inicia la aplicación, antes de que el inicio se considere una sesión nueva. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión. El valor predeterminado es 300 segundos.

* **batchLimit**

   Enviar visitas por lotes. Por ejemplo, si se establece en 50, las visitas se ponen en cola hasta que se almacenan 50, entonces se envían todas las visitas en cola. Requiere `offlineEnabled=true`. El valor predeterminado es `0` (sin lotes).

* **privacyDefault**

   * `optedin`: las visitas se envían inmediatamente.
   * `optedout`: las visitas se descartarán.
   * `optunknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      El valor predeterminado es `optedin`.

      >[!TIP]
      >
      >Esto sólo establece el valor predeterminado. Si este valor se establece o se cambia en el código, el valor definido por el código se guarda en el almacenamiento local y se utiliza a partir de ahora hasta que se cambie o hasta que la aplicación se desinstale y vuelva a instalarse.

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

   (**Requerido por Destinatario**) Su código de cliente asignado.

* **timeout**

   Determina cuánto tiempo espera Target una respuesta.

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

