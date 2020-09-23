---
description: A continuación encontrará las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo de duración, así como un vínculo para solucionar problemas en los datos del ciclo.
keywords: android;library;mobile;sdk
seo-description: A continuación encontrará las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo de duración, así como un vínculo para solucionar problemas en los datos del ciclo.
seo-title: Métricas del ciclo vital
solution: Experience Cloud,Analytics
title: Métricas del ciclo vital
topic: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 70%

---


# Métricas del ciclo vital {#lifecycle-metrics}

A continuación encontrará las métricas y dimensiones que la biblioteca móvil puede medir automáticamente, una vez implementado el ciclo de duración, así como un vínculo para solucionar problemas en los datos del ciclo.

Para obtener más información, vaya a la Base de conocimiento en [Resolución de problemas con los datos](https://helpx.adobe.com/es/analytics/kb/troubleshoot-lifecycle-data.html)del ciclo vital.

## Métricas y dimensiones del ciclo vital {#section_78F036C4296F4BA3A47C2044F79C86C1}

Cuando se configuran, las métricas del ciclo vital se envían en parámetros de datos de contexto a Analytics, en parámetros para el Destinatario con cada llamada de mbox y como señal para la administración de audiencias. Analytics y Destinatario utilizan el mismo formato, mientras que la administración de audiencias utiliza un prefijo diferente para cada métrica.

Para Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se registran mediante la métrica o la dimensión.

### Métricas

* **a.media.name**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Señal de Audience Manager: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cuando cambia el número de versión.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Señal de Audience Manager: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Señal de Audience Manager: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.  >>>>

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Señal de Audience Manager: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa en cada ejecución, incluidos los bloqueos y las instalaciones. También se activa al reanudar desde segundo plano cuando se ha superado el tiempo de espera de la sesión de ciclo vital.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Señal de Audience Manager: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia después del bloqueo. Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Señal de Audience Manager: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación haya estado abierta en primer plano.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Señal de Audience Manager: `c_a_PrevSessionLength`

### Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación. El formato de fecha es `MM/DD/YYYY`.

   * Analytics context data/Target parameter: `a.InstallDate`
   * Señal de Audience Manager: `c_a_InstallDate`

* **ID de aplicación**

   Almacena el nombre y la versión de la aplicación en el siguiente formato:
   `[AppName] [BundleVersion]`.

   Un ejemplo de este formato es `myapp 1.1`.

   * Analytics context data/Target parameter: `a.AppID`
   * Señal de Audience Manager: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Analytics context data/Target parameter: `a.Launches`
   * Señal de Audience Manager: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Señal de Audience Manager: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se usó por última vez.

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Señal de Audience Manager: `c_a_DaysSinceLastUse`

* **Hora del día**

   Calcula la hora en la que se inició la aplicación. Esta métrica utiliza el formato numérico de 24 horas y se utiliza en la partición temporal para determinar las horas de mayor uso.

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Señal de Audience Manager: `c_a_HourOfDay`

* **Día de la semana**

   Número del día en una semana en la que se inició la aplicación.

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Señal de Audience Manager: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   Versión del sistema operativo.

   * Analytics context data/Target parameter: `a.OSVersion`
   * Señal de Audience Manager: `c_a_OSVersion`

* **Días transcurridos desde la última actualización**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Señal de Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Señal de Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.

   * Analytics context data/Target parameter: `a.DeviceName`
   * Señal de Audience Manager: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.

   >[!IMPORTANT]
   >
   >Esta métrica no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

   * Analytics context data/Target parameter: `a.CarrierName`
   * Señal de Audience Manager: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Analytics context data/Target parameter: `a.Resolution`
   * Señal de Audience Manager: `c_a_Resolution`

## Métricas y dimensiones móviles adicionales {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Las siguientes métricas y dimensiones se capturan en variables de soluciones móviles mediante el método mencionado.

* **Ubicación (menos de 10 km)**

   Rellenado con métodos `trackLocation`.

   * Parámetro de Destinatario/datos de contexto de Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica de Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Rellenado con métodos `trackLocation`.

   * Parámetro de Destinatario/datos de contexto de Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica de Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Rellenado con métodos `trackLocation`.

   * Parámetro de Destinatario/datos de contexto de Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica de Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Parámetro de Destinatario/datos de contexto de Analytics:

      * `a.loc.poi`
   * Característica de Audience Manager:

      * `c_a_loc_poi`


* **Distancia hasta el centro del punto de interés**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Parámetro de Destinatario/datos de contexto de Analytics:

      * `a.loc.dist`
   * Característica de Audience Manager:

      * `c_a_loc_dist`
