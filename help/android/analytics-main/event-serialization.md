---
description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
keywords: android;biblioteca;móvil;sdk
seo-description: Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.
seo-title: Serialización de eventos
solution: Marketing Cloud,Analytics
title: Serialización de eventos
topic: Desarrollador e implementación
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Serialización de eventos {#event-serialization}

Las reglas de procesamiento no admiten la serialización de eventos. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer eventos serializados directamente en la llamada del servidor.

```java
cdata.put("&&events", "event1:12341234");
```

Por ejemplo:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

