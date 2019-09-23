---
description: El SDK para iOS 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones nativas de Apple para iPhone y para iPad, enviar contenido de destino en las aplicaciones y aprovechar y recopilar datos de audiencia a través de Audience Manager.
seo-description: El SDK para iOS 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones nativas de Apple para iPhone y para iPad, enviar contenido de destino en las aplicaciones y aprovechar y recopilar datos de audiencia a través de Audience Manager.
seo-title: SDK para iOS 4.x para soluciones de Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK para iOS 4.x para soluciones de Experience Cloud
topic: Desarrollador e implementación
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: 0f6eec995626f4c93f56d59b682083bd0428d9e1

---


# SDK para iOS 4.x para soluciones de Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

El SDK para iOS 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones nativas de Apple para iPhone y para iPad, enviar contenido de destino en las aplicaciones y aprovechar y recopilar datos de audiencia a través de Audience Manager.

>[!IMPORTANT]
>
>El SKU del complemento de marketing móvil de Adobe Analytics es necesario para habilitar el acceso de Mobile Services a las funciones de adquisición móvil, vinculación profunda, geolocalización y mensajería móvil. Para obtener más información, póngase en contacto con el CSM de Adobe.

>[!IMPORTANT]
>
>El SDK para iOS 4.x para soluciones de Experience Cloud ahora es compatible con [iOS 13 y Xcode 11][https://developer.apple.com/ios/]. Para garantizar una compatibilidad perfecta, utilice las versiones más recientes de los SDK 4.x de iOS. Para obtener más información sobre la versión más reciente, consulte las notas de la [versión](/help/ios/rel-notes.md).

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Información que debe recordar:

* Compatible con iOS 5 o posterior

   Para las versiones iOS 11 o posteriores, **debe** tener la versión del SDK 4.13.8 o posterior.

* En la versión 4.2 o posterior del SDK, todas las visitas se envían ahora mediante HTTP POST.

   This has no impact on the data that is collected or reported, but you need to use a packet analyzer that supports inspecting POST data to view hits.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Documentación del usuario de Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services proporciona una nueva interfaz de usuario que aúna las capacidades de marketing móvil para aplicaciones móviles desde Adobe Experience Cloud. Initially, the Mobile service provides seamless integration of app analytics and targeting capabilities from the Adobe Analytics, Adobe Audience Manager, and Adobe Target solutions, and Adobe Experience Platform Identity Service.

Para obtener más información acerca de la interfaz de usuario de Mobile Services y leer la documentación del usuario, consulte [Adobe Mobile Services](/help/using/home.md).

## Uso de Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Desde el 1 de mayo de 2017 no se proporcionarán nuevas mejoras ni se ofrecerá más soporte técnico de ingeniería o Adobe Expert Care.
