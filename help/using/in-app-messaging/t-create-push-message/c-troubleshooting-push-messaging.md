---
description: Esta información resulta útil para solucionar problemas con la mensajería push.
keywords: móvil
seo-description: Esta información resulta útil para solucionar problemas con la mensajería push.
seo-title: Solucionar los problemas de la mensajería push
solution: Marketing Cloud,Analytics
title: Solucionar los problemas de la mensajería push
topic: Métricas
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

Esta información resulta útil para solucionar problemas con la mensajería push.

## ¿Por qué a veces hay retrasos en el envío de mensajes push?

Los siguientes tipos de retraso podrían estar asociados con los mensajes push de Mobile Services:

* **Esperando visitas de Analytics**

   Todos los grupos de informes tienen una configuración para determinar cuándo se deben procesar las visitas de Analytics entrantes. El valor predeterminado es de 1 hora.

   El procesamiento de las visitas de Analytics tarda como máximo 30 minutos, aunque suele completarse en 15-20 minutos. Por ejemplo, supongamos que un grupo de informes procesa las visitas cada hora. Sumando el tiempo de procesamiento necesario de 30 minutos máx., una visita entrante puede tardar hasta 90 minutos en estar disponible para un mensaje push. Si un usuario iniciara la aplicación a las 9:01, la visita se mostraría en la interfaz de usuario de Mobile Services como un nuevo usuario único entre las 10:15 y las 10:30.

* **Espera del servicio push**

   Es posible que el servicio push (APNS o GCM) no envíe el mensaje inmediatamente. Aunque no es habitual, en ocasiones el tiempo de espera ha sido de 5-10 minutos. Puede verificar si el mensaje push se ha enviado al servicio push consultando la vista **[!UICONTROL Informe]** del mensaje push, buscando el mensaje en la tabla **[!UICONTROL Historial de mensajes]y fijándose en el número de** Publicados **.**

   >[!TIP]
   >
   >Este recuento es el número de envíos correctos a los servicios push. Los servicios push no garantizan el envío de un mensaje.

   For more information about the reliability of service, see:

   * [Calidad del servicio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Lifetime of a Message.](https://developers.google.com/cloud-messaging/concept-options#lifetime)

## ¿Por qué mi clave de GCM API para Android no es válida?

* **Clave de API no válida**

   La clave de API puede no ser válida por varios motivos:

   * La clave de API que facilitó no es una clave de servidor con el valor correcto de clave de GCM API.
   * La clave de servidor ha bloqueado las direcciones IP y está impidiendo que los servidores de Adobe envíen un mensaje push.

* **Determinar la validez de la clave de API**

   Para determinar la validez de la clave de API, ejecute el siguiente comando:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   El código de estado de HTTP 401 significa que la clave de API no es válida. De lo contrario, verá algo parecido a esto:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## ¿Por qué no funciona el certificado de APNS?

El certificado de APNS puede no ser válido por varios motivos:

* Es posible que esté usando un certificado de simulación de pruebas en lugar del certificado de producción.
* Está usando un nuevo certificado de producción/simulación de pruebas que no se admite.
* You are using `.p8` file instead of a `.p12` file.

## Resolver errores de mensajes push

**Un ejemplo**

El ejemplo siguiente ilustra cómo se puede resolver un error de push al emplear un VRS.

El cliente siguiente tiene dos aplicaciones iOS:

* Nombre de la aplicación: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID Definition Segment: `a.appid contains “PhotoShop_iOS_app_SF”`
* Nombre de la aplicación: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID Definition Segment: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. Si hay alguna aplicación que **no** lo tiene, los segmentos de audiencia pueden seguir bloqueados indefinidamente y tal vez no pueda volver a enviar mensajes push a los usuarios afectados. For more information about audience segments, see Audience: define and configure audience options for push messages.[](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)
