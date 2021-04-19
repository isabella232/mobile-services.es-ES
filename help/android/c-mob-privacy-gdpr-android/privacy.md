---
description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-title: Configuración del estado de exclusión del usuario
solution: Experience Cloud,Analytics
title: Configuración del estado de exclusión del usuario
topic-fix: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
exl-id: ef5160ac-5a73-4433-b217-1bd990f8456b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 100%

---

# Configuración del estado de exclusión del usuario {#setting-the-user-s-opt-status}

Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.

>[!IMPORTANT]
>
>A partir del SDK 4.15 para Android, si se define el estado de privacidad como `unknown`, se mantienen los resultados de ID de Audience Manager y Experience Cloud.

Puede controlar si la actividad de Analytics, Target y Audience Manager está permitida en un dispositivo mediante la siguiente configuración:

* `privacyDefault` en [la configuración JSON de ADBMobile](/help/android/configuration/json-config/json-config.md).

   Este ajuste controla la configuración inicial que persiste hasta que se cambia en el código.

* El método `Config.setPrivacyStatus`.

   Una vez que haya cambiado la configuración de privacidad empleando este método, el cambio será permanente hasta que vuelva a cambiarse o hasta que se desinstale y vuelva a instalarse la aplicación. Para obtener más información sobre los métodos, consulte  [Métodos de configuración](/help/android/configuration/methods.md).

La siguiente tabla describe todos los estados de privacidad:

* **Opt-in**

   * **Analytics**: se envían las visitas.
   * **Target**: se envían las solicitudes mBox.
   * **Audience Manager**: se envían señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optedin`
   * Valor en `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Desactivar**

   * **Analytics**: se descartan las visitas.
   * **Target**: no se permiten las solicitudes mBox.
   * **Audience Manager**: no se permiten señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optedout`
   * Valor en `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Unknown**

   * **Analytics**: si el seguimiento sin conexión **está** activado, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el seguimiento en línea <b>no está activado</b>, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.
   * **Target**: se envían las solicitudes mBox.
   * **Audience Manager**: se envían señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optunknown`
   * Valor en `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## Ejemplos {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```
