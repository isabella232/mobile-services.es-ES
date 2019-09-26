---
description: Configure las opciones de experiencia de los mensajes en la aplicación, incluido el tipo (pantalla completa, alerta o notificación) y las opciones de visualización, de texto y del botón.
keywords: móvil
seo-description: Configure las opciones de experiencia de los mensajes en la aplicación, incluido el tipo (pantalla completa, alerta o notificación) y las opciones de visualización, de texto y del botón.
seo-title: Mensaje de experiencia en la aplicación
solution: Marketing Cloud,Analytics
title: Mensaje de experiencia en la aplicación
topic: Métricas
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Configure las opciones de experiencia de los mensajes en la aplicación, incluido el tipo (pantalla completa, alerta o notificación) y las opciones de visualización, de texto y del botón.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. En la página Experiencia, escriba el nombre del mensaje.
1. Rellene los campos de la sección **[!UICONTROL Tipo]:**

   * **[!UICONTROL Type
Select the message type for your in-app message campaign:]**

      * **[!UICONTROL Pantalla completa]**
      * **[!UICONTROL Alerta]**
      * **[!UICONTROL Notificación local]**
   * **[!UICONTROL Plantilla]**

      Personalice una plantilla de mensaje interactiva para el contenido.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL Personalizado]**

      Cargue el contenido HTML personalizado (solo pantalla completa). Tiene que proporcionar un vínculo de pulsación y otro de cancelación.

      1. Haga clic en **[!UICONTROL Examinar]y descargue un archivo HTML o arrastre un documento HTML a la ventana.**
      1. Haga clic en **[!UICONTROL Descargar ejemplo]para ver contenido HTML personalizado de ejemplo.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. Rellene los campos de la sección **[!UICONTROL Visualización]:**

   * **[!UICONTROL Tema]**
   Seleccione el tema del mensaje.

   * **[!UICONTROL Diseño]**

      Seleccione el diseño de la aplicación en la pantalla del dispositivo.

   * **[!UICONTROL Dirección URL de imagen]**

      Dirección URL de una imagen. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Imagen agrupada]**

      Ruta a una imagen presente en el paquete de código de la aplicación. Esta opción se usa cuando no hay ninguna imagen o la que hay no está disponible. Puede no estar disponible si, por ejemplo, el dispositivo no tiene conexión. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Rellene los campos de la sección **[!UICONTROL Texto]:**

   * **[!UICONTROL Encabezado]**

      Escriba el texto del encabezado del mensaje.

   * **[!UICONTROL Contenido]**

      Escriba el texto del contenido del mensaje.

1. Rellene los campos de la sección **[!UICONTROL Botones]:**

   * **[!UICONTROL Botón Pulsación]**

      Etiqueta del botón **[!UICONTROL Pulsación].** Tocar este botón cuenta como una pulsación correcta. El usuario se redirige al destino.

   * **[!UICONTROL Destino]**

      Seleccione un destino específico, como un vínculo web, profundo o híbrido, para enviar a los usuarios cuando pulsen en el mensaje. Dirección URL de redireccionamiento de una pulsación correcta.

      Esta dirección URL puede contener la siguiente información:

      * `{userId}`, que se sustituye por el identificador de usuario o se queda en blanco cuando este no se define.
      * `{trackingId}`, que se sustituye por la ayuda (se correlaciona con *la cookie s_vi* ).
      * `{messageId}`, que se sustituye por el identificador único del mensaje en la aplicación.
      * `{lifetimeValue}`, que se sustituye por el valor de duración o por 0 si este no existe.
      Este es un ejemplo de seguimiento del identificador de usuario: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. De lo contrario, cada plataforma admite esquemas que le permiten abrir la aplicación o hacer referencia a ella si esta se ha desarrollado para admitir el esquema personalizado.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Solo se hace un seguimiento de los **[!UICONTROL vínculos profundos.]** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Opcional) Obtenga una vista previa del diseño del mensaje haciendo clic en los siguientes iconos:

   * **[!UICONTROL El resumen]** oculta el panel de vista previa.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Cambiar la orientación]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). En el caso de los relojes, la orientación cambia de una cara redonda a una cuadrada.

   * **[!UICONTROL Vista previa en el reloj de un usuario]**

      To preview your message as it will appear on a user's watch, click watch icon.![](assets/icon_watch.png)

   * **[!UICONTROL Preview on a user's mobile phone]**

      To preview your message as it will appear on a users's mobile phone click phone icon.![](assets/icon_phone.png)

   * **[!UICONTROL Preview on a user's tablet]**

      To preview your message in a user's tablet, click tablet icon.![](assets/icon_tablet.png)

      En la parte inferior del panel de vista previa, puede ver una descripción de la audiencia que seleccionó en el paso anterior. También puede ver una descripción de la audiencia seleccionada en el paso anterior en la parte inferior del panel de vista previa.

1. Configure Schedule options.[](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)
