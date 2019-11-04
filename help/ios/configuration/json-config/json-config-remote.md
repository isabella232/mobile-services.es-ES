---
description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-title: Anular la ruta de configuración JSON de ADBMobile
solution: Experience Cloud,Analytics
title: Anular la ruta de configuración JSON de ADBMobile
topic: Desarrollador e implementación
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Anular la ruta de configuración JSON de ADBMobile {#override-the-adbmobile-json-config-path}

Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.

El método `ADBMobile overrideConfigPath:filePath` le permite especificar la ruta a un archivo de configuración `ADBMobile.json` diferente al iniciarse la aplicación. Se debe llamar a este método en el método `applicationDidFinishLaunchingWithOptions`, y dicha llamada debe ocurrir antes de cualquier otra llamada del SDK de Experience Cloud, como `collectLifecycleData`.

Llamar a este método con una ruta diferente provoca una anulación única del archivo de configuración hasta que se cierra la aplicación.

Por ejemplo:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

