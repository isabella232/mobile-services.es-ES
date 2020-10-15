---
description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
keywords: android;library;mobile;sdk
seo-description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
seo-title: Configuración de Audience Manager
solution: Experience Cloud,Analytics
title: Configuración de Audience Manager
topic: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '88'
ht-degree: 100%

---


# Configuración de Audience Manager {#audience-manager-configuration}

Puede enviar señales y recuperar segmentos del visitante desde Audience Manager.

## Establecer el contexto de la aplicación {#section_37CAE496FF894FCA821F7760605574CA}

**(Requerido)** Se debe llamar al método `setContext()` una vez en el método `onCreate()` de la actividad principal.

Este es un ejemplo de código para este método:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si agregó esta llamada al método al implementar Analytics o Target, no es necesario que lo haga de nuevo.
