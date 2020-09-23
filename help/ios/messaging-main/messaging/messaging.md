---
description: Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones de iOS.
seo-description: Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones de iOS.
seo-title: Mensajería en la aplicación
solution: Experience Cloud,Analytics
title: Mensajería en la aplicación
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 55%

---


# Mensajería en la aplicación {#in-app-messaging}

Esta información le ayuda a utilizar la mensajería en la aplicación en sus aplicaciones de iOS.

To use in-app messaging, you **must** have SDK version 4.2 or later.

Información que debe recordar:

* Los mensajes y las reglas que definen cuándo se muestran se crean en Adobe Mobile Services. For more information, see [Create an in-app message](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Las actualizaciones descritas en esta sección deben realizarse en el SDK para que se muestren los mensajes en la aplicación.

   >[!TIP]
   >
   >Puede completar estos pasos aunque aún no haya definido ningún mensaje. Tras definir los mensajes, se envian de forma dinámica a su aplicación y se mostrarán sin necesidad de actualizar la aplicación en la tienda de aplicaciones.

## Activación de la mensajería en la aplicación {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/requirements.md).

1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Compruebe que el archivo `ADBMobileConfig.json` contiene la configuración necesaria para la mensajería en la aplicación.
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

   Si estos objetos no están configurados, descargue un archivo `ADBMobileConfig.json` actualizado desde Adobe Mobile Services. Para obtener más información, consulte [Implementación principal y ciclo vital](/help/ios/getting-started/requirements.md).

## Seguimiento de mensajes dentro de la aplicación {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Los SDK de iOS Mobile Services realizan un seguimiento de las siguientes métricas para los mensajes en la aplicación:

* Para mensajes en la aplicación de estilo de alerta y pantalla completa:

   * **[!UICONTROL Impresiones]**: cuando el usuario activa un mensaje dentro de la aplicación.
   * **[!UICONTROL Pulsaciones]**: cuando el usuario presiona el botón **[!UICONTROL Pulsación]**.
   * **[!UICONTROL Cancelaciones]**: cuando el usuario presiona el botón **[!UICONTROL Cancelar]**.

* Para los mensajes personalizados en pantalla completa, el contenido HTML del mensaje debe incluir el código adecuado para notificar al sistema de seguimiento del SDK el uso de los botones siguientes:

   * **[!UICONTROL Seguimiento de ejemplo de pulsaciones]** (redirecciones): `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Ejemplo de seguimiento de Cancelación]** (cierre): `adbinapp://cancel`

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

## Imagen de reserva local {#section_DEACC1CE549B4573B556A44A52409941}

Al crear un mensaje de pantalla completa en Adobe Mobile Services, puede especificar de forma opcional una imagen de reserva. Si el mensaje no puede recuperar la imagen deseada de la web, el SDK intenta cargar la imagen con el mismo nombre del paquete de aplicaciones. Esto le permite mostrar el mensaje en su forma original aunque el usuario esté sin conexión o la imagen predeterminada esté inaccesible.

El nombre del recurso de imagen de reserva se especifica al configurar el mensaje en Adobe Mobile Services.

>[!IMPORTANT]
>
>Debe comprobar que el recurso especificado está disponible.

