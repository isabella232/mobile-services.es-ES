---
description: A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.
keywords: android;library;mobile;sdk
seo-description: A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.
seo-title: Video Analytics
solution: Experience Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 100%

---


# Video Analytics  {#video-analytics}

A continuación encontrará más información sobre la medición de vídeo en Android mediante la solución de medición de vídeo.

>[!TIP]
>
>Durante la reproducción de vídeo, se envían llamadas frecuentes de monitoreo del funcionamiento a este servicio para medir el tiempo de reproducción. Estas llamadas de monitoreo del funcionamiento se envían cada diez segundos, lo que crea métricas de participación de vídeo granulares e informes de visitas de vídeo más precisos. Para obtener más información acerca de la solución de medición de vídeo de Adobe, consulte [Medición de audio y vídeo en Adobe Analytics](https://docs.adobe.com/content/help/es-ES/media-analytics/using/media-overview.html).

El proceso general de medición de vídeos es muy similar en todas las plataformas. Este contenido ofrece una visión general de las tareas del desarrollador, con ejemplos de código. La siguiente tabla indica los datos multimedia que se envían a Analytics. Las reglas de procesamiento se utilizan para asignar los datos de contexto a una variable de Analytics.

## Asignación de eventos del reproductor a las variables de Analytics {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Tipo de variable: eVar
      * Caducidad predeterminada: visita
      * Custom Insight (s.prop, se utiliza para las rutas de vídeo)
   * (**Obligatorio**) Cuando un visitante ve el vídeo de alguna manera, esta variable de datos de contexto recopila el nombre del vídeo, tal como se especifica en la implementación. Puede agregar clasificaciones para esta variable.
   * (**Opcional**) La variable de Custom Insight proporciona información de las rutas de vídeo.

* **a.media.name**
   * Tipo de variable: Custom Insight (s.prop)
   * (**Opcional**) Proporciona información sobre la ruta del vídeo.

      >[!IMPORTANT]
      >
      >ExpCare debe habilitar las rutas para esta variable.
   * Tipo de evento: Insight personalizada (s.prop)

* **a.media.segment**
   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página
   * (**Obligatoria**) Recopila datos de segmento del vídeo, incluido el nombre del segmento y el orden en que aparece el segmento en el vídeo.

      Esta variable se rellena habilitando la variable `segmentByMilestones` cuando se realiza un seguimiento automático de eventos de reproductor, o bien estableciendo un nombre de segmento personalizado cuando se realiza un seguimiento manual de eventos de reproductor. Por ejemplo, cuando un visitante ve el primer segmento de un vídeo, SiteCatalyst podría recopilar lo siguiente en la eVar Segments: `1:M:0-25`.

      El método de recopilación de datos de vídeo predeterminado recopila datos en los puntos siguientes:

      * inicio de vídeo (reproducción)
      * inicio de segmento
      * final de vídeo (parada)

      Analytics cuenta la primera vista de segmentos en el inicio del segmento, cuando el visitante empieza a ver. Vistas de segmentos posteriores desde el inicio del segmento.


* **a.contentType**
   * Tipo de variable: eVar
   * Caducidad predeterminada: vista de página
   * Recopila datos sobre el tipo de contenido que un visitante ve.

      Se asigna un tipo de contenido `video` a las visitas enviadas por la medición de vídeo. Desde la perspectiva de medición de vídeo, **Tipo de contenido** permite identificar visitantes de vídeo y calcular tasas de conversión de vídeo.

* **a.media.timePlayed**
   * Tipo de variable: Event
   * Tipo: contador
   * Cuenta el tiempo, en segundos, transcurrido en ver un vídeo desde el último proceso de recopilación de datos (solicitud de imagen).

* **a.media.view**
   * Tipo de variable: Event
   * Tipo: contador
   * Indica que un visitante ha visto alguna parte de un de vídeo.

      Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

* **a.media.segmentView**
   * Tipo de variable: Event
   * Tipo: contador
   * Indica que un visitante ha visto alguna parte de un segmento de vídeo.

      Sin embargo, no proporciona ninguna información sobre qué parte del vídeo ha visualizado el visitante, ni durante cuánto tiempo.

* **a .media.complete**
   * Tipo de variable: Event
   * Tipo: contador
   * Indica que un usuario ha visto un vídeo completo.

      De forma predeterminada, el evento completo se mide 1 segundo antes del final del vídeo. Durante la implementación, puede especificar cuántos segundos desde el final de vídeo quisiera considerar como una vista completa. Para el vídeo en directo y otros flujos que no tienen un final definido, puede especificar un punto personalizado para medir las finalizaciones, por ejemplo, después de un tiempo de visualización específico.


## Configuración de medios {#section_929945D4183C428AAF3B983EFD3E2500}

Configure un objeto `MediaSettings` con los ajustes que quiera usar para realizar seguimiento de vídeo:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Seguimiento de eventos del reproductor {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Para medir la reproducción de vídeo, es preciso realizar llamadas a los métodos `mediaPlay`, `mediaStop`, y `mediaClose` en los momentos apropiados. Por ejemplo, cuando el reproductor se pone en pausa, llame a `mediaStop`. `mediaPlay` se utiliza cuando la reproducción comienza o se reanuda.

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

## Referencia de clases y métodos de medición de medios {#section_50DF9359A7B14DF092634C8E913C77FE}

Estos son los métodos de la clase de medición de medios:

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

   * Este es un ejemplo de código para este método:

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
