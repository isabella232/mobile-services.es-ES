---
description: Esta información resulta útil para solucionar los problemas de mensajería en la aplicación.
keywords: móvil
seo-description: Esta información resulta útil para solucionar los problemas de mensajería en la aplicación.
seo-title: Solucionar los problemas de la mensajería en la aplicación
solution: Experience Cloud,Analytics
title: Resolucion de problemas de la mensajería en la aplicación
topic: Métricas
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Solucionar los problemas de la mensajería en la aplicación{#troubleshooting-in-app-messaging}

Esta información resulta útil para solucionar los problemas de mensajería en la aplicación.

Si completó todos los requisitos de la mensajería en la aplicación y aun así los mensajes no aparecen, compruebe los siguientes puntos:

## ¿Ha aplicado la nueva configuración y el nuevo SDK a la aplicación?

* Compruebe que el SDK sea de la versión 4.2 o superior y que esté correctamente configurado.

* Asegúrese de que haya una sección [Mensajería](/help/using/in-app-messaging/in-app-messaging.md) en la configuración (el archivo JSON descargado) o el punto final remoto Mensajes para que se pueda recuperar desde la administración dinámica de etiquetas.

## Mi mensaje de pantalla completa en Android no aparece. Estoy usando el SDK y la configuración correctos y mis activadores se están cumpliendo.

¿Ha actualizado el archivo de manifiesto para definir la actividad de pantalla completa?

## Mi mensaje de notificación local en Android no funciona.

Verifique si ha declarado en el manifiesto el receptor local de emisiones de notificación. Para obtener más información, consulte el paso número 1 en [Mensajería en la aplicación](/help/android/messaging-main/messaging/messaging.md).

## ¿El mensaje está activo?

Fíjese en la vista de lista en la columna **[!UICONTROL Estado]** de la página Administrar mensaje en la aplicación y verifique si el mensaje está activo.

## Busque la configuración *Mostrar una vez*, *Mostrar siempre*, *Mostrar sin conexión* en la página Audience.

Compruebe si esta configuración es correcta. En la página Audiencia, revise las opciones de la pestaña **[!UICONTROL Activador]**, donde puede especificar la frecuencia con que se muestra el mensaje.

## Si se usa el evento de inicio como activador...

El inicio solo se desencadena en una nueva sesión. Para obtener información sobre cuándo comienza una sesión consulte `lifecycleTimeout` en el archivo de [ADBMobile JSON config](/help/ios/configuration/json-config/json-config.md).

## He actualizado mi mensaje de forma remota, pero en mi aplicación aún aparece el mensaje antiguo.

Complete una de las siguientes tareas:

* A la administración dinámica de etiquetas le puede llevar unos minutos actualizar su punto final con la nueva definición.

   Espere un poco y vuelva a intentarlo.

* La configuración solo se actualiza con un nuevo inicio.

   Si la aplicación se reinició durante el tiempo de espera de sesión del ciclo de vida, es posible que la nueva configuración no se haya descargado.

## Mi imagen no se adapta exactamente al espacio proporcionado en la plantilla.

La plantilla de pantalla completa de mensaje en la aplicación admite la visualización de una imagen, ya sea desde un servidor remoto (URL de imagen) o desde el paquete de aplicación (imagen agrupada). La imagen debe tener un formato de imagen estándar, por ejemplo, JPG, GIF o PNG.

Puesto que las pantallas de los dispositivos pueden tener diferentes dimensiones, es probable que la imagen no se ajuste exactamente al espacio proporcionado en la plantilla. La plantilla siempre muestra el centro de la imagen y recorta (vertical) o funde (horizontal) los laterales si esta no cabe.

Aquí detallamos la colocación exacta y las reglas de cambio de dimensión para cada orientación:

* **Vertical:** la imagen se escala a una altura de 195 px en teléfonos, 529 px en tabletas, centrada si el ancho de la imagen es inferior al del dispositivo y recortada si el ancho de la imagen es superior al del dispositivo.

* **Horizontal:** la imagen se escala al 100 % de la altura del dispositivo, mientras que el ancho se escala al 75 % del ancho del dispositivo con un fundido de salida a la derecha.

   Si tiene problemas con la plantilla de pantalla completa, puede descargar y utilizar la plantilla de HTML personalizado. La plantilla de HTML personalizado proporciona más flexibilidad para las imágenes y ofrece un control total de la plantilla.

## Mis mensajes no reflejan los cambios o actualizaciones que he realizado en la interfaz de usuario.

El SDK trae mensajes nuevos o actualizados al momento del lanzamiento del ciclo de vida. Esto solo se produce cuando la aplicación se cierra o se coloca en segundo plano por un tiempo superior al valor del tiempo de espera del ciclo de vida y, después, vuelve a abrirse.

Complete los pasos siguientes:

1. Corrija la dirección URL de los mensajes en el archivo de configuración para verificar que se ha actualizado el mensaje remoto (por ejemplo, `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Cierre la aplicación.
1. Espere un espacio de tiempo superior al `lifecycleTimeout` en el archivo de configuración.
1. Abra la aplicación, vaya al sitio donde el mensaje deba aparecer y verifique que se ha actualizado.