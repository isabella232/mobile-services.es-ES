---
description: Esta información le ayuda a implementar Apple TV con tvOS.
seo-description: Esta información le ayuda a implementar Apple TV con tvOS.
seo-title: Implementación de Apple TV con tvOS
solution: Experience Cloud,Analytics
title: Implementación de Apple TV con tvOS
topic: Desarrollador e implementación
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Implementación de Apple TV con tvOS {#apple-tv-implementation-with-tvos}

Esta información le ayuda a implementar Apple TV con tvOS.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Información general

Gracias a Apple TV, ahora puede crear aplicaciones para utilizarlas en el entorno nativo de tvOS. Puede crear una aplicación nativa utilizando varios de los marcos disponibles en iOS, o bien mediante plantillas XML y JavaScript.

>[!TIP]
>
>La compatibilidad con tvOS está disponible a partir de la versión 4.7.0 de `AdobeMobileLibrary`.

## Primeros pasos {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Se supone que su proyecto tiene como destino una aplicación para Apple TV y tvOS. Para obtener más información, consulte [tvOS](https://developer.apple.com/tvos/documentation/).

## Configuración de una aplicación nativa para tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Complete los siguientes pasos en su proyecto Xcode:

1. Arrastre la carpeta AdobeMobileLibrary a su proyecto.
1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación de tvOS, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Para obtener más información, consulte la documentación sobre iOS en [iOS](https://developer.apple.com/ios/resources/).

## Configuración de una aplicación TVML/TVJS para tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Arrastre la carpeta `AdobeMobileLibrary` a su proyecto.
1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su aplicación de tvOS, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importe el SDK en el archivo de implementación de su clase `TVApplicationControllerDelegate`.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. En el método `application:didFinishLaunchWithOptions:` de su clase `TVApplicationControllerDelegate`, pase el objeto `TVApplicationController` al SDK con el método `installTVMLHooks:`.

   El SDK de Adobe necesita acceder al `TVApplicationController` de la aplicación para registrarse a sí mismo en el JSContext de la aplicación. Este paso le permite realizar una llamada a los métodos nativos en el SDK de Adobe desde sus archivos JavaScript.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. En sus archivos JavaScript, utilice el objeto `ADBMobile` para acceder a los métodos nativos del SDK de Adobe.

   Para obtener un listado completo de los métodos disponibles, consulte [Métodos TVJS](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

