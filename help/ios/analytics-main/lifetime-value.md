---
description: El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.
seo-description: El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.
seo-title: Valor de duración del visitante
solution: Marketing Cloud,Analytics
title: Valor de duración del visitante
topic: Desarrollador e implementación
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.

Cada vez que envía un valor con `trackLifetimeValueIncrease`, el valor se agrega al valor existente. El valor de duración se almacena en el dispositivo y se puede recuperar en cualquier momento realizando una llamada a `lifetimeValue`. Esto puede utilizarse para almacenar compras acumuladas en el tiempo, visualizaciones de anuncios, visualizaciones de vídeo completas, usos compartidos en medios sociales, cargas de fotografías, etc.

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en Implementación [principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Llame a `trackLifetimeValueIncrease` con la cantidad en que aumenta el valor:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del valor de duración, puede enviar datos de contexto adicionales con cada llamada de seguimiento de acción:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Los valores de datos de contexto deben asignarse a variables personalizadas:

![](assets/map-variable-context-ltv.png)

