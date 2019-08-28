---
description: Este complemento le permite enviar llamadas de AppMeasurement de Android desde el proyecto de PhoneGap.
keywords: android; library; mobile; sdk
seo-description: Este complemento le permite enviar llamadas de AppMeasurement de Android desde el proyecto de PhoneGap.
seo-title: Descripción general del complemento phonegap
solution: Marketing Cloud, Analytics
title: Descripción general del complemento phonegap
topic: Desarrollador e implementación
uuid: c 5 c 32357-d 8 df -458 a-b 0 e 8-e 0 c 56040241 d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Descripción general del complemento phonegap {#phonegap-plug-in}

Este complemento le permite enviar llamadas de AppMeasurement de Android desde el proyecto de PhoneGap. To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nueva versión del SDK de Adobe Experience Cloud

¿Busca información y documentación relacionada con el SDK Mobile de la Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para consultar los documentos más recientes.

>[!IMPORTANT]
>
>En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK Mobile de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Para empezar, vaya a [Launch](https://launch.adobe.com/).
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Instalación del complemento utilizando npm {#section_43229E57C16944C0B51531CB92089189}

Ejecute el siguiente comando:

```java
cordova plugin add adobe-mobile-services
```

## Instalación manual del complemento {#section_EA1FD59C484D44878AB509954DEE6037}

## Incluir el complemento

1. Arrastre `ADBMobile_PhoneGap.java` el archivo a `src` su carpeta.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. Arrastre `ADB_Helper.js` el archivo a la carpeta que contiene `index.html` el archivo

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Por ejemplo, si su paquete se llama `com.example.phonegaptest`, el valor `android-package` sería el siguiente:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Incluir la biblioteca appmeasurement

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. Arrastre el `adobeMobileLibrary.jar` archivo a su `src` carpeta.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. En función de los requisitos de su proyecto, introduzca el nombre, nivel y ubicación de la biblioteca.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. Confirme que ha seleccionado la raíz de la aplicación y **no** una aplicación dentro de una aplicación.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

## Agregar permisos de aplicación

La biblioteca AppMeasurement requiere los siguientes permisos para enviar datos y registrar llamadas de seguimiento sin conexión:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para agregar estos permisos, agregue las siguientes líneas al archivo `AndroidManifest.xml`, que se encuentra en el directorio del proyecto de la aplicación:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Para habilitar la mensajería en la aplicación:

Actualice AndroidManifest.xml para declarar la actividad de pantalla completa y habilitar el controlador de notificación de mensajes:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Si selecciona el diseño modal al crear un mensaje en Adobe Mobile Services, elija uno de los temas siguientes:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Por ejemplo:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

