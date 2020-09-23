---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementar el ciclo vital
solution: Experience Cloud
title: Implementar el ciclo vital
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# Implementar el ciclo vital{#implement-lifecycle}

Para obtener más información sobre las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital, consulte Métricas [del ciclo vital en Android](/help/android/metrics.md) o [Ciclo de vida en iOS](/help/ios/metrics.md).

## iOS

Las métricas del ciclo vital se recopilan automáticamente en iOS.

## Android

En la secuencia de comandos Unity, se establece el contexto de la aplicación para el SDK de Android. Añada el siguiente código a la `Awake()` función de la PRIMERA escena:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Para recopilar métricas del ciclo vital, agregue el siguiente código a todos los scripts de escena:

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

