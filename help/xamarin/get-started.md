---
description: Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.
keywords: Xamarin
seo-description: Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.
seo-title: Xamarin components for Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud,Desarrollador
title: Componentes Xamarin para el SDK de soluciones de Experience Cloud 4.x
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.

Última actualización:**10 de enero de 2019**

## Primeros pasos {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>El SDK de Adobe Mobile ya no está disponible en la Tienda de componentes Xamarin ni en la Galería NuGet. Para descargar los componentes de Xamarin, vaya a [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe el componente ADBMobile a su proyecto Xamarin.Android:

1. Abra el proyecto Xamarin

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Select  from the lib/Android folder.`ADBMobile.XamarinAndroidBinding.dll`****

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Agregar permisos para:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. If you are using In-app messaging, add the following activity and receiver :

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Si está utilizando adquisición, agregue el siguiente receptor:

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importe el componente ADBMobile a su proyecto Xamarin.iOS:

1. Abra el proyecto Xamarin.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Seleccione `ADBMobile.XamarinIOSBinding.dll` en la carpeta **[!UICONTROL lib/ios-Unified]** .

1. Añada el archivo `ADBMobileConfig.json` al proyecto.


