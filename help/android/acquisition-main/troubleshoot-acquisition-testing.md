---
description: En este tema se proporciona información sobre cómo solucionar problemas que podrían ocurrir durante las pruebas de adquisición.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud Services,Analytics
title: Resolución de problemas de pruebas de adquisición
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# Resolución de problemas de pruebas de adquisición {#troubleshoot-acquisition-testing}

En este tema se proporciona información sobre cómo solucionar problemas que podrían ocurrir durante las pruebas de adquisición.

* Si no se especifica lo contrario, el archivo ADBMobileConfig.json debe colocarse en la carpeta `assets`.

   El nombre distingue entre mayúsculas y minúsculas, por lo que no utilice mayúsculas y minúsculas.

* Asegúrese de que `Config.setContext(this.getApplicationContext())` se llama desde la actividad principal.

   Para obtener más información, consulte [Métodos de configuración](../configuration/methods.md).

* Compruebe que los permisos necesarios para el SDK de Mobile se encuentran en el archivo `AndroidManifest.xml`:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Si `referrerTimeout` se establece en 5 en el archivo ADMobileConfig.json, debe enviar la llamada de instalación en un intervalo de tiempo de 5 segundos después de que la aplicación se haya instalado e iniciado por primera vez para ver la información del remitente adjunta a la visita de instalación.

   Para la prueba manual, se recomienda aumentar el tiempo de `referrerTimeout` a 10-15 segundos, de modo que disponga de tiempo suficiente para enviar la información del remitente antes de que se procese la visita de instalación.

* Ejecute todos los pasos en [Prueba de adquisición de vínculos de marketing](t-testing-marketing-link-acquisition.md) y asegúrese de ejecutar primero el comando `adb shell` y, a continuación, lo siguiente:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Para procesar correctamente la intención del remitente, debe ejecutar estos dos comandos de forma independiente. De lo contrario, `adb` omitirá dos veces la información del remitente y los datos recibidos por el receptor de la emisión estarán incompletos.
