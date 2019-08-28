---
description: Esta información le ayuda a implementar Apple TV con tvOS.
seo-description: Esta información le ayuda a implementar Apple TV con tvOS.
seo-title: Implementación de Apple TV con tvOS
solution: Marketing Cloud, Analytics
title: Implementación de Apple TV con tvOS
topic: Desarrollador e implementación
uuid: d 1571 ea 2-a 5 de -4 b 96-a 527-72 abbf 51 fab 8
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

Esta información le ayuda a implementar Apple TV con tvOS.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Gracias a Apple TV, ahora puede crear aplicaciones para utilizarlas en el entorno nativo de tvOS. Puede crear una aplicación nativa utilizando varios de los marcos disponibles en iOS, o bien mediante plantillas XML y JavaScript.

>[!TIP]
>
>La compatibilidad de tvos está disponible a partir `AdobeMobileLibrary` de la versión 4.7.0.

## Primeros pasos {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Supongamos que su proyecto tiene un destino que es una aplicación de Apple TV dirigida a tvos. Para obtener más información, consulte [tvOS](https://developer.apple.com/tvos/documentation/).

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Complete los siguientes pasos en su proyecto Xcode:

1. Arrastre la carpeta AdobeMobileLibrary a su proyecto.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación de tvOS, expanda la sección **Vincular binario con bibliotecas]y agregue las bibliotecas siguientes:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Para obtener más información, consulte la documentación sobre iOS en [iOS](https://developer.apple.com/ios/resources/).

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Arrastre la carpeta `AdobeMobileLibrary` a su proyecto.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación de tvOS, expanda la sección **Vincular binario con bibliotecas]y agregue las bibliotecas siguientes:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importe el SDK en el archivo de implementación de su clase `TVApplicationControllerDelegate`.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   El SDK de Adobe necesita acceder al `TVApplicationController` de la aplicación para registrarse a sí mismo en el JSContext de la aplicación. Este paso le permite realizar una llamada a los métodos nativos en el SDK de Adobe desde sus archivos JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. En sus archivos JavaScript, utilice el objeto `ADBMobile` para acceder a los métodos nativos del SDK de Adobe.

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

