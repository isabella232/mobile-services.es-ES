---
description: Notas de la versión y problemas conocidos de SDK 4.x para iOS en soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos de SDK 4.x para iOS en soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Experience Cloud,Analytics
title: Notas de la versión
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 6c8020b88d22489f86853274d29dbceee504aa06
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 100%

---


# Notas de la versión {#release-notes}

Estas son las notas de la versión, los problemas conocidos y la información sobre correcciones rápidas de los SDK para iOS 4.x para soluciones de Experience Cloud:

**4 de noviembre de 2020: Versión 4.20.0**

* Servicio de ID de visitante: parámetro de estado device_permission añadido cuando se llama a setAdvertisingIdentifier después de habilitar o deshabilitar el seguimiento de anuncios.
* Analytics: se ha corregido un error que retrasaba el envío de visitas de Analytics en una instalación cuando iAd.framework está vinculado y el dispositivo tiene habilitado el seguimiento de anuncios limitado.

**16 de julio de 2020: Versión 4.19.3**

* General: se ha corregido un error que impedía que las direcciones URL de vinculación profunda con varios signos de igual en el parámetro de consulta se gestionaran correctamente.

**24 de marzo de 2020: Versión 4.19.2**

* General: se corrigieron algunas filtraciones en el código de Target.

**12 de marzo de 2020: Versión 4.19.1**

* General: Se ha resuelto un posible bloqueo que se producía cuando se incluyen enumeraciones de Swift en los datos de contexto para las llamadas de seguimiento.
* Target: El ID de sesión de Target ahora se agregará como parámetro de datos de contexto “a.target.sessionId” en la visita interna de Analytics para Target enviada a Adobe Analytics.

**4 de febrero de 2020: Versión 4.19.0**

* Ciclo de vida: se ha agregado una nueva API, pauseCollectingLifecycleData, para mitigar los datos anormales de la duración de la sesión notificados desde algunos dispositivos iOS antiguos.

**8 de noviembre de 2019: Versión 4.18.9**

* En la mensajería de la aplicación: se ha corregido un error que impedía cargar imágenes en caché o agrupadas en los mensajes de pantalla completa.

**20 de septiembre de 2019: Versión 4.18.8**

* Mensajería en la aplicación:

   * En dispositivos con iOS 10 o posterior, el marco de trabajo `UserNotifications` ahora se utiliza para programar notificaciones locales para aplicaciones vinculadas al `UserNotifications.framework`.
   * Los mensajes a pantalla completa ahora utilizan WKWebViews de `WebKit.framework`, que debe estar vinculado en el proyecto Xcode.
   * Se ha corregido un error por el que la carga de pulsaciones no podía utilizarse como atributo para la mensajería dentro de la aplicación.
   * Se ha corregido un problema de bloqueo.

* General: Se ha corregido un error por el que los datos del SDK se sincronizaban con la aplicación watchOS emparejada en cada llamada de Analytics.

**2 de agosto de 2019: Versión 4.18.7**

* Se ha revertido un cambio introducido en la versión 4.18.6 que, en algunos entornos, causaba un bloqueo en dispositivos que ejecutaban una versión de iOS anterior a la 11.0.

* Adobe Target: Se ha agregado la propiedad `requestLocationParameters` en `ADBTargetRequestObject`, que permite enviar la variable impressionId con solicitudes de Target.

**18 de julio de 2019: Versión 4.18.6**

* Adobe Target: Todas las solicitudes ahora incluyen al cliente y `sessionId` en los parámetros de consulta de URL.
* Adobe Target: Se ha corregido una fuga de memoria.
* Servicio de ID de visitante: Las API `visitorAppendToURL` y `visitorGetUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**5 de junio de 2019: Versión 4.18.5**

* Analytics: Anexe el estado de la opción de inclusión push a los datos del ciclo vital cuando las notificaciones push estén habilitadas.

**24 de mayo de 2019: Versión 4.18.4**

* Servicio de ID de visitante: se ha aumentado el tiempo de espera de retorno para la API
   `visitorGetUrlVariablesAsync` a 30 segundos.

* Servicio de ID de visitante: La llamada de API `setPushIdentifier` ahora envía una llamada de sincronización al servicio de ID de visitante cada vez que se realiza la llamada.

Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html).
