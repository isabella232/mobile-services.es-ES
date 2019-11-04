---
description: Puede ver informes de los mensajes push y los mensajes en la aplicación.
keywords: móvil
seo-description: Puede ver informes de los mensajes push y los mensajes en la aplicación.
seo-title: Ver informes de mensajes
solution: Experience Cloud,Analytics
title: Ver informes de mensajes
topic: Métricas
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: ht
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# Ver informes de mensajes{#view-message-reports}

Puede ver informes de los mensajes push y los mensajes en la aplicación.

1. Haga clic en ![icono de informe](assets/icon_report.png) en la columna **[!UICONTROL Informe]** de un mensaje.
1. (**Opcional**) Cree un filtro adhesivo para el informe o cambie el intervalo de tiempo haciendo clic en el icono de **[!UICONTROL Calendario]**.

   Para obtener más información sobre la creación de un filtro adhesivo, consulte [Agregar un filtro adhesivo](/help/using/usage/reports-customize/t-sticky-filter.md).

>[!TIP]
>
>En función del tipo de mensaje que visualice, el informe puede variar.

## Mensajes en la aplicación {#section_90B79BA58E8141F78538C187EB1BF8C7}

Si visualiza informes para un mensaje en la aplicación, se parecerán a la siguiente ilustración:

![mensaje de informe](assets/report_message.png)

### Métricas de mensajes en la aplicación

Esta es una lista de las métricas disponibles para los mensajes en la aplicación:

* **[!UICONTROL Impresión]**, cuando se activa un mensaje.

* **[!UICONTROL Pulsación]**, cuando un usuario presiona el botón **[!UICONTROL Pulsación]** en una alerta o un mensaje a pantalla completa y cuando abre la aplicación desde una notificación local.

* **[!UICONTROL Cancelar]**, cuando un usuario presiona el botón **[!UICONTROL Cancelar]** en una alerta o un mensaje a pantalla completa.

* **[!UICONTROL Tasa de participación]**, esta es una métrica calculada de Adobe Analytics y es el resultado de dividir el número de pulsaciones entre el número de impresiones.

## Mensajes push {#section_BEAFD858CA194185B6F88903446058E9}

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
   * **[!UICONTROL En ejecución]**
   * **[!UICONTROL Ejecutado]**

* **[!UICONTROL Publicado]**

   El número de tokens de dispositivo enviados correctamente al servicio de notificaciones push de Apple/la mensajería de Firebase Cloud (APNS/FCM) por mandar el mensaje a los dispositivos de los usuarios.

* **[!UICONTROL Fallido]**

   El número de tokens de dispositivo que no se han enviado correctamente a APNS/FCM. Algunas posibles razones de los errores:

   * El pushID no es válido

   * La plataforma push (APNS, FCM, etc.) elegida para insertar el mensaje no existe en la aplicación del trabajo. Por ejemplo, la plataforma podría recopilar tokens push de iOS, pero no tiene el servicio APNS configurado.

   * El mensaje puede haber fallado porque el servicio push no estaba correctamente configurado o el sistema Mobile Services está fuera de servicio.
   >[!IMPORTANT]
   >
   >Si tiene un número inusualmente alto de errores, compruebe la configuración de los servicios push. Si los servicios push parecen estar configurados correctamente, póngase en contacto con el servicio de atención al cliente de Adobe.

* **[!UICONTROL Bloqueado]**

   El número de tokens de dispositivo que ya no son válidos para su envío a APNS o FCM. Esto suele significar que la aplicación se ha desinstalado del dispositivo o que el usuario ha cambiado la configuración relacionada con la recepción de mensajes. Android e iOS difieren en la forma de considerar un token bloqueado. Los tokens de Android aparecen inmediatamente en el recuento de bloqueados. Los tokens de iOS aparecen inicialmente como publicados, pero, basándose en la información de APNS, aparecen como bloqueados en los siguientes mensajes.
