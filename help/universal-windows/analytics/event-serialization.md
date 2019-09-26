---
description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-title: Serialización de eventos
solution: Marketing Cloud,Analytics
title: Serialización de eventos
topic: Desarrollador e implementación
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Serialización de eventos {#event-serialization}

Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada al servidor.

```js
cdata["&&events"] = "event1:12341234";
```

Por ejemplo:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```

