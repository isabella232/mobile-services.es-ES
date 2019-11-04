---
description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
seo-title: Configuración de Audience Manager
solution: Experience Cloud,Analytics
title: Configuración de Audience Manager
topic: Desarrollador e implementación
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Configuración de Audience Manager{#audience-manager-configuration}

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
