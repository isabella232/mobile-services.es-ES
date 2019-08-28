---
description: Puede ver informes de los mensajes push y los mensajes en la aplicación.
keywords: móvil
seo-description: Puede ver informes de los mensajes push y los mensajes en la aplicación.
seo-title: Ver informes de mensajes
solution: Marketing Cloud, Analytics
title: Ver informes de mensajes
topic: Métricas
uuid: 0 ac 73 a 81-388 f -4 dfd -84 d 5-21 b 8 db 4 b 8 c 83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Puede ver informes de los mensajes push y los mensajes en la aplicación.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   Para obtener más información sobre la creación de un filtro adhesivo, consulte [Adición de un filtro adhesivo](/help/using/usage/reports-customize/t-sticky-filter.md).

>[!TIP]
>
>Según el tipo de mensaje que esté viendo, el informe puede variar.

## Mensajes en la aplicación {#section_90B79BA58E8141F78538C187EB1BF8C7}

Si visualiza informes para un mensaje en la aplicación, se parecerán a la siguiente ilustración:

![mensaje de informe](assets/report_message.png)

### Métricas de mensajes en la aplicación

Esta es una lista de las métricas disponibles para los mensajes en la aplicación:

* **[!UICONTROL Impresión]**, cuando se activa un mensaje.

* **[!UICONTROL Pulsaciones]**, cuando un usuario pulsa el botón **[!UICONTROL Pulsación]** en una alerta o mensaje a pantalla completa, y cuando un usuario abre la aplicación desde una notificación local.

* **[!UICONTROL Cancelar]**, cuando un usuario pulsa el **[!UICONTROL botón Cancelar]** en una alerta o un mensaje a pantalla completa.

* **[!UICONTROL Tasa de participación]**, una métrica calculada desde Adobe Analytics y es el resultado de la cantidad de pulsaciones divididas por el número de impresiones.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Si visualiza informes para un mensaje push, se parecerán a la siguiente ilustración:

![mensaje push](assets/report_message_push.png)

El gráfico de la parte superior muestra el número de usuarios que abrieron el mensaje.

### Métricas de mensajes push

Esta es una lista de las métricas disponibles para los mensajes push:

* **[!UICONTROL Fecha]**

   Momento en que se insertó el mensaje en los dispositivos desde Mobile Services.

* **[!UICONTROL Estado]**

   El estado del mensaje y los estados disponibles son:

   * **[!UICONTROL Cancelado]**
   * **[!UICONTROL Programado]**
   * **[!UICONTROL Ejecutando]**
   * **[!UICONTROL Ejecutado]**

* **[!UICONTROL Publicado]**

   El número de tokens de dispositivo enviados correctamente al servicio de notificaciones Push de Apple/Firebase Cloud Messaging (APNS/FCM) para enviar el mensaje a los dispositivos de los usuarios.

* **[!UICONTROL Fallido]**

   El número de tokens de dispositivo no se envía correctamente a APNS/FCM. Algunas posibles razones de fallas:

   * El pushID no es válido

   * La plataforma push (APNS, FCM, etc.) proporcionada para insertar no existe para la aplicación del trabajo. Por ejemplo, la plataforma podría recopilar tokens push de iOS, pero no tiene el servicio APNS configurado.

   * El mensaje puede haber fallado porque el servicio push no estaba correctamente configurado o el sistema Mobile Services está fuera de servicio.
   >[!IMPORTANT]
   >
   >Si tiene un número inusualmente alto de errores, compruebe la configuración de los servicios push. Si los servicios push parecen estar configurados correctamente, póngase en contacto con el servicio de atención al cliente de Adobe.

* **[!UICONTROL Bloqueado]**

   Número de tokens de dispositivo que ya no son válidos para enviarse a APNS o FCM. Esto suele significar que la aplicación se ha desinstalado del dispositivo o que el usuario ha cambiado la configuración relacionada con la recepción de mensajes. Android e iOS difieren en la forma de considerar un token bloqueado. Los tokens de Android aparecen inmediatamente en el recuento de bloqueados. Los tokens de iOS aparecen inicialmente como publicados, pero, basándose en la información de APNS, aparecen como bloqueados en los siguientes mensajes.
