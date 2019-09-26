---
description: Aquí encontrará la información de referencia sobre las dimensiones y las métricas móviles predeterminadas.
keywords: móvil
seo-description: Aquí encontrará la información de referencia sobre las dimensiones y las métricas móviles predeterminadas.
seo-title: Métricas de Mobile y referencia de dimensiones
solution: Marketing Cloud,Analytics
title: Métricas de Mobile y referencia de dimensiones
topic: Métricas
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

This information helps you understand more about the default mobile metrics and dimensions.

>[!TIP]
>
>The dimension and metric permissions that are set in Adobe Analytics apply to Mobile Services. When you try to run a report without the proper permissions, an error occurs.

## Métricas {#section_6704C815147D44AF96151D626BEB813C}

Here is the list of default mobile metrics:

* **Primeros lanzamientos**

   Se activa en la primera ejecución tras una instalación o reinstalación.

* **Actualizaciones**

   Se activa en la primera ejecución tras una actualización o cuando cambia el número de versión.

* **Usuarios implicados cada día**

   Se activa cuando la aplicación se utiliza en un día concreto.

   >[!TIP]
   >El evento de usuarios comprometidos diariamente no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

* **Usuarios comprometidos mensualmente**

   Se activa cuando la aplicación se utiliza durante un mes.

   >[!TIP]
   >El evento Usuarios comprometidos mensualmente no se almacena automáticamente en una métrica de Analytics. Debe crear una regla de procesamiento que configure un evento personalizado para capturar esta métrica.

* **Inicios**

   Se activa en una ejecución que no sea una instalación ni una actualización. También se activa cuando la aplicación se extrae del segundo plano. De forma predeterminada, se activa un inicio nuevo si la aplicación se encuentra en segundo plano durante cinco minutos o más. The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. For more information, see the Session Timeout (Seconds) row in Configure SDK Analytics Options.**[](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. Para obtener más información, consulte [Compare Visits and Mobile App Launches](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html) (Comparar visitas e inicios de aplicaciones móviles).

* **Bloqueos**

   Se activa cuando la aplicación no se cierra correctamente. Este evento se envía cuando la aplicación se inicia después de haberse bloqueado.

   >[!TIP]
   >Se considera que la aplicación se bloquea si no se llama al cierre.

* **Duración total de la sesión**

   Duración de la sesión total agregada.

## Dimensiones {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Here is the list of default mobile dimensions:

* **Install Date**

   Fecha del primer inicio después de la instalación. El formato de la fecha es *MM/DD/AAAA*.

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
   >Los inicios desde la última actualización no se almacenan automáticamente en una variable de Analytics. Debe crear una regla de procesamiento para copiar este valor en una variable de Analytics para la generación de informes.

* **Nombre del dispositivo**

   Almacena el nombre del dispositivo. In iOS, a comma-separated, two-digit string identifies the iOS device. El primer número representa la generación del dispositivo y el segundo número versiones diferentes miembros de la familia de dispositivos. Puede consultar la lista completa de los nombres comunes de dispositivos en [iOS Device Versions](/help/ios/reference/device-versions.md) (Versiones de dispositivos iOS).

* **Nombre del operador de telefonía móvil**

   Almacena el nombre del proveedor de servicios móviles.

* **Resolución**

   Anchura y altura en píxeles reales.
