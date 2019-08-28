---
description: Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.
keywords: android; library; mobile; sdk
seo-description: Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.
seo-title: Métricas del ciclo vital
solution: Marketing Cloud, Analytics
title: Métricas del ciclo vital
topic: Desarrollador e implementación
uuid: c 483271 f-f 620-46 f 4-aad 8-d 5 f 02 d 763 f 7 d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics{#lifecycle-metrics}

Lista las métricas y dimensiones que se pueden medir automáticamente mediante la biblioteca móvil.

Para obtener más información, consulte [Solución de problemas de los datos del ciclo vital](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Cuando se configuran, las métricas del ciclo vital se envían en parámetros de datos contextuales a Analytics, en parámetros a Target con cada llamada de mbox y como señal a Audience Manager. Analytics y Target usan el mismo formato y Audience Manager utiliza un prefijo diferente para cada métrica.

En Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se registran usando la métrica o la dimensión que se enumeran a continuación, y se señalan las excepciones.

### Métricas

* **Primeros lanzamientos**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cuando cambia el número de versión.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!TIP]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa en cada ejecución, incluido en caso de bloqueo o al realizar la instalación. También se activa al reanudar desde segundo plano, cuando se supera el tiempo de espera de la sesión de ciclo de duración.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia después del bloqueo. Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación haya estado abierta en primer plano.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación. El formato de fecha `MM/DD/YYYY`es.

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID de aplicación**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Un ejemplo de este formato es `myapp 1.1`.

   * Analytics context data/Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Analytics context data/Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se usó por última vez.

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Hora del día**

   Calcula la hora en la que se inició la aplicación. Esta métrica utiliza el formato numérico de 24 horas y se utiliza en la partición temporal para determinar las horas de mayor uso.

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Día de la semana**

   Número del día en una semana en la que se inició la aplicación.

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   Versión del sistema operativo.

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Días transcurridos desde la última actualización**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Las siguientes métricas y dimensiones se capturan en variables de soluciones móviles según los métodos enumerados en la descripción.

### Métricas

* **Tiempo total de la acción**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.total`
   * Característica de Audience Manager: `c_a_action_time_total`

* **Tiempo de la acción dentro de la aplicación**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Característica de Audience Manager: `c_a_action_time_inapp`

* **Valor de duración (evento)**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`

## Dimensiones

* **Ubicación (menos de 10 km)**

   Populated by `trackLocation` methods.

   * Parámetro de datos contextuales/Target de Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica de Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Populated by `trackLocation` methods.

   * Parámetro de datos contextuales/Target de Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica de Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Populated by `trackLocation` methods.

   * Parámetro de datos contextuales/Target de Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica de Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Rellenado con métodos `trackLocation` cuando el dispositivo está dentro de un punto de interés definido.

   * Analytics context data/Target parameter: `a.loc.poi`
   * Característica de Audience Manager: `c_a_loc_poi`

* **Distancia hasta el centro del punto de interés**

   Rellenado con métodos `trackLocation` cuando el dispositivo está dentro de un punto de interés definido.

   * Analytics context data/Target parameter: `a.loc.dist`
   * Característica de Audience Manager: `c_a_loc_dist`

* **Valor de duración (variable de conversión)**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`
