---
description: Información para ayudarle a implementar métricas del ciclo vital para Android. Las métricas del ciclo vital se recopilan automáticamente para iOS.
keywords: Xamarin
solution: Experience Cloud Services
title: Implementación del ciclo vital
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# Implementación del ciclo vital {#implement-lifecycle}

Esta información le ayuda a implementar métricas del ciclo vital para Android.

>[!TIP]
>
>Las métricas del ciclo vital se recopilan automáticamente para iOS.

Para ver las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

## iOS

En iOS, las métricas del ciclo vital se recopilan automáticamente.

## Android

En la actividad principal, establezca el contexto de aplicación para el SDK para Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

En cada actividad, implemente llamadas al ciclo vital.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
