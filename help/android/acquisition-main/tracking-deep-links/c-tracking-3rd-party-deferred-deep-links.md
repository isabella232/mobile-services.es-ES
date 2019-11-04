---
description: Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-description: Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.
seo-title: Seguimiento de vínculos profundos diferidos de terceros
title: Seguimiento de vínculos profundos diferidos de terceros
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Seguimiento de vínculos profundos diferidos de terceros{#tracking-third-party-deferred-deep-links}

Utilice el SDK para Android para implementar el seguimiento de vínculos profundos diferidos de terceros.

## Vinculación profunda del SDK de Adobe Mobile clásico {#section_D114FA1EB9664EAA82E036A990694B26}

En la actualidad, el SDK de Adobe Mobile admite la vinculación profunda: se espera que el desarrollador de la aplicación utilice la API `collectLifecycleData` del SDK desde la actividad vinculada en profundidad. El SDK adjunta los datos de vínculo profundo procedentes de los parámetros de URL vinculada. Para obtener más información sobre el funcionamiento de la vinculación profunda en el SDK de Adobe Mobile, consulte [Seguimiento de vínculos profundos](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Vinculación profunda con Facebook {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Un creador de anuncios puede crear un anuncio en Facebook como vínculo profundo. Cuando los usuarios hacen clic en el anuncio, este los lleva directamente a la información que les interesa en la aplicación. El vínculo profundo **no** es una URL de plataforma de huellas digitales. No obstante, durante la configuración del anuncio existe la opción de proporcionar un vínculo profundo (URL) de terceros. Un desarrollador de aplicaciones que utilice los SDK y servicios de Adobe Mobile debe introducir en este campo la URL de la plataforma de huellas digitales configurada para Adobe Mobile Services. Si todo está configurado correctamente, el SDK de Facebook pasa esta URL a la aplicación cuando esta se instala o inicia.

## Configuración de los SDK {#section_834CD3109175432B8173ECB6EA7DE315}

Con el fin de prepararse para añadir compatibilidad con la vinculación profunda de Facebook con el SDK de Adobe Mobile, el desarrollador de aplicaciones debe completar las tareas siguientes:

* Introducción al SDK para Android

   Para obtener más información, consulte [Introducción al SDK para Android](https://developers.facebook.com/docs/android/getting-started).

* Configurar vinculación profunda

   Para obtener más información, consulte [Configuración de vínculos profundos](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Si la aplicación está correctamente configurada, la API `trackAdobeDeepLink()` debería permitir la recopilación de la información de vínculo profundo de la campaña de adquisición de Facebook y enviarla a Adobe Mobile Services. Si no se ha enviado a Adobe Mobile Services la visita de la instalación en el primer inicio, esta información se añadirá a la visita del ciclo de duración. En caso contrario, se enviará como visita de vínculo profundo de Adobe.

>[!TIP]
>
>Compruebe que la URL de vínculo profundo tiene una clave denominada `a.deeplink.id`. Si en la URL falta el parámetro de identificación de vínculo profundo, los parámetros de URL no se adjuntarán a los datos de contexto.

Si el vínculo puede atribuirse a una adquisición, el SDK de Adobe Mobile almacenará los datos de adquisición del vínculo profundo de Facebook utilizado para llamar a `trackAdobeDeepLink()`. Estos datos estarán disponibles para el SDK de Adobe Mobile la próxima vez que se inicie. Si se ha registrado una llamada de retorno, también se utilizará la llamada de retorno de Adobe para devolver los datos al cliente.

## Habilitar la vinculación profunda en una aplicación Android {#section_64C15E269E89424B8E3D029F88094620}

1. Registre la aplicación para gestionar vínculos profundos.

   Para obtener más información, consulte [Permitir a otras aplicaciones comenzar su actividad](https://developer.android.com/training/basics/intents/filters.html).

1. Vincule los SDK de Facebook.

   Para añadir en la aplicación la dependencia de gradle de Facebook, complete los pasos en [Introducción al SDK para Android](https://developers.facebook.com/docs/android/getting-started).

1. Para inicializar el SDK de Facebook, complete las instrucciones de la sección *Configuración de Android Studio*.
1. Llame a `trackAdobeDeepLink()` desde la actividad principal.

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

