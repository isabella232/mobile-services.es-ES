---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Creación de un proyecto
solution: Experience Cloud
title: Creación de un proyecto
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# Creación de un proyecto{#building-your-project}

## iOS

Al compilar para iOS, se crea un proyecto Xcode. De forma predeterminada, los archivos `ADBMobileWrapper.mm` y `AdobeMobileLibrary.a` estarán en el grupo Bibliotecas del nuevo proyecto. Siga los pasos manuales siguientes para crear la aplicación:

1. Añada el archivo `ADBMobileConfig.json` al proyecto.

   Asegúrese de que es miembro de la compilación y de los destinatarios necesarios.

1. En la ficha Fases **[!UICONTROL de]** compilación del proyecto, agregue un vínculo a las bibliotecas siguientes:

   * `SystemConfiguration.framework`
(Es posible que esta biblioteca ya esté vinculada).

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Para utilizar los mensajes en la aplicación de notificaciones locales del SDK, debe llamar desde el método `ADBMobile.EnableLocalNotifications();` de Inicio en la primera escena de Unity.

## Android

Al compilar para Android, el `apk` archivo ya incluye el `ADBMobileConfig.json` archivo en la ubicación correcta. De forma predeterminada, también se utiliza el `AndroidManifest.xml` archivo de la `/Plugins/Android` carpeta.

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
