---
description: Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.
title: Implementar la mensajería push con vinculación profunda
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# Implementar la mensajería push con vinculación profunda {#implement-push-messaging-with-deep-linking}

Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.

Puede obtener la dirección URL llamando a `remoteMessage.getData().get("adb_deeplink")` en `FirebaseMessagingService`.

>[!TIP]
>
>Puede definir distintos objetos Intent, dependiendo de si la carga útil incluye o no una URL de vinculación profunda.

1. Complete una de las siguientes tareas:

   * Si la URL de vinculación profunda **está** en la carga útil push, cree un objeto Intent `ACTION_VIEW` con la URL.

      Cuando el usuario hace clic en el mensaje push, se activa un vínculo profundo.

   * Si la URL de vinculación profunda **no está** en la carga útil push, cree un objeto Intent que abra una de las actividades.

## Ejemplo

Esta es una implementación de ejemplo para la clase que se amplía desde `FirebaseMessagingService`:

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
