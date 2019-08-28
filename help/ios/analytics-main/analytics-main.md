---
description: Esta información le ayuda a utilizar el SDK para iOS con Adobe Analytics.
seo-description: Esta información le ayuda a utilizar el SDK para iOS con Adobe Analytics.
seo-title: Información general de Analytics
solution: Marketing Cloud, Analytics
title: Información general de Analytics
topic: Desarrollador e implementación
uuid: 8 c 7 fb 76 a-be 0 b -4465-8151-ece 7 bad 11 b 55
translation-type: tm+mt
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Información general de Analytics {#analytics}

La información de esta sección le ayuda a utilizar el SDK para iOS con Adobe Analytics.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

## Generación de identificadores de seguimiento de Analytics

En los SDK, los identificadores se utilizan para realizar seguimientos de los usuarios. Esta es la jerarquía de identificadores:

1. Identificador de visitante personalizado (VID)
2. Identificador de seguimiento de Analytics (AID)
3. Identificador de Experience Cloud (MID)

>[!TIP]
>
>Las siglas correctas para el identificador de Experience Cloud son ECID. Aunque los SDK todavía usan MID, es el acrónimo antiguo.
El SDK genera el AID, que a veces también se denomina Identificador de seguimiento, cuando la aplicación no está configurada para utilizar una MID. El valor persiste entre inicios y actualizaciones de aplicaciones en `NSUserDefaults`. Si el usuario elimina la aplicación de su dispositivo y luego la reinstala, o si el desarrollador de la aplicación elimina `NSUserDefaults`, el SDK genera un nuevo identificador. Este proceso da como resultado un nuevo usuario en los informes de Analytics.

Para los usuarios de una aplicación que introduce un asistente de servicios de identidad (MID), los valores AID existentes se envían con los resultados de Analytics, y el resultado de Analytics contiene un AID y un MID. Para los nuevos usuarios de una aplicación con un asistente de servicios de identidad, las solicitudes de análisis contienen solo una MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
