---
description: Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.
keywords: android;biblioteca;móvil;sdk
seo-description: Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.
seo-title: Métricas del ciclo vital
solution: Marketing Cloud,Analytics
title: Métricas del ciclo vital
topic: Desarrollador e implementación
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics {#lifecycle-metrics}

Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.

Para obtener más información, consulte [Solución de problemas con los datos](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)del ciclo vital.


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Cuando se configuran, las métricas del ciclo vital se envían en parámetros de datos contextuales a Analytics, en parámetros a Target con cada llamada de mbox y como señal para la gestión de público. Analytics y Target usan el mismo formato, mientras que la gestión de público emplea un prefijo distinto para cada métrica.

Para Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se registran mediante la métrica o la dimensión. El contenido incluye excepciones.

## Métricas

* **Primeros lanzamientos**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cuando cambia el número de versión.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics metric. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa en cada ejecución, incluido en caso de bloqueo o al realizar la instalación. También se activa al reanudar desde segundo plano, cuando se supera el tiempo de espera de la sesión de ciclo de duración.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia después del bloqueo. Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación haya estado abierta en primer plano.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`


## Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación. El formato de fecha es `MM/DD/YYYY`.

   * Analytics Context Data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **ID de aplicación**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Un ejemplo de este formato es `myapp 1.1`.

   * Analytics Context Data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Analytics Context Data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Analytics Context Data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se usó por última vez.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **Hora del día**

   Calcula la hora en la que se inició la aplicación. Esta métrica utiliza el formato numérico de 24 horas y se utiliza en la partición temporal para determinar las horas de mayor uso.

   * Analytics Context Data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **Día de la semana**

   Número del día en una semana en la que se inició la aplicación.

   * Analytics Context Data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   Versión del SO.

   * Analytics Context Data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **Días transcurridos desde la última actualización**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics Context Data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics Context Data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.

   * Analytics Context Data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics Context Data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Analytics Context Data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Las siguientes métricas y dimensiones se capturan en variables de soluciones móviles mediante el método siguiente:

### Métricas

* **Tiempo total de la acción**

   Populated by `trackTimedAction` methods.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Manager signal: `c_a_action_time_total`

* **Tiempo de la acción dentro de la aplicación**

   Populated by `trackTimedAction` methods.
   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Manager signal: `c_a_action_time_inapp`

* **Valor de duración (evento)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Manager signal: `c_a_ltv_amount`

### Dimensiones

* **Ubicación (menos de 10 km)**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target parameter(s):

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Características de Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Populated by `trackLocation` methods.

   * Parámetros de Analytics Context Data/Target:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Características de Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Populated by `trackLocation` methods.

   * Parámetros de Analytics Context Data/Target:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Características de Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Se rellena con métodos `trackLocation` cuando el dispositivo está en un punto de interés definido.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Característica de Audience Manager: `c_a_loc_poi`

* **Distancia hasta el centro del punto de interés**

   Rellenado con métodos `trackLocation` cuando el dispositivo está dentro de un punto de interés definido.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Característica de Audience Manager: `c_a_loc_dist`

* **Valor de duración (variable de conversión)**

   Populated by `trackLifetimeValue` methods.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`
