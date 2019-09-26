---
description: Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.
keywords: android;library;mobile;sdk
seo-description: Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.
seo-title: Seguimiento de vínculos profundos en Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Seguimiento de vínculos profundos
topic: Desarrollador e implementación
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para Android de Adobe Mobile.

## Tracking deep links

1. Añada el SDK al proyecto e implemente métricas del ciclo vital.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core Implementation and Lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Registre la aplicación para gestionar direcciones URL.

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

Además, puede anexar una o más de las siguientes claves reservadas (con valores generados por el usuario) al vínculo profundo o universal:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Estas claves son variables preasignadas para la realización de informes en Adobe Analytics. Para obtener más información sobre asignación y reglas de procesamiento, consulte [Reglas de procesamiento y datos de contexto](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Tracking deferred deep links (for use with Marketing Links)

Con un vínculo profundo diferido, el SDK de Adobe abrirá un nuevo objeto Intent con el vínculo profundo como dato de interpretación. Este proceso se gestiona como un vínculo profundo externo empleando el código anterior.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### Constantes

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

