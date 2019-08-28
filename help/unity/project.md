---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Creación de su proyecto
solution: Marketing Cloud, Desarrollador
title: Creación de su proyecto
uuid: 5550 a 394-6 f 3 f -4 b 87-b 840-89621 d 8 a 0 c 1 e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

Al compilar para iOS, se crea un proyecto Xcode. De forma predeterminada, aparecerán los archivos `ADBMobileWrapper.mm` y `AdobeMobileLibrary.a` en el grupo de Bibliotecas del nuevo proyecto. Lleve a cabo los siguientes pasos manuales requeridos para compilar la aplicación:

1. Añada el archivo `ADBMobileConfig.json` al proyecto.

   Asegúrese de que los objetivos necesarios sean parte de la compilación.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`(Esta biblioteca puede estar vinculada).

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Al compilar para Android, el archivo `apk` ya incluye el archivo `ADBMobileConfig.json` en la ubicación correcta. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

Si tiene que utilizar su propio archivo de manifiesto personalizado, deberá añadir los siguientes cambios.

Agregar permisos para:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Si utiliza mensajería en la aplicación, agregue la siguiente actividad y receptor:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

Si está utilizando adquisición, agregue el siguiente receptor:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
