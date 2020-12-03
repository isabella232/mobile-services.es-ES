---
description: Puede configurar el activador de mensajes en la aplicación para que este sea el ID del mensaje push que se envía cuando un usuario abre la aplicación mediante el mensaje push.
seo-description: Puede configurar el activador de mensajes en la aplicación para que este sea el ID del mensaje push que se envía cuando un usuario abre la aplicación mediante el mensaje push.
seo-title: Activar un mensaje en la aplicación cuando la aplicación se abre desde un mensaje push
title: Activar un mensaje en la aplicación cuando la aplicación se abre desde un mensaje push
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 59%

---


# Activador de mensajes en la aplicación al abrirla mediante un mensaje push{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

Puede configurar el activador de mensajes en la aplicación para que este sea el ID del mensaje push que se envía cuando un usuario abre la aplicación mediante el mensaje push.

1. Obtenga el ID del mensaje push que se enviará al usuario.

   Puede encontrar el ID del mensaje push en la URL durante el flujo de trabajo de creación de mensajes.

   Vea el siguiente ejemplo:

   ![](assets/brandon_task1.png)

1. Guarde y active el mensaje en la aplicación con el siguiente activador:

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >El ID del mensaje push corresponde al ID que utilizó en el paso 1.

   El activador debe añadirse manualmente, ya que no está disponible en la lista desplegable **[!UICONTROL Activador]**.

   ![](assets/brandon_task2.png)

1. Guarde y envíe el mensaje push que tenga el ID de push del paso 1.
1. Haga clic en el mensaje push para abrir la aplicación y verificar que el mensaje en la aplicación se muestre al abrirla.

   Mientras realiza la prueba, recuerde la siguiente información:

   * Después de guardar el mensaje en la aplicación, el archivo de configuración alojado tarda unos 45 segundos en actualizarse con el nuevo mensaje.
   * La aplicación busca actualizaciones de archivos de configuración (el nuevo mensaje en la aplicación) cuando hay un **nuevo** inicio, por lo que debe asegurarse de que la aplicación está activando un nuevo inicio cuando se hace clic en el mensaje push.

   Esto generalmente significa que debe asegurarse de que se ha agotado el tiempo de espera de sesión. El tiempo de espera predeterminado es de 5 minutos.

