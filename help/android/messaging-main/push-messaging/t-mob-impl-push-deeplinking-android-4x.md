---
description: Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.
seo-description: Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.
seo-title: Implementar la mensajería push con vinculación profunda
title: Implementar la mensajería push con vinculación profunda
uuid: e 24 f 9248-8 d 48-4 e 57-84 af -3 a 05 b 72 e 2 a 09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.

Puede obtener la dirección URL llamando `remoteMessage.getData().get("adb_deeplink")` al `FirebaseMessagingService`.

>[!TIP]
>
>Puede definir diferentes intenciones según si la carga útil tiene una URL de vinculación profunda.

1. Complete una de las siguientes tareas:

   * Si la URL de vinculación profunda **está** en la carga útil push, cree un objeto Intent `ACTION_VIEW` con la URL.

      Cuando el usuario hace clic en el mensaje push, se activa un vínculo profundo.

   * Si la URL de vinculación profunda **no está** en la carga útil push, cree un objeto Intent que abra una de las actividades.

## Ejemplo

Here is a sample implementation for the class extending from `FirebaseMessagingService`:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
