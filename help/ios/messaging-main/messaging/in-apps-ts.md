---
description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
keywords: móvil
seo-description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
seo-title: Resolucion de problemas de la mensajería en la aplicación
solution: Experience Cloud,Analytics
title: Resolucion de problemas de la mensajería en la aplicación
topic: Métricas
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: ht
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Resolucion de problemas de la mensajería en la aplicación{#troubleshooting-in-app-messaging}

Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.

Si ha completado todos los requisitos para la mensajería en la aplicación, pero no se muestran mensajes, compruebe los siguientes elementos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

Compruebe que el SDK sea de la versión 4.2 o superior y que esté correctamente configurado. Asegúrese de tener una sección `Messages` en la configuración (archivo JSON descargado) o un punto final remoto Mensajes para que se pueda recuperar desde la administración dinámica de etiquetas.

## Mi mensaje de pantalla completa en Android no aparece. Estoy usando el SDK y la configuración correctos y mis activadores se están cumpliendo.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Asegúrese de haber declarado en el manifiesto el receptor local de emisiones de notificación. Para obtener más información, consulte el paso 2 en [Activación de la mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Vaya a la vista de lista de la página Administrar mensajes en la aplicación y compruebe si está activo en la columna Estado.

## En la pestaña Audiencia encontrará las opciones de configuración *Mostrar una vez*, *Mostrar siempre* y *Mostrar sin conexión*.

Compruebe que estos ajustes están definidos de la forma que desea. En la ficha **[!UICONTROL Audiencia]**, revise las opciones de **[!UICONTROL Activador]**, que le permiten especificar con qué frecuencia se muestran los mensajes.

## Si se usa el evento de inicio como activador...

El inicio solo se desencadena en una nueva sesión. Para obtener más información acerca de cuándo comienza una sesión, consulte la fila `lifecycleTimeout` en el archivo de configuración JSON. Para obtener más información, consulte [Configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

## He actualizado mi mensaje de forma remota, pero en mi aplicación aún aparece el mensaje antiguo.

Complete una de las siguientes tareas:

* A la administración dinámica de etiquetas le puede llevar unos minutos actualizar su punto final con la nueva definición.

   Espere un poco y vuelva a intentarlo.

* La configuración solo se actualiza con un nuevo inicio. 
Si la aplicación se reinició durante el tiempo de espera de sesión de ciclo vital, es posible que la nueva configuración no se haya descargado.

   Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md).

## Mi imagen no se adapta exactamente al espacio proporcionado en la plantilla.

La plantilla de pantalla completa de mensaje en la aplicación admite la visualización de una imagen desde un servidor remoto (URL de imagen) o desde el paquete de aplicaciones (imagen agrupada). La imagen debe tener un formato de imagen estándar como JPG, GIF o PNG.

Puesto que las pantallas de los dispositivos pueden tener diferentes dimensiones, es probable que la imagen no se ajuste exactamente al espacio proporcionado en la plantilla. La plantilla se centra en mostrar el centro de la imagen y, si esta no encaja, recorta (vertical) o difumina (horizontal) los lados.

Aquí detallamos la colocación exacta y las reglas de cambio de dimensión para cada orientación:

* **Vertical**:
   * Una altura de 195 píxeles para teléfonos
   * Una altura de 529 píxeles para tabletas
   * Centrada si la anchura de la imagen es menor que la del dispositivo.
   * Recortada si la anchura de la imagen es mayor que la del dispositivo.

* **Horizontal**:
   * La imagen se escala al 100 % de la altura del dispositivo.
   * La anchura es el 75 % de la del dispositivo, con difuminado en la derecha.

Si tiene problemas con la plantilla de pantalla completa, puede descargar y utilizar la plantilla HTML personalizada. Esta plantilla proporciona más flexibilidad para las imágenes y ofrece un control total de la plantilla.

## Los mensajes en aplicación en un iPhone X no se muestran en el modo de pantalla completa.

Para mostrar los mensajes en aplicación en el modo de pantalla completa en un iPhone X:

1. Agregue `viewport-fit=cover` en la metaetiqueta.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Configure el relleno apropiado en el CSS para los elementos UI principales como:

   ```html
   topelement {
     padding-top:20px;
     /*Status bar height on iOS 11.0*/
     padding-top:constant(safe-area-inset-top);
     /*Status bar height on iOS 11+ */
     padding-top:env(safe-area-inset-top);
     } 
   ```

   Esta configuración evita que los elementos de UI entren en conflicto con la barra de estado.
