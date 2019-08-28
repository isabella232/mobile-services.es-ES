---
description: Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-description: Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-title: Seguimiento de vínculos profundos diferidos de terceros
title: Seguimiento de vínculos profundos diferidos de terceros
uuid: 4 c 798 e 47-7988-4 a 06-a 191-6 c 4 d 05 f 6 ee 61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Tracking third-party deferred deep links{#tracking-third-party-deferred-deep-links}

Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

En la actualidad, el SDK de Adobe Mobile admite la vinculación profunda: se espera que el desarrollador de la aplicación utilice la API `collectLifecycleData` del SDK desde la actividad vinculada en profundidad. El SDK adjunta los datos de vínculo profundo procedentes de los parámetros de URL vinculada. Para obtener más información sobre el funcionamiento de la vinculación profunda en el SDK de Adobe Mobile, consulte [Seguimiento de vínculos profundos](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Un creador de anuncios puede crear un anuncio en Facebook como vínculo profundo. Cuando los usuarios hacen clic en el anuncio, este los lleva directamente a la información que les interesa en la aplicación. El vínculo profundo **no** es una URL de plataforma de huellas digitales. No obstante, durante la configuración del anuncio existe la opción de proporcionar un vínculo profundo (URL) de terceros. Un desarrollador de aplicaciones que utilice los SDK y servicios de Adobe Mobile debe introducir en este campo la URL de la plataforma de huellas digitales configurada para Adobe Mobile Services. Si todo está configurado correctamente, el SDK de Facebook pasa esta URL a la aplicación cuando esta se instala o inicia.

## Configuración de los SDK {#section_834CD3109175432B8173ECB6EA7DE315}

Con el fin de prepararse para añadir compatibilidad con la vinculación profunda de Facebook con el SDK de Adobe Mobile, el desarrollador de aplicaciones debe completar las tareas siguientes:

* Introducción al SDK para Android

   For more information, see [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) .

* Configurar vinculación profunda

   Para obtener más información, consulte [Configuración de vinculación profunda](https://developers.facebook.com/docs/app-ads/deep-linking#os).

If the application is set up correctly, the `trackAdobeDeepLink()` API should enable collecting the deep link information from the Facebook acquisition campaign and send it to Adobe Mobile Service. Si no se ha enviado a Adobe Mobile Services la visita de la instalación en el primer inicio, esta información se añadirá a la visita del ciclo de duración. En caso contrario, se enviará como visita de vínculo profundo de Adobe.

>[!TIP]
>
>Ensure that the deep link URL has a key called `a.deeplink.id`. Si en la URL falta el parámetro de identificación de vínculo profundo, los parámetros de URL no se adjuntarán a los datos de contexto.

Si el vínculo puede atribuirse a una adquisición, el SDK de Adobe Mobile almacenará los datos de adquisición del vínculo profundo de Facebook utilizado para llamar a `trackAdobeDeepLink()`. Estos datos estarán disponibles para el SDK de Adobe Mobile la próxima vez que se inicie. Si se ha registrado una llamada de retorno, también se utilizará la llamada de retorno de Adobe para devolver los datos al cliente.

## Enable deep linking in an Android application {#section_64C15E269E89424B8E3D029F88094620}

1. Registre la aplicación para gestionar vínculos profundos.

   Para obtener más información, consulte [Allowing Other Apps to Start your Activity (Permitir a otras aplicaciones comenzar su actividad)](https://developer.android.com/training/basics/intents/filters.html).

1. Vincule los SDK de Facebook.

   Para añadir en la aplicación la dependencia de gradle de Facebook, complete los pasos en [Getting Started Android SDK (Introducción al SDK para Android)](https://developers.facebook.com/docs/android/getting-started).

1. Para inicializar el SDK de Facebook, complete las instrucciones de la sección *Configuración de Android Studio*.
1. Call `trackAdobeDeepLink()` from the main activity.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

