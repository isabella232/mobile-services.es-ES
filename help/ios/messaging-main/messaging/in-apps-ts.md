---
description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
keywords: mobile
seo-description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
seo-title: Resolucion de problemas de la mensajería en la aplicación
solution: Marketing Cloud,Analytics
title: Resolucion de problemas de la mensajería en la aplicación
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '595'
ht-degree: 100%

---


# Resolucion de problemas de la mensajería en la aplicación {#troubleshooting-in-app-messaging}

Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.

Si ha completado todos los requisitos para la mensajería en la aplicación, pero no aparecen los mensajes, verifique los siguientes elementos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

Compruebe que el SDK sea de la versión 4.2 o superior y que esté correctamente configurado. Asegúrese de tener una sección `Messages` en la configuración (archivo JSON descargado) o un punto final remoto Mensajes para que se pueda recuperar desde la administración dinámica de etiquetas.

## Mi mensaje de pantalla completa en Android no aparece. Estoy utilizando el SDK, la configuración y los activadores correctos.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Asegúrese de haber declarado en el manifiesto el receptor local de emisiones de notificación. Para obtener más información, consulte el paso 2 en [Activación de la mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Revise la vista de lista en la página Administrar mensaje en la aplicación de la columna Estado y verifique si está activo.

## En la pestaña Audiencia encontrará las opciones de configuración *Mostrar una vez*, *Mostrar siempre* y *Mostrar sin conexión*.

Compruebe que estos ajustes están definidos de la forma que desea. En la pestaña **[!UICONTROL Audiencia]**, revise las opciones de **[!UICONTROL Activador]**, que le permiten especificar con qué frecuencia se muestran los mensajes.

## Si se usa el evento de lanzamiento como activador…

El inicio solo se desencadena en una nueva sesión. Para obtener más información acerca de cuándo comienza una sesión, consulte la fila `lifecycleTimeout` en el archivo de configuración JSON. Para obtener más información, consulte [Configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

## He actualizado mi mensaje de forma remota, pero en mi aplicación aún aparece el mensaje antiguo.

Complete una de las siguientes tareas:

* A la administración dinámica de etiquetas le puede llevar unos minutos actualizar su punto final con la nueva definición.

   Espere un poco y vuelva a intentarlo.

* La configuración solo se actualiza con un nuevo inicio.
Si la aplicación se reinició durante el tiempo de espera de sesión de ciclo vital, es posible que la nueva configuración no se haya descargado.

   Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

## La imagen no se ajusta exactamente al espacio proporcionado por la plantilla.

La plantilla de pantalla completa Mensaje en la aplicación admite la visualización de una imagen desde un servidor remoto (URL de imagen) o desde el paquete de aplicaciones (imagen agrupada). La imagen debe tener un formato de imagen estándar como JPG, GIF o PNG.

Puesto que las pantallas de los dispositivos pueden tener diferentes dimensiones, es probable que la imagen no se ajuste exactamente al espacio proporcionado en la plantilla. La plantilla se centra en mostrar el centro de la imagen y, si esta no encaja, recorta (vertical) o difumina (horizontal) los lados.

Aquí detallamos la colocación exacta y las reglas de cambio de dimensión para cada orientación:

* **Vertical**:
   * Una altura de 195 píxeles para teléfonos
   * Una altura de 529 píxeles para tabletas
   * Centrado si el ancho de la imagen es menor que el ancho del dispositivo.
   * Se recorta si el ancho de la imagen es mayor que el ancho del dispositivo.

* **Horizontal**:
   * La imagen se amplió al 100% de la altura del dispositivo.
   * El ancho es del 75% del dispositivo, con una atenuación a la derecha.

Si tiene problemas con la plantilla de pantalla completa, puede descargar y usar la plantilla HTML personalizada. Esta plantilla proporciona más flexibilidad para las imágenes y permite un control total de la plantilla.

## Los mensajes de la aplicación en un iPhone X no se muestran en modo de pantalla completa.

Para mostrar mensajes de la aplicación en modo de pantalla completa en un iPhone X:

1. Agregue `viewport-fit=cover` en la metaetiqueta.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configure el relleno adecuado en la CSS para el elemento de la interfaz de usuario superior, como:

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   Esta configuración evita que los elementos de la interfaz de usuario entren en conflicto con la barra de estado.
