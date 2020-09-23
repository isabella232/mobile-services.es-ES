---
description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
keywords: mobile
seo-description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
seo-title: Resolución de problemas de mensajería en la aplicación
solution: Experience Cloud,Analytics
title: Resolución de problemas de mensajería en la aplicación
topic: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 94%

---


# Resolución de problemas de mensajería en la aplicación{#troubleshooting-in-app-messaging}

Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.

Si ha completado todos los requisitos para la mensajería en la aplicación, pero no se muestran mensajes, compruebe los siguientes elementos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

Asegúrese de tener una sección [Mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md) en la configuración (archivo JSON descargado) o un punto final remoto Mensajes para que se pueda recuperar desde la administración dinámica de etiquetas.

## Mi mensaje de pantalla completa en Android no aparece. Estoy utilizando el SDK, la configuración y los activadores correctos.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Asegúrese de haber declarado en el manifiesto el receptor local de emisiones de notificación. Para obtener más información, consulte el paso 2 en *Activación de la mensajería en la aplicación* en [Mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Para comprobar si su mensaje está activo, vaya a la página Administrar mensaje en la aplicación y, en la columna **[!UICONTROL Estado]**, compruebe la lista de mensajes.

## En la pestaña Audiencia encontrará las opciones de configuración *Mostrar una vez*, *Mostrar siempre* y *Mostrar sin conexión*.

Compruebe que estos ajustes están definidos de la forma que desea. En la pestaña **[!UICONTROL Audiencia]**, revise las opciones de **[!UICONTROL Activador]**, que le permiten especificar con qué frecuencia se muestran los mensajes.

## Si se usa el evento de inicio como activador...

El inicio solo se desencadena en una nueva sesión. Para obtener más información acerca de cuándo comienza una sesión, consulte la fila `lifecycleTimeout` en la [configuración JSON](/help/android/configuration/json-config/json-config.md).

## He actualizado mi mensaje de forma remota, pero en mi aplicación aún aparece el mensaje antiguo.

Recuerde la información siguiente:

* A la administración dinámica de etiquetas le puede llevar unos minutos actualizar su punto final con la nueva definición. Espere un poco y vuelva a intentarlo.
* La configuración solo se actualiza con un nuevo inicio. Si la aplicación se reinició durante el tiempo de espera de sesión de ciclo vital, es posible que la nueva configuración no se haya descargado.

Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

## La imagen no se ajusta exactamente al espacio proporcionado por la plantilla.

La plantilla de pantalla completa Mensaje en la aplicación admite la visualización de una imagen desde un servidor remoto (URL de imagen) o desde el paquete de aplicaciones (imagen agrupada). La imagen debe tener un formato de imagen estándar como JPG, GIF o PNG. Puesto que las pantallas de los dispositivos pueden tener diferentes dimensiones, es probable que la imagen no se ajuste exactamente al espacio proporcionado en la plantilla. La plantilla se centra en mostrar el centro de la imagen y, si esta no encaja, recorta (vertical) o difumina (horizontal) los lados.

Aquí detallamos la colocación exacta y las reglas de cambio de dimensión para cada orientación:

* **Vertical**
   * Una altura de 195 píxeles para teléfonos.
   * Una altura de 529 píxeles para tabletas.
   * Centrado si el ancho de la imagen es menor que el ancho del dispositivo.
   * Se recorta si el ancho de la imagen es mayor que el ancho del dispositivo.

* **Horizontal**
   * La imagen se amplió al 100% de la altura del dispositivo.
   * El ancho es del 75% del dispositivo, con una atenuación a la derecha.

   Si tiene problemas con la plantilla de pantalla completa, puede descargar y usar la plantilla HTML personalizada. Esta plantilla proporciona más flexibilidad para las imágenes y permite un control total de la plantilla.

