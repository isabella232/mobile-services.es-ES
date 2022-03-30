---
description: Creación de proyectos de iOS
keywords: Unity
solution: Experience Cloud Services
title: Creación de un proyecto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Creación de un proyecto{#building-your-project}

## iOS

Al compilar para iOS, se crea un proyecto Xcode. De forma predeterminada, la variable `ADBMobileWrapper.mm` y  `AdobeMobileLibrary.a` estarán en el grupo Bibliotecas del nuevo proyecto. Siga los siguientes pasos manuales necesarios para crear la aplicación:

1. Añada el archivo `ADBMobileConfig.json` al proyecto.

   Asegúrese de que es miembro de la compilación y de los objetivos necesarios.

1. En el **[!UICONTROL Fases de compilación]** del proyecto, agregue un vínculo a las bibliotecas siguientes:

   * `SystemConfiguration.framework`
(Es posible que esta biblioteca ya esté vinculada).

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Para utilizar mensajes en la aplicación de notificaciones locales del SDK, debe llamar a `ADBMobile.EnableLocalNotifications();` del método Start en la primera escena Unity.

## Android

Cuando crea para Android, la variable `apk` el archivo ya incluye la variable `ADBMobileConfig.json` en la ubicación correcta. De forma predeterminada, la variable `AndroidManifest.xml` en su `/Plugins/Android` también se utiliza.

Si necesita utilizar su propio archivo de manifiesto personalizado, se deben agregar los siguientes cambios.

Agregar permisos para:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Si utiliza la mensajería en la aplicación, agregue la siguiente actividad y receptor:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
