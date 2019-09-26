---
description: Notas de la versión y problemas conocidos de los SDK para iOS 4.x para soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos de los SDK para iOS 4.x para soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Marketing Cloud,Analytics
title: Notas de la versión
topic: Desarrollador e implementación
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notas de la versión {#release-notes}

Estas son las notas de la versión, los problemas conocidos y la información sobre correcciones rápidas de los SDK para iOS 4.x para soluciones de Experience Cloud:

**September 20, 2019: Version 4.18.8**

* In App Messaging:

   * En dispositivos con iOS 10 o posterior, el marco de trabajo ahora se utiliza para programar notificaciones locales para aplicaciones vinculadas al `UserNotifications` `UserNotifications.framework`.
   * Los mensajes a pantalla completa ahora utilizan WKWebViews de `WebKit.framework`, que debe estar vinculado en el proyecto Xcode.
   * Se corrigió un error en el cual la carga útil de pulsaciones no se podía usar como características para la mensajería en la aplicación.
   * Se ha corregido un problema de bloqueo.

* General - Fixed a bug where SDK data was synchronized to the paired watchOS app on every Analytics call.

**2 de agosto de 2019: Versión 4.18.7**

* Se ha revertido un cambio introducido en la versión 4.18.6 que, en algunos entornos, causaba un bloqueo en dispositivos que ejecutaban una versión de iOS anterior a 11.0.

* Adobe Target: Se ha agregado la `requestLocationParameters` propiedad en `ADBTargetRequestObject`, que permite que se envíe la variable printId con solicitudes de Target.

**18 de julio de 2019: Versión 4.18.6**

* Adobe Target: Todas las solicitudes ahora incluyen al cliente y `sessionId` en los parámetros de consulta de URL.
* Adobe Target: Se ha corregido una fuga de memoria.
* Servicio de ID de visitante: Las API `visitorAppendToURL` y `visitorGetUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**June 5, 2019: Version 4.18.5**

* Analytics: anexe el estado de la opción de inclusión push a los datos del ciclo vital cuando las notificaciones push estén habilitadas.

**24 de mayo de 2019: Versión 4.18.4**

* Servicio de ID de visitante: se ha aumentado el tiempo de espera de retorno para el
   `visitorGetUrlVariablesAsync` API a 30 segundos.

* Servicio de ID de visitante: la llamada de `setPushIdentifier` API ahora envía una llamada de sincronización al servicio de ID de visitante cada vez que se llama a él.

Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
