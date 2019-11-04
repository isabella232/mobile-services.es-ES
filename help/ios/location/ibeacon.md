---
description: El seguimiento de iBeacon le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.
seo-description: El seguimiento de iBeacon le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.
seo-title: Seguimiento de iBeacon
solution: Experience Cloud,Analytics
title: Seguimiento de iBeacon
topic: Desarrollador e implementación
uuid: 390883db-027e-4d12-8a16-86d514579db1
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Seguimiento de iBeacon {#ibeacon-tracking}

El seguimiento de iBeacon le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.

Los siguientes datos de señalización se envían a Analytics y Target cuando se llama a `trackBeacon`:

* `a.beacon.uuid`: ProximityUUID de la señalización
* `a.beacon.major`: número mayor de la señalización, como un número de almacén
* `a.beacon.minor`: número menor de la señalización, como un número exclusivo dentro de un almacén
* `a.beacon.prox`: los siguientes valores representan la proximidad del usuario a la señalización:

   * `0` es desconocido
   * `1` es inmediato
   * `2` es cerca
   * `3` es lejos

## Seguimiento de iBeacons {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Cuando un dispositivo esté en las inmediaciones de una señalización, realice una llamada a `trackBeacon`:

   ```objective-c
   [ADBMobile trackBeacon:beacon data:nil];
   ```

1. Cuando el usuario deje las inmediaciones de la señalización, borre la señalización actual:

   ```objective-c
   [ADBMobile trackingClearCurrentBeacon];
   ```

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del nombre de acción temporizada, puede enviar datos de contexto adicionales con cada llamada de seguimiento de acción:

```objective-c
[ADBMobile trackBeacon:beacon data:@{@"myapp.ImageLiked" : imageName}];
```

El valor de los datos de contexto debe asignarse a variables personalizadas:

![](assets/map-variable-context-ltv.png)

## Ejemplos {#section_9749238BCBC148998CB18E97D7670D19}

```objective-c
- (void)locationManager:(CLLocationManager *)manager didRangeBeacons:(NSArray *)beacons inRegion:(CLBeaconRegion *)region { 
    if (beacons.count > 0) { 
        CLBeacon *beacon = beacons[0]; 
        // Adobe - track when in range of a beacon 
        [ADBMobile trackBeacon:beacon data:@{@"sampleContextData" : @"sampleContextDataVal"}]; 
    } 
} 
 
// When the user leaves the proximity of the beacon, clear the current beacon 
[ADBMobile trackingClearCurrentBeacon];
```

