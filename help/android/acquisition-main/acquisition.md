---
description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
keywords: android; library; mobile; sdk
seo-description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
seo-title: Adquisición de aplicación móvil
solution: Marketing Cloud, Analytics
title: Adquisición de aplicación móvil
topic: Desarrollador e implementación
uuid: 4 d 32 eae 9-e 856-4 e 40-8 a 29-2 b 5 bccd 106 e 0
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile app acquisition {#mobile-app-acquisition}

Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde la tienda de aplicaciones después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Para obtener más información, consulte [Adobe Analytics: Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using Acquisition and Marketing Links with the Experience Cloud SDKs, see [Acquisition and Marketing Links](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#acquisition-and-marketing-links).

>[!IMPORTANT]
>
>Para utilizar Acquisition **necesita** la versión 4.1 o posterior del SDK.

Los vínculos de Acquisition se deben crear en Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**En las versiones 4.13.1 y posteriores del SDK**:

Si no puede utilizar los vínculos de adquisición creados en Adobe Mobile Services, el SDK puede recopilar y enviar igualmente los datos de adquisición utilizando Google Play Acquisition.

Para recopilar datos de adquisición de una campaña estándar de Google Play Acquisition:

* Utilice el método de adquisición estándar de Google Play Store.

   Se pueden utilizar datos de adquisición personalizados con los pares de valor clave estándar de Google Play Acquisition.

* Cuando el usuario descarga y ejecuta una aplicación como resultado de una adquisición en Google Play Store, los datos del referente se recopilan y envían a Adobe Mobile Services.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      Para obtener más información, consulte [Métodos de configuración](/help/android/configuration/methods.md).

   * Se utiliza el `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` tipo `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` de evento o de evento.

   * A las claves personalizadas que eran parte de los datos de adquisición de Google Play se les agregará " `a.acquisition.custom.`"

Si está utilizando los vínculos de adquisición creados en Adobe Mobile Services, agregue datos personalizados al vínculo de adquisición realizando las siguientes tareas:

1. Agregue a una variable de adquisición el prefijo " `adb`".

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. Se utilizará el `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` tipo `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` de evento.

1. Las claves de datos personalizadas llevan el prefijo "`a.acquisition.custom.`

>[!TIP]
>
>Si envía datos a varios grupos de informes, utilice los datos de adquisición de la aplicación asociada con el primer grupo de informes de su lista de ID de grupos de informes.

Las actualizaciones en esta sección permiten al SDK enviar datos de adquisición desde un vínculo de adquisición.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Agregue la biblioteca [al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto intellij IDEA o Eclipse* en [implementación y ciclo vital de Core](/help/android/getting-started/dev-qs.md).

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

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

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
   >Si envía datos a varios grupos de informes, utilice la configuración de adquisición (servidor de adquisición y appid) de la aplicación asociada al primer grupo de informes de su lista de ID de grupos de informes.

   `acquisition` La configuración los genera Adobe Mobile Services y no debe cambiarse. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Una vez habilitada esta configuración y después del primer inicio de la aplicación, los datos de adquisición se envían automáticamente con la llamada inicial del ciclo vital.

>[!CAUTION]
>
>`referrerTimeout` debe establecerse en un valor superior a 0 para habilitar la adquisición de aplicación.
