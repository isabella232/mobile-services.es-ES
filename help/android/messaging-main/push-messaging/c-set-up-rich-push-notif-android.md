---
description: Puede adjuntar archivos de imagen a sus notificaciones de Android. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.
seo-description: Puede adjuntar archivos de imagen a sus notificaciones de Android. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.
seo-title: Recibir notificaciones push enriquecidas
title: Recibir notificaciones push enriquecidas
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: ht
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Recibir notificaciones push enriquecidas {#receive-rich-push-notifications}

Puede adjuntar archivos de imagen a sus notificaciones de Android. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.

## Gestión del mensaje push enriquecido entrante (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Si la aplicación está en primer plano, el mensaje push lo gestiona la aplicación que extiende la clase `FirebaseMessagingService` y se declara en el archivo de manifiesto del siguiente modo:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>La clase que contiene la implementación `onMessageReceived()` administra los datos recibidos.

Si el mensaje push contiene una URL multimedia, esta estará disponible en el parámetro `RemoteMessage` que se pasa a la función `onMessageReceived()`. La clave a utilizar es `attachment-url`, como se muestra en el siguiente ejemplo de código:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>Si se establece `NotificationCompat.BigPictureStyle`, es posible que las imágenes grandes no se visualicen. Para garantizar que las imágenes grandes se muestren siempre, establezca el `Notification.BigPictureStyle` nativo.

## Ejemplo de notificación push enriquecida {#section_6819316BEDDE45108413B541CA2BB2DC}

Este es un ejemplo de notificación push enriquecida con una imagen:

![](assets/rich-push-notification_example.png)

Para obtener más información acerca de notificaciones push enriquecidas en Android, consulte [Engage with Rich Notifications (Interactuar con notificaciones push)](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
