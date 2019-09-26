---
product: mobile-services
audience: usuario final
user-guide-title: Ayuda de Mobile Services para iOS
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS Help {#ios}

+ [SDK de iOS para soluciones de Experience Cloud 4.x](overview.md)
+ [Notas de la versión](rel-notes.md)
+ Primeros pasos {#getting-started-ios}
   + [Getting started overview](getting-started/getting-started.md)
   + [Antes de empezar](getting-started/requirements.md)
   + [Core implementation and lifecycle](getting-started/dev-qs.md)
   + [Processing rules and context data](getting-started/proc-rules.md)
   + [Integración con Swift](getting-started/swift-integration.md)
   + [Migración a la biblioteca 4.x de iOS](getting-started/migration-v3.md)
+ Configuración {#config-ios}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [Anular la ruta de configuración JSON de ADBMobile](configuration/json-config/json-config-remote.md)
   + [Lotes de visitas](configuration/hit-batching.md)
   + [Métodos de configuración](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Métricas del ciclo vital](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [Seguimiento de estados de aplicaciones](analytics-main/states.md)
   + [Seguimiento de acciones de aplicaciones](analytics-main/actions.md)
   + [Seguimiento de errores de aplicaciones](analytics-main/crashes.md)
   + [Acciones temporizadas](analytics-main/timed-actions.md)
   + [Valor de duración del visitante](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Variable products](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [Serialización de eventos](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Postbacks overview](analytics-main/postback/postback.md)
      + [Ejemplo de postback](analytics-main/postback/postback-example.md)
      + [Postbacks PII](analytics-main/postback/c-pii-postbacks.md)
   + [Métodos de Analytics](analytics-main/analytics-methods.md)
+ Adquisición {#acquisition-ios}
   + [Acquisition overview](acquisition-main/acquisition-main.md)
   + [Adquisición de aplicaciones móviles](acquisition-main/acquisition.md)
   + [Métodos de adquisición](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Seguimiento de vínculos profundos](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Seguimiento de vínculos profundos diferidos de terceros](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Prueba de adquisición de vínculos de marketing](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Prueba de adquisición de V3](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testing legacy acquisition](acquisition-main/t-testing-acquisition.md)
   + [Search Ads de Apple](acquisition-main/c-apple-search-ads.md)
+ Mensajería {#messaging-ios}
   + [Messaging overview](messaging-main/messaging-main.md)
   + Mensajería en la aplicación {#in-app-messaging}
      + [Mensajería en la aplicación](messaging-main/messaging/messaging.md)
      + [Solución de problemas de la mensajería en la aplicación](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [Implementar la mensajería push con vinculación profunda](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Recibir notificaciones push enriquecidas](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Troubleshooting push messaging](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Ubicación {#location-ios}
   + [Información general de ubicación](location/location.md)
   + [Ubicación geográfica y puntos de interés](location/geo-poi.md)
   + [Seguimiento de iBeacon](location/ibeacon.md)
+ Target {#target-ios}
   + [Target overview](target-main/target-main.md)
   + [Métodos de Target](target-main/c-target-methods.md)
   + [Recuperar previamente contenido de ofertas en iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Vista previa de Target en iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Información general de Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service Methods](marketing-cloud/mc-methods.md)
   + [Cooperación entre dispositivos de Experience Cloud](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Métodos de Audience Manager](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Implementación de Apple TV con tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target para TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [Métodos de TVJS](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS extension implementation](ios-ext/ios-ext.md)
   + [Implementación de extensión independiente](ios-ext/c-stand-alone-extension-implementation.md)
+ [Implementación de Apple Watch con WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [Referencia del SDK de iOS](reference/reference.md)
   + [ID de la aplicación](reference/app-ids.md)
   + [Seguimiento de visitantes entre una aplicación y una web móvil](reference/hybrid-app.md)
   + [Versiones de dispositivos iOS](reference/device-versions.md)
+ Reglamento general de protección de datos{#privacy-gdpr-ios}
   + [Reglamento general de protección de datos](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Recuperación de identificadores almacenados](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Configuración del estado de selección del usuario](c-mob-privacy-gdpr-ios/privacy.md)
+ Complemento PhoneGap {#phonegap-ios}
   + [Complemento PhoneGap](phonegap/phonegap.md)
   + [Métodos del complemento PhoneGap](phonegap/phonegap-methods.md)
