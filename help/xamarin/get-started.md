---
description: En este tema se describe cómo empezar a utilizar los componentes Xamarin para el SDK de soluciones móviles 4.x.
keywords: Xamarin
seo-description: En este tema se describe cómo empezar a utilizar los componentes Xamarin para el SDK de soluciones móviles 4.x.
seo-title: Componentes Xamarin para el SDK de soluciones Experience Cloud 4.x
solution: Marketing Cloud,Developer
title: Componentes Xamarin para el SDK de soluciones Experience Cloud 4.x
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

En este tema se describe cómo empezar a utilizar los componentes Xamarin para el SDK de soluciones móviles 4.x.

Last Updated: **January 10, 2019**

## Primeros pasos {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>El SDK de Adobe Mobile ya no está disponible en la Tienda de componentes Xamarin ni en la Galería NuGet. Para descargar los componentes de Xamarin, vaya a [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importe el componente ADBMobile a su proyecto Xamarin.Android:

1. Abra el proyecto Xamarin
1. Abra el cuadro de diálogo **[!UICONTROL Referencias]** y haga clic en la ficha Conjunto **** .Net.
1. Seleccione `ADBMobile.XamarinAndroidBinding.dll` en la carpeta **[!UICONTROL lib/Android]** .
1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.
1. Agregar permisos para:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Si utiliza la mensajería en la aplicación, agregue la siguiente actividad y receptor:

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
1. Abra el cuadro de diálogo **[!UICONTROL Referencias]** y haga clic en la ficha Conjunto **** .Net.
1. Seleccione `ADBMobile.XamarinIOSBinding.dll` en la carpeta **[!UICONTROL lib/ios-Unified]** .
1. Añada el `ADBMobileConfig.json` archivo al proyecto.
