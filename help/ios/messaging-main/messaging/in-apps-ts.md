---
description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
keywords: móvil
seo-description: Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.
seo-title: Solucionar los problemas de la mensajería en la aplicación
solution: Marketing Cloud, Analytics
title: Solucionar los problemas de la mensajería en la aplicación
topic: Métricas
uuid: 58533 aa 3-2 eb 2-4597-8525-77 e 4 e 5975 e 56
translation-type: tm+mt
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Esta información le ayuda a solucionar problemas de la mensajería en la aplicación.

Si ha completado todos los requisitos para la mensajería en la aplicación, pero no se muestran mensajes, compruebe los siguientes elementos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

Compruebe que el SDK sea de la versión 4.2 o superior y que esté correctamente configurado. Ensure that you have a `Messages` section in your configuration (downloaded JSON file), or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Mi mensaje de pantalla completa en Android no aparece. Estoy usando el SDK y la configuración correctos y mis activadores se están cumpliendo.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Asegúrese de haber declarado en el manifiesto el receptor local de emisiones de notificación. For more information, see step 2 in [Enabling In-App Messages](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Vaya a la vista de lista de la página Administrar mensajes en la aplicación y compruebe si está activo en la columna Estado.

## Observe *mostrar una vez*, *mostrar siempre*, *mostrar* la configuración sin conexión en la ficha Audiencia.

Compruebe que estos ajustes están definidos de la forma que desea. En la ficha **[!UICONTROL Audiencia]**, revise las opciones de **Activador], que le permiten especificar con qué frecuencia se muestran los mensajes.[!UICONTROL **

## Si se usa el evento de inicio como activador...

El inicio solo se desencadena en una nueva sesión. For more information about when a session begins, see the `lifecycleTimeout` row in the JSON Config file. Para obtener más información, consulte [Configuración JSON de adbmobile](/help/ios/configuration/json-config/json-config.md).

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

Esta es la colocación exacta y las reglas de cambio de dimensión para cada orientación:

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

1. Add `viewport-fit=cover` in the meta tag.

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
