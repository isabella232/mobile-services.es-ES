---
description: Los estados son las distintas pantallas o vistas de su aplicación.
seo-description: Los estados son las distintas pantallas o vistas de su aplicación.
seo-title: Seguimiento de estados de aplicaciones
solution: Experience Cloud,Analytics
title: Seguimiento de estados de aplicaciones
topic: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '291'
ht-degree: 100%

---


# Seguimiento de estados de aplicaciones {#track-app-states}

Los estados son las distintas pantallas o vistas de su aplicación.

Cada vez que se muestra un nuevo estado en su aplicación (por ejemplo, cuando un usuario navega de la página principal al suministro de noticias), se envía una llamada `trackState`. En Android, suele llamarse a `trackState` cada vez que se carga una nueva actividad.

## Seguimiento de estados {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

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

El `"State Name"` se recoge en la variable `View State` de Adobe Mobile Services y se registra una vista para cada llamada `trackState`. En otras interfaces de Analytics, `View State` se muestra como `Page Name` y `state views` como `page views`.

## Envío de datos adicionales {#section_CFDB4F944496401786A145C209AB387C}

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

## Realización de informes de estado de la aplicación {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Los estados suelen verse mediante un informe de rutas, y así se puede ver cuántos usuarios navegan por la aplicación y qué estados se ven con mayor frecuencia.

|  |  |
|--- |--- |
| Adobe Mobile Services | El informe **[!UICONTROL Ver estados]**. Este informe se basa en las rutas que los usuarios tomaron a través de su aplicación. Un ejemplo de ruta es **[!UICONTROL Inicio]** > **[!UICONTROL Configuración]** > **[!UICONTROL Fuente]**. |
| Adobe Analytics | Los estados pueden verse desde cualquier parte donde puedan verse las Páginas, como los informes **[!UICONTROL Páginas]**, **[!UICONTROL Vistas de la página]** y **[!UICONTROL Ruta]**. |
| Análisis específico | Los estados pueden verse desde cualquier parte donde puedan verse las Páginas empleando la dimensión **[!UICONTROL Página]**, la métrica **[!UICONTROL Vistas de la página]** y los informes **[!UICONTROL Ruta]**. |


