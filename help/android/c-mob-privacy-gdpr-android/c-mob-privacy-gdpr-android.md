---
description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-title: Información sobre Privacidad y Reglamento General de Protección de Datos
title: Información sobre Privacidad y Reglamento General de Protección de Datos
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: ht
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Información sobre Privacidad y Reglamento General de Protección de Datos {#privacy-and-general-data-protection-regulation}

Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Información general

>[!IMPORTANT]
>
>El RGPD **solo** es compatible a partir de la versión 4.16.0 o posterior de SDK de Mobile.

Cuando proporciona software y servicios a una empresa, Adobe actúa como procesador de datos de cualquier dato personal que procese y almacene como parte de la provisión de dichos servicios. Como procesador de datos, Adobe procesa los datos personales de acuerdo con los permisos e instrucciones que su empresa proporcione (y que pueden establecerse, por ejemplo, en el acuerdo entre su empresa y Adobe).

Como controlador de datos, usted puede utilizar los SDK de Adobe Mobile Services para procesar las solicitudes de recuperación y eliminación que sus aplicaciones móviles realicen en virtud del RGPD.

Para las partes de sus aplicaciones móviles correspondientes al SDK de Adobe Mobile, puede utilizar las opciones de configuración y los métodos siguientes:

* Para recuperar datos de los SDK y enviarlos a sus servidores, utilice el método `getAllIdentifiersAsync`.

   Para obtener más información, consulte [Recuperación de identificadores almacenados](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Para establecer su estado de inclusión y ayudarle con una solicitud de eliminación de datos en virtud del RGPD, utilice la siguiente configuración:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obtener más información, consulte [Configuración del estado de exclusión del usuario](/help/android/c-mob-privacy-gdpr-android/privacy.md).