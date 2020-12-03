---
description: El proceso general para medir vídeos es muy similar en todas las plataformas de AppMeasurement. En esta sección se proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.
seo-description: El proceso general para medir vídeos es muy similar en todas las plataformas de AppMeasurement. En esta sección se proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 68%

---


# Video Analytics  {#video-analytics}

El proceso general para medir vídeos es muy similar en todas las plataformas de AppMeasurement. En esta sección se proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.

For more information about Video measurement, see the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/es-ES/media-analytics/using/media-overview.html) guide.  La siguiente tabla indica los datos multimedia que se envían a Analytics. Utilice las reglas de procesamiento para asignar los datos de contexto en la columna Variable de datos de contexto a una variable de Analytics como se describe en la columna Tipo de variable.

## Asignación de eventos del reproductor a las variables de Analytics

* **a.media.name**

   (Requerido) Recopila el nombre del video, tal como se especifica en la implementación, cuando un visitante vista el video de alguna manera.Puede agregar clasificaciones para esta variable.

   **(Opcional)** La variable Custom Insight proporciona información de rutas de vídeo.

   * Nombre de variable: eVar
      * Caducidad predeterminada: visita
      * Custom Insight (s.prop, se utiliza para las rutas de vídeo)

* **a.media.name**

   (**Opcional**) Proporciona información sobre la ruta del vídeo. ClientCare debe habilitar las rutas para esta variable.

   * Tipo de evento: Insight personalizada (s.prop)
   * Custom Insight (s.prop)

* **a.media.segment**

   (**Obligatoria**) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en que aparece el segmento en el vídeo. Esta variable se completa al habilitar la variable `segmentByMilestones` cuando se rastrean eventos de reproductor automáticamente, o al establecer un nombre de segmento personalizado cuando se rastrean eventos de reproductor manualmente.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. El método de recopilación de datos de vídeo predeterminado recopila datos en los puntos de inicio de vídeo (reproducción), inicio de segmento y fin de vídeo (parada).

   Analytics cuenta la primera vista de segmentos en el inicio del segmento, cuando el visitante empieza a ver. Vistas de segmentos posteriores desde el inicio del segmento.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página

* **a.contentType**

   Recopila datos sobre el tipo de contenido que un visitante ve. A las visitas enviadas por medición de vídeo se les asigna un tipo de contenido de &quot;vídeo&quot;. Esta variable no necesita estar reservada exclusivamente para el seguimiento de videos. Tener otro tipo de contenido de informe de contenido usando esta misma variable permite analizar la distribución de visitantes en los distintos tipos de contenido. Por ejemplo, puede etiquetar otros tipos de contenido usando valores como “artículo” o “página de producto” mediante esta variable. Desde una perspectiva de medición de vídeo, Tipo de contenido permite identificar visitantes de vídeo y, por consiguiente, calcular las tasas de conversión de vídeo.

   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página

* **a.media.timePlayed**

   Cuenta el tiempo, en segundos, transcurrido en ver un vídeo desde el último proceso de recopilación de datos (solicitud de imagen).

   * Tipo de variable: Event
   * Tipo: contador

* **a.media.view**

   Indica que un visitante ha visto alguna parte de un de vídeo. Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

   * Tipo de variable: Event
   * Tipo: contador

* **a.media.segmentView**

   Indica que un visitante ha visto alguna parte de un segmento de vídeo. Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

   * Tipo de variable: Event
   * Tipo: contador

* **a .media.complete**

   Indica que un usuario ha visto un vídeo completo. De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de vídeo quisiera considerar como una vista completa. Para vídeo en directo y otros flujos que no tienen un final definido, puede especificar un punto personalizado para medir las finalizaciones. Por ejemplo, después de un tiempo de visualización específico.

   * Tipo de variable: Event
   * Tipo: contador

## Seguimiento de eventos del reproductor {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para medir la reproducción de vídeo, es preciso realizar llamadas a los métodos `mediaPlay`, `mediaStop`, y `mediaClose` en los momentos apropiados. Por ejemplo, cuando el reproductor se pone en pausa se emplea `mediaStop`. `mediaPlay` se utiliza cuando la reproducción comienza o se reanuda.

## Referencia de clases y métodos de medición de medios {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Abre un vídeo para el seguimiento.

   * Esta es la sintaxis para este método:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Abre un objeto `MediaSettings` para el seguimiento.

   * Esta es la sintaxis para este método:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Closes the media item named *`name`*.

   * Esta es la sintaxis para este método:

      ```cpp
      void close(QString name);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Reproduce el elemento de medios llamado *`name`* con un desplazamiento *`offset`* dado (en segundos).

   * Esta es la sintaxis para este método:

      ```cpp
      void play(QString name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **completo**

   Marca de forma manual como completado el elemento de medios en el *`offset`* indicado (en segundos).

   * Esta es la sintaxis para este método:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el *offset* indicado.

   * Esta es la sintaxis para este método:

      ```cpp
      stop(QString name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```cpp
      void click(QString name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
