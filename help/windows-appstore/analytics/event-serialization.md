---
description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-title: Serialización de eventos
solution: Experience Cloud,Analytics
title: Serialización de eventos
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# Serialización de eventos{#event-serialization}

Las reglas de procesamiento no admiten la serialización de eventos. En el SDK móvil, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.

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
