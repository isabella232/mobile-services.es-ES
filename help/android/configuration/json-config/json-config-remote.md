---
description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-title: Anular la ruta de configuración JSON de ADBMobile
solution: Experience Cloud,Analytics
title: Anular la ruta de configuración JSON de ADBMobile
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%

---

# Anular la ruta de configuración JSON de ADBMobile {#override-the-adbmobile-json-config-path}

Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.

El método `Config.overrideConfigStream(configInput)` le permite especificar la ruta a un archivo de configuración `ADBMobile.json` diferente al iniciarse la aplicación. Se debe llamar a este método antes de cualquier otra llamada del SDK de Experience Cloud (antes de `Config.collectLifecycleData()`), normalmente en el método `onCreate` de la primera actividad que se carga.

Llamar a este método con una ruta diferente provoca una anulación única del archivo de configuración hasta que se cierra la aplicación.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
