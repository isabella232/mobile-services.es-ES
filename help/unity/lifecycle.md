---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementar el ciclo de vida
solution: Marketing Cloud,Desarrollador
title: Implementar el ciclo de vida
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implementar el ciclo de vida{#implement-lifecycle}

Para obtener más información sobre las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital, consulte Métricas [del ciclo vital en Android](/help/android/metrics.md) o [Ciclo de vida en iOS](/help/ios/metrics.md).

## iOS

Las métricas del ciclo vital se recopilan automáticamente en iOS.

## Android

En la secuencia de comandos de Unity, usted establece el contexto de aplicación para el SDK de Android. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Para recopilar las métricas del ciclo de vida, añada el siguiente código a todas las secuencias de comandos de las escenas:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

