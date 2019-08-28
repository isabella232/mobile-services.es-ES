---
description: A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.
keywords: android; library; mobile; sdk
seo-description: A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.
seo-title: 'Video Analytics '
solution: Marketing Cloud, Analytics
title: 'Video Analytics '
topic: Desarrollador e implementación
uuid: a 137 cc 27-dc 28-48 c 0-b 08 e -2 ca 17 d 2 c 7 e 1 d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Video Analytics  {#video-analytics}

A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.

>[!TIP]
>
>Durante la reproducción de vídeo, se envían llamadas frecuentes de monitoreo del funcionamiento a este servicio para medir el tiempo de reproducción. Estas llamadas de monitoreo del funcionamiento se envían cada diez segundos, lo que crea métricas de participación de vídeo granulares e informes de visitas de vídeo más precisos. For more information about Adobe's video measurement solution, see [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html).

El proceso general de medición de vídeos es muy similar en todas las plataformas. Este contenido ofrece una visión general de las tareas del desarrollador, con ejemplos de código. La siguiente tabla indica los datos multimedia que se envían a Analytics. Las reglas de procesamiento se utilizan para asignar los datos de contexto a una variable de Analytics.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Tipo de variable: Evar
      * Caducidad predeterminada: visita
      * Insight personalizada (s.prop, se utiliza para rutas de vídeo)
   * (**Obligatorio**) Cuando un visitante visualiza el vídeo de alguna forma, la variable de datos de contenido recopila el nombre del vídeo, según lo especificado en la implementación. Puede añadir clasificaciones para esta variable.
   * (**Opcional**) La variable Insight personalizada proporciona información sobre la ruta del vídeo.

* **a.media.name**
   * Tipo de variable: Perspectiva personalizada (s. prop)
   * (**Opcional**) Proporciona información sobre la ruta del vídeo.

      >[!IMPORTANT]
      >
      >Expcare debe habilitar las rutas para esta variable.
   * Tipo de evento: Insight personalizada (s.prop)

* **a.media.segment**
   * Tipo de variable: Evar
   * Caducidad predeterminada: vista de página
   * (**Obligatorio**) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en el que aparece el segmento en el vídeo.

      Esta variable se rellena habilitando la variable `segmentByMilestones` cuando se realiza un seguimiento automático de eventos de reproductor, o bien estableciendo un nombre de segmento personalizado cuando se realiza un seguimiento manual de eventos de reproductor. Por ejemplo, cuando un visitante ve el primer segmento de un vídeo, SiteCatalyst podría recopilar lo siguiente en la eVar Segments: `1:M:0-25`.

      El método personalizado de recopilación de datos de vídeo obtiene datos en los siguientes puntos:

      * inicio del vídeo (reproducción)
      * comienzo del segmento
      * fin del vídeo (parada)
      Analytics cuenta la primera vista de segmento en el inicio del segmento, cuando el visitante comienza a verlo. El segmento siguiente se visualiza cuando empieza el segmento.


* **a.contentType**
   * Tipo de variable: Evar
   * Caducidad predeterminada: vista de página
   * Recopila datos sobre el tipo de contenido que un visitante ve.

      Hits sent by video measurement are assigned a content type of `video`. Desde la perspectiva de medición de vídeo, **Tipo de contenido** permite identificar visitantes de vídeo y calcular tasas de conversión de vídeo.

* **a.media.timePlayed**
   * Tipo de variable: Evento
   * Tipo: contador
   * Cuenta el tiempo, en segundos, transcurrido viendo un vídeo desde el último proceso de recopilación de datos (solicitud de imagen).

* **a.media.view**
   * Tipo de variable: Evento
   * Tipo: contador
   * Indica que un visitante ha visto alguna parte de un vídeo.

      Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

* **a.media.segmentView**
   * Tipo de variable: Evento
   * Tipo: contador
   * Indica que un visitante ha visto alguna parte de un segmento de vídeo.

      Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

* **a .media.complete**
   * Tipo de variable: Evento
   * Tipo: contador
   * Indica que un usuario ha visto un vídeo completo.

      De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de un vídeo pueden quedar sin ver y, pese a ello, considerarse como una vista completa. Para vídeo en directo y otras transmisiones sin un fin definido, puede especificar un punto personalizado para medir las visualizaciones completas (por ejemplo, después de un tiempo de visualización especificado).


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Configure un objeto `MediaSettings` con los ajustes que quiera usar para realizar seguimiento de vídeo:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Por ejemplo, cuando el reproductor se pone en pausa, llame a `mediaStop`. `mediaPlay` se utiliza cuando la reproducción comienza o se reanuda.

## Clases {#section_16838332727348F990305C0C6B0D795C}

**Clase: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Clase: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

Estos son los métodos de la clase Media Measurement:

* **settingsWith**

   Devuelve un objeto `MediaSettings` con parámetros especificados.

   * Esta es la sintaxis para este método:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Devuelve un objeto `MediaSettings` que se utiliza en el seguimiento de un vídeo de anuncio.
   * Esta es la sintaxis para este método:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Abre un objeto `MediaSettings` para el seguimiento.

   * Esta es la sintaxis para este método:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Cierra el elemento de medios llamado *nombre*.

      * Esta es la sintaxis para este método:
      ```java
      public static void close(String name);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Reproduce el elemento de medios llamado *nombre* con un *desplazamiento* determinado en segundos.
   * Esta es la sintaxis para este método:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **completo**

   Marca de forma manual como completado el elemento de medios en el desplazamiento *offset* indicado en segundos.

   * Esta es la sintaxis para este método:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Notifica al módulo de medios que el vídeo se ha detenido o pausado en el *offset* indicado.

   * Esta es la sintaxis para este método:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Este es el ejemplo de código o este método:

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Notifica al módulo de medios que se ha hecho clic en el elemento de medios.

   * Esta es la sintaxis para este método:

      ```java
      public static void click(String name double offset); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Envía una llamada de acción de seguimiento (sin visualización de página) al estado de medios actual.

   * Esta es la sintaxis para este método:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Media.track("name", null); 
      ```
