---
description: Puede enviar contenido de destino en aplicaciones Android.
keywords: android;library;mobile;sdk
seo-description: Puede enviar contenido de destino en aplicaciones Android.
seo-title: Configuración de Target
solution: Experience Cloud,Analytics
title: Configuración de Target
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '72'
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
