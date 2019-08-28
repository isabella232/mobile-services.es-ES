---
description: Puede enviar contenido de destino en aplicaciones Android.
keywords: android; library; mobile; sdk
seo-description: Puede enviar contenido de destino en aplicaciones Android.
seo-title: Configuración de Target
solution: Marketing Cloud, Analytics
title: Configuración de Target
topic: Desarrollador e implementación
uuid: 09 fe 2 c 9 c -7 b 60-49 c 3-bb 9 d -36 a 30 ce 7 c 350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Puede enviar contenido de destino en aplicaciones Android.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Requerido)** Debe llamarse al `setContext()` método una vez en el `onCreate()` método de la actividad principal.

Por ejemplo:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Si ya agregó esta llamada al método al implementar Analytics o Gestión de público, no es necesario que lo haga de nuevo.
