---
description: El SDK para iOS 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones nativas de Apple para iPhone y para iPad, enviar contenido de destino en las aplicaciones y aprovechar y recopilar datos de audiencia a través de Audience Manager.
solution: Experience Cloud Services,Analytics
title: SDK para iOS 4.x para soluciones de Experience Cloud
topic-fix: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
exl-id: d4dbddf7-c8be-4936-adfb-2f7aa07a0dd4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---

# SDK para iOS 4.x para soluciones de Experience Cloud{#ios-sdk-x-for-experience-cloud-solutions}

El SDK para iOS 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones nativas de Apple para iPhone y para iPad, enviar contenido de destino en las aplicaciones y aprovechar y recopilar datos de audiencia a través de Audience Manager.

>[!IMPORTANT]
>
>A partir de la versión 4.21.0, el SDK de iOS tiene una versión mínima requerida de Xcode 12. Si utiliza Cocoapods para administrar las dependencias en la aplicación, el SDK de Adobe requiere la versión 1.10.0 o posterior de Cocoapods.

Si utiliza 4.21.0 o posterior, lea la documentación teniendo en cuenta los siguientes cambios:

* Cada vez que se mencione un archivo de biblioteca binario, deberá utilizarse su reemplazo de XCFramework:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` > `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` > `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` > `AdobeMobileTV.xcframework`
* Si agrega manualmente los XCFrameworks de Adobe a su proyecto, asegúrese de que no estén integrados.

>[!IMPORTANT]
>
>El SKU del complemento de marketing móvil de Adobe Analytics es necesario para habilitar el acceso de Mobile Services a las funciones de adquisición móvil, vinculación profunda, geolocalización y mensajería móvil. Para obtener más información, contacte con el administrador de éxito de Adobe.

>[!IMPORTANT]
>
>El SDK para iOS 4.x para soluciones de Experience Cloud ahora es compatible con [iOS 13 y Xcode 11](https://developer.apple.com/ios/). Para garantizar una compatibilidad perfecta, utilice las versiones más recientes de los SDK 4.x de iOS. Para obtener más información sobre la versión más reciente, consulte las [notas de la versión](/help/ios/rel-notes.md).

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Información que debe recordar:

* Compatible con iOS 8 o posteriores.

   Para iOS 11 o posterior, **debe** tener la versión 4.13.8 o posterior del SDK.

* En la versión 4.2 o posterior del SDK, todas las visitas se envían ahora mediante HTTP POST.

   Esto no afecta a los datos recopilados o comunicados, pero para ver las visitas debe utilizar un analizador de paquetes que admita la inspección de datos POST.

* Si está actualizando desde una versión previa (2.x o 3.x), consulte la [Guía de migración a 4.x](/help/ios/getting-started/migration-v3.md).

## Documentación del usuario de Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services proporciona una nueva interfaz de usuario que aúna las capacidades de marketing móvil para aplicaciones móviles desde Adobe Experience Cloud. Inicialmente, el servicio Mobile proporciona una integración sin problemas de análisis de aplicaciones y capacidades de segmentación a partir de las soluciones Adobe Analytics, Adobe Audience Manager y Adobe Target, así como del servicio de ID de Adobe Experience Platform.

Para obtener más información acerca de la interfaz de usuario de Mobile Services y leer la documentación del usuario, consulte [Adobe Mobile Services](/help/using/home.md).

## Uso de Bloodhound

>[!IMPORTANT]
>
>Adobe Bloodhound expiró el **30 de abril de 2017**. Desde el 1 de mayo de 2017 no se proporcionarán nuevas mejoras ni se ofrecerá más soporte técnico de ingeniería o Adobe Expert Care.
