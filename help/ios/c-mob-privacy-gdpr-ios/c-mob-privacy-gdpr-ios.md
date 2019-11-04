---
description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-description: Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.
seo-title: Reglamento general de protección de datos
title: Reglamento general de protección de datos
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: ht
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Reglamento general de protección de datos {#privacy-and-general-data-protection-regulation}

Los SDK móviles de Experience Cloud ofrecen API preparadas para el Reglamento general de protección de datos (RGPD) para los controladores, lo que permite a los usuarios recuperar identidades almacenadas de forma local y establecer indicadores de estado de inclusión para la recopilación y transmisión de datos.

>[!IMPORTANT]
>
>El RGPD **solo** es compatible a partir de la versión 4.16.0 o posterior de SDK de Mobile.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Información general

Cuando proporciona software y servicios a una empresa, Adobe actúa como procesador de datos de cualquier dato personal que procese y almacene como parte de la provisión de dichos servicios. Como procesador de datos, Adobe procesa los datos personales de acuerdo con los permisos e instrucciones que su empresa proporcione (y que pueden establecerse, por ejemplo, en el acuerdo entre su empresa y Adobe).

Como controlador de datos, usted puede utilizar los SDK de Adobe Mobile Services para procesar las solicitudes de recuperación y eliminación que sus aplicaciones móviles realicen en virtud del RGPD.

Para las partes de sus aplicaciones móviles correspondientes al SDK de Adobe Mobile, puede utilizar las opciones de configuración y los métodos siguientes:

* Para recuperar datos de los SDK y enviarlos a sus servidores, utilice el método `getAllIdentifiersAsync`.

   Para obtener más información, consulte [Recuperación de identificadores almacenados](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Para establecer su estado de inclusión y ayudarle con una solicitud de eliminación de datos en virtud del RGPD, utilice la siguiente configuración:

   * `privacyDefault`
   * `setPrivacyStatus`
   Para obtener más información, consulte [Configuración del estado de exclusión del usuario](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Información adicional {#section_7C7124C50D85469C8C8714533FB1A37D}

* Para obtener más información sobre el RGPD, consulte [RGPD y tu negocio](https://www.adobe.com/es/privacy/general-data-protection-regulation.html).
* Para ver la documentación de la API de RGPD, vaya a la [API de Reglamento general de protección de datos](https://adobe.io/apis/cloudplatform/gdpr.html).

