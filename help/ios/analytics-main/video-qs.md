---
description: Aquí tiene alguna información sobre la medición de vídeo en iOS mediante hitos de vídeo.
seo-description: Aquí tiene alguna información sobre la medición de vídeo en iOS mediante hitos de vídeo.
seo-title: 'Video Analytics '
solution: Marketing Cloud, Analytics
title: 'Video Analytics '
topic: Desarrollador e implementación
uuid: d 75 fa 415-78 f 6-4 f 50-a 563-76949 f 040138
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Video Analytics  {#video-analytics}

Aquí tiene alguna información sobre la medición de vídeo en iOS mediante hitos de vídeo.

>[!TIP]
>
>Durante la reproducción de vídeo, se envían llamadas frecuentes de monitoreo del funcionamiento a este servicio para medir el tiempo de reproducción. Estas llamadas de monitoreo del funcionamiento se envían cada diez segundos, lo que crea métricas de participación de vídeo granulares e informes de visitas de vídeo más precisos. Para obtener más información, consulte [Medición de audio y vídeo en Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html).

En general, el proceso para medir vídeos es muy similar en todas las plataformas. Este contenido ofrece una visión general básica de las tareas del desarrollador, con ejemplos de código.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

La siguiente tabla indica los datos multimedia que se envían a Analytics. Utilice reglas de procesamiento para asignar los datos de contexto a una variable de Analytics.

* **a.media.name**

   (Obligatoria) Recopila el nombre del vídeo, tal como se especifica en la implementación, cuando un visitante ve el vídeo de alguna manera. Puede agregar clasificaciones para esta variable.

   (Opcional) La variable Insight personalizada proporciona información de rutas de vídeo.

   * Tipo de variable: Evar
   * Caducidad predeterminada: visita
   * Insight personalizada (s.prop, se utiliza para rutas de vídeo)

* **a.media.name**

   (Opcional) Proporciona información de rutas de vídeo. El servicio de atención al cliente debe habilitar las rutas para esta variable.

   * Tipo de variable: Perspectiva personalizada (s. prop)
   * Tipo de evento: Insight personalizada (s.prop)

* **a.media.segment**

   (Obligatoria) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en que aparece el segmento en el vídeo. Esta variable se completa al habilitar la variable `segmentByMilestones` cuando se rastrean eventos de reproductor automáticamente, o al establecer un nombre de segmento personalizado cuando se rastrean eventos de reproductor manualmente. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` Segments evar.

   El método personalizado de recopilación de datos de vídeo obtiene datos en los siguientes puntos:

   * inicio del vídeo (reproducción)
   * comienzo del segmento
   * fin del vídeo (parada)
   Analytics cuenta la primera vista de segmento en el inicio del segmento, cuando el visitante comienza a verlo. El segmento siguiente se visualiza cuando empieza el segmento.

   * Tipo de variable: Evar
   * Caducidad predeterminada: vista de página


* **a.contentType**

   Recopila datos sobre el tipo de contenido que un visitante ve. Hits sent by video measurement are assigned a content type of `video`. Esta variable no necesita estar reservada exclusivamente para el seguimiento de vídeo. El hecho de disponer de otro tipo de contenido de informe de contenido mediante el uso de esta misma variable le permite analizar la distribución de los visitantes entre los distintos tipos de contenido. Por ejemplo, puede etiquetar otros tipos de contenido usando valores como “artículo” o “página de producto” mediante esta variable. Desde la perspectiva de medición de vídeo, Tipo de contenido le permite identificar visitantes de vídeo y calcular tasas de conversión de vídeo.

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

* **a.media.complete**

   Indica que un usuario ha visto un vídeo completo. De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de vídeo quisiera considerar como una vista completa. Para vídeo en directo y otras transmisiones sin un fin definido, puede especificar un punto personalizado para medir las visualizaciones completas; por ejemplo, después de un tiempo de visualización especificado.

   * Tipo de variable: Evento
   * Tipo: contador

## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configure un objeto `ADBMediaSettings` con los ajustes que quiera usar para realizar seguimiento de vídeo:

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Por ejemplo, cuando el reproductor se pone en pausa se emplea `mediaStop`. `mediaPlay` se utiliza cuando la reproducción comienza o se reanuda.

El siguiente ejemplo demuestra el uso de notificaciones de configuración y llamadas a métodos de medios para medir vídeos:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Clases {#section_16838332727348F990305C0C6B0D795C}

### Clase: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Clase: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   Devuelve un objeto `ADBMediaSettings` con parámetros específicos.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   Devuelve un objeto `ADBMediaSettings` para su uso con el seguimiento de un vídeo de anuncio.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   Abre un objeto `ADBMediaSettings` para su seguimiento.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Cierra el elemento de medios llamado *nombre*.

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Reproduce el elemento de medios llamado *name* con un desplazamiento *offset* dado (en segundos).

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Marca de forma manual como completado el elemento de medios en el *offset* indicado (en segundos).

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el *offset* indicado.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```
