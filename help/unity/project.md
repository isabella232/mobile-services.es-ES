---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Creación de un proyecto
solution: Marketing Cloud,Developer
title: Creación de un proyecto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# Building your project{#building-your-project}

## iOS

Al compilar para iOS, se crea un proyecto Xcode. De forma predeterminada, aparecerán los archivos `ADBMobileWrapper.mm` y `AdobeMobileLibrary.a` en el grupo de Bibliotecas del nuevo proyecto. Lleve a cabo los siguientes pasos manuales requeridos para compilar la aplicación:

1. Añada el archivo `ADBMobileConfig.json` al proyecto.

   Asegúrese de que los objetivos necesarios sean parte de la compilación.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
(Es posible que esta biblioteca ya esté vinculada).

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

Si utiliza la mensajería en la aplicación, agregue la actividad y el receptor siguientes:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
