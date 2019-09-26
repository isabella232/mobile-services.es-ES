---
description: Los SDK de Mobile de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-description: Los SDK de Mobile de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-title: Información general sobre el Reglamento general de protección de datos y privacidad
title: Información general sobre el Reglamento general de protección de datos y privacidad
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Los SDK de Mobile de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.

## Nueva versión del SDK de Adobe Experience Platform Mobile

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Información general

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Cuando proporciona software y servicios a una empresa, Adobe actúa como procesador de datos de cualquier dato personal que procese y almacene como parte de la provisión de dichos servicios. Como procesador de datos, Adobe procesa los datos personales de acuerdo con los permisos e instrucciones que su empresa proporcione (y que pueden establecerse, por ejemplo, en el acuerdo entre su empresa y Adobe).

Como controlador de datos, usted puede utilizar los SDK de Adobe Mobile Services para procesar las solicitudes de recuperación y eliminación que sus aplicaciones móviles realicen en virtud del RGPD.

Para las partes de sus aplicaciones móviles correspondientes al SDK de Adobe Mobile, puede utilizar las opciones de configuración y los métodos siguientes:

* Para recuperar datos de los SDK y enviarlos a sus servidores, utilice el método `getAllIdentifiersAsync`.

   Para obtener más información, consulte [Recuperación de identificadores](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)almacenados.

* Para establecer su estado de inclusión y ayudarle con una solicitud de eliminación de datos en virtud del RGPD, utilice la siguiente configuración:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obtener más información, consulte [Configuración del estado](/help/android/c-mob-privacy-gdpr-android/privacy.md)de opción del usuario.