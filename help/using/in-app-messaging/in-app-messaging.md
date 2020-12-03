---
description: Cree y administre mensajes push y en la aplicación, y elabore informes sobre ellos.
keywords: mobile
seo-description: Cree y administre mensajes push y en la aplicación, y elabore informes sobre ellos.
seo-title: Mensajería
solution: Experience Cloud,Analytics
title: Mensajería
topic: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---


# Mensajería {#messaging}

Puede crear y administrar mensajes push y en la aplicación, y elaborar informes sobre ellos.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Si utiliza los SDK móviles de la Adobe Experience Platform con Adobe Launch, también **debe** instalar la extensión de Adobe Analytics Mobile Services para utilizar funciones como, por ejemplo, los enlaces de adquisición. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obtener información sobre el uso de mensajería push y mensajería en la aplicación con los SDK de Adobe Experience Platform, consulte [Configuración de mensajería push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) y [Configuración de mensajería en la aplicación](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## Mensajes en la aplicación {#section_8984F4568BC24D32A87429FFCB5184A6}

Los mensajes en la aplicación se entregan a los usuarios en tiempo real en función de sus acciones y características. Los mensajes se originan a partir de datos de Analytics de los que el SDK ya ha realizado un seguimiento.

Se admiten los siguientes tipos de mensajes:

* Personalizado y temático
* Pantalla completa
* Alertas nativas
* Notificaciones locales

Aquí tiene información adicional para ayudarle a comprender el funcionamiento de la mensajería en la aplicación:

* Los mensajes en la aplicación requieren la versión 4.2 o posteriores del SDK.
* Debe especificar quién tiene derechos de administrador de aplicaciones móviles.

   Estos derechos permiten acceder a los vínculos de adquisición y a los mensajes en la aplicación. Para obtener más información, consulte [Funciones y permisos](/help/using/gs/c-mob-roles-and-permissions.md).
* Después de aprobar un mensaje, este se publica automáticamente en la aplicación.
* El SDK presenta el mensaje a los usuarios cuando se cumplen los parámetros del mensaje, como características, activador y programación.
* Los mensajes pueden contener HTML personalizado o una imagen mediante una URL en línea.

   También se puede especificar una imagen alternativa o de copia de seguridad del paquete de aplicaciones para los mensajes que se activan sin conexión.
* Los mensajes activos y completados proporcionan informes sobre las vistas totales, tasa de pulsaciones, etc.
* Existen plantillas disponibles para mensajes personalizados con las que podrá crear fácilmente sus propios mensajes en la aplicación.

## Mensajes push {#section_90555A55BCE7427A90B1577E14BEF51B}

Los mensajes push se envían a los usuarios que han elegido recibir notificaciones. Puede dirigir dichos mensajes a los usuarios incluidos en segmentos de Analytics o en segmentos personalizados. Se pueden usar para lograr la participación de usuarios pasivos o transmitir información específica sobre la ubicación y la zona horaria, ya que los mensajes aparecen fuera de la aplicación.

Antes de configurar la mensajería push, consulte [Requisitos previos para habilitar la mensajería push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Después de realizar estas tareas, debe configurar la mensajería push en la configuración de la aplicación. Para obtener más información, consulte [Configuración de mensaje push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
