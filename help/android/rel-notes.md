---
description: Notas de la versión y problemas conocidos del SDK para Android 4.x para soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos del SDK para Android 4.x para soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Marketing Cloud,Analytics
title: Notas de la versión
topic: Desarrollador e implementación
uuid: 16 bb 4 de 8-a 216-47 a 8-928 c -0 b 1 e 1421 adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# Notas de la versión {#release-notes}

Estas son las notas de la versión, los problemas conocidos y la información de corrección rápida para Android SDK 4. x para Soluciones de Experience Cloud:

**2 de agosto de 2019: Versión 4.17.9**

* Servicio de ID de visitante: Se corrigió la `StrictMode` infracción al llamar a syncidentifiers.

   Esta infracción se producía al leer las preferencias compartidas en el subproceso principal.

* Adobe Target: Se ha agregado `requestLocationParameters` el atributo en `TargetRequestObject`, que permite que el imsionid se envíe con solicitudes de Target.

**18 de julio de 2019: Versión 4.17.8**

* Adobe Target: Todas las solicitudes ahora incluyen el cliente y el sessionid en los parámetros de consulta de URL.
* Mensajería en la aplicación: Se ha corregido un problema por el que, cuando un mensaje se activaba con una URL de pulsaciones vacías, las aplicaciones de Android se bloqueaban.
* Servicio de ID de visitante: Las API `Visitor.appendToURL` y `Visitor.getUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**6 de junio de 2019: Versión 4.17.7**

* General: Las llamadas de red a niveles de API de Android inferiores a 20 utilizarán ahora TLS 1.1 o TLS 1.2.
* Analytics: el estado de inclusión push adjunta a los datos del ciclo vital cuando se habilitan las notificaciones push.

**24 de mayo de 2019: Versión 4.17.6**

* servicio de ID de visitante - El
   `setPushIdentifier` llamada de API ahora envía una
llamada de sincronización al servicio de ID de visitante cada vez que se llama.

* Servicio de ID de visitante: se ha aumentado la conexión de conexión y lectura
de 2 segundos a 5 segundos.


Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
