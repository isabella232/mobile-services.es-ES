---
description: Puede enviar señales y recuperar segmentos del visitante desde gestión de público.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud Services,Analytics
title: Configuración de Audience Manager
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 100%

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
