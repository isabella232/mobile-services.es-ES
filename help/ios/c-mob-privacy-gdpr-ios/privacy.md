---
description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-description: Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.
seo-title: Configuración del estado de exclusión del usuario
solution: Experience Cloud,Analytics
title: Configuración del estado de exclusión del usuario
topic: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Configuración del estado de exclusión del usuario {#setting-the-user-s-opt-status}

Esta información le será de ayuda para la solicitud de eliminación de datos del RGPD.

>[!IMPORTANT]
>
>A partir de la versión 4.15 de los SDK para iOS de Experience Cloud, establecer el estado de la privacidad en `unknown` resultará en la retención de los resultados de ID de Audience Manager y Experience Cloud.

Puede controlar si la actividad de Analytics, Target y Audience Manager está permitida en un dispositivo mediante la siguiente configuración:

* `privacyDefault` en [la configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

   Este ajuste controla la configuración inicial que persiste hasta que se cambia en el código.

* `setPrivacyStatus`.

   Una vez que haya cambiado la configuración de privacidad empleando este método, el cambio será permanente hasta que vuelva a cambiarse mediante este método, o hasta que desinstale y vuelva a instalar la aplicación.

   Para obtener más información sobre los métodos, consulte  [Métodos de configuración](/help/ios/configuration/json-config/json-config.md).

Esta es la información sobre cada estado de privacidad:

* **Opt-in**

   * Analytics: se envían las visitas.
   * Target: se envían las solicitudes mbox.
   * Audience Manager: se envían señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optedin`
   * Valor en `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Desactivar**

   * Analytics: se descartan las visitas.
   * Target: no se permiten las solicitudes mbox.
   * Audience Manager: no se permiten señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optedout`
   * Valor en `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Unknown**

   * Analytics: si el seguimiento en línea **está** activado, las visitas se guardan hasta que el estado de privacidad cambie a Opt-in (entonces se envían las visitas) u Opt-out (entonces se descartan las visitas).

      Si el seguimiento en línea **no está activado**, las visitas se descartan hasta que el estado de privacidad cambie a Opt-in.

   * Target: se envían las solicitudes mbox.
   * Audience Manager: se envían señales y sincronizaciones de ID.
   * Valor en el archivo de configuración de JSON: `optunknown`
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

