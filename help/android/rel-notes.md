---
description: Notas de la versión y problemas conocidos del SDK para Android 4.x para soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos del SDK para Android 4.x para soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Marketing Cloud,Analytics
title: Notas de la versión
topic: Desarrollador e implementación
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Notas de la versión {#release-notes}

Here is the release notes, known issues, and hot fix information for Android SDK 4.x for Experience Cloud Solutions:

**September 20, 2019: Version 4.17.10**

* General: Fixed locale string generation for some regions on Android API level 21 or newer.

**18 de julio de 2019: Versión 4.17.8**

* Adobe Target: All requests now include the client and the sessionId in the URL query parameters.
* Mensajería en la aplicación: Se ha corregido un problema por el que, cuando un mensaje se activaba con una URL de pulsaciones vacías, las aplicaciones de Android se bloqueaban.
* Servicio de ID de visitante: Las API `Visitor.appendToURL` y `Visitor.getUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**6 de junio de 2019: Versión 4.17.7**

* General: Las llamadas de red en niveles de API de Android inferiores a 20 ahora utilizarán TLS 1.1 o TLS 1.2.
* Analytics: estado de la opción de inclusión push anexada a los datos del ciclo vital cuando las notificaciones push están habilitadas.

**May 24, 2019: Version 4.17.6**

* servicio de ID de visitante: La variable
   `setPushIdentifier` La llamada de API ahora envía una llamada asincrónica al servicio de ID de visitante cada vez que se llama a él.

* Servicio de ID de visitante: se ha aumentado el tiempo de espera de conexión y lectura de 2 a 5 segundos.


Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
