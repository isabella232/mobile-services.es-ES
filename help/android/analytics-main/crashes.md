---
description: Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.
solution: Experience Cloud Services,Analytics
title: Seguimiento de bloqueos de aplicaciones
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 100%

---

# Seguimiento de errores de aplicaciones {#track-app-crashes}

Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.

>[!TIP]
>
>Se realiza un seguimiento de los bloqueos de aplicaciones como parte de las métricas del ciclo vital. Para poder realizar el seguimiento de bloqueos, agregue la biblioteca al proyecto e implemente el ciclo vital. Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

Cuando se implementan las métricas del ciclo vital, se llama a `Config.collectLifecycleData` en el método `OnResume` de cada actividad. En el método `onPause` se llama a `Config.pauseCollectingLifeCycleData`.

En `pauseCollectingLifeCycleData`, se establece un indicador para señalar una salida correcta. Cuando la aplicación se vuelve a iniciar o se reanuda, `collectLifecycleData` comprueba este indicador. Si el indicador señala que la aplicación no se cerró correctamente, se envía un dato de contexto `a.CrashEvent` junto con la siguiente llamada y se comunica un evento de bloqueo.

Para garantizar un informe de bloqueo preciso, debe llamar a `pauseCollectingLifeCycleData` dentro del método `onPause` de cada actividad. Para comprender por qué esto es básico, aquí tiene una ilustración del ciclo de duración de las actividades de Android:

![](assets/android-lifecycle.png)

Para obtener más información acerca del ciclo vital de la actividad de Android, consulte [Actividades](https://developer.android.com/guide/components/activities.html).

*Esta ilustración del ciclo vital de Android la creó y [compartió el grupo Android Open Source Project](https://source.android.com/), y se utiliza de acuerdo con los términos de la [Licencia de atribución de Creative Commons 2.5](https://creativecommons.org/licenses/by/2.5/).*

## ¿Qué puede provocar que se comunique un falso bloqueo?

1. Si está realizando una depuración con un IDE, por ejemplo, Android Studio, volver a iniciar la aplicación desde el IDE mientras la aplicación está en primer plano provocará un bloqueo.

   >[!TIP]
   >
   >Puede evitar este bloqueo poniendo la aplicación en segundo plano antes de volver a iniciarla desde el IDE.

1. Si la última actividad en primer plano de la aplicación pasa a segundo plano y no llama a `Config.pauseCollectingLifecycleData();`; en `onPause`, y entonces usted manualmente o el sistema operativo cierran la aplicación, el siguiente inicio resulta en un bloqueo.

## ¿Cómo se deben gestionar los fragmentos?

Los fragmentos tienen eventos de ciclo vital de aplicación similares a las actividades. Sin embargo, un fragmento no puede estar activo sin estar asociado a una Actividad.

>[!IMPORTANT]
>
>Debe confiar en los eventos de ciclo de duración en los que las actividades contenedoras pueden ejecutar su código. Esto lo gestionará la vista principal del fragmento.

## (Opcional) Implemente llamadas de retorno de ciclo vital de las actividades

Desde el Nivel 14 de la API, Android permite las llamadas de retorno de ciclo vital globales para las actividades. Para obtener más información, consulte [Aplicación](https://developer.android.com/reference/android/app/Application).

Puede utilizar estas llamadas de retorno para garantizar que todas sus actividades llamen correctamente a `collectLifecycleData()` y `pauseCollectingLifecycleData()`. Necesita agregar este código solo en su actividad principal y en cualquier otra actividad en que la aplicación puede iniciarse:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

Para enviar datos de contexto adicionales con su llamada al ciclo de duración empleando `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, debe anular el método `onResume` para esa actividad y asegurarse de llamar a `super.onResume()` después de llamar manualmente a `collectLifecycleData`.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
