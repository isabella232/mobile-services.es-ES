---
description: Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones iOS.
seo-description: Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones iOS.
seo-title: Mensajería en la aplicación
solution: Marketing Cloud,Analytics
title: Mensajería en la aplicación
topic: Desarrollador e implementación
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mensajería en la aplicación {#in-app-messaging}

Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones iOS.

Para utilizar la mensajería en la aplicación **necesita** la versión 4.2 o posterior del SDK.

Información que debe recordar:

* Los mensajes y las reglas que definen el momento en que se muestran se crean en Adobe Mobile Services. Para obtener más información, consulte [Crear un mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Para que se muestren los mensajes en la aplicación, se deben realizar las actualizaciones del SDK que se indican en esta sección.

   >[!TIP]
   >
   >Puede completar estos pasos aunque no tenga ningún mensaje definido. Después de definir los mensajes, se envían de forma dinámica a la aplicación y se muestran sin actualizar la tienda de aplicaciones.

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en Implementación [principal y ciclo de vida](/help/ios/getting-started/requirements.md).

1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for In-App messaging.
1. Para que los mensajes en la aplicación se actualicen de forma dinámica en el inicio, el objeto `remotes` debe estar presente y adecuadamente configurado:

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

   >[!TIP]
   >
   >`messages` o `remotes` es obligatorio.

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obtener más información, consulte Implementación [principal y ciclo vital](/help/ios/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

El SDK de Mobile Services para iOS realiza un seguimiento de las siguientes métricas para sus mensajes dentro de la aplicación:

* Para los mensajes dentro de la aplicación en pantalla completa y de estilo de alerta:

   * **[!UICONTROL Impresiones]**: cuando el usuario activa un mensaje en la aplicación.
   * **[!UICONTROL Pulsaciones]**: cuando el usuario pulsa el botón de **[!UICONTROL pulsación]** .
   * **[!UICONTROL Cancela]**: cuando el usuario pulsa el botón **[!UICONTROL Cancelar]** .

* Para los mensajes personalizados en pantalla completa, el contenido HTML del mensaje debe incluir el código adecuado para notificar al sistema de seguimiento del SDK el uso de los botones siguientes:

   * **[!UICONTROL Seguimiento de ejemplo de pulsaciones]** (redirecciones): `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Cancelar]** (cerrar) seguimiento de ejemplo: `adbinapp://cancel`

* Para notificaciones locales (remotas):

   * **[!UICONTROL Impresiones]**: cuando el usuario activa la notificación.
   * **[!UICONTROL Aperturas]**: cuando el usuario abre la aplicación desde la notificación.
   Aquí tiene un ejemplo de cómo puede incluirse el seguimiento de aperturas:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Al crear un mensaje de pantalla completa en Adobe Mobile Services, tiene la opción de especificar una imagen de reserva. Si su mensaje no es capaz de recuperar su imagen pretendida desde la web, el SDK intenta cargar la imagen con el mismo nombre desde el paquete de la aplicación. Esto le permite mostrar el mensaje en su forma original, aunque el usuario esté sin conexión o la imagen predeterminada no esté disponible.

El nombre de recurso de la imagen de reserva se especifica al configurar el mensaje en Adobe Mobile Services.

>[!IMPORTANT]
>
>Debe asegurarse de que el recurso especificado está disponible.

