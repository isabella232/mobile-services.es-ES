---
description: Esta información le ayuda a utilizar el archivo de configuración ADBMobile.json.
seo-description: Esta información le ayuda a utilizar el archivo de configuración ADBMobile.json.
seo-title: Configuración JSON de ADBMobile
solution: Experience Cloud,Analytics
title: Configuración JSON de ADBMobile
topic-fix: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
exl-id: e3515de3-3aec-4dd0-996d-9c561ad1b1de
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 100%

---

# Configuración JSON de ADBMobile {#adbmobile-json-config}

Esta información le ayuda a utilizar el archivo de configuración `ADBMobile.json`.

## Referencia del archivo de configuración ADBMobileConfig.json {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

El mismo archivo de configuración puede utilizarse para su aplicación en varias plataformas:

>[!TIP]
>
>En **iOS**, el archivo `ADBMobileConfig.json` puede colocarse en cualquier parte accesible del paquete.

* **adquisición**

   Habilita la adquisición de aplicación móvil.

   Si falta esta sección, habilite la adquisición de aplicación móvil y descargue de nuevo el archivo de configuración del SDK. Para obtener más información, consulte *referrerTimeout* más adelante.

   * `server`: servidor de adquisición que se comprueba durante el primer inicio para buscar un referente de adquisición.
   * `appid`: ID generado que identifica de forma exclusiva esta aplicación en el servidor de adquisición.
   * Versión mínima del SDK: 4.1

* **analyticsForwardingEnabled**

   La propiedad en el objeto `audienceManager`. Si `Audience Manager` está configurado y `analyticsForwardingEnabled` está establecido en `true`, todo el tráfico de Analytics se reenvía también a Audience Manager. El valor predeterminado es `false`.

   * Versión mínima del SDK: 4.8.0

* **backdateSessionInfo**

   Activa/desactiva la capacidad de antedatar coincidencias de información de sesión del SDK de Adobe.

   En este momento, las visitas a la información de sesión se realizan sobre bloqueos y duración de la sesión, y pueden habilitarse o deshabilitarse.

   * Si establece el valor en `false`, las coincidencias quedarán **deshabilitadas**.

      El SDK vuelve a su comportamiento anterior a la versión 4.1 de agrupar la información de sesión de la sesión anterior con la primera visita de la sesión siguiente. El SDK de Adobe también adjunta la información de la sesión al ciclo vital actual, lo que evita la creación de una visita inflada. Dado que ya no se crean visitas infladas, disminuye de inmediato la cantidad de visitas.

   * Si no proporciona ningún valor, el predeterminado será `true`, y las coincidencias quedarán **habilitadas**.

      Cuando las visitas están activadas, el SDK de Adobe antepone la visita de información de sesión a 1 segundo después de la última visita de la sesión anterior. Esto significa que los datos de bloqueo y sesión se correlacionarán con la fecha correcta cuando se produjeron. Un efecto secundario es que el SDK puede crear una visita para la visita con fecha anterior. En cada nuevo uso de la aplicación, se antedatará una coincidencia.

   * Versión mínima del SDK: 4.6
   >[!IMPORTANT]
   >
   >La información antedatada de visitas de sesión se envía en una llamada al servidor de información de sesión; podrían aplicarse llamadas de servidor adicionales.


* **batchLimit**

   Umbral del número de visitas que se envían en llamadas consecutivas. Por ejemplo, si `batchLimit` se establece en 10, las visitas anteriores a la décima se almacenarán en la cola. Cuando llega la décima, las 10 visitas se envían de forma consecutiva.

   * El valor predeterminado es `0`, lo que significa que no se permite el agrupamiento.
   * Requiere `offlineEnabled = true`.
   * Versión mínima del SDK: 4.1

* **charset**

   Define el conjunto de caracteres que utiliza para los datos que se envían a Analytics. El conjunto de caracteres se utiliza para convertir los datos entrantes a UTF-8 para su almacenamiento y la elaboración de informes. Para obtener más información, consulte [s.charSet](https://docs.adobe.com/content/help/es-ES/analytics/implementation/vars/config-vars/charset.html).

   * Versión mínima del SDK: 4.0

* **clientCode**

   Su código de cliente asignado.

   >[!IMPORTANT]
   >
   >Target requiere esta variable.

   * Versión mínima del SDK: 4.0

* **coopUnsafe**

   Para los miembros de Device Co-op que necesitan que este valor se establezca en `true`, necesitará colaborar con el equipo de Co-op para solicitar un marcador de lista negra en su cuenta de Device Co-op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

   Recuerde la información siguiente:

   * Cuando `coopUnsafe` está establecido en `true`, `coop_unsafe=1` se añadirá siempre a las coincidencias de Audience Manager y Visitor ID.
   * Si activa el reenvío del lado del servidor de Analytics a Audience Manager, también verá `coop_unsafe=1` en las coincidencias de Analytics.

   Alguna información adicional:

   * Versión mínima del SDK: 4.16.1
   * La propiedad booleana del objeto de `marketingCloud` que, cuando se establece en `true`, hará que el dispositivo sea excluido de la Device Co-Op de Experience Cloud.
   * El valor predeterminado es `false`.
   * Este ajuste **solo** se utiliza para clientes proporcionados por Device Co-op.



* **environmentId**

   La identificación del entorno que desea utilizar. Puede especificar una identificación válida (`environmentId=8`) y, si `environmentId` no está incluida, se utilizará el entorno de producción predeterminado.

   * Versión mínima del SDK: 4.14

* **lifecycleTimeout**

   El valor predeterminado es 300 segundos.

   Especifica la duración en segundos que debe transcurrir entre el momento en que se inicia la aplicación, pero antes de que el inicio se considere una sesión nueva. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión.

   * Versión mínima del SDK: 4.0

* **messages**

   Generado automáticamente por Adobe Mobile Services, define la configuración de la mensajería en la aplicación. Para obtener más información, consulte la sección *Descripción de los mensajes* a continuación.

   * Versión mínima del SDK: 4.2

* **offlineEnabled**

   Cuando está activado, las visitas se ponen en cola mientras el dispositivo está sin conexión y se envían más tarde, cuando el dispositivo se conecta. El grupo de informes debe tener habilitada la marca de fecha y hora para poder utilizar el seguimiento sin conexión. El valor predeterminado es `false`.

   Información importante:

   * Si estas marcas se encuentran habilitadas en el grupo de informes, la propiedad de configuración `offlineEnabled` *debe* ser verdadera.
   * Si no están habilitadas, la propiedad `offlineEnabled` *debe* tener el valor false.

      Si esta configuración no se realiza correctamente, se perderán datos. Si no está seguro de si un grupo de informes se ha habilitado para las marcas de tiempo,   póngase en contacto   con el servicio de atención al cliente o descargue el archivo de configuración desde Adobe Mobile Services. Si está enviando datos de AppMeasurement a un grupo de informes que también recopila datos de JavaScript, tal vez necesite establecer un grupo de informes independiente para datos móviles o incluir una marca de fecha y hora personalizada en todas las visitas de JavaScript que utilicen la variable `s.timestamp`.

   * Versión mínima del SDK: 4.0

* **org**

   Especifica el ID de organización de Experience Cloud para el servicio de ID de Adobe Experience Platform.

   * Versión mínima del SDK: 4.3

* **poi**

   Cada matriz de punto de interés (POI) guarda su nombre, latitud, longitud y radio del área (en metros). El nombre del punto puede ser cualquier cadena. Cuando se envía una llamada a `trackLocation`, si las coordinadas actuales se encuentran dentro de un punto de interés definido, se rellena una variable de datos de contexto que se envía junto con la llamada a `trackLocation`.

   * Versión mínima del SDK: 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >A partir de la versión 4.2, los puntos de interés se definen en la interfaz de Adobe Mobile y se sincronizan de forma dinámica con el archivo de configuración de la aplicación. Esta sincronización requiere el ajuste `analytics.poi`:

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Si el ajuste no está configurado, se debe actualizar el archivo `ADBMobile.json` para que incluya esta línea. Para descargar un archivo de configuración actualizado, consulte [Antes de comenzar](/help/ios/getting-started/requirements.md).

* **postback**

   Abajo se muestra la definición de la plantilla de mensaje &quot;llamada de retorno&quot;:

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   El objeto `payload` del código es una carga útil de ejemplo para una definición de mensaje que irían en el archivo `ADBMobileConfig.json`. Para obtener más información, consulte [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versión mínima del SDK: 4.6

* **privacyDefault**

   * Con `optedin`, las visitas se envían inmediatamente.
   * Con `optedout`, las visitas se descartan.
   * Con `optunknown`, si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      Esto solo establece el valor inicial. Si este valor se establece o se cambia en el código, el nuevo valor se utiliza hasta que se cambia de nuevo, o hasta que la aplicación se desinstala y reinstala. El valor predeterminado es `optedin`.

   * Versión mínima del SDK: 4.0

* **referrerTimeout**

   Cantidad de segundos que el SDK espera los datos del remitente del reenvío de adquisición durante el primer inicio antes de que se agote el tiempo de espera. Si utiliza adquisición, le recomendamos un tiempo de espera de 5 segundos.

   >[!IMPORTANT]
   >
   >La adquisición requiere esta variable. Si la variable se establece en `0` o no se incluye, el SDK no espera datos de adquisición y no se realiza un seguimiento de las métricas de adquisición.

   * Versión mínima del SDK: 4.1

* **remotes**

   Se configura automáticamente y define los puntos finales alojados por Adobe para los archivos de configuración dinámica. En cada inicio se compara el momento de la última actualización de cada archivo de configuración con la versión actual, y las actualizaciones se descargan y se guardan.

   * `analytics.poi` es el punto final para la configuración de puntos de interés alojados.

   * `messages` es el punto final para la configuración de mensajes en la aplicación alojados.

   * Versión mínima del SDK: 4.2

* **rsids**

   Uno o más grupos de informes para recibir datos de Analytics. Las ID de varios grupos de informes deben separarse con comas sin espacios entre ellos.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Analytics requiere esta variable.

   * Versión mínima del SDK: 4.0

* **server**

   El servidor de Analytics o Gestión de público, basado en el nodo principal.

   Esta variable se debe rellenar con el dominio del servidor, sin incluir los prefijos de protocolo `https://` o `https://`. Este prefijo lo gestiona automáticamente la biblioteca y se basa en la variable `ssl`.

   Si `ssl` es `true`, se establece una conexión segura con el servidor. Si `ssl` es `false`, se establece una conexión con el servidor que no es segura.

   >[!IMPORTANT]
   >
   >Analytics o Gestión de público requieren esta variable.

   * Versión mínima del SDK: 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > A partir de la versión 4.10.0, el SSL tiene el valor predeterminado true si no se establece el indicador.

   Habilita (`true`) o deshabilita (`false`) la capacidad para enviar datos de medición mediante SSL (HTTPS).

   Abajo se muestra la definición de la plantilla de mensaje &quot;llamada de retorno&quot;:

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   El objeto `payload` del código es una carga útil de ejemplo para una definición de mensaje que se incluye en el archivo `ADBMobileConfig.json`. Para obtener más información, consulte [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Versión mínima del SDK: 4.0

* **timeout**

   Determina cuánto tiempo espera Target una respuesta.

   * Versión mínima del SDK: 4.0


## Archivo de muestra `ADBMobileConfig.json` {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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

Adobe Mobile Services genera automáticamente el nodo de mensajes y, por lo general, no es necesario cambiarlo en forma manual. Se proporciona la siguiente descripción para la resolución de problemas:

* &quot;messageId&quot;

   * ID generado, obligatorio

* &quot;plantilla&quot;

   * &quot;alert&quot;, &quot;full screen&quot; o &quot;local&quot;
   * obligatorio

* &quot;payload&quot;

   * &quot;html&quot;

      * solo la plantilla de pantalla completa, obligatorio
      * html que define el mensaje
   * &quot;imagen&quot;

      * solo pantalla completa, opcional
      * url de la imagen que se utilizará para una imagen de pantalla completa
   * &quot;altImage&quot;

      * solo pantalla completa, opcional
      * nombre de la imagen agrupada que se utilizará si la dirección URL especificada en
         `image` no está disponible
   * &quot;título&quot;

      * pantalla completa y alerta, obligatorio
      * texto del título para mensaje de pantalla completa o alerta
   * &quot;content&quot;

      * alerta y notificación local, obligatorio
      * subtexto para mensaje de alerta o texto de notificación para mensaje de notificación local
   * &quot;confirm&quot;

      * alerta, opcional
      * texto utilizado en el botón de confirmación
   * &quot;cancel&quot;

      * alerta, obligatorio
      * texto utilizado en el botón Cancelar
   * &quot;url&quot;

      * alerta, opcional
      * acción url que se cargará si se hace clic en el botón de confirmación
   * &quot;wait&quot;

      * notificación local, obligatorio
      * tiempo de espera (en segundos) para publicar la notificación local después de cumplir los criterios









* &quot;showOffline&quot;

   * true o false
   * el valor predeterminado es false

* &quot;showRule&quot;

   * &quot;always&quot;, &quot;once&quot; o &quot;untilClick&quot;
   * obligatorio

* &quot;endDate&quot;

   * cantidad de segundos desde el 1 de enero de 1970
   * el valor predeterminado es 2524730400

* &quot;startDate&quot;

   * cantidad de segundos desde el 1 de enero de 1970
   * el valor predeterminado es 0

* &quot;audiences&quot;

   Conjunto de objetos que define cómo debería mostrarse el mensaje:

   * &quot;key&quot;

      Nombre de la variable que se busca en la visita y que es obligatorio.

   * &quot;matches&quot;

      Tipo de emparejador utilizado al hacer la comparación:

      * eq = es igual que
      * ne = no es igual que
      * co = contiene
      * nc = no contiene
      * sw = empieza con
      * ew = termina con
      * ex = existe
      * nx = no existe
      * lt = menor que
      * le = menor o igual que
      * gt = mayor que
      * ge = mayor o igual que
   * &quot;values&quot;

      Conjunto de valores que se utiliza para comparar el valor de la variable nombrada en el siguiente:

      * key
      * con el tipo de coincidencia en
      * matches


* &quot;triggers&quot;

   Igual que las audiencias, pero estas son las acciones en lugar de la audiencia:

   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
