---
description: La extensión iOS le ayuda a recopilar datos de uso de las aplicaciones del Apple Watch (WatchOS 1), los widgets Today y Photo Editing, y otras aplicaciones de extensión de iOS.
seo-description: La extensión iOS le ayuda a recopilar datos de uso de las aplicaciones del Apple Watch (WatchOS 1), los widgets Today y Photo Editing, y otras aplicaciones de extensión de iOS.
seo-title: Implementación de extensiones iOS
solution: Experience Cloud,Analytics
title: Implementación de extensiones iOS
topic: Desarrollador e implementación
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Implementación de extensiones iOS {#ios-extension-implementation}

La extensión iOS le ayuda a recopilar datos de uso de las aplicaciones del Apple Watch (WatchOS 1), los widgets Today y Photo Editing, y otras aplicaciones de extensión de iOS.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recomendaciones para el uso del SDK para iOS en lugar de su propio wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Se recomienda encarecidamente que utilice el SDK para iOS en vez de su propio envoltorio o “wrapper”.

Apple proporciona un conjunto de API que permite a la aplicación Watch comunicarse con la aplicación contenedora enviándole solicitudes y recibiendo respuestas. Aunque se pueden enviar datos de seguimiento como un diccionario desde la aplicación Watch hasta la aplicación contenedora y, a continuación, llamar a cualquier método de seguimiento de la aplicación contenedora para enviar los datos, esta solución tiene algunas limitaciones.

En la mayoría de los casos, cuando un usuario utiliza la aplicación Watch, la aplicación contenedora se ejecuta en segundo plano y solo es seguro llamar a `TrackLocation`, `TrackActionInBackground` y `TrackBeacon`. El hecho de llamar a otros métodos de seguimiento interfiere con los datos del ciclo vital, por lo que solo debería utilizar estos tres métodos para enviar datos desde la aplicación Watch.

Utilice el SDK para iOS aunque estos tres métodos de seguimiento cumplan con sus requisitos, ya que el SDK para la aplicación Watch incluye todas las funciones de Mobile, excepto la mensajería en la aplicación.

## Primeros pasos {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Asegúrese de que tiene un proyecto con al menos los siguientes destinatarios:
>
>* Un destino para contener la aplicación.
>* Un destino para la extensión.
>



Si trabaja en una aplicación WatchKit, debería tener un tercer destino. Para obtener más información sobre el desarrollo de Apple Watch, consulte [Desarrollo de Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configurar la aplicación contenedora {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Complete los siguientes pasos en su proyecto Xcode:

1. Arrastre la carpeta AdobeMobileLibrary a su proyecto.
1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino de la aplicación contendora.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de la aplicación, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Abra la pestaña **[!UICONTROL Funcionalidades]** en el destino de la aplicación contenedora, habilite **[!UICONTROL Grupos de aplicaciones]** y agregue un nuevo grupo de aplicaciones (por ejemplo, `group.com.adobe.testAp`).

1. En el delegado de la aplicación, establezca el grupo de aplicaciones en `application:didFinishLaunchingWithOptions` antes de realizar ninguna interacción con la biblioteca de Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Confirme que la aplicación se compila sin errores inesperados.

## Configurar la extensión de {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino de la extensión.
1. En la ficha **[!UICONTROL Fases de compilación]** del destino de su extensión, expanda la sección **[!UICONTROL Vincular binario con bibliotecas]** y agregue las bibliotecas siguientes:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Abra la pestaña **[!UICONTROL Funcionalidades]** en el destino de la extensión, habilite **[!UICONTROL Grupos de aplicaciones]** y seleccione el grupo de aplicaciones que agregó en el paso 4 de *Configuración de la aplicación contenedora*, más atrás.

1. En InterfaceController, establezca el grupo de aplicaciones en `awakeWithContext:` antes de realizar cualquier otra interacción con la biblioteca de Adobe Mobile:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Confirme que la aplicación se compila sin errores inesperados.

## Notas adicionales {#section_21497E81231549CB9F164DEECFF5BA0D}

Información que debe recordar:

* Se ha agregado un valor de contexto adicional, `a.RunMode`, para indicar si los datos proceden de la aplicación contenedora o de la extensión:

   * `a.RunMode = Application`

      Este valor significa que la visita procede de la aplicación contendora.
   * `a.RunMode = Extension`

      Este valor significa que la visita procede de la extensión.

* Si actualiza desde una versión anterior del SDK, al iniciar la aplicación contenedora, Adobe migra automáticamente todos los valores predeterminados y los archivos en caché del usuario desde la carpeta de la aplicación contenedora hasta la carpeta compartida del grupo de aplicaciones.
* Si la aplicación contenedora no se llega a abrir, las visitas procedentes de la extensión se descartan.
* El número de versión y el de compilación deben ser los mismos en la aplicación contenedora y en la aplicación de extensión.
* En las aplicaciones de extensión iOS no se activa ninguna llamada de ciclo vital.

