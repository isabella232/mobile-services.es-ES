---
description: Puede enviar mensajes en las aplicaciones que se activen mediante cualquier dato o evento de Analytics. Tras la implementación, los mensajes se envían de forma dinámica a la aplicación y no requieren una actualización de código.
seo-description: Puede enviar mensajes en las aplicaciones que se activen mediante cualquier dato o evento de Analytics. Tras la implementación, los mensajes se envían de forma dinámica a la aplicación y no requieren una actualización de código.
seo-title: Mensajería en la aplicación
solution: Marketing Cloud,Analytics
title: Mensajería en la aplicación
topic: Desarrollador e implementación
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mensajería en la aplicación {#in-app-messaging}

Puede enviar mensajes en las aplicaciones que se activen mediante cualquier dato o evento de Analytics. Tras la implementación, los mensajes se envían de forma dinámica a la aplicación y no requieren una actualización de código.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

>[!IMPORTANT]
>
>En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Para utilizar la mensajería en la aplicación **necesita** la versión 4.2 o posterior del SDK.

Puede crear mensajes, así como las reglas de Adobe Mobile Services que definen cuándo se muestran. Para obtener más información, consulte [Crear un mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Para mostrar mensajes en la aplicación es preciso actualizar el SDK. Puede completar estos pasos aunque aún no haya definido ningún mensaje. Tras definir los mensajes, se enviarán de forma dinámica a su aplicación y se mostrarán sin necesidad de actualizar la aplicación en la tienda de aplicaciones.

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Si seleccionó un diseño modal, elija un de los siguientes temas para el mensaje:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   Por ejemplo:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. In each `collectLifecycleData` call, pass `this` to provide a reference to your current activity:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages` o `remotes` es obligatorio.

   Para que los mensajes en la aplicación se actualicen de forma dinámica en el inicio, el objeto `remotes` debe estar presente y adecuadamente configurado:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obtener más información, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

El SDK de Mobile para Android realiza un seguimiento de las siguientes métricas para sus mensajes dentro de la aplicación:

* Para los mensajes dentro de la aplicación en pantalla completa y de estilo de alerta:

   * **Impresiones**: cuando el usuario activa un mensaje dentro de la aplicación.
   * **Pulsaciones**: cuando el usuario pulsa **[!UICONTROL Pulsaciones]**.
   * **Cancels: when user presses Cancel.******

* Para los mensajes personalizados en pantalla completa, el contenido HTML del mensaje debe incluir el código adecuado para notificar al sistema de seguimiento del SDK el uso de los botones siguientes:

   * **Click-through (redirect) example tracking:**

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Cancelar** (cerrar) seguimiento de ejemplo:

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Al crear un mensaje de pantalla completa, tiene la opción de especificar una imagen de reserva. Si su mensaje no puede recuperar su imagen pretendida desde la web, el SDK intenta cargar la imagen con el mismo nombre desde la carpeta de recursos de su aplicación. Esto le permite mostrar el mensaje en su forma original, aunque el usuario esté sin conexión o la imagen predeterminada no esté disponible.

>[!IMPORTANT]
>
>El nombre del recurso de imagen de reserva se especifica al configurar el mensaje en Adobe Mobile Services y debe asegurarse de que el recurso especificado está disponible.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Los siguientes métodos le permiten configurar los iconos pequeños y grandes que aparecen en el área de notificaciones, así como el icono grande que se muestra cuando aparecen nuevas notificaciones en la bandeja.

* **Config.setSmallIconResourceId(int resourceId)**

   Establece el icono pequeño que se utiliza para las notificaciones creadas por el SDK. Este icono aparece en la barra de estado y es la imagen secundaria que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Here is the code example for this method:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Establece el icono grande que se utiliza para las notificaciones creadas por el SDK. Este icono es la imagen principal que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
