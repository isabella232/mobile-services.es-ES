---
description: Las siguientes tablas listan las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.
seo-description: Las siguientes tablas listan las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.
seo-title: Métricas del ciclo vital
solution: Experience Cloud,Analytics
title: Métricas del ciclo vital
topic: Desarrollador e implementación
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: ht
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# Métricas del ciclo vital {#lifecycle-metrics}

Estas son las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a [Experience Platform Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Métricas y dimensiones del ciclo vital {#section_78F036C4296F4BA3A47C2044F79C86C1}

Después de configurarse, las métricas del ciclo vital se envían en parámetros de datos de contexto a Analytics, en parámetros a Target con cada llamada de mbox y como señal a Audience Manager. Analytics y Target usan el mismo formato, mientras que Audience Manager usa un prefijo distinto para cada métrica.

En Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se comunican usando la métrica o la dimensión de la primera columna.

>[!TIP]
>
>En la descripción se incluyen excepciones.

### Métricas

* **Primeros lanzamientos**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Parámetro de Target/datos contextuales de Analytics: `a.InstallEvent`
   * Señal de Audience Manager: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cada vez que cambia el número de versión.

   * Parámetro de Target/datos contextuales de Analytics: `a.UpgradeEvent`
   * Señal de Audience Manager: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   * Parámetro de Target/datos contextuales de Analytics: `a.DailyEngUserEvent`
   * Señal de Audience Manager: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.

   * Parámetro de Target/datos contextuales de Analytics: `a.MonthlyEngUserEvent`
   * Señal de Audience Manager: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa con cada ejecución, incluidos los bloqueos y las instalaciones. Se activa también cuando la aplicación se inicia de nuevo desde segundo plano cuando se ha superado el tiempo de espera de la sesión del ciclo vital.

   * Parámetro de Target/datos contextuales de Analytics: `a.LaunchEvent`
   * Señal de Audience Manager: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia de nuevo después del bloqueo.  Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Parámetro de Target/datos contextuales de Analytics: `a.CrashEvent`
   * Señal de Audience Manager: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación estuvo abierta en primer plano.

   * Parámetro de Target/datos contextuales de Analytics: `a.PrevSessionLength`
   * Señal de Audience Manager: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Las métricas *Usuarios implicados cada día* y *Usuarios implicados cada mes* no se almacenan automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar estas métricas.

#### Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación.  El formato de fecha es `MM/DD/YYYY`.

   * Target/dato contextual de Analytics: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **ID de aplicación**

   Almacena el nombre y la versión de la aplicación en el formato `[AppName] [BundleVersion]`. Por ejemplo, `myapp 1.1`.

   * Target/dato contextual de Analytics: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Target/dato contextual de Analytics: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Target/dato contextual de Analytics: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se ejecutó por última vez.

   * Target/dato contextual de Analytics: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Hora del día**

   Mide la hora de inicio de la aplicación y usa el formato numérico de 24 horas. Se utiliza en la partición de tiempo para determinar las horas de mayor uso.

   * Target/dato contextual de Analytics: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Día de la semana**

   Número del día de la semana en el que se inició la aplicación.

   * Target/dato contextual de Analytics: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   * Target/dato contextual de Analytics: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion|OS version`

* **Días transcurridos desde la última actualización**

   Días transcurridos desde la última actualización.

   * Target/dato contextual de Analytics: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   * Target/dato contextual de Analytics: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.  cadena de dos dígitos separados por comas que identifica el dispositivo iOS. El primer número representa generalmente la generación del dispositivo y el segundo número representa generalmente versiones de miembros diferentes de la familia del dispositivo. Para ver una lista de nombres de dispositivos comunes, consulte  Versiones de dispositivo iOS.

   * Target/dato contextual de Analytics: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.

   * Target/dato contextual de Analytics: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Target/dato contextual de Analytics: `a.Resolution`
   * Audience Manager: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >Las dimensiones *Días transcurridos desde la última actualización*, *Inicios desde la última actualización* y *Nombre del operador* no se almacenan automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar estos valores en una variable de Analytics para la generación de informes.


## Métricas y dimensiones móviles adicionales {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Las siguientes métricas y dimensiones se capturan en variables de soluciones móviles mediante el método mencionado.

### Métricas

* **Tiempo total de la acción**

   Rellenado con métodos trackTimedAction.

   * Parámetro de Target/datos contextuales de Analytics: `a.action.time.total`
   * Característica de Audience Manager: `c_a_action_time_total`

* **Tiempo de la acción dentro de la aplicación**

   Rellenado con métodos trackTimedAction.

   * Parámetro de Target/datos contextuales de Analytics: `a.action.time.inapp`
   * Característica de Audience Manager: `c_a_action_time_inapp`

* **Valor de duración (evento)**

   Rellenado con métodos trackLifetimeValue.

   * Parámetro de Target/datos contextuales de Analytics: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`


### Dimensiones

* **Ubicación (menos de 10 km)**

   Rellenado con métodos `trackLocation`.

   * Parámetro de Target/datos contextuales de Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica de Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Rellenado con métodos trackLocation.

   * Parámetro de Target/datos contextuales de Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica de Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Rellenado con métodos `trackLocation`.

   * Parámetro de Target/datos contextuales de Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica de Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Se rellena con métodos trackLocation cuando el dispositivo está en un punto de interés definido.

   * Parámetro de Target/datos contextuales de Analytics: `a.loc.poi`
   * Característica de Audience Manager: `c_a_loc_poi`

* **Distancia hasta el centro del punto de interés**

   Se rellena con métodos trackLocation cuando el dispositivo está en un punto de interés definido.

   * Parámetro de Target/datos contextuales de Analytics: `a.loc.dist`
   * Característica de Audience Manager: `c_a_loc_dist`

* **Valor de duración (variable de conversión)**

   Rellenado con métodos trackLifetimeValue.

   * Parámetro de Target/datos contextuales de Analytics: `a.ltv.amount`
   * Característica de Audience Manager: `c_a_ltv_amount`

* **Código de seguimiento**

   Rellenado por Adquisición de aplicación móvil. Generado automáticamente por Adobe Mobile Services.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.trackingcode`
   * Característica de Audience Manager: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nombre de la campaña, también almacenada en la variable de campaña. Rellenado por Adquisición de aplicación móvil.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.name`
   * Característica de Audience Manager: `c_a_referrer_campaign_name`

* **Contenido de campaña**

   El nombre o ID del contenido que se muestra en el vínculo. Rellenado por Adquisición de aplicación móvil.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.content`
   * Característica de Audience Manager: `c_a_referrer_campaign_content`

* **Medio de campaign**

   El medio de marketing, como banners o correo electrónico. Rellenado por Adquisición de aplicación móvil.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.medium`
   * Característica de Audience Manager: `c_a_referrer_campaign_medium`

* **Fuente de campaña**

   Referente original, como un boletín de noticias o una red de medios sociales. Rellenado por Adquisición de aplicación móvil.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.source`
   * Característica de Audience Manager: `c_a_referrer_campaign_source`

* **Término de campaña**

   Palabras clave de pago u otros términos con los que quiera realizar un seguimiento de esta adquisición. Rellenado por Adquisición de aplicación móvil.

   * Parámetro de Target/datos contextuales de Analytics: `a.referrer.campaign.term`
   * Característica de Audience Manager: `c_a_referrer_campaign_term`
