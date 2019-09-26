---
description: Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.
keywords: android;library;mobile;sdk
seo-description: Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.
seo-title: Migración a la biblioteca Android 4.x
solution: Marketing Cloud,Analytics
title: Migración a la biblioteca Android 4.x
topic: Desarrollador e implementación
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

Esta información le ayuda a migrar de las versiones 3.x o 2.x a la versión 4.x de la biblioteca Android.

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Si modifica o elimina los valores en `SharedPreferences` que el SDK espera, el comportamiento inesperado podría provocar incongruencias en los datos.

En la biblioteca de la versión 4.x, los métodos públicos se consolidan en un encabezado. Además, ahora se puede acceder a toda la funcionalidad a partir de métodos en el nivel de clase, por lo que no tiene que seguir la pista de punteros, instancias e instancias únicas.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

En la versión 4 ya no puede asignar en su aplicación variables como events, eVars, props, heirs y lists. En lugar de ello, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics para la realización de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es muy pequeño.

   Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento.

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración.

### Mover el archivo de configuración

1. Mueva el valor establecido para la variable de la primera columna a la variable de la segunda columna.
1. Elimine la antigua variable de configuración de su código.

### Migración desde la versión 3.x

To migrate from version 3.x to 4, move the configuration variable/method value to the  variable.`ADBMobileConfig.json`

| Configuration Variable or Method | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | “ssl” |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |

### Migración desde la versión 2.x

Para migrar de la versión 2.x a la versión 4, mueva el valor de la primera columna a la variable de la segunda columna.

| Variable de configuración | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the  prefix. `"https://"` El prefijo de protocolo se agrega automáticamente en función del ajuste “ssl”. |
| trackingServerSecure | Eliminar. Para conexiones seguras, defina “server” y después habilite “ssl”. |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | “ssl” |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |
| timestamp | Eliminar, ya no es configurable. |
| dc | Eliminar, ya no se utiliza. |
| userAgent | Eliminar, ya no es configurable. |
| dynamicVariablePrefix | Eliminar, ya no se utiliza. |
| visitorNamespace | Eliminar, ya no se utiliza. |
| usePlugins | Eliminar, ya no se utiliza. |
| useBestPractices  todas las llamadas para producir mediciones (getChurnInstance) | Remove, replaced by  Lifecycle Metrics. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

En vez de utilizar las llamadas `track` y `trackLink`, centradas en la web, la versión 4 del SDK emplea los siguientes métodos:

* `trackState`, que son las vistas disponibles en la aplicación, como `home dashboard`, `app settings`, `cart`, etc.

   Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* `trackAction` actions, such as `logons`, `banner taps`, `feed subscriptions`, and so on that occur in your app and that you want to measure.

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## Eventos, props y eVars

En la versión 4 ya no puede asignar directamente en su aplicación variables como events, eVars, props, heirs y lists. Ahora el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics para la realización de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es muy pequeño.

   Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento. Para obtener más información, consulte [Reglas de procesamiento y datos de contexto](/help/android/getting-started/proc-rules.md).

Los valores que asignaba directamente a variables deberían agregarse al HashMap `data`. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server, GeoZip, ID de transacción, Campaign y otras variables estándar

Los datos que configuraba en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse al HashMap `data`. Los únicos datos que se envían con una llamada a `trackState` o `trackAction` son la carga útil del parámetro `data`.

### Reemplazar llamadas de seguimiento

Sustituya los siguientes métodos por una llamada a `trackState` o `trackAction`:

* **Migración desde la versión 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migración desde la versión 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

Elimine las llamadas a los siguientes métodos:

**Versión 3.x**

* `setOnline`
* `setOffline`

**Versión 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

