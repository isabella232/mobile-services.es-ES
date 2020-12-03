---
description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de cada sesión y el tiempo total entre sesiones que tardará la acción en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de cada sesión y el tiempo total entre sesiones que tardará la acción en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-title: Acciones temporizadas
solution: Experience Cloud,Analytics
title: Acciones temporizadas
topic: Developer and implementation
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 100%

---


# Acciones temporizadas {#timed-actions}

Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de cada sesión y el tiempo total entre sesiones que tardará la acción en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.

Las siguientes métricas se incluyen en los informes para acciones temporizadas:

* Total de segundos en la aplicación entre inicio y final: entre sesiones
* Total de segundos entre el inicio y el final (hora del reloj)

Una llamada de retorno opcional le permite realizar acciones adicionales cuando finaliza la acción temporizada:

* Ejecute el código y agregue cualquier lógica: lógica personalizada opcional basada en los resultados de duración.
* Añada datos de contexto antes de pasar duraciones.
* Cancele visitas y duraciones aún no enviadas.

## Seguimiento de acciones temporizadas {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
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

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del nombre de la acción temporizada, puede enviar datos de contexto adicionales con las llamadas de inicio y de actualización de acción:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

El valor de los datos de contexto debe asignarse a variables personalizadas:

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

