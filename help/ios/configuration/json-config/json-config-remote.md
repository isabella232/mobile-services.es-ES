---
description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-description: Puede cargar un archivo de configuración ADBMobile JSON diferente al iniciar la aplicación.
seo-title: Anular la ruta de configuración JSON de ADBMobile
solution: Experience Cloud,Analytics
title: Anular la ruta de configuración JSON de ADBMobile
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 100%

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
