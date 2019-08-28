---
description: La geolocalización le ayuda a medir los datos de ubicación utilizando latitudes, longitudes y puntos de interés predefinidos en sus aplicaciones Android.
seo-description: La geolocalización le ayuda a medir los datos de ubicación utilizando latitudes, longitudes y puntos de interés predefinidos en sus aplicaciones Android.
seo-title: Geolocalización y puntos de interés
solution: Marketing Cloud, Analytics
title: Geolocalización y puntos de interés
topic: Desarrollador e implementación
uuid: b 8209370-cbc 4-40 f 9-97 d 8-017 e 2 d 74 a 377
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

La geolocalización le ayuda a medir los datos de ubicación utilizando latitudes, longitudes y puntos de interés predefinidos en sus aplicaciones Android.

Cada llamada a `trackLocation` envía la siguiente información:

* Latitud, longitud y ubicación en un punto de interés (POI) definido en la interfaz de usuario de Adobe Mobile Services.

   Esta información se pasa a variables de soluciones móviles para la realización automática de informes.

* Distancia al centro y precisión, pasados como datos de contexto.

   Estas variables no se capturan de forma automática. You must map these context data variables by using the instructions in the *Sending Additional Data* section below.

## Actualización de puntos de interés dinámicos {#section_3747B310DD5147E2AAE915E762997712}

A partir de la versión 4.2, los puntos de interés se definen en la interfaz de usuario de Adobe Mobile y se sincronizan de forma dinámica con el archivo de configuración de la aplicación. Esta sincronización requiere `analytics.poi` una configuración en la configuración JSON [de adbmobile](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Si no se ha realizado esta configuración, debe descargar una versión actualizada del archivo `ADBMobile.json` y añadirlo a su aplicación. Para obtener más información, consulte [Descargar el SDK y las herramientas de prueba](/help/android/getting-started/requirements.md).

## Tracking geo-location and POIs {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto intellij IDEA o Eclipse* en [implementación y ciclo vital de Core](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Llame a `trackLocation` para realizar un seguimiento de la ubicación actual:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >Puede llamar `trackLocation` en cualquier momento.

   You can use location strategies to determine the location that is passed to the `trackLocation` call. Para obtener más información, consulte [Estrategias de ubicación de Android](https://developer.android.com/guide/topics/location/strategies.html).

Además, si se determina que la ubicación está en el radio de un punto de interés definido, se envía una variable de datos de contexto `a.loc.poi` junto a la visita de `trackLocation` y se comunica como punto de interés en los informes **Desglose de ubicación**. También se envía una variable de contexto `a.loc.dist` con la distancia en metros desde las coordenadas definidas.

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además de los datos de ubicación, puede enviar datos de contexto adicionales con cada llamada de seguimiento de ubicación:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

El valor de los datos de contexto debe asignarse a variables personalizadas de la interfaz de Adobe Mobile Services:

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

La latitud y la longitud se envían utilizando tres parámetros de datos de contexto diferentes, representando cada uno un nivel de precisión distinto, por lo que se tiene un total de seis parámetros de datos de contexto.

Por ejemplo, las coordenadas lat = 40.93231, long = -111.93152 representan una ubicación con una precisión de 1 metro. Esta ubicación se divide en función del nivel de precisión en las siguientes variables:

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111.9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Algunos niveles de precisión podrían aparecer como `00`, en función de la precisión de la ubicación actual. Por ejemplo, si la ubicación tiene actualmente una precisión de 100 metros, `a.loc.lat.c` y `a.loc.lon.c` se rellenarán con el valor `00`.

Recuerde la información siguiente:

* A `trackLocation` request sends in the equivalent of a `trackAction` call.

* Los puntos de interés no se pasan como parte de llamadas típicas a `trackAction` y `trackState`, por lo que debe utilizar una llamada a `trackLocation` para realizar el seguimiento de estos puntos.

* Debe realizar todas las llamadas necesarias a `trackLocation` para realizar el seguimiento de la ubicación y los puntos de interés.

   Recomendamos llamar a `trackLocation` al iniciar la aplicación y, después, cuando sea necesario, dependiendo de los requisitos de la aplicación.

* Los puntos de interés solo se rellenan una vez que se definen en el archivo de configuración de la aplicación.

   Los puntos de interés no se aplican a llamadas históricas a `trackLocation` realizadas con anterioridad.
* Las llamadas a `trackLocation` permiten el envío de datos de contexto adicionales, como las llamadas a `trackAction`.

* Cuando el diámetro de dos puntos de interés se superpone, se utiliza el primer punto de interés que contenga la ubicación actual.

   Si los puntos de interés se superponen, deberá listarlos en orden, de mayor a menor granularidad, para garantizar que en los informes aparezca el punto de interés más granular.

