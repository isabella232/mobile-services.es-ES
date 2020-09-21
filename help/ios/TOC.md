---
product: mobile-services
audience: end-user
user-guide-title: Guía de iOS de Mobile Services
breadcrumb-title: iOS Guide
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 97%

---


# Mobile Services iOS Guide {#ios}

+ [SDK para iOS 4.x para soluciones de Experience Cloud](overview.md)
+ [Notas de la versión](rel-notes.md)
+ Primeros pasos {#getting-started-ios}
   + [Información general sobre la introducción](getting-started/getting-started.md)
   + [Antes de comenzar](getting-started/requirements.md)
   + [Implementación principal y ciclo vital](getting-started/dev-qs.md)
   + [Reglas de procesamiento y datos de contexto](getting-started/proc-rules.md)
   + [Integración con Swift](getting-started/swift-integration.md)
   + [Migración a la biblioteca iOS 4.x](getting-started/migration-v3.md)
+ Configuración {#config-ios}
   + [Información general sobre la configuración](configuration/configuration.md)
   + [Configuración JSON de ADBMobile](configuration/json-config/json-config.md)
   + [Anular la ruta de configuración JSON de ADBMobile](configuration/json-config/json-config-remote.md)
   + [Lotes de visitas](configuration/hit-batching.md)
   + [Métodos de configuración](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Métricas del ciclo vital](metrics.md)
+ Analytics {#analytics-ios}
   + [Información general de Analytics](analytics-main/analytics-main.md)
   + [Seguimiento de estados de aplicaciones](analytics-main/states.md)
   + [Seguimiento de acciones de aplicaciones](analytics-main/actions.md)
   + [Seguimiento de errores de aplicaciones](analytics-main/crashes.md)
   + [Acciones temporizadas](analytics-main/timed-actions.md)
   + [Valor de duración de visitantes](analytics-main/lifetime-value.md)
   + Variable Products {#products-variable}
      + [Variable products](analytics-main/products/products.md)
      + [Variable products con eVars de comercialización y events (eventos) específicos de productos](analytics-main/products/products-variable-evars-events.md)
   + [Serialización de eventos](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Información general de Postbacks](analytics-main/postback/postback.md)
      + [Ejemplo de Postbacks](analytics-main/postback/postback-example.md)
      + [Postbacks PII ](analytics-main/postback/c-pii-postbacks.md)
   + [Métodos de Analytics](analytics-main/analytics-methods.md)
+ Adquisición {#acquisition-ios}
   + [Información general sobre adquisición](acquisition-main/acquisition-main.md)
   + [Adquisición de aplicación móvil](acquisition-main/acquisition.md)
   + [Métodos de adquisición](acquisition-main/c-acquisition-methods.md)
   + Seguimiento de vínculos profundos {#tracking-deep-links}
      + [Seguimiento de vínculos profundos](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Seguimiento de vínculos profundos diferidos de terceros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Prueba de adquisición de vínculos de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Prueba de adquisición V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Prueba de adquisición de elementos heredados](acquisition-main/t-testing-acquisition.md)
   + [Search Ads de Apple](acquisition-main/c-apple-search-ads.md)
+ Mensajería {#messaging-ios}
   + [Información general sobre mensajería](messaging-main/messaging-main.md)
   + Mensajería en la aplicación {#in-app-messaging}
      + [Mensajería en la aplicación](messaging-main/messaging/messaging.md)
      + [Resolucion de problemas de la mensajería en la aplicación](messaging-main/messaging/in-apps-ts.md)
   + Mensajería push {#push-messaging}
      + [Mensajería push](messaging-main/push-messaging/push-messaging.md)
      + [Implementar la mensajería push con vinculación profunda](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Recibir notificaciones push enriquecidas](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Resolución de problemas de mensajería push ](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Ubicación {#location-ios}
   + [Información general sobre la ubicación](location/location.md)
   + [Geolocalización y puntos de interés](location/geo-poi.md)
   + [Seguimiento de iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Información general de Target](target-main/target-main.md)
   + [Métodos de Target](target-main/c-target-methods.md)
   + [Recuperar previamente contenido de ofertas en iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Vista previa de Target en iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Información general de Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Métodos del servicio de ID de Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Cooperación entre dispositivos de Experience Cloud](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Métodos de Audience Manager](amm/aam-methods.md)
+ Implementación de Apple TV con tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementación de Apple TV con tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target para TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Métodos de TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ Implementación de extensiones iOS {#ios-ext}
   + [Implementación de extensiones iOS](ios-ext/ios-ext.md)
   + [Implementación de extensiones independientes](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementación de Apple Watch con WatchOS 2](apple-watch-implementation-watchkit.md)
+ Referencia del SDK para iOS {#sdk-reference-ios}
   + [Referencia del SDK para iOS ](reference/reference.md)
   + [ID de la aplicación](reference/app-ids.md)
   + [Seguimiento de visitantes entre una aplicación y la web móvil](reference/hybrid-app.md)
   + [Versiones de dispositivo iOS ](reference/device-versions.md)
+ Reglamento general de protección de datos{#privacy-gdpr-ios}
   + [Reglamento general de protección de datos](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recuperación de identificadores almacenados](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Configuración del estado de exclusión del usuario](c-mob-privacy-gdpr-ios/privacy.md)
+ Complemento PhoneGap {#phonegap-ios}
   + [Complemento PhoneGap](phonegap/phonegap.md)
   + [Métodos del complemento PhoneGap](phonegap/phonegap-methods.md)
