---
description: Puede utilizar métodos del complemento PhoneGap de iOS para completar diversas tareas.
keywords: phonegap
seo-description: Puede utilizar métodos del complemento PhoneGap de iOS para completar diversas tareas.
seo-title: Métodos del complemento PhoneGap
solution: Marketing Cloud,Analytics
title: Métodos del complemento PhoneGap
topic: Desarrollador e implementación
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods {#phonegap-plug-in-methods}

Puede utilizar métodos del complemento PhoneGap de iOS para completar diversas tareas.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Devuelve el estado de privacidad del usuario actual. Estos son los estados disponibles:

   * `ADB.optedIn`, donde las visitas se envían inmediatamente.
   * `ADB.optedOut`, donde las visitas se descartan.
   * `ADB.optUnknown`Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan). **** Si el grupo de informes **no tiene** habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.\
      El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.

      * Este es un ejemplo de código para este método:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* Método **setPrivacyStatus**

   Sets the privacy status for the current user to `status`. Puede establecer uno de los siguientes estados:
   * `ADB.optedIn`, donde las visitas se envían inmediatamente.
   * `ADB.optedOut`, donde las visitas se descartan.
   * `ADB.optUnknown` - Si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan).****

      Si el grupo de informes **no tiene** habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Este es un ejemplo de código para este método:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Devuelve el valor de duración del usuario actual. El valor predeterminado es 0.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. De forma predeterminada, el valor de esta variable es `false`.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Obtiene la versión de la biblioteca.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Devuelve el identificador de visitante generado automáticamente. Se trata de un ID de visitante exclusivo y específico para la aplicación que se genera durante el lanzamiento inicial y se almacena y utiliza a partir de ese momento. Este ID se preserva al actualizar la aplicación y se elimina al desinstalarla.

   >[!TIP]
   >
   >If your app upgrades from the Experience Cloud 3.x to 4.x SDK, the previous visitor ID (custom or automatically generated) is retrieved and stored as the custom user identifier (see `getUserIdentifier` below). De este modo, se preservan los datos de visitante tras actualizar el SDK. For new installations on the 4.x SDK, the user identifier is `null`, and tracking identifier is used.

   * Este es un ejemplo de código para este método:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Devuelve el identificador de usuario personalizado si se ha establecido uno, o `null` si no se ha establecido. El valor predeterminado es `null`.

   * Este es un ejemplo de código para este método:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Establece el identificador de usuario como `identifier`.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Establece el token del dispositivo para notificaciones push.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Establece la preferencia de mantenimiento de sesión del ciclo vital.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Solo debe utilizar este método si la aplicación recibe notificaciones en segundo plano.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Fuerza a la biblioteca a enviar todas las visitas en cola, sean cuales sean las opciones de agrupamiento actuales.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Obtiene o establece el número de llamadas de seguimiento almacenadas en la cola sin conexión.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Elimina todas las llamadas de seguimiento almacenadas de la cola sin conexión.

   >[!CAUTION]
   >
   >Tenga cuidado al borrar la cola manualmente ya que la eliminación no puede revertirse.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Indica al SDK que la siguiente reanudación desde segundo plano no debe iniciar una nueva sesión, independientemente del valor del tiempo de espera de sesión del ciclo vital en el archivo de configuración.

   >[!IMPORTANT]
   >
   >Importante: El propósito de este método es que se utilice en aplicaciones que realizan un registro de notificaciones mientras se encuentran en segundo plano, y solo debería invocarse desde el código que se está ejecutando cuando la aplicación esté en segundo plano.

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. For more information, see [Lifecycle metrics](/help/ios/metrics.md).

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Envía una solicitud de recopilación de PII.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Realiza un seguimiento de los clics en vínculos profundos de Adobe.

   >[!TIP]
   >
   >Si la llamada al ciclo vital es un evento de inicio, se anexarán los datos del vínculo de Adobe; de lo contrario, se enviará una llamada adicional.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Realiza un seguimiento de los clics en un mensaje push.

   * Esta es la sintaxis para este método:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Realiza un seguimiento de los clics en un mensaje de notificación local.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Realiza el seguimiento del estado de una aplicación con datos de contexto opcionales. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página. cData is a JSON object with key-value pairs to send in context data.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Estos son los ejemplos de código para este método:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Realiza el seguimiento de una acción en la aplicación. Actions are the things that happen in your app that you want to measure, include `logins`, `banner taps`, `feed subscriptions` and other metrics.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Estos son los ejemplos de código para este método:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Realiza un seguimiento de una acción que ocurre en segundo plano. Esto impide que los eventos del ciclo vital se activen en ciertos escenarios.

   * Esta es la sintaxis para este método:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Estos son los ejemplos de código para este método:

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Envía las coordenadas X e Y actuales. Also uses the points of interest that were defined in the `ADBMobileConfig.json` file to determine if the location provided as a parameter is within any of your POIs. Si las coordinadas actuales se encuentran en un punto de interés definido, se rellena una variable de datos de contexto y se envía junto con la llamada a `trackLocation`.

   * Esta es la sintaxis para este método:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Este es un ejemplo de código para este método:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Agrega una `amount` al valor de duración del usuario.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   Inicia una acción temporizada llamada `action`. Si invoca este método para una acción que ya se ha iniciado, se sobrescribe la acción temporizada anterior.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pasa `cData` para actualizar los datos de contexto asociados a `action` en cuestión. The `cData` passed in is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Esta llamada no envía una visita.

   * Esta es la sintaxis para este método:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Métodos de Target {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Envía una solicitud al servidor de `Target` configurado y devuelve el valor de cadena de la oferta.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Envía una solicitud al servidor de Target configurado.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Borra las cookies de Target del almacenamiento de cookies compartido.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Procesa una solicitud de servicio de Target.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Procesa una solicitud de servicio de Target.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Obtiene el valor de la cookie `PcID` que el servidor de Target devuelve para este visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Establece el ID de visitante personalizado para Target.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Here is the code sample for this group:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Obtiene el ID de visitante personalizado para Target.

   * Esta es la sintaxis para este método:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Permite a los desarrolladores iniciar una campaña de adquisición de aplicación como si el usuario hubiera hecho clic en un vínculo. Esto resulta útil para crear vínculos de adquisición manuales y controlar personalmente el redireccionamiento al App Store (por ejemplo, mediante `SKStoreView`).

   * Esta es la sintaxis para este método:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the `AppDelegate` generated by Cordova, call `[ADBMobile setAdvertisingIdentifier:]` in the `application:didFinishLaunchingWithOptions:` delegate method. For more information, see Configuration Methods.[](/help/ios/configuration/sdk-methods.md)

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Obtiene el perfil del visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   Devuelve el DPUUID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   Devuelve el DPID.

   * Esta es la sintaxis para este método:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Establece el DPID y el DPUUID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Here are the code samples for this method:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Procesa una solicitud de servicio de Audience Manager.

   * Esta es la sintaxis para este método:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Estos son los ejemplos de código para este método:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Restaura el UUID de Audience Manager y elimina el perfil del visitante actual.

   * Este es un ejemplo de código para este método:

      ```java
      ADB.audienceReset(); 
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Devuelve el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   Sincroniza los identificadores proporcionados con el servicio de ID.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Here are the code samples for this method:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Sincroniza los identificadores proporcionados con el servicio de ID de visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   Sincroniza el identificador proporcionado con el servicio de ID de visitante.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   Adjunta los identificadores de visitante a la URL dada.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorIDs` that have been synced.

   * Esta es la sintaxis para este método:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

