---
description: Información para ayudarle a implementar las métricas del ciclo vital para Android. En el caso de iOS, las métricas del ciclo vital se recopilan automáticamente.
keywords: Xamarin
seo-description: Información para ayudarle a implementar las métricas del ciclo vital para Android. En el caso de iOS, las métricas del ciclo vital se recopilan automáticamente.
seo-title: Implementar ciclo vital
solution: Marketing Cloud, Desarrollador
title: Implementar ciclo vital
uuid: 6 dccc 12 e -8 b 57-4231-9 c 74-d 47 bc 0 ac 93 ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Esta información le ayuda a implementar métricas del ciclo vital para Android.

>[!TIP]
>
>En el caso de iOS, las métricas del ciclo vital se recopilan automáticamente.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

En iOS, las métricas del ciclo vital se recopilan automáticamente.

## Android

En la actividad principal, establezca el contexto de aplicación para el SDK de Android.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

En todas las actividades, implemente llamadas del ciclo vital.

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
