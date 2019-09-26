---
description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-title: Anular la ruta de configuración JSON de ADBMobile
solution: Marketing Cloud,Analytics
title: Anular la ruta de configuración JSON de ADBMobile
topic: Desarrollador e implementación
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.

The `Config.overrideConfigStream(configInput)` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

Llamar a este método con una ruta diferente provoca una anulación única del archivo de configuración hasta que se cierra la aplicación.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

