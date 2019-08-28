---
description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
keywords: android; library; mobile; sdk
seo-description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
seo-title: SDK para Android 4.x para soluciones de Experience Cloud
solution: Marketing Cloud, Analytics
title: SDK para Android 4.x para soluciones de Experience Cloud
topic: Desarrollador e implementación
uuid: 56 f 1 ff 41-0365-41 dd-bdde -245 c 823 dff 07
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.

>[!IMPORTANT]
>
>El SKU de Adobe Analytics Mobile Marketing Add-on es necesario para permitir el acceso de Mobile Services a la adquisición móvil, vinculación profunda, geolocalización y capacidades de mensajería móvil. Para obtener más información, póngase en contacto con su Adobe CSM.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

>[!IMPORTANT]
>
>En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

>[!IMPORTANT]
>
>Aunque puede configurar funciones en la interfaz de usuario, estas funciones no funcionarán hasta que descargue el archivo de configuración generado y agregue este archivo al SDK. Para obtener información sobre cómo descargar y configurar los SDK, consulte [Implementación principal y Ciclo vital](/help/android/getting-started/dev-qs.md).

Los SDK admiten las siguientes versiones de Android:

* Versión 4.6.0 y versiones anteriores admiten Android 2.2 (API 8) - Android 5.1.1 (API 22)
* Versión 4.6.1 y versiones posteriores admiten Android 2.3 (API 9) o posterior

Información que debe recordar:

* En la versión 4.2 o posterior, todas las visitas se envían ahora mediante HTTP POST.

   Esto no afecta a los datos recopilados o comunicados, pero es necesario utilizar un analizador de paquetes que admita la inspección de datos POST para ver las visitas.

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
