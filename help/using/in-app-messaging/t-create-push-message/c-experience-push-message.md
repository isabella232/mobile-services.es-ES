---
description: Puede configurar opciones de experiencia para mensajes push y mensajes push enriquecidos, incluidas las opciones de nombre, texto del mensaje y destino. También puede configurar opciones avanzadas, incluidas las de carga útil y las opciones personalizadas de los dispositivos iOS.
keywords: móvil
seo-description: Puede configurar opciones de experiencia para mensajes push y mensajes push enriquecidos, incluidas las opciones de nombre, texto del mensaje y destino. También puede configurar opciones avanzadas, incluidas las de carga útil y las opciones personalizadas de los dispositivos iOS.
seo-title: Mensaje push de experiencia
solution: Marketing Cloud,Analytics
title: Mensaje push de experiencia
topic: Métricas
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: push message {#experience-push-message}

Puede configurar opciones de experiencia para mensajes push y mensajes push enriquecidos, incluidas las opciones de nombre, texto del mensaje y destino. También puede configurar opciones avanzadas, incluidas las de carga útil y las opciones personalizadas de los dispositivos iOS.

1. En la página Audiencia para un nuevo mensaje push, haga clic en **[!UICONTROL Experiencia]**.

   ![pantalla de mensaje push de experiencia](assets/experience-push-message.png)

1. Escriba el nombre del mensaje.
1. Rellene los campos siguientes de la sección **[!UICONTROL Mensaje]:**

   * **[!UICONTROL Contenido]**

      Especifique el texto del mensaje. Puede escribir 140 caracteres como máximo.

   * **[!UICONTROL URL de recursos multimedia]**

      Escriba la URL del archivo multimedia que va a usar en el mensaje de notificación push. Para conocer los requisitos para utilizar notificaciones push enriquecidas, consulte *Requisitos para notificaciones* push enriquecidas a continuación.

      >[!IMPORTANT]
      >
      >Para mostrar una imagen o un vídeo en una notificación push, recuerde lo siguiente:
      > * El dato `attachment-url` se gestiona en la carga útil push.
      > * La URL de recursos multimedia debe ser capaz de gestionar solicitudes de picos.


   * **[!UICONTROL Destino]**

      Seleccione un destino específico, como un vínculo web, profundo o híbrido, para enviar a los usuarios cuando pulsen en el mensaje. For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >When you use the * **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Solo se hace un seguimiento de los **[!UICONTROL vínculos profundos].**

## Requisitos para notificaciones push enriquecidas

Here are the requirements for sending rich push notifications:

* **Versiones admitidas**

   Las notificaciones push enriquecidas son compatibles con las siguientes versiones:
   * Android 4.1.0 o una versión posterior
   * iOS 10 o una versión posterior

      >[!IMPORTANT]
      >
      >Recuerde la información siguiente:
      >* Rich push messages sent to earlier versions will still be sent but only the text is displayed.
      >* En este momento no se ofrece compatibilidad de visualización.


* **Formatos de archivo**

   Estos son los formatos de archivo admitidos:
   * Imágenes: JPG y PNG
   * Animaciones (solo iOS): GIF
   * Vídeos (solo iOS): MP4

* **Formatos de URL**
   * Solo HTTPS

* **Tamaño**
   * Images must be in a 2:1 format, or they will be cropped.

Para obtener más información sobre cómo configurar notificaciones push enriquecidas, consulte los siguientes temas:

* [Receive Push Notifications in Android](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Receive Rich Push Notifications in iOS](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

To configure a push message on the Experience page:

1. (**Optional**) Click the **[!UICONTROL Show Advanced Options]** link to configure additional options:

   * **[!UICONTROL Carga útil: datos]**

      Proporcione una carga útil push personalizada en JSON que se enviará a la aplicación mediante una notificación push o local. El límite para Android e iOS es de 4 KB.

   * **[!UICONTROL Opciones de Apple: categoría]**

      Proporcione una categoría para las notificaciones push o locales. Para obtener más información, consulte [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) (Gestión del soporte para notificaciones de su aplicación) en la *biblioteca para desarrolladores de iOS*.

   * **[!UICONTROL Opciones de Apple: sonido]**

      Proporcione el nombre del archivo de sonido en el paquete de aplicaciones que se debe reproducir. Se establece si no se reproduce un sonido de alerta predeterminado. Para obtener más información, consulte [Managing Your App’s Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) (Gestión del soporte para notificaciones de su aplicación) en la *biblioteca para desarrolladores de iOS*.

   * **[!UICONTROL Opciones de Apple: contenido disponible]**

      Seleccione esta opción para que, cuando el mensaje llegue, iOS active la aplicación en segundo plano y le permita ejecutar código basado en la carga útil del mensaje. Para obtener más información, consulte la sección [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) (Servicio de producción de notificaciones push de Apple) en la *biblioteca para desarrolladores de iOS*.

1. (Opcional) Obtenga una vista previa del diseño del mensaje haciendo clic en los siguientes iconos:

   * **[!UICONTROL x Summary}**

      Oculta el panel de vista previa. Click preview to display the preview pane again.![](assets/icon_preview.png)

   * **[!UICONTROL Change the orientation]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). En el caso de los relojes, la orientación cambia de una esfera de reloj redonda a una cuadrada.

   * **[!UICONTROL Preview on a user's watch]**

      To preview your message as it will appear on a users's watches click watch icon.![](assets/icon_watch.png)

   * **[!UICONTROL Vista previa en el teléfono móvil de un usuario]**

      To preview your message as it will appear on a users's mobile phones click phone icon.![](assets/icon_phone.png)

   * **[!UICONTROL Vista previa en una tablet del usuario]**

      To preview your message in a user's tablet, click tablet icon.![](assets/icon_tablet.png)
   En la parte inferior del panel de vista previa, puede ver una descripción de la audiencia que seleccionó en el paso anterior.

1. (**Optional**) Click **[!UICONTROL Test]** to push your message to specified devices for testing purposes.
1. Seleccione el servicio y escriba los tokens push de por lo menos un dispositivo en el que desee insertar el mensaje.

   Especifique los tokens en una lista separada por comas para insertar el mensaje en más de un dispositivo.

1. Configurar the scheduling options for the message.

   For more information, see Schedule: push message.[](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md)
