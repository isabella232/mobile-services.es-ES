---
description: El seguimiento de señalización le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.
keywords: android;biblioteca;móvil;sdk
seo-description: El seguimiento de señalización le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.
seo-title: Seguimiento de señalización
solution: Marketing Cloud,Analytics
title: Seguimiento de señalización
topic: Desarrollador e implementación
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Seguimiento de señalización {#beacon-tracking}

El seguimiento de señalización le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.

Los siguientes datos de señalización se envían a Analytics y Target cuando se llama a `trackBeacon`:

* `a.beacon.uuid` - ProximityUUID de la señalización
* `a.beacon.major`: número mayor de la señalización (por ejemplo, número de almacén)
* `a.beacon.minor`: número menor de la señalización (por ejemplo, un número exclusivo dentro de un almacén)
* `a.beacon.prox`: los valores 0-3 representan la proximidad del usuario a la señalización.

Este es el significado de estos valores:

* 0: proximidad desconocida
* 1: proximidad inmediata
* 2: proximidad cercana
* 3: proximidad lejana

Estos datos de señalización se capturan en variables de soluciones móviles.

## Señalizaciones de seguimiento {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* IntelliJ IDEA o Eclipse en la implementación [principal y el ciclo vital](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Obtenga la ubicación de la señalización.

   Hay disponibles varias bibliotecas de terceros para escanear señalizaciones LE Bluetooth, dependiendo del fabricante de la señalización.
1. Una vez obtenida la información de la señalización, utilice la siguiente llamada para realizar un seguimiento de la ubicación:

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. Cuando el usuario deje las inmediaciones de la señalización, borre la señalización actual:

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además de los datos de señalización, puede enviar datos de contexto adicionales con cada llamada a `trackBeacon`:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

Los valores de datos de contexto deben asignarse a variables personalizadas en Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

