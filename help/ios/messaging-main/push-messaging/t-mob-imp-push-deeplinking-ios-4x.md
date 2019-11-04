---
description: Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.
seo-description: Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave adb_deeplink.
seo-title: Implementar la mensajería push con vinculación profunda
title: Implementar la mensajería push con vinculación profunda
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Implementar la mensajería push con vinculación profunda {#implement-push-messaging-with-deep-linking}

Después de configurar la URL de vinculación profunda en la interfaz de usuario de Adobe Mobile Services, esta URL estará en la carga útil push con la clave `adb_deeplink`.

1. En AppDelegate puede recuperar la URL de vinculación profunda y manejarla por su cuenta en las siguientes ubicaciones:

   * En `application:didFinishLaunchingWithOptions`:

      Si la aplicación no está en ejecución cuando se produce un clic en un mensaje push, puede obtener la carga útil de push desde `launchOptions`. La URL de vinculación profunda está en el diccionario de la carga útil, en la clave `adb_deeplink`.

   * Los métodos delegados para notificación remota

      En las aplicaciones `didReceiveRemoteNotification:` o `didReceiveRemoteNotification:fetchCompletionHandler:` puede obtener la URL accediendo al diccionario `userInfo` mediante la clave `adb_deeplink`.

   * Los métodos delegados para `UNUserNotificationCenter`

      En el método `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` puede obtener la carga push desde el diccionario `userInfo`, en la clave `adb_deeplink`.

Por ejemplo:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

