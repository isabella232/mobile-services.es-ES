---
description: Configure las opciones de experiencia de los mensajes en la aplicación, incluido el tipo (pantalla completa, alerta o notificación) y las opciones de visualización, de texto y del botón.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Experience  Mensaje en la aplicación
topic-fix: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
exl-id: eeb1527d-c546-4951-9947-db810fdb8eee
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 100%

---

# Experience: Mensaje en la aplicación {#experience-in-app-message}

Configure las opciones de experiencia de los mensajes en la aplicación, incluido el tipo (pantalla completa, alerta o notificación) y las opciones de visualización, de texto y del botón.

1. En la aplicación, haga clic en **[!UICONTROL Mensajería]** > **[!UICONTROL Gestionar mensajes]** > **[!UICONTROL Crear mensaje]** > **[!UICONTROL Crear en la aplicación]**.
1. En la página Experiencia, escriba el nombre del mensaje.
1. Rellene los campos de la sección **[!UICONTROL Tipo]**:

   * **[!UICONTROL Tipo]** Seleccione el tipo de mensaje para su campaña de mensajes en la aplicación:

      * **[!UICONTROL Pantalla completa]**
      * **[!UICONTROL Alerta]**
      * **[!UICONTROL Notificación local]**
   * **[!UICONTROL Plantilla]**

      Personalice una plantilla de mensaje interactiva para el contenido.

      >[!TIP]
      >
      >Esta opción solo se muestra al seleccionar el tipo de mensaje **[!UICONTROL Pantalla completa]**.

   * **[!UICONTROL Personalizado]**

      Cargue el contenido HTML personalizado (solo pantalla completa). Debe proporcionar un vínculo de pulsación y un vínculo de cancelación.

      1. Haga clic en **[!UICONTROL Examinar]** y descargue un archivo HTML o arrastre un documento HTML a la ventana.
      1. Haga clic en **[!UICONTROL Descargar ejemplo]** para ver contenido HTML personalizado de ejemplo.

      >[!TIP]
      >
      >Esta opción solo se muestra al seleccionar el tipo de mensaje **[!FPantalla completa]**.



1. Rellene los campos de la sección **[!UICONTROL Visualización]**:

   * **[!UICONTROL Tema]**

   Seleccione el tema del mensaje.

   * **[!UICONTROL Diseño]**

      Seleccione el diseño de la aplicación en la pantalla del dispositivo.

   * **[!UICONTROL Dirección URL de imagen]**

      Dirección URL de una imagen. Si tiene problemas con el tamaño al utilizar la plantilla de pantalla completa, consulte *Mi imagen no se adapta exactamente al espacio proporcionado en la plantilla* en [Solucionar los problemas de la mensajería en la aplicación](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Imagen agrupada]**

      Ruta a una imagen en el paquete de código de la aplicación. Esta opción se utiliza cuando no hay ninguna imagen. O la imagen no está disponible. Puede no estar disponible si, por ejemplo, el dispositivo no tiene conexión. Si tiene problemas con el tamaño al utilizar la plantilla de pantalla completa, consulte *Mi imagen no se adapta exactamente al espacio proporcionado en la plantilla* en [Solucionar los problemas de la mensajería en la aplicación](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Rellene los campos de la sección **[!UICONTROL Texto]**:

   * **[!UICONTROL Header]**

      Escriba el texto del encabezado del mensaje.

   * **[!UICONTROL Contenido]**

      Escriba el texto del contenido del mensaje.

1. Rellene los campos de la sección **[!UICONTROL Botones]**:

   * **[!UICONTROL Botón Pulsación]**

      Etiqueta del botón **[!UICONTROL Pulsación]**. Un toque en este botón cuenta como una pulsación correcta. Se redirige al usuario al destino.

   * **[!UICONTROL Destino]**

      Seleccione un destino específico, como un vínculo web, profundo o híbrido, para enviar a los usuarios cuando pulsen en el mensaje. Dirección URL de redireccionamiento de una pulsación correcta.

      Esta dirección URL puede contener la siguiente información:

      * `{userId}`, que se sustituye por el identificador de usuario o se queda en blanco cuando este no se define.
      * `{trackingId}`, que se sustituye por la ayuda (se correlaciona con la cookie *s_vi*).
      * `{messageId}`, que se sustituye por el ID único del mensaje en la aplicación.
      * `{lifetimeValue}`, que se sustituye por el valor de duración o por 0 si este no existe.

      Este es un ejemplo de seguimiento del identificador de usuario: `https://www.mysite.com?uid={userId}`.

      Si la URL de pulsación utiliza `https://` o `https://`, se abrirá en el explorador del dispositivo fuera de la aplicación. De lo contrario, cada plataforma admite esquemas que le permiten abrir la aplicación o hacer referencia a ella si esta se ha desarrollado para admitir el esquema personalizado.

      >[!TIP]
      >
      >Cuando se usan los tipos de destino **[!UICONTROL Vínculo web]** o **[!UICONTROL Vínculo personalizado]**, no se realiza un seguimiento del tipo de destino. Solo se hace un seguimiento de los **[!UICONTROL vínculos profundos.]** Para obtener más información, consulte [Destinos](/help/using/acquisition-main/c-create-destinations.md).


1. (Opcional) Obtenga una vista previa del diseño del mensaje haciendo clic en los siguientes iconos:

   * **[!UICONTROL Resumen]** oculta el panel de vista previa.

      Haga clic en ![vista previa](assets/icon_preview.png) para volver a mostrar el panel de vista previa.

   * **[!UICONTROL Cambiar la orientación]**

      Para cambiar la orientación de la vista previa del modo vertical al horizontal, haga clic en ![orientación](assets/icon_orientation.png). En el caso de los relojes, la orientación cambia de una esfera de reloj redonda a una cuadrada.

   * **[!UICONTROL Vista previa en el reloj de un usuario]**

      Para obtener una vista previa del mensaje tal como aparecerá en el reloj de un usuario, haga clic en el ![icono del reloj](assets/icon_watch.png).

   * **[!UICONTROL Vista previa en el teléfono móvil de un usuario]**

      Para obtener una vista previa del mensaje tal como aparecerá en el teléfono móvil de un usuario, haga clic en el ![icono del teléfono móvil](assets/icon_phone.png).

   * **[!UICONTROL Vista previa en la tableta del usuario]**

      Para obtener una vista previa del mensaje en la tableta del usuario, haga clic en el ![icono de la tableta](assets/icon_tablet.png).

      En la parte inferior del panel de vista previa, puede ver una descripción de la audiencia que seleccionó en el paso anterior. También puede ver una descripción de la audiencia seleccionada en el paso anterior en la parte inferior del panel de vista previa.

1. Configure las [Opciones de programación](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
