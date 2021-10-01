---
description: Puede adjuntar archivos de imagen a las notificaciones de Apple. La adición de componentes visuales puede aumentar significativamente la participación de los usuarios con las notificaciones push.
title: Recibir notificaciones push enriquecidas
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 39%

---

# Recibir notificaciones push enriquecidas {#receive-rich-push-notifications}

Puede adjuntar archivos de imagen a las notificaciones de Apple. La adición de componentes visuales puede aumentar significativamente la participación de los usuarios con las notificaciones push.

Para recibir notificaciones push enriquecidas en su aplicación iOS:

1. Implemente la mensajería push para la aplicación completando los pasos indicados en [Mensajería push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Compruebe que puede enviar un mensaje push de texto a la aplicación.
1. Añada una extensión del servicio de notificaciones completando los siguientes pasos:

   1. En el proyecto Xcode, seleccione **[!UICONTROL Archivo]** > **[!UICONTROL Nuevo]** > **[!UICONTROL Target]**.
   1. Seleccione **[!UICONTROL Extensión del servicio de notificaciones]**.
   1. Compruebe que el archivo `NotificationService.m` existe.

1. Abra el archivo `NotificationService.m` y compruebe que existen los siguientes métodos delegados:

   * Un método para recibir una solicitud de notificación.
   * Un método para gestionar la caducidad de la extensión de servicio.

      Para recibir notificaciones push enriquecidas, se utiliza el primer método :

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      Con este método, puede usar la URL de medios desde `userInfo` con la clave `attachment-url`. Después de descargar el archivo en un directorio local, agregue la ruta local a `bestAttemptContent.attachments`.

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


Para obtener más información sobre las notificaciones push enriquecidas con iOS, consulte [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
