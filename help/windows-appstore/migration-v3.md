---
description: En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK 4.x Universal App Store para Windows 8.1 para soluciones Experience Cloud.
seo-description: En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK 4.x Universal App Store para Windows 8.1 para soluciones Experience Cloud.
seo-title: Migrar a los SDK 4.x
solution: Experience Cloud,Analytics
title: Migrar a los SDK 4.x
topic: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 24%

---


# Migrar a los SDK 4.x {#migrate-to-the-x-sdks}

En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK 4.x Universal App Store para Windows 8.1 para soluciones Experience Cloud.

Con el cambio a la versión 4.x, ahora se puede acceder a toda la funcionalidad a través de métodos estáticos, por lo que ya no se debe realizar un seguimiento de sus propios objetos.

Las siguientes secciones explican cómo migrar de la versión 3.x a la versión 4.x.

## Eliminación de propiedades no utilizadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probablemente notó un nuevo `ADBMobileConfig.json` archivo incluido con la descarga. Este archivo contiene la configuración global específica de la aplicación y reemplaza a la mayoría de las variables de configuración que se usaban en versiones anteriores. Este es un ejemplo de archivo `ADBMobileConfig.json`:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración. Mueva el valor establecido para la variable en la primera columna a la variable en la segunda columna y, a continuación, elimine la variable de configuración antigua del código.

## Migración desde 3.x

| Variable/método de configuración | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Eliminar, ya no se utiliza. |
| linkTrackVars | Eliminar, ya no se utiliza. |
| linkTrackEvents | Eliminar, ya no se utiliza. |

## Actualización de llamadas y variables de seguimiento {#section_96E7D9B3CDAC444789503B7E7F139AB9}

En lugar de utilizar las llamadas `Track` `TrackLink` y los enfoques web, la versión 4 del SDK utiliza dos métodos que tienen un poco más de sentido en el mundo móvil:

* `TrackState` Los estados son las vistas disponibles en la aplicación, como &quot;panel principal&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* `TrackAction` Las acciones son cosas que suceden en la aplicación y que desea medir, como &quot;inicios de sesión&quot;, &quot;toques en banners&quot;, &quot;suscripciones de fuentes&quot; y otras métricas. Estas llamadas no incrementan las vistas de página.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

## Eventos, props, eVars

Si ha observado los métodos [del](/help/windows-appstore/c-configuration/methods.md)SDK, probablemente se esté preguntando dónde establecer eventos, eVars, props, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para el sistema de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

Los valores que asignaba directamente a variables deberían agregarse a los datos de contexto. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server, GeoZip, ID de transacción, Campaña y otras variables estándar**

Cualquier otro dato que configurara en el objeto de medición, incluidas las variables enumeradas arriba, debería agregarse a los datos de contexto en su lugar.

Para decirlo de forma sencilla, los únicos datos enviados con una llamada `TrackState` o `TrackAction` son la carga útil en el `data` parámetro .

### Reemplazo de las llamadas de seguimiento

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

### Migración desde 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## ID de visitante personalizado {#section_2CF930C13BA64F04959846E578B608F3}

Reemplace la variable `visitorID` con una llamada a `setUserIdentifier`.

## Seguimiento sin conexión {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

En todo el código, elimine las llamadas a los siguientes métodos:

### Migración desde 3.x

* `SetOnline`
* `SetOffline`

## Variable Products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como la variable no está disponible en las reglas de procesamiento, puede utilizar la siguiente sintaxis para establecer `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

En este ejemplo, el valor de `"&&products"` es `";Cool Shoe`&quot; y debe seguir la sintaxis de la cadena de productos para el tipo de evento que está rastreando.