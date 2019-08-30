---
description: Puede utilizar métodos del complemento PhoneGap de iOS para completar diversas tareas.
keywords: android; library; mobile; sdk
seo-description: Puede utilizar métodos del complemento PhoneGap de iOS para completar diversas tareas.
seo-title: Métodos del complemento phonegap
solution: Marketing Cloud, Analytics
title: Métodos del complemento phonegap
topic: Desarrollador e implementación
uuid: bc 3 db 9 ce -81 b 7-45 ec -88 aa -6020 c 1 db 5 d 9 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Puede utilizar métodos del complemento PhoneGap de Android para completar diversas tareas.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Devuelve el estado de privacidad del usuario actual.

   Estos son los estados disponibles:

   * `ADB.optedIn`: Las visitas se envían inmediatamente.
   * `ADB.optedOut`: Las visitas se descartan.
   * `ADB.optUnknown`: Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan). **** Si el grupo de informes **no tiene** habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

      El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

   * Este es un ejemplo de código para este método:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* Método **setPrivacyStatus**

   Sets the privacy status for the current user to `status`.

   Puede establecer uno de los siguientes estados:

   * `ADB.optedIn`: Las visitas se envían inmediatamente.
   * `ADB.optedOut`: Las visitas se descartan.
   * `ADB.optUnknown`: Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan). **** Si el grupo de informes **no tiene** habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es 0.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. De forma predeterminada, el valor de esta variable es `false`.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtiene la versión de la biblioteca.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Devuelve el identificador de visitante generado automáticamente.

   Se trata de un ID de visitante exclusivo y específico para la aplicación que se genera durante el lanzamiento inicial y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación y se elimina al desinstalarla.

   >[!TIP]
   >
   >Si la aplicación se actualiza del SDK 3. x al 4. x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. Para obtener más información, consulte `getUserIdentifier`, más adelante. Este ID preserva los datos de visitante al actualizar el SDK.

   Para nuevas instalaciones sobre el SDK 4.x, el identificador de usuario tiene el valor `null` y se utiliza el identificador de seguimiento.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Si se ha establecido un identificador de usuario personalizado, devuelve este identificador; si no se ha establecido el identificador, devuelve `null`. El valor predeterminado es `null`.

   * Este es un ejemplo de código para este método:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Establece el identificador de usuario como `identifier`.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Establece el token del dispositivo para notificaciones push.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Esta es la sintaxis para este método:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Establece la preferencia de mantenimiento de sesión del ciclo vital.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Solo debe utilizar este método si la aplicación recibe notificaciones en segundo plano.

   * Este es un ejemplo de código para este método:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Fuerza a la biblioteca a enviar todas las visitas en cola, sean cuales sean las opciones de agrupamiento actuales.

   * Este es un ejemplo de código para este método:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtiene o establece el número de llamadas de seguimiento almacenadas en la cola sin conexión.

   * Este es un ejemplo de código para este método:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Elimina todas las llamadas de seguimiento almacenadas de la cola sin conexión.

   >[!WARNING]
   >
   >Tenga cuidado al borrar la cola manualmente, ya que no puede revertirse.

   * Este es un ejemplo de código para este método:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envía una solicitud de recopilación de PII.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.collectPII(piiData,success, fail);
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Realiza un seguimiento de los clics en vínculos profundos de Adobe.

   >[!TIP]
   >
   >Si la llamada del ciclo vital es un evento de inicio, se adjuntarán los datos de Adobe Link; de lo contrario, se enviará una llamada adicional.

   * Esta es la sintaxis para este método:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

   `cData`: objeto JSON con pares de clave-valor para enviar en los datos de contexto.

   * Esta es la sintaxis para este método:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Aquí se muestran muestras de código para este método:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Realiza el seguimiento de una acción en la aplicación. Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * Esta es la sintaxis para este método:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Estos son los ejemplos de código de este método:

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Envía las coordenadas x e y actuales. También utiliza puntos de interés definidos en el archivo `ADBMobileConfig.json` para determinar si la ubicación proporcionada como parámetro se encuentra en alguno de sus puntos de interés. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   Inicia una acción temporizada llamada `action`.

   Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pasa `cData` para actualizar los datos de contexto asociados con `action`&gt;.

   Los datos `cData` que se pasan se anexan a los ya existentes para la acción. Si la misma clave ya está definida para `action`, los datos se sobrescriben.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   Finaliza una acción temporizada.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Devuelve si la acción temporizada está en progreso o no.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Realiza un seguimiento para determinar si un usuario entra en la proximidad de una señalización.

   * Esta es la sintaxis para este método:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Borra los datos de señalizaciones una vez que el usuario abandona la proximidad de la señalización.

   * Esta es la sintaxis para este método:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Métodos de Target {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Envía una solicitud al servidor de `Target` configurado y devuelve el valor de cadena de la oferta.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envía una solicitud al servidor de `Target` configurado.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Borra las cookies de `Target` del almacenamiento de cookies compartido.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Obtiene el valor de la cookie `SessionID` que el servidor de Target devuelve para este visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Obtiene el valor de la cookie `PcID` que el servidor de `Target` devuelve para este visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Establece el ID de visitante personalizado para Target.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Obtiene el ID de visitante personalizado para Target.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Envía una solicitud al servidor de Target configurado y devuelve el valor de cadena de la oferta.

   * Esta es la sintaxis para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Estos son los ejemplos de código de este método:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. Para obtener más información, consulte [Métodos de configuración](/help/android/configuration/methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtiene el perfil del visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   Devuelve el DPUUID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   Devuelve el DPID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Establece el DPID y el DPUUID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Estos son los ejemplos de código de este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Procesa una solicitud de servicio de Audience Manager.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Estos son los ejemplos de código de este método:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID y purga el perfil del visitante actual.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Devuelve el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   Sincroniza los identificadores proporcionados con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Estos son los ejemplos de código de este método:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincroniza los identificadores proporcionados con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   Sincroniza el identificador proporcionado con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   Adjunta los identificadores de visitante a la URL dada.

   * Esta es la sintaxis para este método:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
