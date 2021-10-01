---
description: Información para ayudarle con Video Analytics.
solution: Experience Cloud,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 71%

---

# Video Analytics  {#video-analytics}

Información para ayudarle con Video Analytics.

La medición de vídeo se describe detalladamente en la guía [Medición de flujo continuo en Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=es). El proceso general de medición de vídeos es muy similar en todas las plataformas de AppMeasurement. Esta sección de inicio rápido proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.

La siguiente tabla indica los datos multimedia que se envían a Analytics. Utilice reglas de procesamiento para asignar los datos de contexto a una variable de Analytics.

* **a.media.name**

   (Obligatorio) Recopila el nombre del vídeo, tal como se especifica en la implementación, cuando un visitante ve el vídeo de alguna manera. Puede agregar clasificaciones para esta variable.

   (**Opcional**) La variable de Custom Insight proporciona información de las rutas de vídeo.

   * Tipo de variable: eVar
   * Caducidad predeterminada: visita
   * Custom Insight (s.prop, se utiliza para las rutas de vídeo)

* **a.media.name**

   (Opcional) Proporciona información sobre la ruta del vídeo. El servicio de atención al cliente debe habilitar las rutas para esta variable.

   Tipo de evento: Insight personalizada (s.prop)

   * Tipo de variable: Custom Insight (s.prop)

* **a.media.segment**

   (Obligatoria) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en que aparece el segmento en el vídeo. Esta variable se completa al habilitar la variable `segmentByMilestones` cuando se rastrean eventos de reproductor automáticamente, o al establecer un nombre de segmento personalizado cuando se rastrean eventos de reproductor manualmente. Por ejemplo, cuando un visitante ve el primer segmento de un vídeo, SiteCatalyst podría recopilar lo siguiente en el eVar de segmento `1:M:0-25`.

   El método de recopilación de datos de vídeo predeterminado recopila datos en los puntos siguientes:

   * inicio de vídeo (reproducción)
   * inicio de segmento
   * final de vídeo (parada)

   Analytics cuenta la primera vista de segmentos en el inicio del segmento, cuando el visitante empieza a ver. Vistas de segmentos posteriores desde el inicio del segmento.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página


* **a.contentType**

   Recopila datos sobre el tipo de contenido que un visitante ve. A las visitas enviadas por la medición de vídeo se les asigna un tipo de contenido de &quot;vídeo&quot;. Esta variable no necesita estar reservada exclusivamente para el seguimiento de vídeo. El hecho de disponer de otro tipo de contenido de informe de contenido mediante el uso de esta misma variable le permite analizar la distribución de los visitantes entre los distintos tipos de contenido. Por ejemplo, podría etiquetar otros tipos de contenido con valores como &quot;artículo&quot; o &quot;página de producto&quot; usando esta variable. Desde la perspectiva de medición de vídeo, el tipo de contenido le permite identificar visitantes de vídeo y calcular tasas de conversión de vídeo.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página

* **a.media.timePlayed**

   Cuenta el tiempo, en segundos, transcurrido en ver un vídeo desde el último proceso de recopilación de datos (solicitud de imagen).

   * Tipo de variable: Event
   * Tipo: contador

* **a.media.view**

   Indica que un visitante ha visto alguna parte de un de vídeo. Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

   * Variable: Evento
   * Tipo: contador

* **a.media.segmentView**

   Indica que un visitante ha visto alguna parte de un segmento de vídeo. Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

   * Tipo de variable: Event
   * Tipo: contador

* **a .media.complete**

   Indica que un usuario ha visto un vídeo completo. De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de vídeo quisiera considerar como una vista completa. Para vídeo en directo y otros flujos que no tienen un final definido, puede especificar un punto personalizado para medir las finalizaciones. Por ejemplo, después de un tiempo de visualización específico.

   * Tipo de variable: Event
   * Tipo: contador

## Configuración de medios {#section_929945D4183C428AAF3B983EFD3E2500}

Configure un objeto `MediaSettings` con los ajustes que quiera usar para realizar seguimiento de vídeo:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Seguimiento de eventos del reproductor {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para medir la reproducción de vídeo, es preciso realizar llamadas a los métodos `Play`, `Stop`, y `Close` en los momentos apropiados. Por ejemplo, cuando el reproductor se pone en pausa se emplea `Stop`. `Play` se utiliza cuando la reproducción comienza o se reanuda.

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

## Referencia de clases y métodos de medición de medios {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Devuelve un objeto `MediaSetting` con parámetros especificados.

   * Esta es la sintaxis para este método:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Devuelve un objeto `MediaSettings` que se utiliza en el seguimiento de un vídeo de anuncio.

   * Esta es la sintaxis para este método:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Apertura (winJS: open)**

   Rastrea una apertura de medios con la configuración definida en `settings`.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Cerrar (winJS: close)**

   Rastrea un cierre multimedia para el elemento multimedia denominado *name*.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS: play)**

   Realiza el seguimiento de una reproducción de contenido para el elemento multimedia denominado *`name`* en el *offset* dado (en segundos).

   * Esta es la sintaxis para este método:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Complete (winJS: complete)**

   Marca de forma manual como completado el elemento de medios en el *offset* indicado (en segundos).

   * Esta es la sintaxis para este método:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
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
      ADB.Media.stop("mediaName", 4);
      ```

* **Haga clic (winJS: click)**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS: track)**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADB.Media.track("mediaName", null);
      ```
