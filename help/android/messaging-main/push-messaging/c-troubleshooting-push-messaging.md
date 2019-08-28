---
description: Esta información le ayuda a solucionar problemas de la mensajería push.
keywords: móvil
seo-description: Esta información le ayuda a solucionar problemas de la mensajería push.
seo-title: Solución de problemas de mensajería push
solution: Marketing Cloud, Analytics
title: Solución de problemas de mensajería push
topic: Métricas
uuid: 9 c 4 a 9371-6691-4 a 2 c-a 6 c 1-b 9 f 901 a 41599
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Solución de problemas de la mensajería push {#troubleshooting-push-messaging}

Esta información le ayuda a solucionar problemas de la mensajería push.

## ¿Por qué a veces hay retrasos en el envío de mensajes push?

Los siguientes tipos de retraso podrían estar asociados con los mensajes push de Mobile Services:

* Espera de visitas de Analytics

   Todos los grupos de informes tienen una configuración para determinar cuándo se deben procesar las visitas de Analytics entrantes. El valor predeterminado es una hora, a cada hora en punto. El procesamiento en sí de las visitas de Analytics puede tardar hasta 30 minutos, aunque suele completarse en 15-20 minutos. Por ejemplo, supongamos que un grupo de informes procesa las visitas cada hora. Si tiene en cuenta el tiempo de procesamiento de un máximo de 30 minutos, una visita entrante puede tardar hasta 90 minutos en estar disponible para un mensaje push. Si un usuario inicia la aplicación a las 9:01, la visita se mostraría en la interfaz de usuario de Mobile Services como un nuevo usuario único entre las 10:15 y las 10:30.

* Espera del servicio push

   Es posible que el servicio push (APNS o FCM) no envíe el mensaje inmediatamente. Aunque no es frecuente, se han visto retrasos de 5-10 minutos. En la página Mensajes puede comprobar que el mensaje push se ha enviado al servicio push al hacer clic en el vínculo **Ver** del mensaje. En el informe, el número de envíos correctos al servicio push se indica en la columna **[!UICONTROL Publicado].**

   >[!TIP]
   >
   >Los servicios push no garantizan que se envíe un mensaje.

   Para obtener más información acerca de la fiabilidad de los servicios, consulte la documentación apropiada:

   * **APNS**: [calidad de servicio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [Duración de un mensaje](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## ¿Por qué mis mensajes push se cortan o no se expanden?

En el caso de algunos dispositivos Android, es posible que deba utilizar `NotificationCompat.BigTextStyle` para visualizar los mensajes.
