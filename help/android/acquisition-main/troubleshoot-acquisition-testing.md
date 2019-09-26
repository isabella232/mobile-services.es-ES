---
description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
keywords: android;library;mobile;sdk
seo-description: En este tema se proporciona información sobre cómo solucionar problemas que podría tener durante las pruebas de adquisición.
seo-title: Troubleshoot Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshoot Acquisition testing
topic: Desarrollador e implementación
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Troubleshoot Acquisition testing {#troubleshoot-acquisition-testing}

This topic provides information about how to troubleshoot issues you might face during Acquisition testing.

* Si no se especifica lo contrario, el archivo ADBMobileConfig.json debe colocarse en la `assets` carpeta.

   El nombre distingue entre mayúsculas y minúsculas, por lo que no utilice mayúsculas y minúsculas.

* Ensure that  is called from your main activity.`Config.setContext(this.getApplicationContext())`

   Para obtener más información, consulte Métodos [de configuración](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Asegúrese de que los permisos necesarios para el SDK de Mobile están presentes en el `AndroidManifest.xml` archivo:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si `referrerTimeout` se establece en 5 en el archivo ADMobileConfig.json, debe enviar la intención de instalación en un intervalo de tiempo de 5 segundos después de que la aplicación se haya instalado e iniciado por primera vez para ver la información del referente adjunta a la visita de instalación.

   Para la prueba manual, se recomienda aumentar el tiempo `referrerTimeout` a 10-15 segundos, de modo que disponga de tiempo suficiente para enviar la información del referente antes de que se procese la visita de instalación.

* Ejecute todos los pasos en [Prueba de adquisición](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) de vínculos de marketing y asegúrese de ejecutar primero el `adb shell` comando y, a continuación, lo siguiente:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para procesar correctamente la intención del referente, debe ejecutar estos dos comandos de forma independiente. De lo contrario, `adb` se omitirá dos veces la información del referente y los datos recibidos por el receptor de la emisión estarán incompletos.

