---
description: Aquí encontrará la información de referencia sobre las dimensiones y las métricas móviles predeterminadas.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Métricas de Mobile y referencia de dimensiones
topic-fix: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
exl-id: ddfbf11e-a4c3-4d59-92b3-1d192dc3e7cd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 100%

---

# Métricas de Mobile y referencia de dimensiones {#mobile-metrics-and-dimensions-reference}

Esta información le ayuda a conocer mejor las métricas y dimensiones móviles predeterminadas.

>[!TIP]
>
>Los permisos de dimensiones y métricas que se establecen en Adobe Analytics se aplican a Mobile Services. Cuando intenta ejecutar un informe sin los permisos adecuados, se produce un error.

## Métricas {#section_6704C815147D44AF96151D626BEB813C}

Esta es la lista de métricas móviles predeterminadas:

* **Primeros lanzamientos**

   Se activa en la primera ejecución tras una instalación o reinstalación.

* **Actualizaciones**

   Se activa en la primera ejecución tras una actualización o cuando cambia el número de versión.

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!TIP]
   >
   >El evento Usuarios implicados cada día no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza durante un mes.

   >[!TIP]
   >El evento Usuarios implicados cada mes no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

* **Inicios**

   Se activa en una ejecución que no sea una instalación ni una actualización. También se activa cuando la aplicación se extrae del segundo plano. De forma predeterminada, se activa un inicio nuevo si la aplicación se encuentra en segundo plano durante cinco minutos o más. El periodo de ejecución en segundo plano que transcurre antes de activarse un inicio nuevo se puede configurar en las **[!UICONTROL opciones de SDK Analytics]** en la página Administrar configuración de aplicación. Para obtener más información, consulte la fila *Tiempo de espera de sesión (segundos)* en [Configurar opciones de análisis de SDK](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Los resultados obtenidos en los informes pueden diferir debido al modo en que se calculan las visitas en [!UICONTROL Adobe Analytics] y los inicios de las aplicaciones móviles en [!UICONTROL Adobe Mobile Services]. Para obtener más información, consulte [Comparar visitas e inicios de aplicaciones móviles](https://helpx.adobe.com/es/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Bloqueos**

   Se activa cuando la aplicación no se cierra correctamente. Este evento se envía cuando la aplicación se inicia después de un bloqueo.

   >[!TIP]
   >Se considera que la aplicación se bloquea si no se invoca el evento de cierre.

* **Duración total de la sesión**

   Duración de la sesión total agregada.

## Dimensiones {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Esta es la lista de dimensiones móviles predeterminadas:

* **Fecha de instalación**

   Fecha del primer lanzamiento después de la instalación. La fecha tiene el formato *MM/DD/AAAA*.

* **ID de aplicación**

   Almacena el nombre y la versión de la aplicación en el siguiente formato: `[AppName] [BundleVersion]`. Por ejemplo, `myapp 1.1`.

* **Número de inicios**

   Número de veces que una aplicación se ha iniciado o se ha extraído del segundo plano.

* **Días transcurridos desde el primer uso**

   Número de días transcurridos desde que se ejecutó por primera vez.

* **Días transcurridos desde el último uso**

   Número de días transcurridos desde que se usó por última vez.

* **Hora del día**

   Mide la hora en que la aplicación se inició y usa el formato numérico de 24 horas. Esta dimensión también se usa en la división horaria para determinar las horas de uso máximo.

* **Día de la semana**

   Número del día de la semana en el que se inició la aplicación.

* **Sistema operativo**

   Sistema operativo del dispositivo.

* **Versión del sistema operativo**

   Versión del sistema operativo.

* **Días transcurridos desde la última actualización**

   Número de días transcurridos desde que se cambió el número de versión de la aplicación.

   >[!TIP]
   >
   >Días transcurridos desde la última actualización no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

* **Veces que se ha iniciado desde la última actualización**

   Número de inicios realizados desde que se cambió el número de versión de la aplicación.

   >[!TIP]
   >
   >Inicios desde la última actualización no se almacena automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo. En iOS, una cadena de dos dígitos separados por comas identifica el dispositivo iOS. El primer número representa la generación del dispositivo y el segundo representa versiones de miembros diferentes de la familia del dispositivo. Puede consultar la lista completa de los nombres comunes de dispositivos en [Versiones de dispositivos iOS](/help/ios/reference/device-versions.md).

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles.

* **Resolución**

   Anchura y altura en píxeles reales.
