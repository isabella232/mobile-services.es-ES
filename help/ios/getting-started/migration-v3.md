---
description: Esta información le ayuda a hacer la migración de las versiones 3.x o 2.x a la versión 4.x de la biblioteca iOS.
seo-description: Esta información le ayuda a hacer la migración de las versiones 3.x o 2.x a la versión 4.x de la biblioteca iOS.
seo-title: Migración a la biblioteca 4. x iOS
solution: Marketing Cloud, Analytics
title: Migración a la biblioteca 4. x iOS
topic: Desarrollador e implementación
uuid: 5668972 b-f 355-4 e 03-9 df 0-8 c 82 ddf 6809 b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

Esta información le ayuda a hacer la migración de las versiones 3.x o 2.x a la versión 4.x de la biblioteca iOS.

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  Si modifica o elimina los valores en `NSUserDefaults` que el SDK espera, el comportamiento inesperado podría provocar incongruencias en los datos.

En la versión 4. x de la biblioteca SDK de iOS, los métodos públicos se consolidan en un encabezado. Además, ahora se puede acceder a la funcionalidad mediante métodos de nivel de clase, por lo que no es necesario realizar un seguimiento de los punteros, instancias o singletons.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

En la versión 4 ya no puede asignar directamente en su aplicación variables como events, eVars, props, heirs y lists. En lugar de ello, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics para la realización de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es muy pequeño.

   Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento.

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

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


### Mover el archivo de configuración

Para mover el archivo de configuración:

1. Mueva el valor establecido para la variable de la primera columna a la variable de la segunda columna.
1. Elimine la antigua variable de configuración de su código.

### Información de migración

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración.

#### Migración desde la versión 3.x

Mueva el valor de la primera columna a la variable en la segunda columna.

| Variable de configuración | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| offlineTrackingEnabled | “offlineEnabled” |
| offlineHitLimit | “batchLimit” |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | “ssl” |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |


#### Migración desde la versión 2.x

Mueva el valor de la primera columna a la variable en la segunda columna.

| Variable de configuración | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", elimine el `"https://"` prefijo. El prefijo de protocolo se agrega automáticamente en función del ajuste “ssl”. |
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
| useBestPractices  todas las llamadas para producir mediciones (getChurnInstance ) | Eliminar, reemplazada por métricas del ciclo vital. Para obtener más información, consulte [Métricas del ciclo vital](//help/ios/metrics.md). |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

En vez de utilizar las llamadas `track` y `trackLink`, centradas en la web, la versión 4 del SDK emplea los siguientes métodos:

* `trackState:data:` son las visualizaciones disponibles en su aplicación, `home dashboard``app settings``cart`como, etc.

   Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* `trackAction:data:` acciones, como `logons``banner taps`, `feed subscriptions`y otras métricas que se producen en la aplicación y que desea medir.

El parámetro `data` para ambos métodos es un `NSDictionary` que contiene pares de nombre-valor que se envían como datos de contexto.

### Eventos, props, evars

En la versión 4 ya no puede asignar directamente en su aplicación variables como events, eVars, props, heirs y lists. Ahora el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics para la realización de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es muy pequeño.

   Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento. Para obtener más información, consulte [Reglas de procesamiento y datos de contexto](/help/ios/getting-started/proc-rules.md).

Los valores que asignaba directamente a variables deberían agregarse al   `data``NSDictionary`. This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### Appsection/Server, geozip, transaction ID, Campaign y otras variables estándar

Los datos que configuraba en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse al   `data``NSDictionary`. Los únicos datos que se envían con una llamada a `trackState` o `trackAction` son la carga útil del parámetro `data`.

### Reemplazar llamadas de seguimiento

En su código, sustituya los siguientes métodos con una llamada a `trackState` o `trackAction`:

#### Migración desde la versión 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migración desde la versión 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier:`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

En su código, elimine las llamadas a los métodos siguientes:

### Versión 3.x

* `setOnline`
* `setOffline`

### Versión 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como la variable no está disponible en las reglas de procesamiento, puede utilizar la siguiente sintaxis para establecer `products`products:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)