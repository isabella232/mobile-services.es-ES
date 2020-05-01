---
description: Esta información le ayuda a implementar la biblioteca Android y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.
keywords: android;library;mobile;sdk
seo-description: Esta información le ayuda a implementar la biblioteca Android y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.
seo-title: Implementación principal y ciclo vital
solution: Marketing Cloud,Analytics
title: Implementación principal y ciclo vital
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: tm+mt
source-git-commit: dae60a21286edc28c84b7638da214b824abf0cd3

---


# Implementación principal y ciclo vital {#core-implementation-and-lifecycle}

Esta información le ayuda a implementar la biblioteca Android y a recopilar métricas del ciclo vital como lanzamientos, actualizaciones, sesiones, usuarios comprometidos, etcétera.

## Descargar el SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Para descargar los SDK, debe utilizar Android 2.2 o una versión posterior.

1. Complete los pasos de las secciones siguientes para configurar un grupo de informes de desarrollo y descargar una versión previamente rellenada del archivo de configuración:

   * [Crear un grupo de informes](/help/android/getting-started/requirements.md)
   * [Descargar el SDK](/help/android/getting-started/requirements.md)

1. Descargue y descomprima el archivo `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` y compruebe que contiene los siguientes componentes de software:

   * `adobeMobileLibrary.jar`, esta es la biblioteca que se utilizará con los simuladores y dispositivos Android.

   * `ADBMobileConfig.json`, que es el archivo de configuración del SDK personalizado para su aplicación.
   >[!IMPORTANT]
   >
   >Si descarga el SDK fuera de la interfaz de usuario de Adobe Mobile Services, el archivo `ADBMobileConfig.json` deberá configurarse de forma manual. Si no tiene experiencia previa con Analytics ni con el SDK de Mobile y desea configurar un grupo de informes de desarrollo y descargar una versión previamente rellenada del archivo de configuración, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

## Añadir el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse {#section_B89510FBB4C646AEA73A185B966E54D3}

**Proyecto IntelliJ IDEA**

Para añadir el SDK y el archivo de configuración a su proyecto:

1. Añada el archivo `ADBMobileConfig.json` a la carpeta `assets` de su proyecto.

1. En el panel Navegación del proyecto, haga clic en el proyecto con el botón secundario.
1. Seleccione **[!UICONTROL Abrir configuración del módulo]**.
1. En **[!UICONTROL Configuración del proyecto]**, seleccione **[!UICONTROL Bibliotecas]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. Seleccione **[!UICONTROL Java]** y busque el archivo `adobeMobileLibrary.jar`.
1. Seleccione los módulos donde quiere usar la biblioteca móvil.
1. Haga clic en **[!UICONTROL Aplicar]** y en **[!UICONTROL Aceptar]** para cerrar la ventana Configuración del módulo.

**Proyecto Eclipse**

Para añadir el SDK y el archivo de configuración a su proyecto:

1. Añada el archivo `ADBMobileConfig.json` a la carpeta `assets` de su proyecto.
1. En **[!UICONTROL Eclipse IDE]**, haga clic con el botón secundario en el nombre del proyecto.
1. Haga clic en **[!UICONTROL Ruta de compilación]** > **[!UICONTROL Agregar archivos externos]**.
1. Select `adobeMobileLibrary.jar`.
1. Haga clic en **[!UICONTROL Abrir]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** > **[!UICONTROL Configure Build Path]**.
1. En la ficha **[!UICONTROL Ordenar y exportar]**, asegúrese de que **`adobeMobileLibrary.jar`** está seleccionado.

## Añadir permisos de aplicaciones {#section_2EAF73ABF6424647B219A63B33B02CD5}

La biblioteca AppMeasurement requiere los siguientes permisos para enviar datos y registrar llamadas de seguimiento sin conexión:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para agregar estos permisos, agregue las siguientes líneas al archivo `AndroidManifest.xml`, que se encuentra en el directorio del proyecto de la aplicación:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Establecer el contexto de la aplicación {#set-application-context}

Se debe agregar el siguiente código en el método `onCreate` de la actividad principal:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## Implementar métricas del ciclo vital {#section_BA686C09021F474AADDE8690BBB910F7}

Después de habilitar el ciclo vital, cada vez que inicie la aplicación se enviará una visita para medir inicios, actualizaciones, sesiones, usuarios comprometidos y muchas otras métricas. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

**Complete los siguientes pasos en cada actividad de la aplicación:**

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. En la función `onResume`, inicie la recopilación de datos del ciclo vital:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. En la función `onPause`, ponga en pausa la recopilación de datos del ciclo vital:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>Debe añadir estas llamadas a todas las actividades para garantizar la precisión al realizar informes de bloqueo. Para obtener más información, consulte [Seguimiento de bloqueos de aplicaciones](/help/android/analytics-main/crashes.md).

## Incluir datos adicionales en las llamadas al ciclo vital

Para incluir datos adicionales en las llamadas a métricas del ciclo vital, pase a `collectLifecycleData` un parámetro adicional que contenga datos de contexto:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

El valor de los datos de contexto adicionales que se envían con `collectLifecycleData` debe asignarse a variables personalizadas en Adobe Mobile Services:

![](assets/map-variable-lifecycle.png)

Otras métricas del ciclo vital se recopilan automáticamente. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

## Qué hacer a continuación {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Complete las siguientes tareas:

* [Seguimiento de estados de aplicaciones](/help/android/analytics-main/states.md)
* [Seguimiento de acciones de aplicaciones](/help/android/analytics-main/actions.md)

