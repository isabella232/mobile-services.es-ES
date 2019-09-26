---
description: Los estados son las distintas pantallas o vistas de su aplicación.
seo-description: Los estados son las distintas pantallas o vistas de su aplicación.
seo-title: Seguimiento de estados de aplicaciones
solution: Marketing Cloud,Analytics
title: Seguimiento de estados de aplicaciones
topic: Desarrollador e implementación
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Seguimiento de estados de aplicaciones {#track-app-states}

Los estados son las distintas pantallas o vistas de su aplicación.

Cada vez que se muestra un nuevo estado en su aplicación (por ejemplo, cuando un usuario navega de la página principal al suministro de noticias), se envía una llamada `trackState`. En Android, suele llamarse a `trackState` cada vez que se carga una nueva actividad.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* IntelliJ IDEA o Eclipse en la implementación [principal y el ciclo vital](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. En la función `onCreate`, llame a `trackState` para enviar una visita para esta vista de estado:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In other Analytics interfaces, `View State` is reported as `Page Name`, and `state views` is reported as `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

Además del `"State Name"`, puede enviar datos de contexto adicionales con cada llamada de acción de seguimiento:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

El valor de los datos de contexto debe asignarse a variables personalizadas de Adobe Mobile Services:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Los estados suelen verse mediante un informe de ruta, lo que le permite ver cuántos usuarios navegan por su aplicación y qué estados se ven con más frecuencia.

|  |  |
|--- |--- |
| Adobe Mobile Services  | El informe **[!UICONTROL Ver estados.]** Este informe se basa en las rutas que los usuarios tomaron a través de su aplicación. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics | Los estados pueden verse desde cualquier parte donde puedan verse las Páginas, como los informes **Páginas**, **[!UICONTROL Vistas de la página]** y **Ruta[!UICONTROL .]** |
| Análisis específico | Los estados pueden verse desde cualquier parte donde puedan verse las Páginas empleando la dimensión **Página**, la métrica **[!UICONTROL Vistas de la página]** y los informes **Ruta[!UICONTROL .]** |


