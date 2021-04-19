---
description: Puede enviar contenido de destino en aplicaciones Android.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Puede enviar contenido de destino en aplicaciones Android.
seo-title: Configuración de Target
solution: Experience Cloud,Analytics
title: Configuración de Target
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 100%

---

# Configuración de Target {#target-configuration}

Puede enviar contenido de destino en aplicaciones Android.

## Establecer el contexto de la aplicación {#section_37CAE496FF894FCA821F7760605574CA}

**(Requerido)** Se debe llamar al método `setContext()` una vez en el método `onCreate()` de la actividad principal.

Por ejemplo:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si ya agregó esta llamada al método al implementar Analytics o Audience Manager, no es necesario que lo haga de nuevo.
