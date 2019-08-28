---
description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo en cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo en cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-title: Acciones temporizadas
solution: Marketing Cloud, Analytics
title: Acciones temporizadas
topic: Desarrollador e implementación
uuid: dbcbac 5 a -6345-49 f 6-b 050-0 db 05292 f 005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo en cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.

Para las acciones temporizadas se comunican las siguientes métricas:

* Total de segundos en la aplicación entre inicio y final (entre sesiones)
* Total de segundos entre inicio y final (tiempo de reloj)

Una llamada de retorno opcional le permite realizar acciones adicionales cuando se completa la acción temporizada:

* Ejecutar código y agregar cualquier lógica: lógica personalizada opcional basada en los resultados de duración.
* Agregar datos de contexto antes de pasar las duraciones.
* Cancelar visitas y duraciones no enviadas todavía.

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en [Implementación principal y Ciclo vital](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Llame a `trackTimedActionStart` y proporcione un nombre de acción temporizada y datos de contexto opcionales.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Opcional) Para agregar datos de contexto adicionales en cualquier momento, llame a `trackTimedActionUpdate` con el nombre de la acción temporizada.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Cuando el evento se complete, llame a `trackTimedActionEnd` y transfiera el nombre de la acción temporizada y `TimedActionBlock` (llamada de retorno), que buscará todos los datos y calculará las duraciones.

   Las métricas de eventos temporizados se guardan en variables de soluciones móviles para la realización automática de informes.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del nombre de la acción temporizada, puede enviar datos de contexto adicionales con las llamadas de inicio y de actualización de acción:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Los valores de datos de contexto deben asignarse a variables personalizadas:

![](assets/map-variable-context-ltv.png)

## Ejemplo {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```
