---
description: A continuación encontrará las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo de duración, así como un vínculo para solucionar problemas en los datos del ciclo.
keywords: android;biblioteca;móvil;sdk
seo-description: A continuación encontrará las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo de duración, así como un vínculo para solucionar problemas en los datos del ciclo.
seo-title: Métricas del ciclo vital
solution: Marketing Cloud,Analytics
title: Métricas del ciclo vital
topic: Desarrollador e implementación
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Lifecycle metrics{#lifecycle-metrics}

Esta sección proporciona información sobre las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo vital, y un vínculo para solucionar problemas con los datos del ciclo vital. Para obtener más información sobre la solución de problemas, vaya a [Solucionar problemas con los datos](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)del ciclo vital.

## Nueva versión del SDK de Adobe Experience Platform Mobile

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Cuando se configuran, las métricas del ciclo vital se envían en parámetros de datos contextuales a Analytics, en parámetros a Target con cada llamada de mbox y como señal para la gestión de público. Analytics y Target usan el mismo formato, mientras que la gestión de público emplea un prefijo distinto para cada métrica.

Para Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se registran mediante la métrica o la dimensión, y se anotan las excepciones.

### Métricas

* **Primeros lanzamientos**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Parámetro de Target/dato contextual de Analytics: `a.InstallEvent`
   * Señal de Audience Manager: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cuando cambia el número de versión.

   * Parámetro de Target/dato contextual de Analytics: `a.UpgradeEvent`
   * Señal de Audience Manager: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Parámetro de Target/dato contextual de Analytics: `a.DailyEngUserEvent`
   * Señal de Audience Manager: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Parámetro de Target/dato contextual de Analytics: `a.MonthlyEngUserEvent`
   * Señal de Audience Manager: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa en cada ejecución, incluido en caso de bloqueo o al realizar la instalación. También se activa al reanudar desde segundo plano, cuando se supera el tiempo de espera de la sesión de ciclo de duración.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Parámetro de Target/dato contextual de Analytics: `a.LaunchEvent`
   * Señal de Audience Manager: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia después del bloqueo.  Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Parámetro de Target/dato contextual de Analytics: `a.CrashEvent`
   * Señal de Audience Manager: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación haya estado abierta en primer plano.

   * Parámetro de Target/dato contextual de Analytics: `a.PrevSessionLength`
   * Señal de Audience Manager: `c_a_PrevSessionLength`


### Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación. El formato de la fecha es MM/DD/AAAA.

   * Parámetro de Target/dato contextual de Analytics: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID de aplicación**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Un ejemplo de este formato es `myapp 1.1`.

   * Parámetro de Target/dato contextual de Analytics: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Parámetro de Target/dato contextual de Analytics: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Parámetro de Target/dato contextual de Analytics: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se usó por última vez.

   * Parámetro de Target/dato contextual de Analytics: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Hora del día**

   Calcula la hora en la que se inició la aplicación.  Esta métrica utiliza el formato numérico de 24 horas y se utiliza en la partición temporal para determinar las horas de mayor uso.

   * Parámetro de Target/dato contextual de Analytics: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Día de la semana**

   Número del día en una semana en la que se inició la aplicación.

   * Parámetro de Target/dato contextual de Analytics: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   The OS version.

   * Parámetro de Target/dato contextual de Analytics: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Días transcurridos desde la última actualización**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics variable. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Parámetro de Target/dato contextual de Analytics: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Parámetro de Target/dato contextual de Analytics: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.

   * Parámetro de Target/dato contextual de Analytics: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.  Importante: Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Parámetro de Target/dato contextual de Analytics: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Parámetro de Target/dato contextual de Analytics: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Las siguientes métricas y dimensiones las captura en variables de soluciones móviles el método indicado en la columna **Descripción**.

### Métricas

* **Tiempo total de la acción**

   Populated by `trackTimedAction` methods.

   * Parámetro de Target/dato contextual de Analytics: `a.action.time.total`
   * Audience Manager Trait: `c_a_action_time_total`

* **Tiempo de la acción dentro de la aplicación**

   Populated by `trackTimedAction` methods.

   * Parámetro de Target/dato contextual de Analytics: `a.action.time.inapp`
   * Característica de Audience Manager: `c_a_action_time_inapp`

* **Valor de duración (evento)**

   Populated by `trackLifetimeValue` methods.

   * Parámetro de Target/dato contextual de Analytics: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`

### Dimensiones

* **Ubicación (menos de 10 km)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Características de Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Rellenado con métodos trackLocation.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Características de Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Rellenado con métodos trackLocation.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager Traits:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Rellenado con métodos trackLocation cuando el dispositivo está dentro de un punto de interés definido.

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Audience Manager Trait: `c_a_loc_poi`

* **Distancia hasta el centro del punto de interés**

   Rellenado con métodos trackLocation cuando el dispositivo está dentro de un punto de interés definido.

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Característica de Audience Manager: `c_a_loc_dist`

* **Valor de duración (variable de conversión)**

   Rellenado con métodos trackLifetimeValue.

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

* **Código de seguimiento**

   Rellenado por la función de adquisición de aplicaciones móviles y generado automáticamente por Adobe Mobile Services.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience Manager Trait: `c_a_referrer_campaign_trackingcode`

* ** Campaign

   Nombre de la campaña, también almacenada en la variable de campaña. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Audience Manager Trait: `c_a_referrer_campaign_name`

* **Contenido de campaña**

   El nombre o ID del contenido que se muestra en el vínculo. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Audience Manager Trait: `c_a_referrer_campaign_content`

* **Medio de campaign**

   El canal de marketing, como un banner o correo electrónico. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Característica de Audience Manager: `c_a_referrer_campaign_medium`

* **Fuente de campaña**

   Referente original, como un boletín de noticias o una red de medios sociales. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience Manager Trait: `c_a_referrer_campaign_source`

* **Término de campaña**

   Palabras clave de pago u otros términos con los que quiera realizar un seguimiento de esta adquisición. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience Manager Trait: `c_a_referrer_campaign_term`
