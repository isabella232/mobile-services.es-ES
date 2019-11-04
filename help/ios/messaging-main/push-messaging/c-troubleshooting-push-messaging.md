---
description: Esta información le ayuda a solucionar problemas de la mensajería push.
keywords: móvil
seo-description: Esta información le ayuda a solucionar problemas de la mensajería push.
seo-title: Resolución de problemas de mensajería push
solution: Experience Cloud,Analytics
title: Resolución de problemas de mensajería push
topic: Métricas
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Resolución de problemas de mensajería push {#troubleshooting-push-messaging}

Esta información le ayuda a solucionar problemas de la mensajería push.

## ¿Por qué a veces hay retrasos en el envío de mensajes push?

Los siguientes tipos de retraso podrían estar asociados con los mensajes push de Mobile Services:

* **Espera de visitas de Analytics**

   Todos los grupos de informes tienen una configuración para determinar cuándo se deben procesar las visitas de Analytics entrantes. El valor predeterminado es una hora, a cada hora en punto. El procesamiento en sí de las visitas de Analytics puede tardar hasta 30 minutos, aunque suele completarse en 15-20 minutos.

   Por ejemplo, supongamos que un grupo de informes procesa las visitas cada hora. Si tiene en cuenta el tiempo de procesamiento de un máximo de 30 minutos, una visita entrante puede tardar hasta 90 minutos en estar disponible para un mensaje push. Si un usuario inicia la aplicación a las 9:01, la visita se mostraría en la interfaz de usuario de Mobile Services como un nuevo usuario único entre las 10:15 y las 10:30.

* **Espera del servicio push**

   Puede que el servicio push (APNS o GCM) no envíe el mensaje inmediatamente. Aunque no es frecuente, se han visto retrasos de 5-10 minutos. En la página Mensajes puede comprobar que el mensaje push se ha enviado al servicio push al hacer clic en el vínculo Ver del mensaje. En el informe, el número de envíos correctos al servicio push se indica en la columna Publicado.

   >[!TIP]
   >
   >Los servicios push no garantizan el envío de un mensaje. Para obtener más información acerca de la fiabilidad de los servicios, consulte la documentación apropiada:
   >
   >* **APNS**: [calidad de servicio](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [duración de un mensaje](https://developers.google.com/cloud-messaging/concept-options)


## ¿Cómo renuevo mi certificado de servicio push de Apple?

Para enviar mensajes push se requiere un certificado de servicio push válido. Mobile Services le avisará cuando su certificado esté caducado o a punto de caducar. Si recibe esta notificación, complete los siguientes pasos para renovar su certificado:

1. Haga clic en **[!UICONTROL Administrar configuración de aplicación]**.
2. Para eliminar el certificado actual, desplácese hasta **[!UICONTROL Servicios push]** y haga clic en **[!UICONTROL Eliminar]**.
3. Configure y pruebe el nuevo certificado.

   Para obtener más información, consulte [Requisitos previos para habilitar la mensajería push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

4. Haga clic en **[!UICONTROL Guardar]**.

## ¿Por qué no puedo ver mis mensajes push en un simulador iOS?

Los simuladores iOS no son compatibles con la mensajería push.
