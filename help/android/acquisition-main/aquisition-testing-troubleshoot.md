---
description: La siguiente información ayuda a solucionar problemas de prueba de adquisición.
keywords: android; Adquisición; prueba
seo-description: La siguiente información ayuda a solucionar problemas de prueba de adquisición.
seo-title: Resolución de problemas de las pruebas de adquisición
solution: Marketing Cloud, Analytics
title: Resolución de problemas de las pruebas de adquisición
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Resolución de problemas de las pruebas de adquisición {#aquistion-testing-troubleshooting}

A continuación se indican algunos problemas que podría afrontar al probar Adquisición y algunas posibles soluciones:

* Si no se especifica lo contrario, el archivo adbmobileconfig. json debe colocarse en la carpeta assets.

* El nombre distingue entre mayúsculas y minúsculas, por lo que no debe proporcionar un nombre en letras minúsculas.

   Debe asegurarse de que se llama `Config.setContext(this.getApplicationContext())` desde la actividad principal. Para obtener más información, consulte [Métodos de configuración](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* En el archivo AndroidManifest.xml proporcionado faltan algunos permisos de usuario, estos son necesarios para enviar datos y registrar llamadas de seguimiento sin conexión:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* En la configuración, si el tiempo de espera del referente está establecido, `referrerTimeout: 5`es necesario enviar la calidad de instalación en un intervalo de tiempo de 5 segundos después de que la aplicación se instale e inicie por primera vez para ver la información del referente anexada a la visita de instalación.

   Para realizar pruebas manuales, aumente `referrerTimeout` a 10 a 15 segundos, de modo que haya suficiente tiempo para enviar la información del referente antes de que se procese la visita de instalación.

* Es importante ejecutar todos los pasos en [Comprobación de la adquisición de Vínculo de marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) en orden y asegurarse de ejecutar `adb` el shell y, a continuación, lo siguiente:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Debe ejecutar estos dos comandos de forma independiente para procesar correctamente la calidad del referente. De lo contrario `adb` , duplica la información del referente y los datos recibidos por el receptor de emisión estarán incompletos.
