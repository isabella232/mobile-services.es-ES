---
description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
keywords: android;biblioteca;móvil;sdk
seo-description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
seo-title: SDK para Android 4.x para soluciones de Experience Cloud
solution: Marketing Cloud,Analytics
title: SDK para Android 4.x para soluciones de Experience Cloud
topic: Desarrollador e implementación
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.

## Nueva versión del SDK de Adobe Experience Platform Mobile

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>El SKU del complemento de marketing móvil de Adobe Analytics es necesario para habilitar el acceso de Mobile Services a las funciones de adquisición móvil, vinculación profunda, geolocalización y mensajería móvil. Para obtener más información, póngase en contacto con el CSM de Adobe.

>[!IMPORTANT]
>
>Aunque puede configurar funciones en la interfaz de usuario, estas funciones no funcionarán hasta que descargue el archivo de configuración generado y agregue este archivo al SDK. Para obtener información sobre la descarga y configuración de los SDK, consulte Implementación [principal y ciclo vital](/help/android/getting-started/dev-qs.md).

Los SDK admiten las siguientes versiones de Android:

* Versión 4.6.0 y versiones anteriores admiten Android 2.2 (API 8) - Android 5.1.1 (API 22)
* Versión 4.6.1 y versiones posteriores admiten Android 2.3 (API 9) o posterior

Información que debe recordar:

* En la versión 4.2 o posterior, todas las visitas se envían ahora mediante HTTP POST.

   Esto no afecta a los datos recopilados o notificados, pero debe utilizar un analizador de paquetes que admita la inspección de datos POST para ver las visitas.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services proporciona una interfaz de usuario que aúna las capacidades de marketing móvil para aplicaciones móviles desde Adobe Experience Cloud. Para obtener más información acerca de la interfaz de usuario y leer la documentación del usuario, consulte [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/).

## Notas de la versión {#section_F8181DC052D44DD2A99AB40A41F6792C}

Para obtener la información más reciente sobre las versiones de Experience Cloud, consulte [Notas de la versión de Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

## Uso de Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Desde el 1 de mayo de 2017 no se proporcionarán nuevas mejoras ni se ofrecerá más soporte técnico de ingeniería o Adobe Expert Care.
