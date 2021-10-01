---
description: Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para iOS de Adobe Mobile.
solution: Experience Cloud,Analytics
title: Seguimiento de vínculos profundos
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
exl-id: a8b20233-d800-4318-ad4f-39229d8b3a5e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 100%

---

# Seguimiento de vínculos profundos{#tracking-deep-links}

Puede utilizar esta información para realizar un seguimiento de vínculos profundos y vínculos profundos diferidos en sus aplicaciones móviles mediante el SDK para iOS de Adobe Mobile.

Para obtener más información acerca de cómo los especialistas en marketing utilizan la vinculación profunda en sus aplicaciones, consulte [Adquisición](/help/ios/acquisition-main/acquisition.md) en la documentación de Mobile Services.

## Seguimiento de vínculos profundos

1. Añada el SDK al proyecto e implemente métricas del ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Registre la aplicación para gestionar comunicaciones entre aplicaciones o vínculos universales de soporte.

   Para obtener más información, consulte [Comunicaciones entre aplicaciones](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) o [Vínculos universales de compatibilidad](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Haga un seguimiento de vínculos profundos en openURL.

   Este es un ejemplo de vínculo profundo de seguimiento:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

El SDK de Adobe Mobile puede analizar pares de datos (claves y valores) que se adjuntan a cualquier vínculo profundo o universal, siempre que el vínculo contenga una clave con la etiqueta `a.deeplink.id` y un valor correspondiente no nulo y generado por el usuario. Todos los pares de datos (clave y valor) adjuntos al vínculo se analizan, se adjuntan a una visita del ciclo vital y se envían a Adobe Analytics, siempre que el vínculo contenga la clave y valor `a.deeplink.id`.

Si lo desea, puede adjuntar al vínculo profundo o universal una o más de las siguientes claves reservadas (con valores generados por el usuario):

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Estas claves son variables preasignadas para la realización de informes en Adobe Analytics. Para obtener más información sobre asignación y reglas de procesamiento, consulte [Reglas de procesamiento y datos de contexto](/help/ios/getting-started/proc-rules.md).

### Seguimiento de vínculos profundos diferidos

1. Registre llamadas de respuesta de datos de Adobe.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Gestionar `ADBMobileDataEventDeepLink` dentro de `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Información pública de vinculación profunda {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Métodos

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Constantes

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```
