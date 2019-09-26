---
description: Información para ayudarle con el Análisis de vídeo.
seo-description: Información para ayudarle con el Análisis de vídeo.
seo-title: 'Video Analytics '
solution: Marketing Cloud,Analytics
title: 'Video Analytics '
topic: Desarrollador e implementación
uuid: f45dac3b-cd2e-4fba-a3b2-c243640ecfa4
translation-type: tm+mt
source-git-commit: 1c0b7dadc28f772e903baa8605016e70f05081d7

---


# Video Analytics  {#video-analytics}

Información para ayudarle con el Análisis de vídeo.

Video measurement is described in detail in the [Measuring video and audio in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guide. En general, el proceso para medir vídeos es muy similar en todas las plataformas de AppMeasurement. Esta sección de inicio rápido contiene información general básica de las tareas de los programadores junto con ejemplos de código.

La siguiente tabla indica los datos multimedia que se envían a Analytics. Use processing rules to map the context data to an Analytics variable.

* **a.media.name**

   (**Required**) Collects the name of the video, as specified in the implementation, when a visitor views the video in some way.You can add classifications for this variable.

   (**Opcional**) La variable Insight personalizada proporciona información sobre la ruta del vídeo.

   * Tipo de variable: eVar
   * Caducidad predeterminada: visita
   * Insight personalizada (s.prop, se utiliza para rutas de vídeo)

* **a.media.name**

   (**Opcional**) Proporciona información sobre la ruta del vídeo. ClientCare debe habilitar las rutas para esta variable.

   * Tipo de evento: Insight personalizada (s.prop).
   * Tipo de variable: Perspectiva personalizada (s.prop)

* **a.media.segment**

   (**Obligatorio**) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en el que aparece el segmento en el vídeo.

   Esta variable se completa al habilitar la variable `segmentByMilestones` cuando se rastrean eventos de reproductor automáticamente, o al establecer un nombre de segmento personalizado cuando se rastrean eventos de reproductor manualmente. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segments eVar.

   El método predeterminado de recopilación de datos de vídeo recopila datos en los siguientes puntos: inicio de vídeo (reproducción), comienzo de vídeo y fin de vídeo (detención). Analytics cuenta la primera vista de segmento en el inicio del segmento, cuando el visitante comienza a verlo. El segmento siguiente se visualiza cuando empieza el segmento.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página

* **a.contentType**

   Recopila datos sobre el tipo de contenido que un visitante ve. Se asigna un tipo de contenido “vídeo” a las visitas enviadas por la medición de vídeo. Esta variable no necesita estar reservada exclusivamente para el seguimiento de vídeo. Tener otro tipo de contenido de informe de contenido con la misma variable permite analizar la distribución de visitantes en los diferentes tipos de contenido. Por ejemplo, puede etiquetar otros tipos de contenido usando valores como “artículo” o “página de producto” mediante esta variable.

   Desde una perspectiva de medición de vídeo, Tipo de contenido permite identificar visitantes de vídeo y, por consiguiente, calcular las tasas de conversión de vídeo.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página

* **a.media.timePlayed**

   Cuenta el tiempo, en segundos, transcurrido en ver un vídeo desde el último proceso de recopilación de datos (solicitud de imagen).

   * Tipo de variable: Evento
   * Tipo: contador

* **a.media.view**

   Indica que un visitante ha visto alguna parte de un vídeo. Sin embargo, no proporciona información sobre qué parte del vídeo ha visualizado el visitante ni sobre cuánto tiempo lo ha visualizado.

   * Tipo de variable: Evento
   * Tipo: contador

* **a.media.segmentView**

   Indica que un visitante ha visto alguna parte de un segmento de vídeo. Sin embargo, no proporciona información sobre qué parte del vídeo ha visualizado el visitante ni sobre cuánto tiempo lo ha visualizado.

   * Tipo de variable: Evento
   * Tipo: contador

* **a .media.complete**

   Indica que un usuario ha visto un vídeo completo. De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de vídeo quisiera considerar como una vista completa. Para vídeo en vivo y otros flujos que no tienen un final definido, puede especificar un punto personalizado para medir finalizaciones. Por ejemplo, después de un tiempo de visualización específico.

   * Tipo de variable: Evento
   * Tipo: contador

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configure un objeto `MediaSettings` con los ajustes que quiera usar para realizar seguimiento de vídeo:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. Por ejemplo, cuando el reproductor se pone en pausa se emplea `Stop`. `Play` se utiliza cuando la reproducción comienza o se reanuda.

## Clases {#section_16838332727348F990305C0C6B0D795C}

### Clase: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

### Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Devuelve un objeto `MediaSettings` con parámetros especificados.

   * Esta es la sintaxis para este método:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith)**

   Devuelve un objeto `MediaSettings` que se utiliza en el seguimiento de un vídeo de anuncio.

   * Esta es la sintaxis para este método:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **Open (winJS: open)**

   Tracks a media open using the settings defined in `settings`.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.open(mySettings);
      ```

* **Cerrar (winJS: close)**

   Realiza un seguimiento del cierre de un recurso para el elemento multimedia llamado *`name`*.

   * Esta es la sintaxis para este método:

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **Play (winJS: play)**

   Realiza un seguimiento de la reproducción de un recurso para el elemento multimedia llamado *`name`* con el desfase *offset* dado (en segundos).

   * Esta es la sintaxis para este método:

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **Complete (winJS: complete)**

   Marca de forma manual como completado el elemento de medios en el *offset* indicado (en segundos).

   * Esta es la sintaxis para este método:

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **Stop (winJS: stop)**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el *offset* indicado.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **Haga clic en (winJS: click)**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **Track (winJS: track)**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.track("mediaName",  null);
      ```
