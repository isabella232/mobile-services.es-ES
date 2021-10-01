---
description: Puede enviar mensajes en la aplicación que se activen a partir de cualquier evento o dato de análisis. Después de la implementación, los mensajes se envían de forma dinámica a la aplicación y no requieren una actualización de código.
solution: Experience Cloud,Analytics
title: Mensajería en la aplicación
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 100%

---

# Mensajería en la aplicación  {#in-app-messaging}

Puede enviar mensajes en la aplicación que se activen a partir de cualquier evento o dato de análisis. Después de la implementación, los mensajes se envían de forma dinámica a la aplicación y no requieren una actualización de código.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

>[!IMPORTANT]
>
>En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Si utiliza los SDK móviles de la Adobe Experience Platform con Adobe Launch, también **debe** instalar la extensión de Adobe Analytics Mobile Services para utilizar funciones como, por ejemplo, mensajería en la aplicación y notificaciones push. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Para obtener información sobre el uso de la mensajería push y la mensajería en la aplicación con los SDK de Experience Cloud, consulte [Configuración de mensajería push](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) y [Configuración de mensajería en la aplicación](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Para utilizar la mensajería en la aplicación **necesita** la versión 4.2 o posterior del SDK.

Puede crear mensajes y reglas de Adobe Mobile Services que definen cuándo se visualizan esos mensajes. Para obtener más información, consulte [Crear un mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Para mostrar mensajes en la aplicación, se debe actualizar el SDK. Puede completar estos pasos aunque aún no haya definido ningún mensaje. Tras definir los mensajes, se enviarán de forma dinámica a su aplicación y se mostrarán sin necesidad de actualizar la aplicación en la tienda de aplicaciones.

## Activación de la mensajería en la aplicación {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Actualice el archivo `AndroidManifest.xml` para declarar la actividad de pantalla completa y habilitar el controlador de notificación de mensajes:

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

1. En cada llamada a `collectLifecycleData`, pase `this` para proporcionar una referencia para su actividad actual:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Compruebe que el archivo `ADBMobileConfig.json` contiene la configuración necesaria para la mensajería en la aplicación.

   >[!IMPORTANT]
   >
   >`messages` o `remotes` es obligatorio.

   Para que los mensajes en la aplicación se actualicen de forma dinámica en el inicio, el objeto `remotes` debe estar presente y adecuadamente configurado:

   ```js
   "messages": [ 
       { 
           "messageId": "de45c43c-37bf-441f-8cbd-cc3ba3469ebe", 
           "template": "fullscreen", 
           "showOffline": false, 
           "showRule": "always", 
           "endDate": 2524730400, 
           "startDate": 0, 
           "audiences": [], 
           "triggers": [], 
           "payload": { // contents change depending on template 
               "html": "<html>html code goes here</html>" 
           }, 
       }, 
       … 
   ] 
   "remotes" : { 
       "analytics.poi": "https://assets.adobedtm.com/…/yourfile.json", 
       "messages": "https://assets.adobedtm.com/…/yourfile.json" 
   }
   ```

   Si este objeto no está configurado, descargue un archivo `ADBMobileConfig.json` actualizado desde Adobe Mobile Services. Para obtener más información, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

## Seguimiento de mensajes dentro de la aplicación {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Los SDK de Android Mobile hacen un seguimiento de las siguientes métricas para sus mensajes en la aplicación:

* Para mensajes en la aplicación de estilo de alerta y pantalla completa:

   * **Impresiones**: cuando el usuario activa un mensaje dentro de la aplicación.
   * **Pulsaciones**: cuando el usuario presiona el botón **[!UICONTROL Pulsación]**.
   * **Cancelaciones**: cuando el usuario pulsa **[!UICONTROL Cancelar]**.

* Para los mensajes personalizados en pantalla completa, el contenido HTML del mensaje debe incluir el código adecuado para notificar al sistema de seguimiento del SDK el uso de los botones siguientes:

   * **Seguimiento de ejemplo de pulsaciones** (redirecciones):

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * Ejemplo de seguimiento de **Cancelación** (cierre):

      `adbinapp://cancel`

## Imagen de reserva local {#section_DEACC1CE549B4573B556A44A52409941}

Al crear un mensaje de pantalla completa, puede especificar una imagen de reserva. Si el mensaje no puede recuperar la imagen deseada de la web, el SDK intenta cargar la imagen con el mismo nombre desde la carpeta de recursos de la aplicación. Esto le permite mostrar el mensaje en su forma original, aunque el usuario esté sin conexión o no sea posible acceder a la imagen predeterminada.

>[!IMPORTANT]
>
>El nombre del recurso de imagen de reserva se especifica al configurar el mensaje en Adobe Mobile Services, y es necesario asegurarse de que el recurso especificado esté disponible.

## Configuración de los iconos de notificación {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Los siguientes métodos le permiten configurar los iconos pequeños y grandes que aparecen en el área de notificaciones, así como el icono grande que se muestra cuando aparecen nuevas notificaciones en la bandeja.

* **Config.setSmallIconResourceId(int resourceId)**

   Establece el icono pequeño que se utiliza para las notificaciones creadas por el SDK. Este icono aparece en la barra de estado y es la imagen secundaria que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Este es un ejemplo de código para este método:

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
