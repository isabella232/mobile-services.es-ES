---
audience: end-user
user-guide-title: Guía de Mobile Services para Android
breadcrumb-title: Guía de Android
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 99%

---


# Guía de Mobile Services para Android{#android}

+ [SDK para Android 4.x para soluciones de Experience Cloud](overview.md)
+ [Notas de la versión](rel-notes.md)
+ Primeros pasos {#getting-started-android}
   + [Primeros pasos](getting-started/getting-started.md)
   + [Antes de comenzar](getting-started/requirements.md)
   + [Implementación principal y ciclo vital](getting-started/dev-qs.md)
   + [Reglas de procesamiento y datos de contexto ](getting-started/proc-rules.md)
   + [Migración a la biblioteca Android 4.x](getting-started/migration-v3.md)
+ Configuración{#configuration-android}
   + [Información general sobre la configuración](configuration/configuration.md)
   + [Archivo de configuración JSON de ADBMobile](configuration/json-config/json-config.md)
   + [Anular la ruta de configuración JSON de ADBMobile](configuration/json-config/json-config-remote.md)
   + [Agrupamiento de visitas](configuration/hit-batching.md)
   + [Métodos de configuración](configuration/methods.md)
+ [Métricas del ciclo vital](metrics.md)
+ Analytics {#analytics-android}
   + [Información general de Analytics](analytics-main/analytics-main.md)
   + [Seguimiento de estados de aplicaciones](analytics-main/states.md)
   + [Seguimiento de acciones de aplicaciones](analytics-main/actions.md)
   + [Seguimiento de errores de aplicaciones](analytics-main/crashes.md)
   + [Acciones temporizadas](analytics-main/timed-actions.md)
   + [Valor de duración de visitantes](analytics-main/lifetime-value.md)
   + Variable Products {#products-variable}
      + [Variable products](analytics-main/products/products.md)
      + [Variable products con eVars de comercialización y eventos específicos de productos](analytics-main/products/products-variable-evars-events.md)
   + [Serialización de eventos](analytics-main/event-serialization.md)
   + [Video Analytics ](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Información general de Postbacks](analytics-main/postbacks/postbacks.md)
      + [Ejemplo de Postbacks](analytics-main/postbacks/postback-example.md)
      + [Postbacks PII](analytics-main/postbacks/c-pii-postbacks.md)
   + [Métodos de Analytics](analytics-main/analytics-methods.md)
+ Adquisición {#acquisition-android}
   + [Información general sobre adquisición](acquisition-main/acquisition-main-android.md)
   + [Adquisición de aplicación móvil](acquisition-main/acquisition.md)
   + [Métodos de adquisición ](acquisition-main/acquisition-methods.md)
   + Seguimiento de vínculos profundos {#tracking-deep-links}
      + [Seguimiento de vínculos profundos](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Seguimiento de vínculos profundos diferidos de terceros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Prueba de adquisición de vínculos de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Prueba de adquisición V3 ](acquisition-main/t-testing-version-3-acquisition.md)
   + [Prueba de adquisición de elementos heredados](acquisition-main/t-testing-acquisition.md)
   + [Resolución de problemas de pruebas de adquisición](acquisition-main/troubleshoot-acquisition-testing.md)
+ Mensajería {#messaging-android}
   + [Información general sobre mensajería](messaging-main/messaging-main-android.md)
   + Mensajería en la aplicación {#inapp-messaging}
      + [Mensajería en la aplicación ](messaging-main/messaging/messaging.md)
      + [Resolución de problemas de mensajería en la aplicación ](messaging-main/messaging/in-apps-ts.md)
   + Mensajería push {#push-messaging}
      + [Mensajería push](messaging-main/push-messaging/push-messaging.md)
      + [Implementar la mensajería push con vinculación profunda](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Recibir notificaciones push enriquecidas](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Resolución de problemas de mensajería push](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Ubicación {#location}
   + [Información general sobre la ubicación](location/location.md)
   + [Geolocalización y puntos de interés](location/geo-poi.md)
   + [Seguimiento de señalización](location/beacon.md)
+ Target {#target-android}
   + [Información general de Target](target-main/target-main.md)
   + [Configuración de Target](target-main/target.md)
   + [Métodos de Target](target-main/c-target-methods.md)
   + [Recuperación previa del contenido de ofertas en Android](target-main/c-mob-target-prefetch-android.md)
   + [Vista previa de Target en Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud {#experience-cloud-android}
   + [Información general de Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Configuración de Experience Cloud ID](c-marketing-cloud/mcvid.md)
   + [Métodos del servicio de ID de Adobe Experience Platform](c-marketing-cloud/mc-methods.md)
+ Audience Manager {#audience-manager-android}
   + [Información general de Audience Manager](audience-manager/audience-manager.md)
   + [Configuración de Audience Manager](audience-manager/audiencemgmt.md)
   + [Métodos de Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Wearables {#wearables-android}
   + [Información general de Wearables](wearables/wearables.md)
   + [Android Wearables: Introducción ](wearables/android-wearable.md)
   + [Android Wearables: Notas adicionales ](wearables/c-android-wearables--additional-notes.md)
+ Referencia del SDK para Android {#sdk-reference-android}
   + [Introducción a la referencia del SDK para Android](/help/android/reference/reference.md)
   + [ID de la aplicación](/help/android/reference/app-ids.md)
   + [Seguimiento de visitantes entre una aplicación y la web móvil](/help/android/reference/hybrid-app.md)
   + [Widgets de Android](/help/android/reference/widgets.md)
+ Reglamento general de protección de datos {#gdpr-privacy-android}
   + [Información general sobre privacidad y RGPD](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Recuperación de identificadores almacenados](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Configuración del estado de exclusión del usuario](c-mob-privacy-gdpr-android/privacy.md)
+ Complemento PhoneGap {#phonegap-android}
   + [Información general del complemento PhoneGap](phonegap/phonegap.md)
   + [Métodos del complemento PhoneGap](phonegap/phonegap-methods.md)
