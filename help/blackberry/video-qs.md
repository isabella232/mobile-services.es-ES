---
description: En general, el proceso para medir vídeos es muy similar en todas las plataformas de AppMeasurement. Esta sección proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.
seo-description: En general, el proceso para medir vídeos es muy similar en todas las plataformas de AppMeasurement. Esta sección proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.
seo-title: 'Video Analytics '
title: 'Video Analytics '
uuid: 0 d 2731 f 3-77 a 9-4 db 1-9 a 8 c -1 e 56 c 212 ecb 4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics  {#video-analytics}

En general, el proceso para medir vídeos es muy similar en todas las plataformas de AppMeasurement. Esta sección proporciona una descripción general básica de las tareas del desarrollador junto con ejemplos de código.

Para obtener más información sobre la medición de vídeo, consulte [la](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guía Medición de audio y vídeo en Adobe Analytics. La siguiente tabla indica los datos multimedia que se envían a Analytics. Utilice reglas de procesamiento para asignar los datos de contexto en la columna Variable de datos de contexto a una variable de Analytics en la columna Tipo de variable.

## Asignar eventos del reproductor a variables de Analytics

* **a.media.name**

   (Obligatoria) Recopila el nombre del vídeo, tal como se especifica en la implementación, cuando un visitante ve el vídeo de alguna manera. Puede agregar clasificaciones para esta variable.

   **(Opcional)** La variable Perspectiva personalizada proporciona información de rutas de vídeo.

   * Nombre de la variable: Evar
      * Caducidad predeterminada: visita
      * Insight personalizada (s.prop, se utiliza para rutas de vídeo)

* **a.media.name**

   (**Opcional**) Proporciona información sobre la ruta del vídeo. ClientCare debe habilitar las rutas para esta variable.

   * Tipo de evento: Insight personalizada (s.prop)
   * Insight personalizada (s.prop)

* **a.media.segment**

   (**Obligatorio**) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en el que aparece el segmento en el vídeo. Esta variable se completa al habilitar la variable `segmentByMilestones` cuando se rastrean eventos de reproductor automáticamente, o al establecer un nombre de segmento personalizado cuando se rastrean eventos de reproductor manualmente.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. El método de recopilación de datos de vídeo predeterminado recopila datos en los puntos de inicio (play), segment start y video end (stop).

   Analytics cuenta la primera vista de segmento en el inicio del segmento, cuando el visitante comienza a verlo. El segmento siguiente se visualiza cuando empieza el segmento.

   * Tipo de variable: Evar
   * Caducidad predeterminada: vista de página

* **a.contentType**

   Recopila datos sobre el tipo de contenido que un visitante ve. Se asigna un tipo de contenido “vídeo” a las visitas enviadas por la medición de vídeo. Esta variable no necesita estar reservada exclusivamente para el seguimiento de vídeo. Tener otro tipo de contenido de informe de contenido con la misma variable permite analizar la distribución de visitantes en los diferentes tipos de contenido. Por ejemplo, puede etiquetar otros tipos de contenido usando valores como “artículo” o “página de producto” mediante esta variable. Desde una perspectiva de medición de vídeo, Tipo de contenido permite identificar visitantes de vídeo y, por consiguiente, calcular las tasas de conversión de vídeo.

   * Tipo de variable: Evar
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

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Por ejemplo, cuando el reproductor se pone en pausa se emplea `mediaStop`. `mediaPlay` se utiliza cuando la reproducción comienza o se reanuda.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Abre un vídeo para efectuar su seguimiento.

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

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * Esta es la sintaxis para este método:

      ```cpp
      void play(QString name, double offset);
      ```

   * Este es un ejemplo de código para este método:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **completo**

   Marca de forma manual como completado el elemento de medios en el *`offset`indicado (en segundos).*

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
