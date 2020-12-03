---
description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada al servidor.
seo-description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada al servidor.
seo-title: Serialización de eventos
solution: Experience Cloud,Analytics
title: Serialización de eventos
topic: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

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

