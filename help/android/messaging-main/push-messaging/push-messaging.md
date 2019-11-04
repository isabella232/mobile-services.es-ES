---
description: Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.
seo-description: Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.
seo-title: Mensajería push
solution: Experience Cloud,Analytics
title: Mensajería push
topic: Desarrollador e implementación
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Mensajería push {#push-messaging}

Adobe Mobile y el SDK de Adobe Mobile le permiten enviar mensajes push a sus usuarios. El SDK también le permite realizar fácilmente un informe de los usuarios que han abierto la aplicación haciendo clic en un mensaje push.

Para utilizar la mensajería push **necesita** la versión 4.6 o posterior del SDK.

>[!IMPORTANT]
>
>No establezca de forma manual el Experience Cloud ID dentro de la aplicación. Con esto se crea un nuevo usuario exclusivo que no recibirá mensajes push debido a su estado Opt-in. Por ejemplo, suponga que un usuario que ha solicitado recibir mensajes push inicia sesión en la aplicación. A continuación, si establece de forma manual el identificador dentro de la aplicación, se crea un nuevo usuario exclusivo que no ha solicitado recibir estos mensajes. Este nuevo usuario no recibirá ningún mensaje push.
>
>No está permitido migrar la aplicación a un nuevo grupo de informes. En caso de hacerlo, podría desajustarse la configuración de push y los mensajes no se enviarían.

## Habilitar la mensajería push {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Si su aplicación ya está configurada para utilizar mensajería mediante Firebase Cloud Messaging (FCM), es posible que algunos de estos pasos ya estén completados.

1. Compruebe que el archivo `ADBMobileConfig.json` contiene la configuración necesaria para la mensajería push.

   El objeto `"marketingCloud"` debe tener la propiedad `"org"` configurada para la mensajería push.

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

1. Se debe pasar el ID/token de registro al SDK empleando el método `Config.setPushIdentifier(final String registrationId)`.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Habilite la realización de informes pasando su actividad en el método `collectLifecycleData`.

   Estos son los requisitos para habilitar los informes de clics en mensajes push:

   * En su implementación de `FireBaseMessageService`, el objeto Bundle que contiene los datos de mensajes, que se pasan al método `onMessageReceived` con el objeto RemoteMessage, se debe añadir al objeto Intent que se utiliza para abrir la actividad de destino mediante un clic. Esto se puede hacer con el método `putExtras`. Para obtener más información, consulte [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle)))
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * En la actividad de destino del clic, se debe pasar la actividad al SDK mediante la llamada `collectLifecycleData`.

      Recuerde la información siguiente:

      * Use `Config.collectLifecycleData(this)` o `Config.collectLifecycleData(this, contextData)`.

      * **No** utilice `Config.collectLifecycleData()`.



