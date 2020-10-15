---
description: El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.
seo-description: El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.
seo-title: Valor de duración de visitantes
solution: Experience Cloud,Analytics
title: Valor de duración de visitantes
topic: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '173'
ht-degree: 100%

---


# Valor de duración de visitantes {#visitor-lifetime-value}

El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario.

Cada vez que envía un valor con `trackLifetimeValueIncrease`, el valor se agrega al valor existente. El valor de duración se almacena en el dispositivo y se puede recuperar en cualquier momento realizando una llamada a `lifetimeValue`. Esto puede utilizarse para almacenar compras acumuladas en el tiempo, visualizaciones de anuncios, visualizaciones de vídeo completas, usos compartidos en medios sociales, cargas de fotografías, etc.

## Seguimiento del valor de duración de visitantes {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Llame a `trackLifetimeValueIncrease` con la cantidad en que aumenta el valor:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del valor de duración, puede enviar datos de contexto adicionales con cada llamada de seguimiento de acción:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

El valor de los datos de contexto debe asignarse a variables personalizadas:

![](assets/map-variable-context-ltv.png)

