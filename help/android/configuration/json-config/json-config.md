---
description: Esta información le ayuda a utilizar el archivo de configuración ADBMobile.json.
seo-description: Esta información le ayuda a utilizar el archivo de configuración ADBMobile.json.
seo-title: Configuración JSON de ADBMobile
solution: Experience Cloud,Analytics
title: Configuración JSON de ADBMobile
topic: Desarrollador e implementación
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: ht
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Archivo de configuración JSON de ADBMobile {#adbmobile-json-config}

Esta información le ayuda a comprender las variables del archivo de configuración ADBMobile.json.

## Referencia del archivo de configuración `ADBMobileConfig.json` {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

El mismo archivo de configuración puede utilizarse para su aplicación en varias plataformas:

>[!TIP]
>
>En **Android**, el archivo `ADBMobileConfig.json` debe colocarse en la carpeta `assets`.

Esta es una lista de las variables del archivo JSON y la versión mínima del SDK que necesita para cada variable:

* **acquisition**
   * Versión mínima del SDK: 4.1
   * Habilita la adquisición de aplicación móvil.
      * `server`, que es el servidor de adquisición que se comprueba durante el primer inicio para buscar un referente de adquisición.
      * `appid`, que es el ID generado que identifica de forma exclusiva esta aplicación en el servidor de adquisición.
   Si falta esta sección, habilite la adquisición de aplicación móvil y descargue de nuevo el archivo de configuración del SDK. Para obtener más información, consulte *referrerTimeout* en esta lista de variables.

* **analyticsForwardingEnabled**
   * La versión mínima del SDK es 4.8.0.
   * El valor predeterminado es `false`.

      La propiedad en el objeto `audienceManager`. Si Audience Manager está configurado y `analyticsForwardingEnabled` está establecido en `true`, todo el tráfico de Analytics se reenvía también a Audience Manager.

* **backdateSessionInfo**
   * Versión mínima del SDK: 4.6.
   * Activa/desactiva la capacidad de antedatar coincidencias de información de sesión del SDK de Adobe.

      Actualmente, las coincidencias de información de la sesión se componen de errores y de la duración de sesión, y se pueden habilitar o deshabilitar.

      **Habilitar o deshabilitar coincidencias**

      * Si establece el valor en `false`, las coincidencias quedarán **deshabilitadas**. El SDK vuelve al comportamiento previo a la versión 4.1, que consiste en agrupar la información de la sesión anterior con la primera coincidencia de la sesión subsiguiente. El SDK de Adobe también adjunta la información de la sesión al ciclo de vida actual, lo que evita que se cree una visita inflada. Dado que dejan de crearse visitas infladas, se produce un descenso inmediato en el recuento de visitas.

      * Si no proporciona ningún valor, el predeterminado será `true`, y las coincidencias quedarán **habilitadas**. Cuando las visitas están activadas, el SDK de Adobe antedata la visita de información de sesión a 1 segundo después de la visita final en la sesión anterior. Esto significa que los datos de bloqueos y de sesión estarán correlacionados con la fecha correcta en la que se produjeron. Un efecto secundario es que el SDK podría crear una visita para la visita antedatada. En cada nuevo uso de la aplicación, se antedatará una coincidencia.

         >[!IMPORTANT]
         >
         >La información antedatada de visitas de sesión se envía en una llamada al servidor de información de sesión y podrían aplicarse llamadas de servidor adicionales.

* **batchLimit**
   * Versión mínima del SDK: 4.1
   * Umbral del número de visitas que se envían en llamadas consecutivas.

      Por ejemplo, si `batchLimit` se establece en 10, las visitas anteriores a la décima se almacenarán en la cola. Cuando llega la décima, las 10 visitas se envían de forma consecutiva.

      Recuerde la información siguiente:

      * El valor predeterminado es `0`, lo que significa que no se permite el agrupamiento.
      * Requiere `offlineEnabled = true`.

* **charset**
   * Versión mínima del SDK: 4.0
   * Define el conjunto de caracteres que utiliza para los datos que se envían a Analytics.

      El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes.

* **clientCode**
   * Versión mínima del SDK: 4.0
   * Su código de cliente asignado.

      >[!IMPORTANT]
      >
      >Target requiere esta variable.

* **coopUnsafe**
   * Versión mínima del SDK: 4.16.1
   * La propiedad booleana del objeto de `marketingCloud` que, cuando se establece en `true`, hará que el dispositivo sea excluido de la Device Co-Op de Experience Cloud.
   * El valor predeterminado es `false`.
   * Este ajuste **solo** se utiliza para clientes proporcionados por Device Co-op.
   Para los miembros de Device Co-op que necesitan que este valor se establezca en `true`, necesitará colaborar con el equipo de Co-op para solicitar un marcador de lista negra en su cuenta de Device Co-op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

   Recuerde la información siguiente:

   * Cuando `coopUnsafe` está establecido en `true`, `coop_unsafe=1` se añadirá siempre a las coincidencias de Audience Manager y Visitor ID.
   * Si activa el reenvío del lado del servidor de Analytics a Audience Manager, también verá `coop_unsafe=1` en las coincidencias de Analytics.


* **environmentId**
   * Versión mínima del SDK: 4.14
   * La identificación del entorno que desea utilizar.

      Puede especificar una identificación válida (`environmentId=8`) y, si `environmentId` no está incluida, se utilizará el entorno de producción predeterminado.

* **lifecycleTimeout**
   * Versión mínima del SDK: 4.0
   * El valor predeterminado es 300 segundos.

      Especifica el tiempo en segundos que debe transcurrir entre inicios de la aplicación para que el inicio se considere una nueva sesión. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva.

      El tiempo que la aplicación permanece en segundo plano no se incluye en la duración de la sesión.

* **messages**

   * Versión mínima del SDK: 4.2
   * Lo genera automáticamente Adobe Mobile Services y define la configuración para la mensajería en la aplicación. Para obtener más información, consulte la sección *Descripción de mensajes*, más adelante.

* **offlineEnabled**

   * Versión mínima del SDK: 4.0
   * Cuando está activado, las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde, cuando el dispositivo se conecta.

      El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión.

      El valor predeterminado es `false`.

      >[!IMPORTANT]
      >
      >Si estas marcas se encuentran habilitadas en el grupo de informes, la propiedad de configuración `offlineEnabled` **debe** ser verdadera. Si no están habilitadas, la propiedad `offlineEnabled` **debe** tener el valor false.
      >
      >Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se han habilitado las marcas de fecha y hora, póngase en contacto con Customer Care o descargue el archivo de configuración desde Adobe Mobile Services.

      Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite establecer un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp`.

* **org**

   * Versión mínima del SDK: 4.3
   * Especifica el ID de organización de Experience Cloud para el servicio de ID.

* **poi**
   * Versión mínima del SDK: 4.0
   * Cada matriz de punto de interés (POI) guarda su nombre, latitud, longitud y radio del área del punto, en metros.

      El nombre del punto puede ser cualquier cadena. Cuando se envía una llamada a `trackLocation`, si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto que se envía junto con la llamada a `trackLocation`.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      A partir de la versión 4.2, los puntos de interés se definen en la interfaz de Adobe Mobile y se sincronizan de forma dinámica con el archivo de configuración de la aplicación. Esta sincronización requiere el ajuste `analytics.poi`:

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      Si el ajuste no está configurado, se debe actualizar el archivo `ADBMobile.json` para que incluya esta línea. Para descargar un archivo de configuración actualizado, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

* **postback**
   * Versión mínima del SDK: 4.6
   * Esta es la definición de la plantilla de mensaje "llamada de retorno":

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      El objeto `payload` del código es una carga útil de ejemplo para una definición de mensaje que se incluye en el archivo `ADBMobileConfig.json`. Para obtener más información, consulte [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * Versión mínima del SDK: 4.0
   * El valor predeterminado es `optedin`.
      * Con `optedin`, las visitas se envían inmediatamente.
      * Con `optedout`, las visitas se descartan.
      * Con `optunknown`, si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).
      Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a `optedin`.  Esto solo establece el valor inicial. Si este valor se establece o se cambia en el código, el nuevo valor se utiliza hasta que se cambia de nuevo, o hasta que la aplicación se desinstala y reinstala.


* **referrerTimeout**
   * Versión mínima del SDK: 4.1
   * Tiempo máximo en segundos que el SDK espera los datos de referente de adquisición durante el primer inicio. Si utiliza adquisición, recomendamos un tiempo de espera de 5 segundos.

      >[!IMPORTANT]
      >
      >La adquisición requiere esta variable. Si la variable se establece en `0` o no se incluye, el SDK no espera datos de adquisición y no se realiza un seguimiento de las métricas de adquisición.

* **remotes**
   * Versión mínima del SDK: 4.2
   * Se configura automáticamente y define los puntos finales alojados por Adobe para los archivos de configuración dinámica.

      En cada inicio se compara el momento de la última actualización de cada archivo de configuración con la versión actual, y las actualizaciones se descargan y se guardan.
      * `analytics.poi` es el punto final para la configuración de puntos de interés alojados.
      * `messages` es el punto final para la configuración de mensajes en la aplicación alojados.

* **rsids**
   * Versión mínima del SDK: 4.0
   * Uno o más grupos de informes para recibir datos de Analytics. Los ID de grupos de informes deben separarse con comas, sin espacios intermedios.

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Analytics requiere esta variable.

* **server**
   * Versión mínima del SDK: 4.0
   * El servidor de Analytics o Audience Manager, basado en el nodo principal. Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `https://` o `https://`. Este prefijo lo gestiona automáticamente la biblioteca y se basa en la variable `ssl`. Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

* **ssl**
   * Versión mínima del SDK: 4.0
   * El valor predeterminado es `false`.

      Habilita (`true`) o deshabilita (`false`) la capacidad para enviar datos de medición mediante SSL (HTTPS).

      Abajo se muestra la definición de la plantilla de mensaje "llamada de retorno":

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * Versión mínima del SDK: 4.0
   * Determina cuánto tiempo espera Target una respuesta.


## Archivo de muestra `ADBMobileConfig.json` {#section_4655EF79744649E5A5AE19E3224C472C}

Aquí tiene un archivo `ADBMobileConfig.json` de ejemplo:

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## Descripción de mensajes {#section_B97D654BA92149CE91F525268D7AD71F}

Adobe Mobile Services genera automáticamente el nodo de mensajes y no suele ser necesario cambiarlo de forma manual. Se proporciona la siguiente descripción con propósitos de solución de problemas:

* "messageId"
* ID generado, requerido
* "template"
   * "alert", "fullscreen" o "local"
   * requerido

* "showOffline"
   * true o false
   * el valor predeterminado es false

* "showRule"
   * "always", "once" o "untilClick"
   * requerido

* "endDate"
   * número de segundos desde el 1 de enero de 1970
   * el valor predeterminado es 2524730400

* "startDate"
   * número de segundos desde el 1 de enero de 1970
   * el valor predeterminado es 0

* "payload"
   * "html"
      * solo plantilla de pantalla completa, requerido
      * html que define el mensaje
   * "image"
      * solo pantalla completa, opcional
      * url de la imagen a utilizar para una imagen de pantalla completa
   * "altImage"
      * solo pantalla completa, opcional
      * nombre de la imagen agrupada a usar si la url especificada en
         * image
         * no está disponible
   * "title"
      * pantalla completa y alerta, requerido
      * texto del título de un mensaje de pantalla completa o alerta
   * "content"
      * alerta y notificación local, requerido
      * subtexto para un mensaje de alerta, o texto de notificación para un mensaje de notificación local
   * "confirm"
      * alerta, opcional
      * texto usado en el botón de confirmar
   * "cancel"
      * alerta, requerido
      * texto usado en el botón de cancelar
   * "url"
      * alerta, opcional
      * acción url a cargar si se hace clic en el botón de confirmar
   * "wait"
      * notificación local, requerido
      * tiempo a esperar (en segundos) para publicar la notificación local después de cumplir sus criterios



* "audiences"
   * matriz de objetos que define cómo se debería mostrar el mensaje
   * "key"
      * nombre de variable a buscar en la visita, requerido
* "matches"
   * tipo de operador de coincidencia utilizado al hacer la comparación
   * eq = es igual a
   * ne = no es igual a
   * co = contiene
   * nc = no contiene
   * sw = comienza con
   * ew = termina con
   * ex = existe
   * nx = no existe
   * lt = menor que
   * le = menor o igual que
   * gt = mayor que
   * ge = mayor o igual que
* "values"
   * una matriz de valores que se utiliza para comparar el valor de la variable nombrada en
      * key
      * utilizando el tipo de operador de coincidencia de
      * matches
* "triggers"
   * como las audiencias, aunque esta es la acción, no la audiencia
   * "key"
   * "matches"
   * "values"
