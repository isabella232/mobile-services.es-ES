---
description: Información para ayudarle a implementar métricas del ciclo vital para Android. Las métricas del ciclo vital se recopilan automáticamente para iOS.
keywords: Xamarin
seo-description: Información para ayudarle a implementar métricas del ciclo vital para Android. Las métricas del ciclo vital se recopilan automáticamente para iOS.
seo-title: Implementación del ciclo vital
solution: Experience Cloud
title: Implementación del ciclo vital
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 7%

---


# Implementación del ciclo vital {#implement-lifecycle}

Esta información le ayuda a implementar métricas del ciclo vital para Android.

>[!TIP]
>
>Las métricas del ciclo vital se recopilan automáticamente para iOS.

Para ver las métricas y dimensiones que la biblioteca móvil puede medir automáticamente después de implementar el ciclo vital, consulte Métricas [del ciclo vital](/help/ios/metrics.md).

## iOS

En iOS, las métricas del ciclo vital se recopilan automáticamente.

## Android

En la actividad principal, establezca el contexto de la aplicación para el SDK de Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

En todas las actividades, implemente llamadas al ciclo vital.

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
