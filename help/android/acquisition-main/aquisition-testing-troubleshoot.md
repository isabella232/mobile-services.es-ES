---
description: La siguiente información le ayuda a solucionar los problemas de las pruebas de adquisición.
keywords: android;Acquisition;testing
seo-description: La siguiente información le ayuda a solucionar los problemas de las pruebas de adquisición.
seo-title: Resolución de problemas de pruebas de adquisición
solution: Experience Cloud,Analytics
title: Resolución de problemas de pruebas de adquisición
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---


# Resolución de problemas de pruebas de adquisición {#aquistion-testing-troubleshooting}

Estos son algunos de los problemas que podría tener al probar la adquisición y algunas posibles soluciones:

* Si no se especifica lo contrario, el archivo ADBMobileConfig.json debe colocarse en la carpeta de recursos.

* El nombre distingue entre mayúsculas y minúsculas, por lo que no proporcione un nombre en letras minúsculas.

   Debe asegurarse de que se llame a `Config.setContext(this.getApplicationContext())` desde la actividad principal. Para obtener más información, consulte [Métodos de configuración](https://docs.adobe.com/content/help/es-ES/mobile-services/android/configuration-android/methods.html).

* Faltan algunos permisos de usuario en el archivo AndroidManifest.xml proporcionado; estos permisos son necesarios para enviar datos y registrar llamadas de seguimiento sin conexión:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* En la configuración, si el tiempo de espera del remitente está establecido en `referrerTimeout: 5`, significa que debe enviar la intención de instalación en un intervalo de tiempo de 5 segundos después de que la aplicación se haya instalado e iniciado por primera vez para ver la información del referente adjunta a la visita de instalación.

   Para las pruebas manuales, aumente el tiempo de `referrerTimeout` a 10-15 segundos, de modo que haya tiempo suficiente para enviar la información del remitente antes de que se procese la visita de instalación.

* Es importante ejecutar todos los pasos en [Prueba de adquisición de vínculo de marketing](https://docs.adobe.com/content/help/es-ES/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) en orden y asegurarse de ejecutar `adb` Shell y, a continuación, lo siguiente:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Debe ejecutar estos dos comandos de forma independiente para procesar la intención del remitente. De lo contrario, `adb` omitirá dos veces la información del remitente y los datos recibidos por el receptor de la emisión estarán incompletos.
