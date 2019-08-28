---
description: Puede adjuntar archivos de imagen a sus notificaciones de Apple. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.
seo-description: Puede adjuntar archivos de imagen a sus notificaciones de Apple. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.
seo-title: Recibir notificaciones push enriquecidas
title: Recibir notificaciones push enriquecidas
uuid: 0 dbda 409-cf 49-4 eb 8-90 ee-baf 27911 dc 07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Puede adjuntar archivos de imagen a sus notificaciones de Apple. Agregar componentes visuales puede aumentar de forma significativa la interacción del usuario con las notificaciones push.

Para recibir notificaciones push enriquecidas en su aplicación iOS:

1. Implemente la mensajería push para la aplicación completando los pasos indicados en [Mensajería push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Compruebe que puede enviar un mensaje push de texto a la aplicación.
1. Agregue una extensión del servicio de notificaciones completando los siguientes pasos:

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Seleccione **[!UICONTROL Extensión del servicio de notificaciones]**.
   1. Compruebe que el archivo `NotificationService.m` existe.

1. Abra el archivo `NotificationService.m` y compruebe que existen los siguientes métodos delegados:

   * Un método para recibir una solicitud de notificación.
   * Un método para gestionar la caducidad de la extensión del servicio.

      Para recibir notificaciones push enriquecidas, se utiliza el primer método:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      En este método, puede obtener la URL de medios `userInfo` utilizando `attachment-url` la clave. Después de descargar el archivo en un directorio local, agregue la ruta local.`bestAttemptContent.attachments`

      Este es un ejemplo de código para este método:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


Para obtener más información acerca de notificaciones push enriquecidas en iOS, consulte [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
