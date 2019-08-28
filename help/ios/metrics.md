---
description: Las siguientes tablas listan las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.
seo-description: Las siguientes tablas listan las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.
seo-title: Métricas del ciclo vital
solution: Marketing Cloud, Analytics
title: Métricas del ciclo vital
topic: Desarrollador e implementación
uuid: b 795 e 383-d 59 b -4 a 3 c -9 e 14-ffe 8 fb 58412 c
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lifecycle metrics {#lifecycle-metrics}

Estas son las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Después de configurarse, las métricas del ciclo vital se envían en parámetros de datos de contexto a Analytics, en parámetros a Target con cada llamada de mbox y como señal a Audience Manager. Analytics y Target usan el mismo formato, mientras que Audience Manager usa un prefijo distinto para cada métrica.

En Analytics, los datos de contexto que se envían con cada llamada de seguimiento del ciclo vital se capturan automáticamente y se comunican usando la métrica o la dimensión de la primera columna.

>[!TIP]
>
>Las excepciones se proporcionan en la descripción.

### Métricas

* **Primeros lanzamientos**

   Se activa la primera vez que se ejecuta después de la instalación o reinstalación.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Actualizaciones**

   Se activa la primera vez que se ejecuta después de una actualización o cada vez que cambia el número de versión.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza en un mes concreto.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Inicios**

   Se activa con cada ejecución, incluidos los bloqueos y las instalaciones. Se activa también cuando la aplicación se inicia de nuevo desde segundo plano cuando se ha superado el tiempo de espera de la sesión del ciclo vital.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Bloqueos**

   Se activa cuando la aplicación no se envía al segundo plano antes de cerrarse. El evento se envía cuando la aplicación se inicia de nuevo después del bloqueo.  Los informes de bloqueo de Adobe Mobile no implementan un controlador global de excepciones no detectadas.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Duración de la sesión anterior**

   Notifica el número de segundos que duró una sesión de aplicación anterior, según el tiempo que la aplicación estuvo abierta en primer plano.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Las métricas *Usuarios comprometidos diariamente* y *Usuarios* comprometidos mensualmente no se almacenan automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que establezca un evento personalizado para capturar estas métricas.

### Dimensiones

* **Install Date**

   Fecha del primer inicio después de la instalación.  El formato de fecha `MM/DD/YYYY`es.

   * Target/dato contextual de Analytics: `a.InstallDate`
   * Gestión de público: `c_a_InstallDate`

* **ID de aplicación**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. Por ejemplo, `myapp 1.1`.

   * Target/dato contextual de Analytics: `a.AppID`
   * Gestión de público: `c_a_AppID`

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

   * Target/dato contextual de Analytics: `a.Launches`
   * Gestión de público: `c_a_Launches`

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

   * Target/dato contextual de Analytics: `a.DaysSinceFirstUse`
   * Gestión de público: `c_a_DaysSinceFirstUse`

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se ejecutó por última vez.

   * Target/dato contextual de Analytics: `a.DaysSinceLastUse`
   * Gestión de público: `c_a_DaysSinceLastUse`

* **Hora del día**

   Mide la hora de inicio de la aplicación y usa el formato numérico de 24 horas. Se utiliza en la partición de tiempo para determinar las horas de mayor uso.

   * Target/dato contextual de Analytics: `a.HourOfDay`
   * Gestión de público: `c_a_HourOfDay`

* **Día de la semana**

   Número del día de la semana en el que se inició la aplicación.

   * Target/dato contextual de Analytics: `a.DayOfWeek`
   * Gestión de público: `c_a_DayOfWeek`

* **Versión del sistema operativo**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   * Target/dato contextual de Analytics: `a.OSVersion`
   * Gestión de público: `c_a_OSVersion|OS version`

* **Días transcurridos desde la última actualización**

   Días transcurridos desde la última actualización.

   * Target/dato contextual de Analytics: `a.DaysSinceLastUpgrade`
   * Gestión de público: `c_a_DaysSinceLastUpgrade`

* **Inicios transcurridos desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   * Target/dato contextual de Analytics: `a.LaunchesSinceUpgrade`
   * Gestión de público: `c_a_LaunchesSinceUpgrade`

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo.  cadena de dos dígitos separados por comas que identifica el dispositivo iOS. El primer número representa generalmente la generación del dispositivo y el segundo número representa generalmente versiones de miembros diferentes de la familia del dispositivo. Para ver una lista de nombres de dispositivos comunes, consulte  Versiones de dispositivo iOS.

   * Target/dato contextual de Analytics: `a.DeviceName`
   * Gestión de público: `c_a_DeviceName`

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles indicado en el dispositivo.

   * Target/dato contextual de Analytics: `a.CarrierName`
   * Gestión de público: `c_a_CarrierName`

* **Resolución**

   Anchura por altura en píxeles reales.

   * Target/dato contextual de Analytics: `a.Resolution`
   * Gestión de público: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >*Los días transcurridos desde la última actualización*, *los usos transcurridos desde la última actualización**y* las dimensiones de nombre de portador no se almacenan automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar los valores en una variable de Analytics para los informes.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

El método enumerado captura las siguientes métricas y dimensiones en las variables de soluciones móviles.

### Métricas

* **Tiempo total de la acción**

   Rellenado con métodos trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **Tiempo de la acción dentro de la aplicación**

   Rellenado con métodos trackTimedAction.

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **Valor de duración (evento)**

   Rellenado con métodos trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### Dimensiones

* **Ubicación (menos de 10 km)**

   Populated by `trackLocation` methods.

   * Parámetro de Target/dato contextual de Analytics:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Característica Gestión de público:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Ubicación (menos de 100 m)**

   Rellenado con métodos trackLocation.

   * Parámetro de Target/dato contextual de Analytics:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Característica Gestión de público:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Ubicación (menos de 1 m)**

   Populated by `trackLocation` methods.

   * Parámetro de Target/dato contextual de Analytics:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Característica Gestión de público:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Nombre del punto de interés**

   Se rellena con métodos trackLocation cuando el dispositivo está en un punto de interés definido.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **Distancia hasta el centro del punto de interés**

   Se rellena con métodos trackLocation cuando el dispositivo está en un punto de interés definido.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **Valor de duración (variable de conversión)**

   Rellenado con métodos trackLifetimeValue.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **Código de seguimiento**

   Rellenado por Adquisición de aplicación móvil. Generado automáticamente por Adobe Mobile Services.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Nombre de la campaña, también almacenada en la variable de campaña. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **Contenido de campaña**

   El nombre o ID del contenido que se muestra en el vínculo. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **Medio de campaign**

   El medio de marketing, como banners o correo electrónico. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **Fuente de campaña**

   Referente original, como un boletín de noticias o una red de medios sociales. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **Término de campaña**

   Palabras clave de pago u otros términos con los que quiera realizar un seguimiento de esta adquisición. Rellenado por Adquisición de aplicación móvil.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
