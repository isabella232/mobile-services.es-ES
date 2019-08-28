---
description: Cree y administre mensajes push y en la aplicación, y elabore informes sobre ellos.
keywords: móvil
seo-description: Cree y administre mensajes push y en la aplicación, y elabore informes sobre ellos.
seo-title: Mensajería
solution: Marketing Cloud, Analytics
title: Mensajería
topic: Métricas
uuid: e 32 d 3 e 35-2 d 09-4 ddf -8919-75 dc 895 abcb 3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Mensajería {#messaging}

Puede crear, administrar e informar sobre mensajes push y en la aplicación.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obtener información sobre el uso de mensajería push y mensajería en la aplicación con los SDK de Adobe Experience Platform, consulte [Configuración de mensajería push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) y [Configuración de mensajería en la aplicación](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## Mensajes en la aplicación {#section_8984F4568BC24D32A87429FFCB5184A6}

Los mensajes en la aplicación se entregan a los usuarios en tiempo real en función de sus acciones y características. Los mensajes se originan a partir de datos de Analytics de los que el SDK ya ha realizado un seguimiento.

Los tipos de mensajes compatibles son los siguientes:

* Personalizados y con tema
* Pantalla completa
* Alertas nativas
* Notificaciones locales

Para ayudarle a comprender cómo funciona la mensajería en la aplicación, aquí tiene información adicional:

* Los mensajes en la aplicación requieren la versión 4.2 o posterior del SDK.
* Debe especificar quién cuenta con derechos de administrador de aplicaciones móviles.

   Estos derechos permiten el acceso a vínculos de adquisición y mensajes en la aplicación. Para obtener más información, consulte [Funciones y permisos](/help/using/gs/c-mob-roles-and-permissions.md).
* Una vez que se aprueba un mensaje, se publica automáticamente en la aplicación.
* El SDK presenta el mensaje a los usuarios cuando los parámetros del mensaje, como características, activador y programa, se cumplen.
* Los mensajes pueden contener HTML personalizado o una imagen con una URL en línea.

   También se puede especificar una imagen alternativa o de copia de seguridad desde el paquete de aplicación para los mensajes que se activan cuando no hay conexión.
* Los mensajes activos y completados proporcionan informes sobre las vistas totales, tasa de pulsaciones, etc.
* Existen plantillas disponibles para mensajes personalizados con las que podrá crear fácilmente sus propios mensajes en la aplicación.

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

Los mensajes push se envían a los usuarios que han elegido recibir notificaciones. Puede dirigir dichos mensajes a los usuarios incluidos en segmentos de Analytics o en segmentos personalizados. Se pueden usar para lograr la participación de usuarios pasivos o transmitir información específica sobre la ubicación y la zona horaria, ya que los mensajes aparecen fuera de la aplicación.

Antes de configurar la mensajería push, consulte [Requisitos previos para activar la mensajería push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Una vez que haya realizado estas tareas, debe configurar la mensajería push en la configuración de la aplicación. Para obtener más información, consulte [Configurar la mensajería push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).