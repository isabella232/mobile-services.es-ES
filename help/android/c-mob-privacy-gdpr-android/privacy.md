---
description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-title: Configuración del estado de selección del usuario
solution: Marketing Cloud,Analytics
title: Configuración del estado de selección del usuario
topic: Desarrollador e implementación
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Puede controlar si la actividad de Analytics, Target y Audience Manager está permitida en un dispositivo mediante la siguiente configuración:

* `privacyDefault` en [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

   Este ajuste controla la configuración inicial que persiste hasta que se cambia en el código.

* El `Config.setPrivacyStatus` método.

   Una vez que haya cambiado la configuración de privacidad empleando este método, el cambio será permanente hasta que vuelva a cambiarse o hasta que se desinstale y vuelva a instalarse la aplicación. Para obtener más información sobre los métodos, consulte [Métodos de configuración](/help/android/configuration/methods.md).

La siguiente tabla describe todos los estados de privacidad:

* **Opt-in**

   * **Analytics**: se envían las visitas.
   * **Target**: se envían las solicitudes mbox.
   * **Audience Manager**: se envían señales y sincronizaciones de ID.
   * Value in the JSON Config file: `optedin`
   * Valor en `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Desactivar**

   * **Analytics**: se descartan las visitas.
   * **Target**: no se permiten las solicitudes mbox.
   * **Audience Manager**: no se permiten señales y sincronizaciones de ID.
   * Value in the JSON config file: `optedout`
   * Valor en `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Unknown**

   * **Analytics**: If offline tracking **enabled**, hits are saved until the privacy status changes to opt-in (hits are sent) or opt-out (hits are discarded).

      Si el seguimiento en línea <b>no está activado</b>, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.
   * **Target**: se envían las solicitudes mbox.
   * **Audience Manager**: se envían señales y sincronizaciones de ID.
   * Value in the JSON config file: `optunknown`
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

