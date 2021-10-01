---
description: Esta información le ayuda a hacer la migración de las versiones 3.x o 2.x a la versión 4.x de la biblioteca iOS.
solution: Experience Cloud,Analytics
title: Migración a la biblioteca iOS 4.x
topic-fix: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
exl-id: a58067e0-b6f4-4900-ba3f-7256d9259420
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 100%

---

# Migración a la biblioteca iOS 4.x{#migrating-to-the-x-ios-library}

Esta información le ayuda a hacer la migración de las versiones 3.x o 2.x a la versión 4.x de la biblioteca iOS.

>[!IMPORTANT]
>
>El SDK utiliza `NSUserDefaults` a fin de almacenar los datos necesarios para calcular los usuarios únicos, las métricas del ciclo vital y otros datos relacionados con la función principal del SDK.  Si modifica o elimina los valores en `NSUserDefaults` que el SDK espera, el comportamiento inesperado podría provocar incongruencias en los datos.

En la biblioteca de la versión 4.x del SDK para iOS, los métodos públicos se consolidan en un encabezado. Además, ahora se puede acceder a la funcionalidad a partir de métodos en el nivel de clase, por lo que no tiene que seguir la pista de punteros, instancias e instancias únicas.

## Eventos, props y eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

En la versión 4, ya no puede asignar variables como eventos, eVars, props, herederos y listas en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para el sistema de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto.

   Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

>[!TIP]
>
>Los valores que se han asignado directamente a variables deben agregarse ahora al NSDictionary `data`.

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


### Mover el archivo de configuración

Para mover el archivo de configuración:

1. Mueva el valor establecido para la variable de la primera columna a la variable de la segunda columna.
1. Elimine la variable de configuración antigua del código.

### Información de migración

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración.

#### Migración desde la versión 3.x

Mueva el valor de la primera columna a la variable de la segunda columna.

| Variable de configuración | Variable en el archivo `ADBMobileConfig.json` |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |


#### Migración desde la versión 2.x

Mueva el valor de la primera columna a la variable de la segunda columna.

| Variable de configuración | Variable en el archivo `ADBMobileConfig.json` |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, quite el prefijo `"https://"`. El prefijo de protocolo se agrega automáticamente según la configuración &quot;ssl&quot;. |
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
| useBestPractices todas las llamadas para producir mediciones (getChurnInstance) | Eliminar, sustituido por métricas del ciclo vital. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md). |


## Actualización de llamadas y variables de seguimiento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

En vez de utilizar las llamadas `track` y `trackLink`, centradas en la web, la versión 4 del SDK emplea los siguientes métodos:

* Los estados `trackState:data:` son las vistas que están disponibles en la aplicación, como `home dashboard`, `app settings` o `cart`, entre otros.

   Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* Las acciones `trackAction:data:`, como `logons`, `banner taps`, `feed subscriptions` y otras métricas que se producen en la aplicación y que desea medir.

El parámetro `data` para ambos métodos es un `NSDictionary` que contiene pares de nombre-valor que se envían como datos de contexto.

### Eventos, props y eVars

En la versión 4, ya no puede asignar variables como eventos, eVars, props, herederos y listas en la aplicación. El SDK ahora utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para sistema de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto.

   Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento. Para obtener más información, consulte [Reglas de procesamiento y Datos de contexto](/help/ios/getting-started/proc-rules.md).

Los valores que asignaba directamente a variables deberían agregarse al `data` `NSDictionary`. Esto significa que las llamadas a `setProp` y `setEvar`, así como las asignaciones a datos de contexto persistentes, deberían eliminarse para agregar sus valores al parámetro `data`.

### AppSection/Server, GeoZip, Transaction ID, Campaign y otras variables estándar

Los datos que configuraba en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse al `data` `NSDictionary`. Los únicos datos que se envían con una llamada a `trackState` o `trackAction` son la carga útil del parámetro `data`.

### Reemplazo de las llamadas de seguimiento

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

## ID de visitante personalizado {#section_2CF930C13BA64F04959846E578B608F3}

Reemplace la variable `visitorID` con una llamada a `setUserIdentifier:`.

## Seguimiento sin conexión {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

El seguimiento sin conexión se habilita en el archivo `ADBMobileConfig.json` y el resto de la configuración sin conexión se realiza automáticamente.

En su código, elimine las llamadas a los métodos siguientes:

### Versión 3.x

* `setOnline`
* `setOffline`

### Versión 2.x

* `forceOffline`
* `forceOnline`

## Variable products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como la variable no está disponible en las reglas de procesamiento, puede utilizar la siguiente sintaxis para establecer `products`products:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)
