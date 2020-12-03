---
description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-title: Información sobre Privacidad y Reglamento General de Protección de Datos
title: Información sobre Privacidad y Reglamento General de Protección de Datos
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 78%

---


# Información sobre Privacidad y Reglamento General de Protección de Datos {#privacy-and-general-data-protection-regulation}

Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Información general

>[!IMPORTANT]
>
>El RGPD **solo** es compatible a partir de la versión 4.16.0 o posterior de SDK de Mobile.

Cuando Adobe proporciona software y servicios a una empresa, Adobe actúa como procesador de datos para cualquier dato personal que procesa y almacena como parte de la prestación de estos servicios. Como procesador de datos, Adobe procesa los datos personales de acuerdo con el permiso e instrucciones de su compañía (por ejemplo, según lo establecido en su acuerdo con Adobe).

Como controlador de datos, puede utilizar los SDK de Adobe Mobile Services para admitir solicitudes de recuperación y eliminación de solicitudes del RGPD de sus aplicaciones móviles.

Para las partes de sus aplicaciones móviles correspondientes al SDK de Adobe Mobile, puede utilizar las opciones de configuración y los métodos siguientes:

* Para recuperar datos de los SDK y enviarlos a sus servidores, utilice el método `getAllIdentifiersAsync`.

   Para obtener más información, consulte [Recuperación de identificadores almacenados](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Para establecer su estado de inclusión y ayudarle con una solicitud de eliminación de datos en virtud del RGPD, utilice la siguiente configuración:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obtener más información, consulte [Configuración del estado de exclusión del usuario](/help/android/c-mob-privacy-gdpr-android/privacy.md).