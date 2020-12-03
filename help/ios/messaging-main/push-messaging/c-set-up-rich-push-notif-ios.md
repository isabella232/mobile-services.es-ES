---
description: Puede adjuntar archivos de imagen a sus notificaciones de Apple. Añadir componentes visuales puede aumentar significativamente la participación de los usuarios con las notificaciones push.
seo-description: Puede adjuntar archivos de imagen a sus notificaciones de Apple. Añadir componentes visuales puede aumentar significativamente la participación de los usuarios con las notificaciones push.
seo-title: Recibir notificaciones push enriquecidas
title: Recibir notificaciones push enriquecidas
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 35%

---


# Recibir notificaciones push enriquecidas {#receive-rich-push-notifications}

Puede adjuntar archivos de imagen a sus notificaciones de Apple. Añadir componentes visuales puede aumentar significativamente la participación de los usuarios con las notificaciones push.

Para recibir notificaciones push enriquecidas en la aplicación de iOS:

1. Implemente la mensajería push para la aplicación completando los pasos indicados en [Mensajería push](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Compruebe que puede enviar un mensaje push de texto a la aplicación.
1. Añada una extensión del servicio de notificaciones siguiendo estos pasos:

   1. In your Xcode project, select  **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. Seleccione **[!UICONTROL Extensión del servicio de notificaciones]**.
   1. Compruebe que el archivo `NotificationService.m` existe.

1. Abra el archivo `NotificationService.m` y compruebe que existen los siguientes métodos delegados:

   * Un método para recibir una solicitud de notificación.
   * Un método para gestionar la caducidad de la extensión de servicio.

      Para recibir notificaciones push enriquecidas, se utiliza el primer método:

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


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
