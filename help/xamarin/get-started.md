---
description: Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.
keywords: Xamarin
seo-description: Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.
seo-title: Componentes Xamarin para SDK 4. x de Experience Cloud
solution: Marketing Cloud, Desarrollador
title: Componentes Xamarin para SDK 4. x de Experience Cloud
uuid: e 7 a 48107-bd 0 e -47 d 6-b 49 c-dfdae 189 ac 37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

Este tema describe cómo empezar a utilizar el SDK de los componentes Xamarin para soluciones de Mobile 4.x.

Última actualización:**10 de enero de 2019**

## Primeros pasos {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>El SDK de Adobe Mobile ya no está disponible en la tienda de componentes Xamarin ni en la galería nuget. Para descargar los componentes de Xamarin, vaya a [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe el componente adbmobile al proyecto Xamarin. Android:

1. Abra el proyecto Xamarin

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Seleccione `ADBMobile.XamarinAndroidBinding.dll` una de las carpetas **[!UICONTROL lib/Android]** .

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Agregar permisos para:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Si utiliza mensajería en la aplicación, agregue la siguiente actividad y receptor:

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

Importe el componente adbmobile al proyecto Xamarin. iOS:

1. Abra el proyecto Xamarin.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Seleccione `ADBMobile.XamarinIOSBinding.dll` entre la carpeta **[!UICONTROL lib/ios-unified]** .

1. Añada el archivo `ADBMobileConfig.json` al proyecto.


