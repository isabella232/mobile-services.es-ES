---
description: Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.
keywords: android;library;mobile;sdk
seo-description: Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.
seo-title: Seguimiento de vínculos profundos en Adobe Mobile Services
solution: Experience Cloud,Analytics
title: Seguimiento de vínculos profundos
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: ht
source-git-commit: e28340249c22d9f121d5c21205227ee758fb9e1b
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# Seguimiento de vínculos profundos

Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.

## Seguimiento de vínculos profundos

1. Añada el SDK al proyecto e implemente métricas del ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Registre la aplicación para gestionar direcciones URL.

   Para obtener más información, consulte [Direcciones URL](https://developer.android.com/training/basics/intents/filters.html).
1. Transfiera la interpretación de las actividades con vínculo profundo al SDK de Adobe mediante `collectLifecycleData`.

   Este es un ejemplo de vínculo profundo de seguimiento:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

El SDK de Adobe Mobile puede analizar pares de datos (claves y valores) que se adjuntan a cualquier vínculo profundo o universal, siempre que el vínculo contenga una clave con la etiqueta `a.deeplink.id` y un valor correspondiente no nulo y generado por el usuario. Todos los pares de datos (clave y valor) adjuntos al vínculo se analizan, se adjuntan a una visita del ciclo de duración y se envían a Adobe Analytics, siempre que el vínculo contenga la clave y valor `a.deeplink.id`.

Además, puede adjuntar al vínculo profundo o universal una o más de las siguientes claves reservadas (con valores generados por el usuario):

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Estas claves son variables preasignadas para la realización de informes en Adobe Analytics. Para obtener más información sobre asignación y reglas de procesamiento, consulte [Reglas de procesamiento y datos de contexto](https://docs.adobe.com/content/help/es-ES/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Seguimiento de vínculos profundos diferidos (para su uso con vínculos de marketing)

Con un vínculo profundo diferido, el SDK de Adobe abrirá un nuevo objeto Intent con el vínculo profundo como datos de intención. Este proceso se gestiona como un vínculo profundo externo con el código anterior.

## Información pública de vinculación profunda {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

