---
description: En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK Universal App Store 4.x de Windows 8.1 para soluciones de Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Migración a los SDK 4.x
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 25%

---

# Migración a los SDK 4.x {#migrate-to-the-x-sdks}

En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK Universal App Store 4.x de Windows 8.1 para soluciones de Experience Cloud.

Con el paso a la versión 4.x, ahora se puede acceder a toda la funcionalidad a través de métodos estáticos, por lo que ya no se realiza un seguimiento de sus propios objetos.

Las siguientes secciones le guían a través de la migración de la versión 3.x a la versión 4.x.

## Eliminación de propiedades no utilizadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probablemente notó un nuevo `ADBMobileConfig.json` incluido en la descarga. Este archivo contiene ajustes globales y específicos de la aplicación y reemplaza la mayoría de las variables de configuración utilizadas en versiones anteriores. Este es un ejemplo de archivo `ADBMobileConfig.json`:

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

Las siguientes tablas listan las variables de configuración que debe mover al archivo de configuración. Mueva el conjunto de valores de la variable de la primera columna a la variable de la segunda columna y, a continuación, elimine la variable de configuración antigua del código.

## Migración desde 3.x

| Variable de configuración/Método | en la variable `ADBMobileConfig.json` archivo. |
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

En lugar de usar el foco web `Track` y `TrackLink` , la versión 4 del SDK emplea dos métodos que tienen más sentido en el mundo móvil:

* `TrackState` Los estados son las visualizaciones disponibles en su aplicación, como &quot;tablero de inicio&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* `TrackAction` Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, &quot;inicios de sesión&quot;, &quot;pulsaciones en banners&quot;, &quot;suscripciones a fuentes&quot; y otras métricas. Estas llamadas no incrementan las visualizaciones de página.

La variable `contextData` para ambos métodos contiene pares de nombre-valor que se envían como datos de contexto.

## Eventos, props y eVars

Si ha visto el [Métodos SDK](/help/windows-appstore/c-configuration/methods.md), probablemente se esté preguntando dónde se configuran los eventos, las eVars, las props, los herederos y las listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para el sistema de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

Para obtener más información, consulte *Reglas de procesamiento* en [Analytics](/help/windows-appstore/analytics/analytics.md).

Cualquier valor que asignara directamente a variables debe agregarse a los datos de contexto. Esto significa que llama a `SetProp`, `SetEvar`, y las asignaciones a datos de contexto persistentes deberían eliminarse, así como los valores agregados a los datos de contexto.

**AppSection/Server, GeoZip, Transaction ID, Campaign y otras variables estándar**

Los demás datos que configurara en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse a los datos de contexto.

Para decirlo llanamente, los únicos datos que se envían con un `TrackState` o `TrackAction` es la carga útil en la variable `data` parámetro.

### Reemplazo de las llamadas de seguimiento

En todo su código, sustituya los siguientes métodos con una llamada a `trackState` o `trackAction`:

### Migración desde 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## ID de visitante personalizado {#section_2CF930C13BA64F04959846E578B608F3}

Reemplace la variable `visitorID` con una llamada a `setUserIdentifier`.

## Seguimiento sin conexión {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

El seguimiento sin conexión está habilitado en la variable `ADBMobileConfig.json` archivo. El resto de la configuración sin conexión se realiza automáticamente.

En todo el código, elimine las llamadas a los siguientes métodos:

### Migración desde 3.x

* `SetOnline`
* `SetOffline`

## Variable products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Como la variable no está disponible en las reglas de procesamiento, puede utilizar la siguiente sintaxis para establecer `products`products:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

En este ejemplo, el valor de `"&&products"` es `";Cool Shoe`&quot; y debe seguir la sintaxis de la cadena de products para el tipo de evento que esté rastreando.
