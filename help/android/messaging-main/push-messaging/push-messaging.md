---
description: Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.
seo-description: Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.
seo-title: Mensajería push
solution: Marketing Cloud,Analytics
title: Mensajería push
topic: Desarrollador e implementación
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.

Para utilizar la mensajería push **necesita** la versión 4.6 o posterior del SDK.

>[!IMPORTANT]
>
>No configure manualmente el ID de Experience Cloud dentro de la aplicación. Con esto se crea un nuevo usuario exclusivo que no recibirá mensajes push debido a su estado Opt-in. Por ejemplo, suponga que un usuario que ha solicitado recibir mensajes push inicia sesión en la aplicación. A continuación, si establece de forma manual el identificador dentro de la aplicación, se crea un nuevo usuario exclusivo que no ha solicitado recibir estos mensajes. Este nuevo usuario no recibirá ningún mensaje push.
>
>No se admite mover la aplicación a un nuevo grupo de informes. En caso de hacerlo, podría desajustarse la configuración de push y los mensajes no se enviarían.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Si la aplicación ya está configurada para utilizar la mensajería mediante Firebase Cloud Messaging (FCM), es posible que ya se hayan completado algunos de los siguientes pasos.

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Obtenga el ID/token de registro mediante la API de Firebase Cloud Messaging (FCM).

   * Para obtener más información acerca de la configuración de FCM, consulte [Set Up a Firebase Cloud Messaging Client App on Android (Configurar una aplicación cliente de Firebase Cloud Messaging en Android)](https://firebase.google.com/docs/cloud-messaging/android/client).
   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Habilite la realización de informes pasando su actividad en el método `collectLifecycleData`.

   Estos son los requisitos para habilitar los informes de clics en mensajes push:

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. This can be done using the  method. `putExtras` For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * En la actividad de destino del clic, se debe pasar la actividad al SDK mediante la llamada `collectLifecycleData`.

      Recuerde la información siguiente:

      * Use  or .`Config.collectLifecycleData(this)``Config.collectLifecycleData(this, contextData)`

      * Do **not** use `Config.collectLifecycleData()`.



