---
description: Este tema proporciona información sobre cómo solucionar problemas que podría presentarse durante las pruebas de adquisición.
keywords: android; library; mobile; sdk
seo-description: Este tema proporciona información sobre cómo solucionar problemas que podría presentarse durante las pruebas de adquisición.
seo-title: Resolución de problemas de adquisición de adquisición
solution: Marketing Cloud, Analytics
title: Resolución de problemas de adquisición de adquisición
topic: Desarrollador e implementación
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Resolución de problemas de adquisición de adquisición {#troubleshoot-acquisition-testing}

Este tema proporciona información sobre cómo solucionar problemas que podría presentarse durante las pruebas de adquisición.

* Si no se especifica lo contrario, el archivo adbmobileconfig. json debe colocarse en `assets` la carpeta.

   El nombre distingue entre mayúsculas y minúsculas, por lo que no utilice letras mayúsculas ni minúsculas.

* Asegúrese `Config.setContext(this.getApplicationContext())` de que se llama desde la actividad principal.

   Para obtener más información, consulte [Métodos de configuración](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Asegúrese de que los permisos necesarios para el SDK de Mobile están presentes en `AndroidManifest.xml` el archivo:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si se `referrerTimeout` establece como 5 en el archivo admobileconfig. json, debe enviar la calidad de instalación en un intervalo de tiempo de 5 segundos después de que la aplicación se instaló e inicie por primera vez para ver la información del referente anexada a la visita de instalación.

   Para realizar pruebas manuales, recomendamos que aumente `referrerTimeout` a 10 a 15 segundos, de modo que tenga tiempo suficiente para enviar la información del referente antes de que se procese la visita de instalación.

* Ejecute todos los pasos en [la adquisición de Comprobación de vínculos de marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) y asegúrese de ejecutar primero `adb shell` el comando y, a continuación, lo siguiente:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para procesar correctamente la calidad del referente, debe ejecutar estos dos comandos de forma independiente. De lo contrario `adb` , se ocultará la información del referente y los datos recibidos por el receptor de emisión estarán incompletos.

