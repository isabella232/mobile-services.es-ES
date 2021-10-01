---
description: En esta sección se describe cómo migrar de la versión 3.x de un SDK móvil de Windows anterior al SDK 4.x de la Plataforma universal de Windows para las soluciones de Experience Cloud.
solution: Experience Cloud,Analytics
title: Migrar a 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 27%

---

# Migración a los SDK 4.x{#migrate-to-x}

En esta sección se describe cómo migrar de la versión 3.x del SDK móvil de Windows al SDK 4.x de la Plataforma universal de Windows para las soluciones de Experience Cloud.

Con el paso a la versión 4.x, ahora se puede acceder a toda la funcionalidad a través de métodos estáticos. Ya no es necesario realizar un seguimiento de sus propios objetos.

Las siguientes secciones le guían a través de la migración de la versión 3.x a la versión 4.x.

## Eliminación de propiedades no utilizadas {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Probablemente haya notado un nuevo archivo `ADBMobileConfig.json` incluido con su descarga. Este archivo contiene ajustes globales y específicos de la aplicación, y reemplaza la mayoría de las variables de configuración utilizadas en versiones anteriores.

Este es un ejemplo de archivo `ADBMobileConfig.json`:

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

### Migración desde 3.x

La siguiente tabla proporciona una lista de variables en los SDK 3.x y el nuevo nombre en los SDK 4.x:

| Variable de configuración/Método | Variable en el archivo `ADBMobileConfig.json`. |
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

En lugar de utilizar las llamadas `Track` y `TrackLink` centradas en la web, la versión 4 del SDK emplea dos métodos que tienen un poco más de sentido en el mundo móvil:

* `TrackState` Los estados son las visualizaciones disponibles en su aplicación, como &quot;tablero de inicio&quot;, &quot;configuración de la aplicación&quot;, &quot;carrito&quot;, etc. Estos estados son similares a las páginas de un sitio web y las llamadas `trackState` incrementan las visualizaciones de página.

* `TrackAction` Las acciones son cosas que suceden en la aplicación y que es interesante medir, por ejemplo, &quot;inicios de sesión&quot;, &quot;pulsaciones en banners&quot;, &quot;suscripciones a fuentes&quot; y otras métricas. Estas llamadas no incrementan las visualizaciones de página.

El parámetro `contextData` para ambos métodos contiene pares de nombre-valor que se envían como datos de contexto.

### Eventos, props y eVars

Si ha visto los [métodos del SDK](/help/universal-windows/c-configuration/methods.md), probablemente se esté preguntando dónde establecer eventos, eVars, props, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para el sistema de informes.

Las reglas de procesamiento ofrecen las siguientes ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

Para obtener más información, consulte la sección *Reglas de procesamiento* en [Información general de Analytics](/help/universal-windows/analytics/analytics.md).

Cualquier valor que asignara directamente a variables debe agregarse a los datos de contexto. Esto significa que las llamadas a `SetProp`, `SetEvar` y las asignaciones a datos de contexto persistentes deben eliminarse, y los valores deben agregarse a los datos de contexto.

### AppSection/Server, GeoZip, Transaction ID, Campaign y otras variables estándar

Los demás datos que configurara en el objeto de medición, incluidas las variables arriba indicadas, deberían agregarse a los datos de contexto. Es decir, los únicos datos que se envían con una llamada `TrackState` o `TrackAction` son la carga útil del parámetro `data`.

**Reemplazo de las llamadas de seguimiento**

En todo su código, sustituya los siguientes métodos con una llamada a `trackState` o `trackAction`:

**Migración desde 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Servicio de ID personalizado {#section_2CF930C13BA64F04959846E578B608F3}

Reemplace la variable `visitorID` con una llamada a `setUserIdentifier`.

## Seguimiento sin conexión {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

El seguimiento sin conexión está habilitado en el archivo `ADBMobileConfig.json` . El resto de la configuración sin conexión se realiza automáticamente.

En todo el código, elimine las llamadas a los siguientes métodos:

**Migración desde 3.x:**

* SetOnline
* SetOffline

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

El valor de `"&&products"` (en este ejemplo, el valor es `";Cool Shoe`&quot;) debe seguir la sintaxis de la cadena de products para el tipo de evento que esté rastreando.
