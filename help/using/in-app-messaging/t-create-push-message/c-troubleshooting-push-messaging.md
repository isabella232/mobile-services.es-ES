---
description: Esta información resulta útil para solucionar problemas con la mensajería push.
keywords: móvil
seo-description: Esta información resulta útil para solucionar problemas con la mensajería push.
seo-title: Solucionar los problemas de la mensajería push
solution: Experience Cloud,Analytics
title: Resolución de problemas de mensajería push
topic: Métricas
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Solucionar los problemas de la mensajería push{#troubleshooting-push-messaging}

Esta información resulta útil para solucionar problemas con la mensajería push.

## ¿Por qué a veces hay retrasos en el envío de mensajes push?

Los siguientes tipos de retraso podrían estar asociados con los mensajes push de Mobile Services:

* **Esperando las visitas de Analytics**

   Todos los grupos de informes tienen una configuración para determinar cuándo se deben procesar las visitas de Analytics entrantes. El valor predeterminado es de 1 hora.

   El procesamiento de las visitas de Analytics tarda como máximo 30 minutos, aunque suele completarse en 15-20 minutos. Por ejemplo, supongamos que un grupo de informes procesa las visitas cada hora. Sumando el tiempo de procesamiento necesario de 30 minutos máx., una visita entrante puede tardar hasta 90 minutos en estar disponible para un mensaje push. Si un usuario iniciara la aplicación a las 9:01, la visita se mostraría en la interfaz de usuario de Mobile Services como un nuevo usuario único entre las 10:15 y las 10:30.

* **Espera del servicio push**

   Es posible que el servicio push (APNS o GCM) no envíe el mensaje inmediatamente. Aunque no es habitual, en ocasiones el tiempo de espera ha sido de 5-10 minutos. Puede verificar si el mensaje push se ha enviado al servicio push consultando la vista **[!UICONTROL Informe]** del mensaje push, buscando el mensaje en la tabla **[!UICONTROL Historial de mensajes]** y fijándose en el número de **[!UICONTROL Publicados]**.

   >[!TIP]
   >
   >Este número es la cantidad de mensajes que se han entregado al servicio push. Los servicios push no garantizan el envío de un mensaje.

   Para obtener más información sobre la fiabilidad del servicio, consulte:

   * [calidad de servicio](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [ciclo vital de un mensaje](https://developers.google.com/cloud-messaging/concept-options#lifetime).

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

   También puede comprobar la validez de un token de registro reemplazando `"ABC"` por el token.

## ¿Por qué no funciona el certificado de APNS?

El certificado de APNS puede no ser válido por varios motivos:

* Es posible que esté usando un certificado de simulación de pruebas en lugar del certificado de producción.
* Está usando un nuevo certificado de producción/simulación de pruebas que no se admite.
* Está usando un archivo `.p8` en lugar de un archivo `.p12`.

## Resolver errores de mensajes push

**Un ejemplo**

El ejemplo siguiente ilustra cómo se puede resolver un error de push al emplear un VRS.

El cliente siguiente tiene dos aplicaciones iOS:

* Nombre de la aplicación: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * Segmento de definición de VRSID: `a.appid contains “PhotoShop_iOS_app_SF”`
* Nombre de la aplicación: PhotoShop_app_iOS
   * RSID principal: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * Segmento de definición de VRSID: `a.os contains “iOS”`

En este ejemplo, si un empleado de Photoshop envía un mensaje push a la aplicación *PhotoShop_iOS_app_SF*, todos los usuarios de la aplicación *PhotoShop_iOS_app_SF* lo recibirán según lo esperado. En cambio, si un empleado envía un mensaje a la aplicación *PhotoShop_app_LA* porque su segmento de definición de VRSID es incorrecto (`iOS`iOS en lugar de `a.os contains "PhotoShop_iOS_app_LA"`), el mensaje se envía a **todos** los usuarios de iOS en *AllAdobe PhotoShop_apps*. Aunque el mensaje llegue a los usuarios de *PhotoShop_iOS_app_LA*, también bloquea los identificadores push para los usuarios de *PhotoShop_iOS_app_SF* porque la aplicación *PhotoShop_iOS_app_SF* tiene un certificado diferente. Si el segmento se hubiera definido como `a.os contains “PhotoShop_iOS_app_LA”`, el mensaje push solo se habría enviado a los usuarios de *PhotoShop_iOS_app_LA*.

Si se transmiten con el certificado push *PhotoShop_IOS_app_LA*, los identificadores push de *PhotoShop_iOS_app_SF* regresarán con un estado no válido `invalid`.

>[!CAUTION]
>
>Después de crear un mensaje push para una aplicación que usa un VRS y hacer clic en **[!UICONTROL Guardar y enviar]**, aparece una alerta que recuerda que todas las aplicaciones que figuran en la lista **deben** tener un certificado válido. Si hay alguna aplicación que **no** lo tiene, los segmentos de audiencia pueden seguir bloqueados indefinidamente y tal vez no pueda volver a enviar mensajes push a los usuarios afectados. Para obtener más información sobre los segmentos de audiencia, consulte [Audience: definir y configurar las opciones de audiencia para los mensajes push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
