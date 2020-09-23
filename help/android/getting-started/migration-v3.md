---
description: Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.
keywords: android;library;mobile;sdk
seo-description: Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.
seo-title: Migración a la biblioteca Android 4.x
solution: Experience Cloud,Analytics
title: Migración a la biblioteca Android 4.x
topic: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 59%

---


# Migración a la biblioteca Android 4.x {#migrating-to-the-android-x-library}

Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.

>[!IMPORTANT]
>
>El SDK utiliza `SharedPreferences` a fin de almacenar los datos necesarios para calcular los usuarios únicos, las métricas del ciclo vital y otros datos relacionados con la función principal del SDK.  Si modifica o elimina los valores en `SharedPreferences` que el SDK espera, el comportamiento inesperado podría provocar incongruencias en los datos.

En la biblioteca de la versión 4.x, los métodos públicos se consolidan en un encabezado. Además, ahora se puede acceder a toda la funcionalidad a través de métodos de nivel de clase, por lo que no es necesario realizar un seguimiento de punteros, instancias o singletones.

## Eventos, props y eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

En la versión 4, ya no puede asignar variables como eventos, eVars, props, herederos y listas en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para sistema de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto.

   Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

>[!TIP]
>
>Los valores que asignaba directamente a variables deberían agregarse al HashMap `data`.

## Eliminación de propiedades no utilizadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

El nuevo archivo `ADBMobileConfig.json` contiene ajustes globales y específicos de la aplicación, y reemplaza la mayoría de las variables de configuración utilizadas en versiones anteriores. Este es un ejemplo de archivo `ADBMobileConfig.json`:

```js
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
        "poi" : [
                    ["san francisco",37.757144,-122.44812,7000],
                    ["santa cruz",36.972935,-122.01725,600]
                ]
    },
 "target" : {
  "clientCode" : "myTargetClientCode",
  "timeout" : 5
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```

## Mover el archivo de configuración y migración a la versión 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración.

### Mover el archivo de configuración

1. Mueva el valor establecido para la variable en la primera columna a la variable en la segunda columna.
1. Elimine la variable de configuración antigua del código.

### Migración desde la versión 3.x

Para migrar de la versión 3.x a la 4, mueva el valor de método/variable de configuración a la variable `ADBMobileConfig.json`.

| Variable de configuración o método | Variable en el archivo `ADBMobileConfig.json` |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |

### Migración desde la versión 2.x

Para migrar de la versión 2.x a la versión 4, mueva el valor de la primera columna a la variable de la segunda columna.

| Variable de configuración | Variable en el archivo `ADBMobileConfig.json` |
| --- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, remove the `"https://"` prefix. El prefijo de protocolo se agrega automáticamente según la configuración &quot;ssl&quot;. |
| trackingServerSecure | Eliminar. Para conexiones seguras, defina &quot;server&quot; y luego habilite &quot;ssl&quot;. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |
| timestamp | Eliminar, ya no se puede configurar. |
| dc | Eliminar, ya no se utiliza. |
| userAgent | Eliminar, ya no se puede configurar. |
| dynamicVariablePrefix | Eliminar, ya no se utiliza. |
| visitorNamespace | Eliminar, ya no se utiliza. |
| usePlugins | Eliminar, ya no se utiliza. |
| useBestPractices todas las llamadas para producir mediciones ( getChurnInstance) | Eliminar, sustituido por métricas del ciclo vital. |

## Actualización de llamadas y variables de seguimiento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

En vez de utilizar las llamadas `track` y `trackLink`, centradas en la web, la versión 4 del SDK emplea los siguientes métodos:

* `trackState`, que son las vistas que están disponibles en la aplicación, como `home dashboard`, `app settings` o `cart`, entre otros.

   Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* Las acciones `trackAction`, como `logons`, `banner taps`, `feed subscriptions` y otras que se producen en la aplicación y que desea medir.

El parámetro `contextData` para ambos métodos es un `HashMap<String, Object>`, que contiene los pares de nombre-valor que se envían como datos de contexto.

## Eventos, props y eVars

En la versión 4, ya no puede asignar variables como eventos, eVars, props, herederos y listas directamente en la aplicación. El SDK ahora utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para sistema de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización al almacén de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto.

   Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento. Para obtener más información, consulte Reglas [de procesamiento y Datos](/help/android/getting-started/proc-rules.md)de contexto.

Los valores que asignaba directamente a variables deberían agregarse al HashMap `data`. Esto significa que las llamadas a `setEvar` y `setProp`, así como las asignaciones a datos de contexto persistentes, deberían eliminarse para agregar sus valores al parámetro `data`.

## AppSection/Server, GeoZip, Transaction ID, Campaign y otras variables estándar

Los datos que configuraba en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse al HashMap `data`. Los únicos datos que se envían con una llamada a `trackState` o `trackAction` son la carga útil del parámetro `data`.

### Reemplazo de las llamadas de seguimiento

Sustituya los siguientes métodos por una llamada a `trackState` o `trackAction`:

* **Migración desde la versión 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migración desde la versión 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## ID de visitante personalizado {#section_2CF930C13BA64F04959846E578B608F3}

Reemplace la variable `visitorID` con una llamada a `setUserIdentifier`.

## Seguimiento sin conexión {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

El seguimiento sin conexión se habilita en el archivo `ADBMobileConfig.json` y el resto de la configuración sin conexión se realiza automáticamente.

Elimine las llamadas a los siguientes métodos:

**Versión 3.x**

* `setOnline`
* `setOffline`

**Versión 2.x**

* `forceOffline`
* `forceOnline`

## Variable Products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para obtener más información acerca de la variable products, consulte [Variable Products](/help/android/analytics-main/products/products.md).

