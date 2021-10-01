---
description: El seguimiento de señalización le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud,Analytics
title: Seguimiento de señalización
topic-fix: Developer and implementation
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
exl-id: b8493e9d-ed1c-4404-a218-47a18a9c8faa
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 100%

---

# Seguimiento de señalización {#beacon-tracking}

El seguimiento de señalización le permite medir y segmentar microubicaciones empleando iBeacon y Bluetooth de baja energía.

Los siguientes datos de señalización se envían a Analytics y Target cuando se llama a `trackBeacon`:

* `a.beacon.uuid`: ProximityUUID de la señalización
* `a.beacon.major`: número mayor de la señalización (por ejemplo, número de almacén)
* `a.beacon.minor`: número menor de la señalización (por ejemplo, un número único dentro de un almacén)
* `a.beacon.prox`: los valores 0-3 representan la proximidad del usuario a la señalización.

Significados de estos valores:

* 0 = desconocido
* 1 = inmediato
* 2 = cerca
* 3 = lejos

Estos datos de señalización se capturan en variables de soluciones móviles.

## Seguimiento de señalizaciones {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Recopile la ubicación de señalizaciones.

   Hay varias bibliotecas de terceros disponibles para explorar señalizaciones LE Bluetooth, según el fabricante de la señalización.
1. Una vez obtenida la información de la señalización, use la siguiente llamada para hacer el seguimiento de la ubicación:

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

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además de los datos de señalización, puede enviar datos de contexto adicionales con cada llamada a `trackBeacon`:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

El valor de los datos de contexto debe asignarse a variables personalizadas de la interfaz de Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)
