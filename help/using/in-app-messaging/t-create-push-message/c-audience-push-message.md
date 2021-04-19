---
description: Puede definir y configurar las opciones de audiencia para los mensajes push, incluidas las opciones de intervalos de fechas, segmentos de Analytics y segmentos personalizados.
keywords: móvil
seo-description: Puede definir y configurar las opciones de audiencia para los mensajes push, incluidas las opciones de intervalos de fechas, segmentos de Analytics y segmentos personalizados.
seo-title: 'Audience: Definir y configurar segmentos de audiencias para los mensajes push'
solution: Experience Cloud,Analytics
title: 'Audience: Definir y configurar segmentos de audiencias para los mensajes push'
topic-fix: Metrics
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
exl-id: d1062a76-2e72-4649-8497-58617a7a47cb
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 100%

---

# Audience: mensajes push {#audience-define-and-configure-audience-segments-for-push-messages}

Puede definir y configurar las opciones de audiencia para los mensajes push, incluidas las opciones de intervalos de fechas, segmentos de Analytics y segmentos personalizados.

## Definir segmentos de audiencia {#section_7C4D2393CF7441959FE2381A02867CAC}

Cuando se crea un segmento de audiencia para mensajería push, este podría incluir a usuarios de una o varias aplicaciones porque los grupos de informes o los grupos de informes virtuales pueden contener datos de una aplicación o más. Para obtener información sobre los grupos de informes virtuales, consulte   [Grupos de informes virtuales](/help/using/manage-apps/c-mob-vrs.md).

En Adobe Mobile Services, los especialistas en marketing solo pueden insertar una aplicación por plataforma. Si los especialistas en marketing intentan insertar segmentos que contienen usuarios de varias aplicaciones, se muestra una advertencia que indica que continuar puede provocar errores de inserción graves y la posible lista de usuarios bloqueados. Si se produce un error de inserción, consulte *Resolver errores de mensajes push* en   [Solucionar los problemas de la mensajería push](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Para usar datos de Audience Manager en su definición de segmento, consulte [Audience Analytics](https://docs.adobe.com/content/help/es-ES/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>Si los usuarios de la aplicación están en una lista bloqueados, los especialistas en marketing **nunca** podrán volver a enviarles mensajes push.

Si elige un segmento de audiencia que contiene usuarios de varias aplicaciones, podría aparecer esta alerta:

![nombre de aplicación múltiple](assets/multiple_appname.png)

El nombre de la aplicación se basa en la versión reducida del appId, que el SDK de Mobile Services envía automáticamente a Adobe Analytics con el formato `<app name> <version number> (<bundle id>)`.

>[!TIP]
>
>El número de versión es opcional.

Se eliminan hasta 6 conjuntos de números para la versión y 5 conjuntos de números para el ID del paquete.

Por ejemplo:

* `Bea[rd]cons 1.0 (123)` aparecerá como `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` aparecerá como `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` aparecerá como `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` aparecerá como `Bea[rd]cons (.6)`

Para enviar el mensaje push a las aplicaciones de la lista, seleccione la casilla de verificación **[!UICONTROL Sí, deseo continuar.]** y haga clic en **[!UICONTROL Enviar]**.

## Prácticas recomendadas

Tenga presentes estas recomendaciones:

* Para reducir las confusiones, **evite** definir grupos de informes virtuales de aplicación móvil que contengan datos de varias aplicaciones.
* Use un ID único de aplicación como parte de un segmento de audiencia **siempre** que quiera enviar un mensaje push.
Esto garantiza que las notificaciones push se envíen a un segmento de audiencia que **solo** pertenezca a una aplicación.

### Ejemplos

A continuación se proporcionan algunos ejemplos para ayudarle a definir correctamente los segmentos:

**Sí**: El especialista en marketing proporciona certificados push para las versiones de iOS y Android de una aplicación, por ejemplo, para Adobe Photoshop. El especialista en marketing puede enviar una notificación push a un segmento de usuario que abarque ambas plataformas.

**No**: Los especialistas en marketing proporcionan certificados push para las versiones de iOS y Android de una aplicación, por ejemplo, para Adobe Photoshop. Si el especialista en marketing crea y usa un segmento de *todos los usuarios activos en los últimos 30 días*, solo los usuarios de la aplicación Adobe Photoshop de iOS y Android reciben la notificación push y todos los usuarios de la aplicación Adobe Illustrator de iOS y Android pasarán a estar en la lista de bloqueados. Si desea ver un ejemplo más detallado, consulte *Resolver errores de mensajes push* en   [Solucionar los problemas de la mensajería push](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configurar segmentos de audiencia {#section_A92C60885A30421B8150820EC1CCBF13}

1. Vaya a la página Audience para ver un nuevo mensaje push.

   Para obtener más información, consulte [Crear un mensaje en la aplicación](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   Al configurar las opciones de audiencia, recuerde la siguiente información **importante**:

   * La **[!UICONTROL Audiencia participante estimada]** es el número de dispositivos que se ajustan al segmento de Adobe Analytics **y** el número de dispositivos participantes.

      Puede realizar una vista del número de usuarios de los segmentos seleccionados que han habilitado la recepción de mensajes y que recibirán el mensaje push. El número total de usuarios de la aplicación se muestra por debajo de la estimación, independientemente del estado de inclusión.

   * El **[!UICONTROL Total]** es el número de dispositivos que se ajustan al segmento de Adobe Analytics.

   * Los mensajes push se envían a los dispositivos que forman parte de un segmento definido de Adobe Analytics **y** que hayan elegido recibirlos.

      Esto significa que el SDK ha enviado el valor `True` en la eVar Inclusión del mensaje push.

   * Aunque el dispositivo tenga un token válido, el mensaje no se inserta en el dispositivo a menos que Adobe Analytics haya establecido la marca de inclusión.

   * Para obtener más información sobre la solución de problemas con la mensajería push, consulte estos temas:

      * [Mensajería push en iOS](https://docs.adobe.com/content/help/es-ES/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Mensajería push en Android](https://docs.adobe.com/content/help/es-ES/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. Rellene los campos siguientes:

   * **[!UICONTROL Durante el]**

      Escriba el lapso de tiempo para la audiencia estimada. En la lista desplegable **[!UICONTROL Durante el]**, seleccione una opción:

   * **[!UICONTROL Último]** permite seleccionar un lapso de tiempo relativo (por ejemplo, los últimos 7, 30 o 60 días) desde el momento en el que el mensaje está programado para su inserción.

      Por ejemplo, si selecciona los últimos 30 días y programa la inserción del mensaje para el 31 de octubre, la audiencia estimada sería el número de usuarios que han decidido recibir mensajes push los 30 días anteriores al 31 de octubre.

   * **[!UICONTROL Intervalo estático]** permite seleccionar un intervalo estático mediante la selección de las fechas de inicio y fin para el rango de audiencia estimado.

      En el ejemplo anterior, si selecciona un intervalo de fechas del 1 al 15 de octubre, pero programa la inserción del mensaje para el 31 de octubre, la audiencia estimada sería el número de usuarios que han elegido recibir mensajes push en el intervalo de fechas estático especificado (del 1 al 15 de octubre).

   * **[!UICONTROL Segmentos de Analytics]**

      Seleccione un segmento de Adobe Analytics existente en la lista desplegable. Para obtener más información, consulte [Generar segmentos](https://docs.adobe.com/content/help/es-ES/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL Segmentos personalizados]**

      Seleccione una métrica o variable en la lista desplegable (por ejemplo, **[!UICONTROL Días transcurridos desde el último uso]** o **[!UICONTROL Punto de interés]**) y, a continuación, configure el filtro como desee. Por ejemplo, el siguiente segmento personalizado está dirigido a los usuarios que disponen de un teléfono móvil con iOS y que se encuentran en la región de California (Estados Unidos).
   >[!IMPORTANT]
   >
   >En la sección **[!UICONTROL Crear audiencia]**, si hace clic en **[!UICONTROL Y]**, aparece un cuadro de diálogo donde se le recuerda que todas las aplicaciones de la lista **deben** tener un certificado válido. Si hace clic en **[!UICONTROL O]** aparece el cuadro de diálogo predeterminado. Para obtener más información sobre los certificados válidos y los grupos de informes, consulte [Grupos de informes virtuales](/help/using/manage-apps/c-mob-vrs.md).
