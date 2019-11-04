---
description: En la interfaz de usuario de Adobe Mobile Services, puede programar un mensaje push para que se entregue inmediatamente, más tarde o como evento recurrente. Estos eventos se pueden programar con periodicidad diaria, semanal o mensual.
keywords: móvil
seo-description: En la interfaz de usuario de Adobe Mobile Services, puede programar un mensaje push para que se entregue inmediatamente, más tarde o como evento recurrente. Estos eventos se pueden programar con periodicidad diaria, semanal o mensual.
seo-title: Programación  Mensaje push
solution: Experience Cloud,Analytics
title: Programación  Mensaje push
topic: Métricas
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
translation-type: ht
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Programación: mensajes push{#schedule-push-message}

En la interfaz de usuario de Adobe Mobile Services, puede programar un mensaje push para que se entregue inmediatamente, más tarde o como evento recurrente. Estos eventos se pueden programar con periodicidad diaria, semanal o mensual.

>[!TIP]
>
>Los usuarios pueden modificar la configuración de programación en un trabajo de mensaje push en cualquier momento. Si la fecha para enviar un mensaje con programación recurrente no existe, por ejemplo, un trabajo con recurrencia mensual todos los días 31, el día 31 de febrero (o quinto martes del mes) no se envía ningún mensaje.

Recuerde la información siguiente:

* El formato de fecha y hora correcto es `hh:mm` y `mm/dd/yyyy`.

* Un mensaje programado se puede editar del modo siguiente:

   * Cambiar la fecha por otra posterior.
   * Se puede cambiar el intervalo de repetición por otro intervalo.

      Por ejemplo, si originalmente tenía un mensaje que se enviaba todos los días, puede modificar la recurrencia para que sea mensual.

## Antes de programar mensajes push recurrentes

Antes de programar mensajes push recurrentes, **debe** saber lo siguiente:

* Las opciones que se muestran en la lista desplegable **[!UICONTROL Repetir]** dependen de la fecha que escriba o seleccione.

   Por ejemplo, si escribe `Saturday, October 7`, se muestran las siguientes opciones:

   * **[!UICONTROL Nunca]**
   * **[!UICONTROL Cada día]**
   * **[!UICONTROL Cada sábado]**
   * **[!UICONTROL Día 7 de cada mes]**
   * **[!UICONTROL Primer sábado de cada mes]**

* Los mensajes push se programan y envían según la hora del meridiano de Greenwich (GMT).

   Por ejemplo, si programa un mensaje recurrente para que se envíe todos los sábados a las 12:00 (mediodía) **PST**, a partir del 7 de octubre el mensaje se enviará los sábados a las 19:00 **GMT**.
* Los mensajes se envían de forma distinta dependiendo de si se encuentra en EE. UU., Europa o Asia.

   Por ejemplo, si está en San José (California), y programa un mensaje para que se envíe el ***31 de octubre*** a las 17:30 **PST**, este se enviará el ***1 de noviembre*** a las 00:30 **GMT**. Si se halla en Tokio y programa un mensaje para que se envíe el ***1 de enero*** a las 5:30, se enviará el ***31 de diciembre*** a las 20:30 **GMT**.
* Los mensajes push se envían una hora antes o después, según el horario de ahorro energético.
* Al consultar el informe de los mensajes push, estos se muestran en la zona horaria local configurada en su sistema.

   Por ejemplo, si la hora de inicio son las 12:00 **PST**, aunque el mensaje se envíe a las 19:00 **GMT**, en el informe se indicará que la hora de envío fue las 12:00 **PST**.

## Programar un mensaje push recurrente {#section_675BD754E5A04423A1751193698A978F}

1. Para enviar un nuevo mensaje push, en la página Programar, seleccione **[!UICONTROL Programado]** o **[!UICONTROL Ahora]**.

   Para obtener más información, consulte [Crear un mensaje en la aplicación](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   Si selecciona **[!UICONTROL Ahora]** el mensaje se inserta inmediatamente. Para evitar que el mensaje se programe inmediatamente, haga clic en **[!UICONTROL Guardar como borrador]**.

   ![](assets/schedule-push-message.png)

1. Si selecciona **[!UICONTROL Programado]**, haga clic en el icono del calendario y seleccione o escriba una fecha de inicio.
1. Escriba una hora. 
1. En **[!UICONTROL Repetir]**, seleccione una de las opciones siguientes:

   * **[!UICONTROL Nunca]**
   * **[!UICONTROL Cada día]**
   * **[!UICONTROL Cada miércoles]**
   * **`<Day x>`del mes**

      Las opciones mostradas cambian dependiendo del día que seleccione o escriba como fecha de inicio.
   * **`<nth day>`de cada mes**

      El valor mostrado cambia dependiendo de la fecha que haya seleccionado o escrito como fecha de inicio.

1. En **[!UICONTROL Finalizar repetición]**, escriba una fecha y hora de finalización.
1. Haga clic en una de las opciones siguientes:

   * **[!UICONTROL Guardar como borrador]**

      Esta opción guarda el mensaje en el formato de borrador. Puede elegir esta opción, bien para guardar un mensaje no terminado, o bien para guardar un mensaje a fin de que otro usuario pueda editarlo y aprobarlo antes de activarlo.

      Si selecciona **[!UICONTROL Ahora]** en el paso anterior, el borrador del mensaje se envía inmediatamente al activarlo. Si ha seleccionado una fecha y hora para insertar el mensaje, este se inserta en función de esta programación.

   * **[!UICONTROL Guardar y programar]**

      Esta opción envía el mensaje en el día y la hora programados.

Para insertar el borrador del mensaje más tarde, realice una de estas tareas:

* Haga clic en **[!UICONTROL Gestionar mensajes]**, seleccione la casilla de verificación que hay junto al mensaje y haga clic en **[!UICONTROL Activar seleccionados]**.
* Haga clic en **[!UICONTROL Guardar y enviar]** para guardar el mensaje y enviarlo.
