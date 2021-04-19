---
description: Esta es una lista de métodos de TVJS que proporciona la biblioteca tvOS.
seo-description: Esta es una lista de métodos de TVJS que proporciona la biblioteca tvOS.
seo-title: Métodos de TVJS
solution: Experience Cloud,Analytics
title: Métodos de TVJS
topic-fix: Developer and implementation
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
exl-id: 4e0c6a29-953d-49fc-b44f-533dd393ffb1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 100%

---

# Métodos de TVJS {#tvjs-methods}

Esta es una lista de métodos de TVJS que proporciona la biblioteca tvOS.

## Métodos de configuración {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Devuelve la versión actual de la biblioteca de Adobe Mobile.

   * Esta es la sintaxis para este método:

      ```objective-c
      version()
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Devuelve: `String`

* **privacyStatus**

   Arroja la representación de NSUInteger del estado de privacidad del usuario actual.

   Estas son las opciones:

   * `ADBMobilePrivacyStatusOptIn`: Las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: Se descartan las visitas.
   * `ADBMobilePrivacyStatusUnknown`: si el seguimiento en línea está activado, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in. El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Esta es la sintaxis para este método:

      ```objective-c
      privacyStatus()
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Devuelve: `Number`

* **setPrivacyStatus**

   Establece el estado de privacidad del usuario actual en uno de los siguientes valores:

   * `ADBMobilePrivacyStatusOptIn`: Las visitas se envían inmediatamente.
   * `ADBMobilePrivacyStatusOptOut`: Se descartan las visitas.
   * `ADBMobilePrivacyStatusUnknown`: Si el seguimiento en línea está activado, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

   Si el seguimiento en línea no está activado, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Esta es la sintaxis para este método:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es `0`.

   * Esta es la sintaxis para este método:

      ```objective-c
      lifetimeValue()
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Devuelve: `Number`

* **userIdentifier**

   Devuelve el identificador del usuario si se ha establecido uno personalizado. Devuelve “nil” si no se ha establecido un identificador personalizado. El valor predeterminado es `nil`.

   >[!IMPORTANT]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. Esto preserva los datos de visitante al actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario es nil hasta que se establece.

   * Esta es la sintaxis para este método:

      ```objective-c
      userIdentifier()
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Devuelve: `String`

* **setUserIdentifier**

   Establece el identificador de usuario.

   * Esta es la sintaxis para este método:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Devuelve: N/A

   * Parámetro:  `userID`

      * Tipo: String
      * Nuevo identificador de este usuario.

* **setAdvertisingIdentifier**

   Establece el IDFA en el SDK y, si se ha establecido en el SDK, el IDFA se envía durante el ciclo vital. También se puede acceder al IDFA en Señales (Postbacks).

   >[!IMPORTANT]
   >
   >Recupere el IDFA desde las API de Apple solo si está utilizando un servicio publicitario. Si recupera el IDFA y no lo utiliza de forma apropiada, podría rechazarse la aplicación.

   * Esta es la sintaxis para este método:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Devuelve: N/A
   * Parámetro: `idfa`
      * Tipo: `String`
      * IDFA obtenido de la API de Apple.

* **setDebugLogging**

   Establece la preferencia de registro de depuración.

   * Esta es la sintaxis para este método:

      ```objective-c
      setDebugLogging(logging)
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Devuelve: N/A
   * Parámetros: `logging`
      * Tipo: `Bool`
      * Valor que indica si el SDK de Adobe debe registrarse en la consola de depuración.


## Métodos de Analytics {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. Los estados son las visualizaciones disponibles en su aplicación, como el tablero de inicio, la configuración de la aplicación, el carrito, etcétera. Estos estados son similares a las páginas de un sitio web y las llamadas trackState incrementan las visualizaciones de página.

   Si el estado está vacío, en los informes se muestra app name app version (build). Si observa este valor en los informes, asegúrese de que establece el estado en cada llamada a trackState.

   >[!TIP]
   >
   >Esta es la única llamada de seguimiento que incrementa las visualizaciones de página.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Devuelve: N/A
      * Parámetro: `stateName`
         * Tipo: `String`
         * Nombre del estado de la página
      * Parámetro: `contextData`
         * Tipo: objeto
         * Datos de contexto adicionales para esta visita.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Realiza el seguimiento de una acción en la aplicación. Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, inicios de sesión, toques en banners, suscripciones a fuentes y otras métricas.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Devuelve: N/A
      * Parámetros: `actionName`
         * Tipo: String
         * Nombre de la acción que se está rastreando.
      * Parámetro: `contextData`
         * Tipo: objeto
         * Datos de contexto adicionales para esta visita.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Envía las coordenadas de latitud y longitud actuales.

   También utiliza puntos de interés (POI) definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Devuelve: N/A
      * Parámetro: `lat`
         * Tipo: número
         * Latitud de la ubicación.
      * Parámetro: `lon`
         * Tipo: número
         * Longitud de la ubicación.
      * Parámetro: `contextData`
         * Tipo: objeto
         * Datos de contexto adicionales para esta visita.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Agrega una cantidad al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Devuelve: N/A
      * Parámetro: `increaseAmount`
         * Tipo: número
         * Cantidad que se debe agregar al valor de duración actual del usuario.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Inicia una acción temporizada con acción de nombre. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Devuelve: N/A
      * Parámetro: `name`
         * Tipo: String
         * Nombre de la acción temporizada que se está iniciando.
      * Parámetro: `contextData`
         * Tipo: objeto
         * Datos de contexto adicionales para esta visita.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Se transfieren datos para actualizar los datos de contexto asociados con la acción determinada.

   Los datos que se transfieren se anexan a los ya existentes para la acción determinada. Si la misma clave ya está definida, los datos se sobrescriben.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Devuelve: N/A
      * Parámetro: `name`
         * Tipo: String
         * Nombre de la acción temporizada que se está actualizando.
      * Parámetro: `contextData`
         * Tipo: objeto
         * Datos de contexto adicionales para esta visita.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Finaliza una acción temporizada.

   Si proporciona una función de llamada de retorno, puede acceder a los valores de hora definitivos. Si no se proporciona ninguna llamada de retorno o si la llamada de retorno arroja un valor true, el SDK de Adobe envía una visita automáticamente. Cuando la llamada de retorno devuelve un valor false, la visita de la acción temporizada se suprime.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Devuelve: N/A
      * Parámetros: `name`
         * Tipo: String
         * Nombre de la acción temporizada que se está finalizando.
      * Parámetro: `callback`
         * Tipo: `function(inAppDuration, totalDuration, data)`
         * Método de llamada de retorno que tiene como parámetros `inAppDuration` (número), `totalDuration` (número), y `data` (objeto de datos de contexto).

            Puede suprimir el envío al SDK de la última visita devolviendo un valor `false` en su función de llamada de retorno.
      * Este es un ejemplo de código para este método:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Devuelve si la acción temporizada está en progreso o no.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Devuelve: Bool
      * Parámetro: `name`
         * Tipo: `String`
         * Nombre de la acción temporizada para la que debe comprobar la existencia.
   * Este es un ejemplo de código para este método:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Devuelve el identificador de visitante generado automáticamente.

   Se trata de un ID único de visitante y específico para la aplicación que generan los servidores de Adobe. Si no se puede acceder a los servidores de Adobe en el momento de la generación, el ID se genera mediante la CFUUID de Apple. El valor se genera en el primer inicio y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación, se guarda y se restaura durante el proceso de copia de seguridad de la aplicación estándar y se elimina al desinstalarla.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. Esto preserva los datos de visitante al actualizar el SDK. Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario tiene el valor `nil` y se utiliza el identificador de seguimiento. Para obtener más información, consulte abajo la fila userIdentifier.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackingIdentifier()
      ```

      * Devuelve: `String`
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Fuerza la biblioteca a enviar todas las visitas en la cola sin conexión, sin importar cuántas haya en la cola.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Devuelve: N/A
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Borra todas las visitas de la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackingClearQueue()
      ```

      * Devuelve: N/A
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Recupera el número de visitas que hay actualmente en la cola sin conexión.

   * Esta es la sintaxis para este método:

      ```objective-c
      trackingGetQueueSize()
      ```

      * Devuelve: número
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Métodos de Audience Manager {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Devuelve el perfil del visitante que se haya obtenido más recientemente.

   Devuelve null si todavía no se ha enviado ninguna señal. El perfil del visitante está guardado en `NSUserDefaults` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```objective-c
      audienceVisitorProfile()
      ```

      * Devuelve: objeto
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   Devuelve el DPID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      audienceDpid()
      ```

      * Devuelve: String
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   Devuelve el DPUUID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      audienceDpuuid()
      ```

      * Devuelve: `String`
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   Establece dpid y dpuuid. Si están establecidos, se envían con cada señal.

   * Esta es la sintaxis para este método:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Devuelve: N/A
      * Parámetro: `dpid`
         * Tipo: `String`
         * ID de proveedor de datos de Audience Manager.
      * Parámetro: `dpuuid`
         * Tipo: `String`
         * Identificador para la combinación de usuario y proveedor de datos.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Envía a Audience Manager una señal con características y obtiene una devolución de los segmentos coincidentes en una función de llamada de retorno.

   * Esta es la sintaxis para este método:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Parámetro: `traits`
         * Tipo: objeto
         * Diccionario de características para este usuario.
      * Parámetro: `callback`
         * Tipo: función(perfil)
         * El perfil arrojado por el Audience Manager en el parámetro de la función de llamada de retorno.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Restaura el UUID de Audience Manager y purga el perfil del visitante actual.

   * Este es un ejemplo de código para este método:

      ```objective-c
      audienceReset()
      ```

      * Devuelve: N/A
      * Parámetro: Ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## Métodos del servicio de ID {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Recupera el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Devuelve: String
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Además del Experience Cloud ID, puede establecer los ID de cliente adicionales que se pueden asociar a cada visitante. La API de visitante acepta varios ID de cliente para el mismo visitante, con un identificador de tipo de cliente para separar el ámbito de los distintos ID de cliente. Este método corresponde a setCustomerIDs en la biblioteca JavaScript.

   * Esta es la sintaxis para este método:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Devuelve: N/A
      * Parámetro: `identifiers`

         * Tipo: `Object`
         * Identificadores para sincronizar con el servicio de ID del usuario actual.
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   Sincroniza los identificadores proporcionados con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Devuelve: N/A
      * Parámetros: `identifiers`
         * Tipo: `Object`
         * Identificadores para sincronizar con el servicio de ID del usuario actual.
      * Parámetro: `authState`
         * Tipo: ADBMobileVisitorAuthenticationState
         * El estado de autenticación del usuario y los valores posibles incluyen:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   Sincroniza el tipo de identificador y el valor proporcionados con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Devuelve: N/A
      * Parámetro: `idType`
         * Tipo: `String`
         * Tipo de identificador que está sincronizando.
      * Parámetro: `identifier`
         * Tipo: `String`
         * Valor del identificador que está sincronizando.
      * Parámetro: `authState`
         * Tipo: Estado de autenticación del usuario ADBMobileVisitorAuthenticationState
Authentication. Entre los posibles valores están:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   Recupera una matriz de objetos ADBVisitorID de solo lectura. La siguiente muestra de código es un ejemplo de objeto VisitorID:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Esta es la sintaxis para este método:

      ```objective-c
      visitorGetIDsJs()
      ```

      * Devuelve: `Array [Object]`

      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Métodos de Target {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Devuelve el ID de terceros.

   * Esta es la sintaxis para este método:

      ```objective-c
      targetThirdPartyID()
      ```

      * Devuelve: `String`
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Establece el ID de terceros.

   * Esta es la sintaxis para este método:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Devuelve: N/A
      * Parámetros: `thirdPartyID`
         * Tipo: `String`
         * ID de tercero para usar en solicitudes de destino.
   * Este es un ejemplo de código para este método:

   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Devuelve el valor de PcID.

   * Esta es la sintaxis para este método:

      ```objective-c
      targetPcID()
      ```

      * Devuelve: `String`
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Devuelve el ID de sesión.

   * Esta es la sintaxis para este método:

      ```objective-c
      targetSessionID()
      ```

      * Devuelve: `String`
      * Parámetros: ninguno
   * Este es un ejemplo de código para este método:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
