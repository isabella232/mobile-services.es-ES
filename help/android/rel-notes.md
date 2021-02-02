---
description: Notas de la versión y problemas conocidos de SDK 4.x para Android en soluciones de Experience Cloud.
seo-description: Notas de la versión y problemas conocidos de SDK 4.x para Android en soluciones de Experience Cloud.
seo-title: Notas de la versión
solution: Experience Cloud,Analytics
title: Notas de la versión
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 8b5842068c602f3f9b1c020c1c9a686eb0e56b74
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Notas de la versión {#release-notes}

Estas son las notas de la versión, los problemas conocidos y la información de correcciones urgentes del SDK 4.x de Android para las soluciones de Experience Cloud:

**3 de abril de 2020: 4.18.2**

* Mensajería en la aplicación: por motivos de seguridad, WebViews creada por el SDK ahora establece la propiedad &#39;setAllowFileAccess&#39; como false.

**12 de marzo de 2020: 4.18.1**

* Target: el ID de sesión de Target ahora se agregará como parámetro de datos de contexto “a.target.sessionId” en la visita interna de Analytics para Target enviada a Adobe Analytics.

**16 de enero de 2020: 4.18.0**

* Adquisición: Se ha agregado una nueva API, `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, para admitir las API de referente de instalación de Google Play.

   Para obtener más información sobre la instalación de las API de referente, consulte [¿Sigue usando InstallBroadcast? Cambie a la API de Play Referrer antes del 1 de marzo de 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html).

**20 de septiembre de 2019: Versión 4.17.10**

* General: Se corrigió la generación de cadenas de configuración regional en algunas regiones del nivel 21 o posterior de la API de Android.

**18 de julio de 2019: Versión 4.17.8**

* Adobe Target: Todas las solicitudes ahora incluyen al cliente y el sessionId en los parámetros de consulta de URL.
* Mensajería en la aplicación: Se ha corregido un problema por el que, cuando un mensaje se activaba con una URL de pulsaciones vacías, las aplicaciones de Android se bloqueaban.
* Servicio de ID de visitante: Las API `Visitor.appendToURL` y `Visitor.getUrlVariablesAsync` ya no codifican dos veces sus valores devueltos.

   La doble codificación provocaba que los valores devueltos de esas API se marcaran con indicadores de ciertas revisiones de seguridad.

**6 de junio de 2019: Versión 4.17.7**

* General: Las llamadas de red en niveles de API de Android inferiores a 20 ahora utilizarán TLS 1.1 o TLS 1.2.
* Analytics: Se anexa el estado de la opción de inclusión push a los datos del ciclo vital cuando las notificaciones push estén habilitadas.

**24 de mayo de 2019: Versión 4.17.6**

* Servicio de ID de visitante:
   La llamada de API `setPushIdentifier` ahora envía una llamada de sincronización al servicio de ID de visitante cada vez que se realiza la llamada.

* Servicio de ID de visitante: se ha aumentado el tiempo de espera de conexión y lectura de 2 a 5 segundos.


Para obtener más información sobre las notas de la versión actuales y anteriores de todas las soluciones, consulte [Notas de la versión de Adobe Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html).
