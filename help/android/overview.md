---
description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
keywords: android;library;mobile;sdk
seo-description: El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.
seo-title: SDK para Android 4.x para soluciones de Experience Cloud
solution: Experience Cloud,Analytics
title: SDK para Android 4.x para soluciones de Experience Cloud
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---


# SDK para Android 4.x para soluciones de Experience Cloud {#android-sdk-x-for-experience-cloud-solutions}

El SDK para Android 4.x para soluciones de Experience Cloud le permite realizar mediciones de aplicaciones Android nativas, enviar contenido de destino en una aplicación, y aprovechar y recopilar datos de audiencias mediante la Gestión de público.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>El SKU del complemento de marketing móvil de Adobe Analytics es necesario para habilitar el acceso de Mobile Services a las funciones de adquisición móvil, vinculación profunda, geolocalización y mensajería móvil. Para obtener más información, contacte con el administrador de éxito de Adobe.

>[!IMPORTANT]
>
>Aunque puede configurar funciones en la interfaz de usuario, estas no funcionarán hasta que descargue el archivo de configuración generado y lo agregue al SDK. Para obtener información sobre la descarga y configuración de los SDK, consulte [Implementación principal y ciclo vital](/help/android/getting-started/dev-qs.md).

Los SDK admiten las siguientes versiones de Android:

* La versión 4.6.0 o anteriores admiten Android 2.2 (API 8)-Android 5.1.1 (API 22)
* La versión 4.6.1 o posteriores admiten Android 2.3 (API 9) o posterior

Información que debe recordar:

* En la versión 4.2 y posterior, todas las visitas se envían ahora mediante HTTP POST.

   Esto no afecta a los datos recopilados o comunicados, pero para ver las visitas debe utilizar un analizador de paquetes que admita la inspección de datos POST.

* Si está actualizando desde una versión previa, consulte la [Guía de migración a 4.x](/help/android/getting-started/migration-v3.md).

## Documentación del usuario de Adobe Mobile {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services proporciona una interfaz de usuario que aúna las capacidades de marketing móvil para aplicaciones móviles desde Adobe Experience Cloud. Para obtener más información acerca de la interfaz de usuario de y leer la documentación del usuario, consulte [Adobe Mobile Services](https://docs.adobe.com/content/help/es-ES/mobile-services/using/home.html).

## Notas de la versión {#section_F8181DC052D44DD2A99AB40A41F6792C}

Para obtener la información más reciente sobre las versiones de Experience Cloud, consulte [Notas de la versión de Experience Cloud](https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html).

## Uso de Bloodhound

>[!IMPORTANT]
>
>Adobe Bloodhound expiró el **30 de abril de 2017**. Desde el 1 de mayo de 2017 no se proporcionarán nuevas mejoras ni se ofrecerá más soporte técnico de ingeniería o Adobe Expert Care.
