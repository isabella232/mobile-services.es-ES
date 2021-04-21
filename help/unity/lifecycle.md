---
description: Medir métricas y dimensiones que la biblioteca móvil puede medir automáticamente
keywords: Unity
solution: Experience Cloud
title: Implementar el ciclo vital
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Implementar el ciclo vital{#implement-lifecycle}

Para obtener más información sobre las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital, consulte [Métricas del ciclo vital en Android](/help/android/metrics.md) o [Ciclo de vida en iOS](/help/ios/metrics.md).

## iOS

Las métricas del ciclo vital se recopilan automáticamente en iOS.

## Android

En la secuencia de comandos Unity, se establece el contexto de aplicación para el SDK de Android. Agregue el siguiente código a la función `Awake()` de la PRIMERA escena:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Para recopilar métricas del ciclo vital, agregue el siguiente código a todas las secuencias de comandos de las escenas:

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
