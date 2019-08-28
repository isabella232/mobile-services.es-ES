---
description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-title: Configuración del estado de exclusión del cliente
solution: Marketing Cloud, Analytics
title: Configuración del estado de exclusión del cliente
topic: Desarrollador e implementación
uuid: 44 a 09 a 25-93 c 6-4 e 1 a-b 69 e -710018 e 8 b 6 c 3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Puede controlar si la actividad de Analytics, Target y Audience Manager está permitida en un dispositivo mediante la siguiente configuración:

* `privacyDefault` en [la configuración JSON de adbmobile](/help/ios/configuration/json-config/json-config.md).

   Este ajuste controla la configuración inicial que persiste hasta que se cambia en el código.

* `setPrivacyStatus`.

   Una vez que haya cambiado la configuración de privacidad empleando este método, el cambio será permanente hasta que vuelva a cambiarse mediante este método, o hasta que desinstale y vuelva a instalar la aplicación.

   Para obtener más información sobre los métodos, consulte [Métodos de configuración](/help/ios/configuration/json-config/json-config.md).

Esta es la información sobre cada estado de privacidad:

* **Opt-in**

   * Analytics: se envían las visitas.
   * Target: se envían las solicitudes mbox.
   * Audience Manager: se envían señales y sincronizaciones de ID.
   * Value in the JSON config file: `optedin`
   * Valor en `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Desactivar**

   * Analytics: se descartan las visitas.
   * Target: no se permiten las solicitudes mbox.
   * Audience Manager: no se permiten señales y sincronizaciones de ID.
   * Value in the JSON config file: `optedout`
   * Valor en `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Desconocido**

   * Analytics: si el seguimiento en línea **está** activado, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el seguimiento en línea **no está activado**, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Target: se envían las solicitudes mbox.
   * Audience Manager: se envían señales y sincronizaciones de ID.
   * Value in the JSON config file: `optunknown`
   * Valor en `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Ejemplos {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

