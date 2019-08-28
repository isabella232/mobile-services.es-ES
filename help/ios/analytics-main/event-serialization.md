---
description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-title: Serialización de eventos
solution: Marketing Cloud, Analytics
title: Serialización de eventos
topic: Desarrollador e implementación
uuid: 19 a 27 df 4-0998-403 d -800 c -26 ff 61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Serialización de eventos {#event-serialization}

Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Por ejemplo:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

