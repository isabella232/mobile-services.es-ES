---
description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila y envía automáticamente los datos de adquisición a Adobe Mobile Services.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila y envía automáticamente los datos de adquisición a Adobe Mobile Services.
seo-title: Adquisición de aplicación móvil
solution: Experience Cloud,Analytics
title: Adquisición de aplicación móvil
topic-fix: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
exl-id: 266f0266-38f5-410b-ae14-92874fb0e7ce
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 100%

---

# Adquisición de aplicación móvil {#mobile-app-acquisition}

Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila y envía automáticamente los datos de adquisición a Adobe Mobile Services.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Para usar Acquisition, **debe** tener SDK versión 4.1 o posterior.

Los vínculos de Acquisition deben crearse en Adobe Mobile Services. Para obtener más información, consulte [Adquisición](/help/using/acquisition-main/acquisition-main.md).

**En las versiones 4.18.0 y posteriores del SDK**:

A partir del 1 de marzo de 2020, Google dejará de utilizar el mecanismo de difusión por intención install_referrer. Para obtener más información, consulte [¿Todavía utiliza InstallBroadcast? Cambie a la API de Play Referrer antes del 1 de marzo de 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html). Para seguir recopilando información del referente de instalación de la tienda Google Play, actualice la aplicación para que utilice la versión 4.18.0 o posterior del SDK.

Cuando desaparezca, en lugar de crear un `BroadcastReceiver`, deberá recopilar la URL del referente de instalación de una nueva API de Google y pasar la URL resultante al SDK.

1. Agregue el paquete del referente de instalación de Google Play a las dependencias del archivo de gradle:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Para recuperar la dirección URL del referente desde la API de instalación del referente, siga los pasos en [Obtención del referente de instalación](https://developer.android.com/google/play/installreferrer/library#install-referrer).

1. Pase la URL del referente al SDK:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Para evitar llamadas de API innecesarias en la aplicación, Google recomienda que solo invoque la API una vez inmediatamente después de la instalación.

Para decidir la mejor manera de utilizar las API del referente de instalación de Google Play en la aplicación, consulte la documentación de Google. A continuación se muestra un ejemplo de cómo utilizar el SDK de Adobe con las API de referente de instalación de Google Play:

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**En las versiones 4.13.1 y posteriores del SDK**:

Si no puede utilizar los vínculos de adquisición creados en Adobe Mobile Services, el SDK puede recopilar y enviar igualmente los datos de adquisición utilizando Google Play Acquisition.

Para recopilar datos de adquisición de una campaña estándar de Google Play Acquisition:

* Utilice el método de adquisición estándar de Google Play Store.

   Se pueden utilizar datos de adquisición personalizados con los pares de valor clave estándar de Google Play Acquisition.

* Cuando el usuario descarga y ejecuta una aplicación como resultado de una adquisición en Google Play Store, los datos del referente se recopilan y envían a Adobe Mobile Services.

   * Los datos se almacenan y quedan disponibles en la instancia de `AdobeDataCallback` registrada anteriormente en el SDK.

      Para obtener más información, consulte [Métodos de configuración](/help/android/configuration/methods.md).

   * Se utilizan los tipos de evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

   * A las claves personalizadas que eran parte de los datos de adquisición de Google Play se les agregará &quot; `a.acquisition.custom.`&quot;

Si está utilizando los vínculos de adquisición creados en Adobe Mobile Services, agregue datos personalizados al vínculo de adquisición realizando las siguientes tareas:

1. Agregue a una variable de adquisición el prefijo &quot; `adb`&quot;.

   Cuando el SDK recibe los datos de adquisición de Adobe Mobile Services la primera vez que se inicia, los datos se almacenan y están disponibles en la instancia `AdobeDataCallback` registrada anteriormente con el SDK. Para obtener más información, consulte [Métodos de configuración](/help/android/configuration/methods.md).

1. Se utilizan los tipos de evento `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` o `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH`.

1. A las claves de los datos personalizados se les agregará el prefijo “`a.acquisition.custom.`”

>[!TIP]
>
>Si está enviando datos a varios grupos de informes, utilice los datos de adquisición de la aplicación asociada al primer grupo en su lista de ID de grupos de informes.

Las actualizaciones en esta sección permiten al SDK enviar datos de adquisición desde un vínculo de adquisición.

## Seguimiento de adquisición móvil {#section_CEA30C652AC8470784B8054E299B80FA}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implemente `BroadcastReceiver` para el referente:

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. Actualice `AndroidManifest.xml` para habilitar el `BroadcastReceiver` que se creó en el paso anterior:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. Compruebe que el archivo `ADBMobileConfig.json` contiene la configuración de adquisición necesaria:

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >Si está enviando datos a varios grupos de informes, utilice la configuración de adquisición (servidor de adquisición y appid) de la aplicación asociada al primer grupo en su lista de ID de grupos de informes.

   La configuración de `acquisition` la genera Adobe Mobile Services y no debería cambiarse. Para obtener más información sobre cómo descargar un archivo `ADBMobileConfig.json` personalizado con los ajustes de `acquisition` preconfigurados, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

Una vez habilitada esta configuración y después del primer inicio de la aplicación, los datos de adquisición se envían automáticamente con la llamada inicial del ciclo vital.

>[!CAUTION]
>
>`referrerTimeout` debe estar establecido en un valor mayor que 0 para habilitar la adquisición de aplicación.
