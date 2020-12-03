---
description: Esta información le ayuda a solucionar problemas de la mensajería push.
keywords: mobile
seo-description: Esta información le ayuda a solucionar problemas de la mensajería push.
seo-title: Resolución de problemas de mensajería push
solution: Experience Cloud,Analytics
title: Resolución de problemas de mensajería push
topic: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---


# Resolución de problemas de mensajería push {#troubleshooting-push-messaging}

Esta información le ayuda a solucionar problemas de la mensajería push.

## ¿Por qué a veces hay retrasos en el envío de mensajes push?

Los siguientes tipos de retraso podrían estar asociados con los mensajes push de Mobile Services:

* Espera de visitas de Analytics

   Todos los grupos de informes tienen una configuración para determinar cuándo se deben procesar las visitas de Analytics entrantes. El valor predeterminado es una hora, a cada hora en punto. El procesamiento en sí de las visitas de Analytics puede tardar hasta 30 minutos, aunque suele completarse en 15-20 minutos. Por ejemplo: un grupo de informes procesa las visitas cada hora. Si se tiene en cuenta el tiempo de procesamiento de un máximo de 30 minutos, una visita entrante puede tardar hasta 90 minutos en estar disponible para un mensaje push. Si un usuario inicia la aplicación a las 9:01, la visita se mostraría en la interfaz de usuario de Mobile Services como un nuevo usuario único entre las 10:15 y las 10:30.

* Espera del servicio push

   Puede que el servicio push (APNS o FCM) no envíe el mensaje inmediatamente. Aunque no es frecuente, se han visto retrasos de 5-10 minutos. En la página Mensajes puede comprobar que el mensaje push se ha enviado al servicio push al hacer clic en el vínculo **[!UICONTROL Ver]** del mensaje. En el informe, el número de envíos correctos al servicio push se indica en la columna **[!UICONTROL Publicado]**.

   >[!TIP]
   >
   >Los servicios push no garantizan el envío de un mensaje.

   Para obtener más información acerca de la fiabilidad de los servicios, consulte la documentación apropiada:

   * **APNS**: [Calidad del servicio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [Duración de un mensaje](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## ¿Por qué mis mensajes push se cortan o no se expanden?

En el caso de algunos dispositivos Android, es posible que deba utilizar `NotificationCompat.BigTextStyle` para visualizar los mensajes.
