---
description: Notas de la versión y problemas conocidos de los SDK para iOS 4.x para soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos de los SDK para iOS 4.x para soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Marketing Cloud,Analytics
title: Notas de la versión
topic: Desarrollador e implementación
uuid: e 1613 dc 5-02 a 4-43 a 7-997 a -29 b 4 de 98 b 4 d 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# Notas de la versión {#release-notes}

Estas son las notas de la versión, los problemas conocidos y la información de corrección rápida para los SDK para iOS 4. x para Soluciones de Experience Cloud:

**2 de agosto de 2019: Versión 4.18.7**

* Se ha revertido un cambio introducido en la versión 4.18.6 que, en algunos entornos, provocaba un bloqueo en dispositivos que ejecutaban una versión de iOS anterior a la 11.0.

* Adobe Target: Se ha agregado `requestLocationParameters` la propiedad in `ADBTargetRequestObject`, que permite que el imsionid se envíe con solicitudes de Target.

**18 de julio de 2019: Versión 4.18.6**

* Adobe Target: Todas las solicitudes ahora incluyen al cliente y `sessionId` en los parámetros de consulta de URL.
* Adobe Target: Se ha corregido una fuga de memoria.
* Servicio de ID de visitante: Las API `visitorAppendToURL` y `visitorGetUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**5 de junio de 2019: Versión 4.18.5**

* Analytics: Anexe el estado de inclusión push a los datos del ciclo vital cuando se habilitan las notificaciones push.

**24 de mayo de 2019: Versión 4.18.4**

* Servicio de ID de visitante: se ha aumentado el tiempo de espera de retorno para el
   `visitorGetUrlVariablesAsync` API a 30 segundos.

* Servicio de ID de visitante: ahora, la llamada `setPushIdentifier` de API envía una llamada de sincronización al servicio de ID de visitante cada vez que se llama.

Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
