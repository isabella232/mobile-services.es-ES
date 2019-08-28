---
description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
keywords: android; library; mobile; sdk
seo-description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
seo-title: Configuración de Audience Manager
solution: Marketing Cloud, Analytics
title: Configuración de Audience Manager
topic: Desarrollador e implementación
uuid: f 68 d 5 b 2 e-fa 2 c -4 db 6-98 ad-d 1855 a 2 c 45 ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Puede enviar señales y recuperar segmentos de visitantes desde Audience Manager.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Requerido)** Debe llamarse al `setContext()` método una vez en el `onCreate()` método de la actividad principal.

Este es un ejemplo de código para este método:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si ha agregado esta llamada de método al implementar Analytics o Target, no necesita agregarla de nuevo.
