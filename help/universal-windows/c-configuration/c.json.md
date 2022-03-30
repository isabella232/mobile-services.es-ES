---
description: Información para ayudarle a utilizar el archivo de configuración JSON de ADBMobile.
solution: Experience Cloud Services,Analytics
title: Configuración de ADBMobileConfig.json
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 44%

---

# Archivo de configuración ADBMobileConfig.json {#adbmobileconfig-json-config}

Información para ayudarle a utilizar el archivo de configuración JSON de ADBMobile.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Los métodos de configuración llevan el prefijo &quot;Config&quot;.

* **rsids**

   (**Requerido por Analytics**) Uno o más grupos de informes para recibir datos de Analytics. Las ID de varios grupos de informes deben separarse con comas sin espacios entre ellos.

   * Esta es la sintaxis para este método:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Necesario para Analytics y Gestión de público**). Servidor de Analytics o Gestión de público, basado en el nodo principal. Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `"https://"` o `"https://"`. La biblioteca gestiona automáticamente el prefijo de protocolo en función de la variable `ssl` variable.

   Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **charset**

   Define el conjunto de caracteres que utiliza para los datos enviados a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes. Para obtener más información, consulte la [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=es) en la documentación de Adobe Analytics.

* **ssl**

   Habilita (`true`) o deshabilita (`false`) que envía datos de medición a través de SSL (`HTTPS`). El valor predeterminado es `false`.

* **offlineEnabled**

   Cuando está activado (`true`), las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde, cuando el dispositivo está en línea. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

   Si las marcas de hora están habilitadas en el grupo de informes, la variable `offlineEnabled` propiedad configuration *must* be `true`. Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor `false`.

   Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes tiene habilitada la marca de fecha y hora, póngase en contacto con el Servicio de atención al cliente. Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite configurar un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp` variable.

   El valor predeterminado es `false`.

* **lifecycleTimeout**

   Especifica la duración en segundos que debe transcurrir entre el momento en que se inicia la aplicación, antes de que el inicio se considere una sesión nueva. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión.

   El valor predeterminado es 300 segundos.

* **batchLimit**

   Envíe visitas en lotes.

   Por ejemplo, si se configura como `50`, las visitas se ponen en cola hasta que se almacenan 50 y luego se envían todas. Requiere `offlineEnabled=true`y el valor predeterminado es `0` (Sin agrupamiento).

* **privacyDefault**

   Las opciones son:

   * `optedin`: las visitas se envían inmediatamente.
   * `optedout`: las visitas se descartarán.
   * `optunknown` : Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (entonces se envían las visitas) u excluido (entonces se descartan las visitas). Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      Esto establece únicamente el valor predeterminado. Si este valor se establece o se cambia en el código, el valor definido por el código se guarda en el almacenamiento local y se utiliza en adelante hasta que se cambie, o hasta que la aplicación se desinstale y se vuelva a instalar.

      El valor predeterminado es `optedin`.

* **poi**

   Cada matriz de punto de interés (POI) guarda su nombre, latitud, longitud y radio del área (en metros). El nombre del punto puede ser cualquier cadena. Cuando se envía una llamada a `trackLocation`, si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto que se envía junto con la llamada a `trackLocation`.

   * Este es un ejemplo de código para esta variable:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Requerido por Target**) Su código de cliente asignado.

* **timeout**

   Determina cuánto tiempo espera Target una respuesta.

El siguiente es un ejemplo de `ADBMobileConfig.json` archivo:

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
