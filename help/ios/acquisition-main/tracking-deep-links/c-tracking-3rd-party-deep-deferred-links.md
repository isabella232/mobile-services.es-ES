---
description: Utilice el SDK para iOS para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-description: Utilice el SDK para iOS para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-title: Seguimiento de vínculos profundos diferidos de terceros
title: Seguimiento de vínculos profundos diferidos de terceros
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 90%

---


# Seguimiento de vínculos profundos diferidos de terceros {#tracking-third-party-deferred-deep-links}

Utilice el SDK para iOS para implementar el seguimiento de vínculos profundos diferidos de terceros.

## Vinculación profunda del SDK de Adobe Mobile clásico {#section_D114FA1EB9664EAA82E036A990694B26}

En la actualidad, Adobe Mobile SDK admite la vinculación profunda: se espera que el desarrollador de la aplicación realice una llamada a la API `trackAdobeDeepLink` y pase la URL de vinculación profunda (URL de plataforma de huellas digitales generada en Adobe Mobile Services durante la confirmación). El SDK envía un ping a la plataforma de huellas digitales para obtener datos de adquisición y los adjunta como parte del ciclo vital a los datos de contexto de las llamadas de instalación e inicio de Analytics. Además, el SDK también adjunta los datos de vinculación profunda procedentes de los parámetros de URL de vinculación profunda. Para obtener más información al respecto, consulte [Seguimiento de vínculos profundos](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Vinculación profunda con Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Un creador de anuncios puede crear un anuncio en Facebook como vínculo profundo. Cuando los usuarios hacen clic en el anuncio en Facebook, esta se dirige a la información que les interesa en la aplicación. El vínculo profundo **no** es una URL de plataforma de huellas digitales. No obstante, durante la configuración del anuncio existe la opción de proporcionar un vínculo profundo (URL) de terceros. Se espera que un desarrollador de aplicaciones que utilice los SDK y servicios de Experience Cloud Mobile introduzca en este campo la URL de la plataforma de huellas digitales configurada para Mobile Services. Si todo está configurado correctamente, el SDK de Facebook pasa esta URL a la aplicación cuando esta se instala o inicia.

## Configuración de los SDK {#section_834CD3109175432B8173ECB6EA7DE315}

1. Configurar el SDK de Facebook.

   Para obtener más información, consulte lo siguiente:

   * [Introducción al SDK de Facebook para iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Configuración de vinculación profunda](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Para configurar el SDK, llame a `trackAdobeDeepLink` y pase la URL a los SDK:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Compruebe que la URL de vínculo profundo tenga una clave con el nombre `a.deeplink.id`. No se adjuntará ningún parámetro de URL a los datos de contexto si en la URL falta el parámetro `a.deeplink.id`.

Si la aplicación se configura como se ha indicado arriba, la versión actual del AMSDK funcionará bien y adjuntará correctamente los datos de vinculación profunda a las llamadas de instalación e inicio de Analytics.

## Habilitar la funcionalidad en una aplicación de ejemplo {#section_64C15E269E89424B8E3D029F88094620}

1. Registre un esquema de dirección URL.

   Asegúrese de que ha registrado un esquema de URL, que es el mismo que la URL del vínculo profundo.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Vincule los SDK de Facebook.

   ![Recursos de Facebook](assets/link-fb-sdk.jpg)

1. Edit `AppDelegate`.

   1. Importe los encabezados.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. Agregue el controlador para la vinculación profunda diferida.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. Llame a la API de `trackAdobeDeepLink` y pase la URL del vínculo profundo a los SDK.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

