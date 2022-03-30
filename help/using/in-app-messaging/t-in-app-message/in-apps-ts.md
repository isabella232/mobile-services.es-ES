---
description: Esta información resulta útil para solucionar los problemas de mensajería en la aplicación.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Resolucion de problemas de la mensajería en la aplicación
topic-fix: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
exl-id: 6be5beef-3bde-49f8-9ec0-c5d32bd43045
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 100%

---

# Resolucion de problemas de la mensajería en la aplicación {#troubleshooting-in-app-messaging}

Esta información resulta útil para solucionar los problemas de mensajería en la aplicación.

Si ha completado todos los requisitos para la mensajería en la aplicación, pero no aparecen los mensajes, controle los siguientes elementos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

* Compruebe que el SDK sea de la versión 4.2 o superior y que esté correctamente configurado.

* Asegúrese de que haya una sección [Mensajería](/help/using/in-app-messaging/in-app-messaging.md) en la configuración (el archivo JSON descargado) o el punto final remoto Mensajes para que se pueda recuperar desde la administración dinámica de etiquetas.

## Mi mensaje de pantalla completa en Android no aparece. Estoy utilizando el SDK, la configuración y los activadores correctos.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Verifique si ha declarado en el manifiesto el receptor local de emisiones de notificación. Para obtener más información, consulte el paso número 1 en [Mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Fíjese en la vista de lista en la columna **[!UICONTROL Estado]** de la página Administrar mensaje en la aplicación y verifique si el mensaje está activo.

## Busque la configuración *Mostrar una vez*, *Mostrar siempre*, *Mostrar sin conexión* en la página Audience.

Compruebe si esta configuración es correcta. En la página Audiencia, revise las opciones de la pestaña **[!UICONTROL Activador]**, donde puede especificar la frecuencia con que se muestra el mensaje.

## Si se usa el evento de lanzamiento como activador…

El inicio solo se desencadena en una nueva sesión. Para obtener información sobre cuándo comienza una sesión consulte  `lifecycleTimeout` en el archivo de [ADBMobile JSON config](/help/ios/configuration/json-config/json-config.md).

## He actualizado mi mensaje de forma remota, pero en mi aplicación aún aparece el mensaje antiguo.

Complete una de las siguientes tareas:

* A la administración dinámica de etiquetas le podría llevar unos minutos actualizar su punto final con la nueva definición.

   Espere un poco y vuelva a intentarlo.

* La configuración solo se actualiza con un nuevo inicio.

   Si la aplicación se reinició durante el tiempo de espera de sesión de ciclo vital, es posible que la nueva configuración no se haya descargado.

## La imagen no se ajusta exactamente al espacio proporcionado por la plantilla.

La plantilla de pantalla completa Mensaje en la aplicación admite la visualización de una imagen desde un servidor remoto (URL de imagen) o desde el paquete de aplicaciones (imagen agrupada). La imagen debe tener un formato de imagen estándar, por ejemplo, JPG, GIF o PNG.

Debido a que las pantallas de los dispositivos tienen muchas dimensiones diferentes, es probable que la imagen no se ajuste exactamente al espacio proporcionado por la plantilla. La plantilla siempre se centra en mostrar el centro de la imagen y recorta (vertical) o funde (horizontal) los lados si la imagen no cabe.

Aquí detallamos la colocación exacta y las reglas de cambio de dimensión para cada orientación:

* **Vertical**, donde la imagen se escala a una altura de 195 píxeles para teléfono, 529 píxeles para tablet, centrada si la anchura de la imagen es menor que la del dispositivo y recortada si la anchura de la imagen es mejor que la del dispositivo.

* **Horizontal**, donde la imagen se amplía al 100% de la altura del dispositivo, la anchura es del 75% del dispositivo y con atenuación a la derecha.

   Si tiene problemas con la plantilla de pantalla completa, puede descargar y usar la plantilla HTML personalizada. La plantilla HTML personalizada proporciona más flexibilidad para las imágenes y permite un control total de la plantilla.

## Mis mensajes no reflejan los cambios o las actualizaciones que he realizado en la interfaz de usuario.

El SDK obtiene mensajes nuevos o actualizados en el momento del inicio del ciclo vital. Esto solo se produce cuando la aplicación se cierra o se pone en segundo plano para buenos valores que superan el tiempo de espera del ciclo vital y luego se vuelve a abrir.

Complete los pasos siguientes:

1. Corrija la dirección URL de los mensajes en el archivo de configuración para verificar que se ha actualizado el mensaje remoto (por ejemplo, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Cierre la aplicación.
1. Espere un espacio de tiempo superior al `lifecycleTimeout` en el archivo de configuración.
1. Abra la aplicación, vaya al sitio donde el mensaje deba aparecer y verifique que se ha actualizado.
