---
description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-title: Anular la ruta de configuración JSON de adbmobile
solution: Marketing Cloud, Analytics
title: Anular la ruta de configuración JSON de adbmobile
topic: Desarrollador e implementación
uuid: 0 d 1 be 674-c 634-4 a 48-aa 31-5701681911 b 9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Se debe llamar a este método en el método `applicationDidFinishLaunchingWithOptions`, y dicha llamada debe ocurrir antes de cualquier otra llamada del SDK de Experience Cloud, como `collectLifecycleData`.

Cuando se llama a este método con una ruta diferente, se produce una anulación única del archivo de configuración hasta que se cierra la aplicación.

Por ejemplo:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

